# 跨交易所套利程序 — MVP

说明
- 本项目实现一个最小可行的两交易所跨所套利扫描与执行程序，基于 Python 与 ccxt。
- 支持两种模式：
  - paper: 只模拟决策，不实际下单
  - live: 使用交易所 API 下单（高风险，运行前务必理解代码并测试）

结构
- main.py: 程序入口，循环扫描并执行套利
- exchanges.py: 交易所封装（ccxt）
- arbitrage.py: 套利核心逻辑
- config_example.json: 配置示例
- requirements.txt: 依赖

安全提示
- 切勿把真实 API key 提交到公共仓库。
- 开始前在 sandbox 或使用极低金额进行测试。
- 注意订单撮合延迟、撤单失败和资金不足这类实际风险。

运行示例（模拟模式）
1. 创建虚拟环境并安装依赖：
   pip install -r requirements.txt
2. 复制 config_example.json 为 config.json，填写你需要的交易所与参数（如果是 live 模式，填写 API key/secret）
3. 运行：
   python main.py --config config.json --mode paper

下一步建议
- 添加更健壮的订单管理（分片下单、撤单与回滚）
- 支持 WebSocket 订阅实时订单簿
- 添加并行多对扫描与异步处理
