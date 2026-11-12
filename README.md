# CHARLS 数据导入与合并脚本
#1. 加载必要的 R 包
library(haven)   # 用于读取 Stata 的 .dta 格式文件
library(dplyr)   # 用于数据清洗与左连接合并
#2. 定义文件路径
path_harm  <- "D:/1222/2026.11/Charles/H_CHARLS_D_Data.dta"
path_blood <- "D:/1222/2026.11/Charles/Blood_20140429.dta"
#3. 导入数据
cat("正在导入 Harmonized CHARLS 数据...\n")
charls_harm <- read_dta(path_harm)
cat("Harmonized 数据导入成功！样本量:", nrow(charls_harm), "行 | 变量数:", ncol(charls_harm), "列\n\n")
cat("正在导入血检数据...\n")
charls_blood <- read_dta(path_blood)
cat("血检数据导入成功！样本量:", nrow(charls_blood), "行 | 变量数:", ncol(charls_blood), "列\n\n")
#4. 预览两张表的关键识别字段（ID）
cat("--- Harmonized 数据前 6 个变量名 ---\n")
print(head(names(charls_harm), 6))
cat("\n--- 血检数据前 6 个变量名 ---\n")
print(head(names(charls_blood), 6))
#5. 提示下一步：
#运行这段代码后，请看一下控制台打印出的两张表的 ID 变量叫什么名字
#通常 Harmonized 中的个人ID可能是 ID, IDNUM 或 pidid 等，
#确认后我们可以通过 charls_analytic <- left_join(charls_harm, charls_blood, by = "你的ID字段名") 完成合并！
