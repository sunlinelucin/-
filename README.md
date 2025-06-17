项目名称

大模型生成文本检测（二分类）

项目简介

本项目旨在区分人类撰写文本与大模型（如GPT-4o、Llama3等）生成文本。项目基于BERT预训练模型，采用迁移学习和深度学习方法，完成文本二分类任务。数据集为JSONL格式，包含训练集和测试集。

目录与文件说明
train.jsonl
训练数据集，JSONL格式，每行一个样本，包含text和label字段（0=人类，1=大模型）。

test.jsonl
测试数据集，JSONL格式，每行一个样本，仅包含text字段，无标签。

test.ipynb
Jupyter Notebook，包含数据加载、模型定义、训练、评估和预测的完整代码流程。适合交互式实验和调试。
best.pt
训练过程中保存的最佳模型参数文件（PyTorch格式），F1分数最高时自动保存。
submit.txt
测试集的预测结果文件，每行为一个样本的预测标签（0或1），可直接用于比赛或评测平台提交。
venv/
Python虚拟环境目录，包含项目依赖库（可选）。
运行环境
Python 3.8+
推荐使用Anaconda或venv虚拟环境
主要依赖库：
torch
transformers
scikit-learn
tqdm
numpy
安装依赖（如未安装）：
Apply to test.ipynb
Run
运行方法
1. 训练与预测（推荐在Jupyter Notebook中运行）
打开test.ipynb，按单元格顺序依次运行。
训练过程会自动加载train.jsonl，并在每个epoch后评估F1分数，保存最佳模型为best.pt。
训练完成后，Notebook会自动加载最佳模型，对test.jsonl进行预测，并将结果写入submit.txt。
2. 结果说明
训练过程中会在控制台输出每轮的损失和F1分数，便于观察模型收敛情况。
训练结束后，submit.txt文件中每一行对应测试集一条文本的预测标签（0=人类，1=大模型）。
best.pt为当前训练过程中F1分数最高的模型参数，可用于后续加载和推理。
文件作用总结
train.jsonl：训练数据
test.jsonl：测试数据
test.ipynb：主代码，包含数据处理、模型训练、评估和预测
best.pt：最佳模型参数
submit.txt：测试集预测结果
venv/：虚拟环境（可选）
注意事项
若首次运行，BERT模型会自动从HuggingFace下载，需保证网络畅通或提前下载至本地。
若内存有限，可在Notebook中调整批次大小（BATCH_SIZE）或只用部分数据进行调试。
预测结果仅供参考，实际效果与训练集规模、模型参数等有关。
