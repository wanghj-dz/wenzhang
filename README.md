# GitCode 使用 HTTPS + 令牌 登录指南

## 账号信息
- **GitCode 用户名**: wanghj_dz
- **访问令牌**: mKa6mqkfzvVkQQo9FbUi1hio

## 使用 HTTPS + 令牌 登录的方法

### 方法一：直接在URL中使用令牌（最简单）

```bash
# 克隆仓库
git clone https://wanghj_dz:mKa6mqkfzvVkQQo9FbUi1hio@gitcode.com/wanghj_dz/wenzhang.git

# 推送更改
cd wenzhang
git add .
git commit -m "提交描述"
git push origin main

# 拉取更新
git pull origin main
```

### 方法二：配置Git全局设置（一次配置，永久使用）

```bash
# 设置全局配置，以后所有GitCode操作都会自动使用令牌
git config --global url.https://wanghj_dz:mKa6mqkfzvVkQQo9FbUi1hio@gitcode.com/.insteadOf https://gitcode.com/

# 然后可以直接使用正常的Git命令
git clone https://gitcode.com/wanghj_dz/wenzhang.git
git push origin main
git pull origin main
```

### 方法三：使用凭证管理器（Windows推荐）

```bash
# 设置凭证缓存（临时有效）
git config --global credential.helper cache
# 默认15分钟有效，可以修改超时时间
git config --global credential.helper 'cache --timeout=3600'

# 首次操作时会提示输入用户名和令牌，之后会自动使用缓存的凭证
git clone https://gitcode.com/wanghj_dz/wenzhang.git
```

## 注意事项
- 请妥善保管访问令牌，不要在公共场合泄露
- 使用HTTPS方式无需配置SSH密钥，但每次操作都会通过网络传输凭证
- 访问令牌具有一定的权限范围，请注意安全
- 如果令牌失效或被撤销，请使用新的令牌更新配置
