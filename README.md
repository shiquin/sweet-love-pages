# 甜心小店入口

GitHub Pages 发布此目录。访问者打开 `zsy.qzz.io` 后，页面会自动跳到小店当前的 HTTPS 地址，也可以手动点击「打开小店」。

## 发布设置

1. 在 GitHub 仓库的 Pages 设置里选择 `Deploy from a branch`，发布 `main` 分支的根目录。配置自定义域名 `zsy.qzz.io`。
2. 域名注册成功后，在权威 DNS 服务为 `zsy.qzz.io` 添加四条 A 记录，指向 `185.199.108.153`、`185.199.109.153`、`185.199.110.153` 和 `185.199.111.153`。
3. GitHub 验证 DNS 并签发证书后，开启 `Enforce HTTPS`。

[GitHub Pages 自定义域名设置](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)

## 更新跳转目标

隧道重启时可能分配新地址。部署服务器上的 `tools/sync-pages-redirect.py --publish --watch` 每 30 秒检查 `public-url.txt`。发现新地址后，脚本先检查小店健康状态，再将新目标推送到 Pages 仓库的 `main` 分支。GitHub Pages 重新发布后，入口会跳转到新地址。服务器需要有该仓库的推送权限。去掉 `--watch` 可执行一次同步。
