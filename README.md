# 动森照片转绘 · Animal Crossing Photo Transfer

把现实照片转成《集合啦！动物森友会 / Animal Crossing: New Horizons》游戏截图风格的 Codex Skill。

**保留照片辨识度，再进行风格转译。** 将人物转成圆头、短身体的原创动森玩家，用圆润 3D 模型、柔和光照与简化游戏材质重现原来的风景、服饰和动作。不是把每张照片都变成同一个热带小岛。

## 能做什么

- 转绘人物、旅行风景、城市街道、庭院、室内和宠物照片。
- 保留原图构图、地貌、人物数量、配饰和主要动作。
- 生成图片并输出可复用提示词，或只写提示词。
- 默认保留原图比例、使用无 HUD 照片模式；可按要求加入轻量中文 HUD。
- 生成后自检，对严重失败进行一次针对性修复。

默认目标是 Nintendo Switch 版《新地平线》的视觉语言。峡谷等非原生游戏场景会按动森模型语言转译，输出是 AI 生成的风格图，不是实际游戏截图。

## 安装

向 Codex 发送：

```text
请安装这个 Codex Skill：https://github.com/qinthqod/animal-crossing-photo-transfer
仓库内 Skill 路径：skills/animal-crossing-photo-transfer
```

或者克隆仓库后，将 `skills/animal-crossing-photo-transfer` 文件夹复制到 `~/.codex/skills/`。若已有同名技能，先备份现有版本再更新。

也可使用 Codex 自带 skill-installer：

```text
使用 skill-installer 从 qinthqod/animal-crossing-photo-transfer 安装
skills/animal-crossing-photo-transfer
```

安装后，在下一轮对话调用该技能。

## 使用

上传照片后说：

```text
使用 $animal-crossing-photo-transfer 转绘这张图。
```

其他示例：

```text
转成动森风格，保留帽子和墨镜，不要 HUD。
```

```text
把这张庭院照转成动森游戏场景，只输出提示词，不加人物。
```

```text
保留峡谷地貌和坐姿，不改成海岛，加上轻量时间与小地图 HUD。
HUD 时间使用虚构示例值 10:30。
```

用户指定的角色、比例、UI、场景和输出方式优先于默认设置。

## 工作流程

1. 分析照片中的主体、空间关系、相机、动作、光照和材质。
2. 确定要保留的特征，将人物与环境转成 ACNH 模型语言。
3. 使用当前环境可用的图像生成工具；提示词模式跳过生图。
4. 检查风格、角色比例、地貌、动作和 UI，必要时窄修复一次。
5. 交付图片及可复用提示词。

本技能包含指令与元数据，不是独立网页应用，也不自带图片生成后端。正常使用 Codex 内置生图能力时，技能本身不需要配置 API Key；实际可用能力取决于运行环境。

## 提示词示例与验证

见 [examples/prompts.md](examples/prompts.md)。示例可直接作为测试请求使用；实际转绘时需提供自己的照片。

当前工作流已在湖岸人物照、峡谷人物照，以及两张图的轻量 HUD 编辑上做过人工测试。构图与人物线索基本保留；远景可能略模糊，复杂草编纹理和地形也可能偏离原图，仍需逐图自检。不是模型效果保证或自动化基准。

## 仓库结构

```text
skills/animal-crossing-photo-transfer/
  SKILL.md
  agents/openai.yaml
examples/prompts.md
README.md
LICENSE
```

`SKILL.md` 是核心工作流；`agents/openai.yaml` 是 Codex 显示名称、简介和默认调用语句。

## 贡献

欢迎通过 Issue 提供失败类型、复现请求和预期行为，通过 Pull Request 改进指令。分享图片前请确认有权公开；无需提供私人照片即可讨论角色比例、地形变化、材质或 HUD 问题。

## 灵感与版权

工作流结构受到 [ekkojiang/zelda-screenshot-transfer](https://github.com/ekkojiang/zelda-screenshot-transfer) 启发，本技能重新编写了适用于动森的角色、材质、动作、UI 和修复规则。

技能指令与本仓库文档采用 [MIT License](LICENSE)。该许可不授予 Nintendo 游戏、商标、角色或其他第三方素材的权利，也不涵盖用户上传的照片。

这是非官方项目，与 Nintendo 或 Animal Crossing 没有隶属、赞助或认可关系。游戏名称用于描述目标视觉风格；请勿将生成结果表述为官方截图或官方授权作品。
