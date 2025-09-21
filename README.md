# EasyData 数据集转换与划分工具使用说明

本工具用于将 **百度飞桨 EasyData 平台导出的 COCO 数据集** 转换为 **YOLO 格式**，并按照指定比例划分为 `train/val/test` 三个子集，方便直接用于 YOLO 系列模型训练。

---
## 数据集格式说明
- **数据集标准格式.zip**  
  一个存放了百度飞桨 EasyData 平台COCO格式和YOLO标准格式的数据集样例文件，用于对照学习格式

## 📦 工具说明

- **cocotoyolo.exe**  
  功能：将 EasyData 导出的 **COCO 格式数据集** 转换为 **YOLO 格式标注**
  需要自行创建一个空文件夹labels
  输出：生成 `labels/` 文件夹，每张图片对应一个同名 `.txt` 标签文件  

- **huafen.exe**  
  功能：按照比例自动划分数据集  
  输出：需要自行创建一个最终划分好数据集的空文件夹，标准 YOLO 数据集目录结构，包括 `images/` 与 `labels/` 的 `train/val/test` 子集  

---

## ⚙️ 使用步骤

1. **准备数据**  
   - 将 EasyData 导出的数据集解压，确保包含图片和 `annotations.json` 文件  
   - 推荐将数据集目录重命名为英文（避免训练过程因中文路径报错）  

2. **运行 cocotoyolo.exe**  
   - 双击运行 `cocotoyolo.exe`  
   - 选择任务模式：`目标检测` 或 `实例分割`  
   - 手动创建一个 `labels/` 文件夹，并选择其路径作为输出目录  
   - 点击转换，生成 YOLO 格式的标签文件  

3. **运行 huafen.exe**  
   - 双击运行 `huafen.exe`  
   - 选择包含图片和标签的文件夹
   - 手动创建一个 `dataset_yolo` 文件夹
   - 自动按比例划分数据集，生成标准 YOLO 训练数据集目录：  
     ```
     dataset_yolo/
       images/train/*.jpg
       images/val/*.jpg
       images/test/*.jpg
       labels/train/*.txt
       labels/val/*.txt
       labels/test/*.txt
     ```

4. **检查结果**  
   - 确认 `labels/` 与 `images/` 文件夹一一对应  
   - 确认输出目录名为英文，避免训练脚本报错  

---

## 📂 最终目录结构示例
