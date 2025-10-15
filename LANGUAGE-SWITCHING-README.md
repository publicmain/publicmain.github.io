# 全网站语言切换功能说明

## 概述
整个网站现已支持中英文切换功能，用户可以在任何页面点击语言切换按钮即可切换语言。

## 功能特性

### ✅ 已实现
1. **全局语言切换** - 所有页面导航菜单自动翻译
2. **语言持久化** - 用户选择的语言保存在localStorage中
3. **自动注入** - 语言切换按钮自动添加到导航菜单最后
4. **无刷新切换** - 点击按钮立即切换，无需刷新页面
5. **同步更新** - 切换语言后所有元素同步更新

### 📄 已添加脚本的页面 (20+页面)
- ✅ index.html (首页)
- ✅ about-us.html (关于我们)
- ✅ history.html (历史)
- ✅ course-grid.html (课程列表)
- ✅ course-sec.html, course-olevel.html, course-alevel.html, course-ial.html
- ✅ admissions.html (招生)
- ✅ admissions-apply.html, admissions-requirements.html, admissions-fees.html
- ✅ admissions-policies.html, admissions-agents.html, admissions-regulatory.html
- ✅ calendar.html (日历)
- ✅ student-life.html (学生生活)
- ✅ contacts.html (联系我们)
- ✅ gallery.html (图库)
- ✅ team.html (团队)

## 技术实现

### 核心文件
- **js/global-language.js** - 全局语言管理器
- **js/language-data.js** - 日历相关翻译数据
- **js/custom-calendar.js** - 自定义日历实现

### 翻译内容
目前已翻译的内容包括：
- 导航菜单所有链接
- 搜索框占位符
- 常用按钮文本（阅读更多、了解更多、查看全部等）
- 日历页面所有文本
- 事件小部件文本
- 页脚常用文本

## 使用方法

### 用户端
1. 打开任何页面
2. 在导航菜单最后找到语言切换按钮 (🌐 + 文本)
3. 点击按钮即可在中英文之间切换
4. 选择的语言会自动保存，下次访问保持

### 开发端

#### 添加新的翻译文本
编辑 `js/global-language.js` 中的 `translations` 对象：

```javascript
const translations = {
  en: {
    myNewKey: "English Text",
    // ...
  },
  zh: {
    myNewKey: "中文文本",
    // ...
  }
};
```

#### 在HTML中使用翻译
添加 `data-i18n` 属性：

```html
<h1 data-i18n="myNewKey">Default Text</h1>
```

#### 在JavaScript中使用翻译
```javascript
const text = window.globalLanguageManager.getText('myNewKey');
```

#### 添加新页面支持
在页面底部添加脚本引用：

```html
<!-- Global Language Switcher -->
<script src="js/global-language.js"></script>
```

## 浏览器兼容性
- ✅ Chrome 60+
- ✅ Firefox 55+
- ✅ Safari 11+
- ✅ Edge 79+
- ✅ 现代移动浏览器

## 文件结构
```
js/
├── global-language.js       # 全局语言管理器 (新增)
├── language-data.js         # 日历相关翻译
└── custom-calendar.js       # 自定义日历

已修改的HTML文件 (20+ 文件)
├── index.html
├── calendar.html
├── about-us.html
├── ...
└── team.html
```

## 常见问题

### Q: 如何更改默认语言？
A: 编辑 `js/global-language.js` 第136行：
```javascript
this.currentLanguage = localStorage.getItem('site-language') || 'en'; // 改为 'zh'
```

### Q: 如何添加更多语言？
A: 在 `translations` 对象中添加新语言键，例如：
```javascript
const translations = {
  en: { ... },
  zh: { ... },
  ja: { ... }, // 日语
};
```

### Q: 语言按钮在哪里显示？
A: 自动注入到主导航菜单的最后一个位置，显示为 🌐 + 语言文本

### Q: 如何自定义按钮样式？
A: 在CSS中添加样式：
```css
.global-language-toggle {
  /* 自定义样式 */
}
```

## 未来扩展
可以考虑添加：
- [ ] 更多页面内容的翻译
- [ ] 更多语言支持（如马来语、泰米尔语）
- [ ] 图片文本的多语言版本
- [ ] PDF文档的多语言版本

## 技术支持
如有问题，请检查浏览器控制台的错误信息。

