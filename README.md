# 哈工大（深圳）ICS 课表生成

> 本项目无任何质量保障与技术支持，请您确保自己能读懂本项目的源码，方可使用。

## 功能介绍

- 支持使用用户名与密码便捷登录，并自动获取所有课表生成需要的信息。
- 支持自动推断学期开始日期。
- 支持手动填写部分参数，当自动获取失败时仍可生成。
- 无隐私泄露顾虑，且源代码开放易读。

## 前置条件

- Python 3
- Poetry: <https://python-poetry.org/docs/#installation>

## 初始化项目

1. 执行 `poetry install`。
2. 将 Jupyter Notebook 的内核指定为 Poetry 环境。

## 配置

请修改 `exp.ipynb` 笔记本，并选择下面任意一种方法，设置参数：

### 方法 A：自动推断

- `SHOULD_INFER_SEMESTER`：是否将学期自动设置为当前学期，请设置成 `True`。

#### （推荐）方法 A1：用户名和密码

- `USERNAME`：统一身份认证用户名（学号）。
- `PASSWORD`：统一身份认证密码。

#### 方法 A2：Cookie

- `COOKIE`：访问 `http://jw.hitsz.edu.cn` 时使用的 cookie 字段，获取方法此处不作教学。

### 方法 B：手动指定

自己使用浏览器抓包，将对于路径 `http://jw.hitsz.edu.cn/xszykb/queryxszykbzong` 的请求进行捕获或回放，然后把得到的 JSON 文件放在 `./general_schedule.json`。

- `REQUEST_DATA`：指定学年和学期，请仿照 `REQUEST_DATA_EXAMPLE` 进行设置。
- `START_DATE`：该学期开始日期。
- `SHOULD_INFER_SEMESTER`：请设置成 `False`。
- `CALENDAR_NAME`：ICS 文件名。
- `ALARMS`：日程提醒，如不需要提醒可设置为空列表。

## 运行

打开 Jupyter Notebook `exp.ipynb`，然后运行所有 cells，最终会在项目目录下生成一个 ICS 文件。关于 Jupyter Notebook 的使用方法此处不作教学。