# Instagram Caption Generator - SPEC.md

## 1. Concept & Vision

一款精致的 Instagram 文案生成器，帮助用户快速创建引人注目的英文文案。设计风格融合了 Instagram 标志性的渐变美学与现代极简主义，营造出既熟悉又高端的体验。整体感觉：时尚、创意、社交媒体友好。

## 2. Design Language

### Aesthetic Direction
- 渐变色为主视觉元素，致敬 Instagram 经典配色
- 大量留白，卡片式布局，圆角元素
- 微妙的阴影和悬浮效果增加层次感

### Color Palette
- Primary Gradient: `#833AB4` → `#FD1D1D` → `#F77737`
- Background: `#FAFAFA`
- Card Background: `#FFFFFF`
- Text Primary: `#262626`
- Text Secondary: `#8E8E8E`
- Border: `#DBDBDB`

### Typography
- Headings: 'Outfit', sans-serif (Google Fonts)
- Body: 'Inter', sans-serif (Google Fonts)
- Font sizes: 标题 2rem, 副标题 1.25rem, 正文 1rem, 小字 0.875rem

### Spatial System
- Container max-width: 640px (移动优先)
- Card padding: 24px
- Element spacing: 16px
- Border radius: 12px (cards), 8px (buttons), 50px (inputs)

### Motion Philosophy
- Button hover: scale(1.02), 200ms ease-out
- Card hover: translateY(-2px), shadow 加深
- 复制成功: 短暂脉冲动画 + checkmark 图标
- 加载生成: 按钮内旋转加载指示器

## 3. Layout & Structure

### Page Structure
```
[Header - Logo + 标语]
[Hero Section - 标题 + 简短描述]
[Input Card]
  - 关键词输入框 (带 emoji 提示)
  - 生成按钮
[Results Area]
  - 多张文案卡片
  - 每张卡片: 文案文本 + 复制按钮
[Tips Section - 使用小贴士]
[Footer - 版权信息]
```

### Responsive Strategy
- Mobile-first (320px - 480px)
- Tablet (481px - 768px)
- Desktop (>768px)
- 全宽输入框，固定宽度容器居中

## 4. Features & Interactions

### Core Features
1. **关键词输入**: 用户输入中文或英文关键词
2. **文案生成**: 基于关键词生成 6 条不同的 Instagram 英文文案
3. **一键复制**: 点击复制按钮，文案自动复制到剪贴板
4. **复制反馈**: 显示"Copied!"提示，2 秒后消失

### Interaction Details
- 输入框: placeholder 提示"输入关键词，如：beach sunset..."
- 生成按钮: 点击后显示加载状态，禁止重复点击
- 复制按钮: 点击后变为 "✓ Copied" 状态
- 空输入提交: 输入框抖动 + 红色边框提示

### 文案生成逻辑
使用预设的文案模板库，结合用户输入的关键词，随机组合生成多样化的 caption：
- 包含 hashtag 格式
- 包含 emoji
- 多种风格：励志、浪漫、幽默、简约

## 5. Component Inventory

### Input Card
- States: default, focused (渐变边框), error (红色边框 + 抖动)
- 输入框高度: 48px
- 清除按钮: 输入内容后显示

### Generate Button
- States: default (渐变背景), hover (亮度提升), loading (显示 spinner), disabled (灰色)
- 全宽，高度 52px
- 渐变背景 + 白色文字

### Caption Card
- 白色背景，12px 圆角，轻微阴影
- 文案文本 + 复制按钮
- Hover: 阴影加深

### Copy Button
- States: default (outline 样式), hover (填充背景), success (绿色 + ✓)
- 位置: 卡片右上角

## 6. Technical Approach

- 纯前端实现，无后端依赖
- 所有代码在一个 HTML 文件中
- 使用 CSS Variables 管理主题
- 使用 fetch API 调用 AI (可选) 或纯前端模板生成
- Google Fonts CDN 加载字体
- Meta 标签完整 SEO 配置
