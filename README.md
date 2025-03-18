# Model-integration-based-on-Swin_Unetr
#### Model integration based on Swin_Unetr to solve precise segmentation of the target area for rectal cancer.
#### Dataset is from 靶区分割挑战赛 2025/3/17
#### Submitting institution: Sichuan University
#### main author：Hawkyu


# 基于Swin_Unetr集成的直肠癌靶区图像分割研究
## Introduction
  直肠癌的精准分割对于疾病的诊断、治疗规划以及预后分析具有重要意义。近年来，基于深度学习的医学图像分割方法取得了显著进展，特别是U-Net及其变体、基于残差网络的模型以及Transformer架构的应用。其中，Swin-UNETR（Shifted Window U-Net Transformer）作为一种结合Swin Transformer和U-Net编码-解码结构的分割网络，在医学图像分割任务中表现出较强的全局建模能力和局部特征提取能力。然而，单一模型在不同样本和不同病变类型上的泛化能力仍然存在局限。在本次任务中，我们主要引入了模型集成技术，通过融合多个具有不同敛散特性的神经网络，提升模型的鲁棒性和泛化能力。实验结果表明，相较于单个神经网络，集成模型在多个测试样本上的Dice系数均有显著提升。这一结果证明了模型集成技术在直肠癌靶向区域分割任务中的科学性和可行性，为计算机辅助诊断提供了更可靠的解决方案。
    模型集成技术（Model Ensemble Techniques）是机器学习和深度学习中常用的方法，旨在通过组合多个模型的预测结果来提升性能、降低误差，并提高泛化能力。根据集成方式不同，可分为加权平均，Bagging，Boosting，Stacking多种。针对直肠癌靶区图像分割任务，我们采用了投票方式，根据多个Swin_Unetr模型输出的mask掩码，在同一维度的不同Tensor张量取众数。得到集成模型的最终输出
  选择 Swin-UNETR 进行模型集成，主要是因为它结合了 Swin Transformer 的全局特征建模能力和 UNETR 的高效分割结构，相比传统 CNN（如 MutilUNet3D），能够更好地捕捉远程依赖并提升对复杂结构的识别能力。同时，Swin-UNETR 采用层次化特征提取，适用于 3D 医学图像分割，并在多个医学任务中取得良好效果
## Analysis
  我们采用了对直肠癌靶向区域图像数据集具有不同敛散程度的神经网络进行训练和测试。为了进一步提升模型的泛化能力和鲁棒性，我们引入了模型集成技术，通过融合多个单独训练的神经网络，综合各个模型的优势，从而增强整体的预测性能。实验结果表明，单个的Swin_Unetr在经过500轮以上的训练之后，在验证集上推理得到的dice系数平均为0.8809。而在五个Swin_Unetr模型集成之后，得到的集成模型，在同样的验证集上，平均dice系数为0.9153。证明了模型集成技术在直肠癌靶向区域图像数据集，具有良好的普适性和科学性。
![1742286998322](https://github.com/user-attachments/assets/a4759a52-1f91-45b8-bda2-2e8ed0008ea9)


