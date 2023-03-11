# 3d 个人网站

最终效果：[taixinf.github.io](taixinf.github.io)

可以把这个`shell`脚本放到项目目录中，新建`deploy.sh`,将仓库 git 地址修改成你自己的

```shell
#!/usr/bin/env sh

# 确保脚本抛出遇到的错误
set -e

# 生成静态文件
npm run build

# 如果是发布到自定义域名
# echo 'www.yourwebsite.com' > CNAME

git init
git add -A
git commit -m 'deploy'

# 如果你想要部署到 https://USERNAME.github.io
git push -f git@github.com:USERNAME/USERNAME.github.io.git main

# 如果发布到 https://USERNAME.github.io/<REPO>  REPO=github上的项目
# git push -f git@github.com:USERNAME/<REPO>.git master:gh-pages

```

然后在 config.json 中加入

```
"scripts": {
	...
    "deploy": "bash deploy.sh"
  },
```

就可以运行`npm run deploy`实现自动化部署咯。
