# PR Flight Recorder ✈️
**一个可控、可审计、可回放的 PR Review Agent**：生成“带证据”的代码审查意见，并记录完整执行轨迹（Flight Recorder）。

> 我们做的不是聊天机器人，而是**代码变更工作流系统**：可度量、可回放、可持续迭代。

---

## 为什么要做这个？
很多“AI 代码审查”demo 在生产环境翻车，原因通常是：
- 输出**不可复现**、不稳定
- 结论缺乏**证据**（容易幻觉/瞎编）
- 没有**审计链路**，无法 debug、无法合规、无法 A/B

PR Flight Recorder 从系统工程角度出发：
- **Evidence-first**：每条问题必须引用具体代码片段（snippet）
- **Validation Gate**：无法验证的结论直接丢弃（防胡说）
- **Flight Recorder**：每次运行生成 `trace.json`，可回放、可复盘、可评测

---

## 现在（Week1 MVP）你能得到什么？
✅ 解析 unified diff（git patch）为结构化表示  
✅ 安全默认路由（Week1：只评论，不写代码）  
✅ 启发式 Reviewer：输出结构化问题列表（带证据）  
✅ Validator：丢弃无证据/不合规输出  
✅ 生成可直接贴进 PR 的 Markdown 报告  
✅ 生成 `trace.json`（完整执行过程日志）

---

## 快速开始
### 1) 环境要求
- Python 3.11+

### 2) 运行一次 review（在 repo 根目录）
```bash
python -m agent.cli --repo . --diff-file eval/cases/0001.diff
