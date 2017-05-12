# 微信公众号批量抓取工具
## 运行环境
1. 需要安装Python 3.5 如果运行2.7的会出现一点小bug 目前暂时没有精力改成2.7版本

2. 关于安装库，我用的都是标准的，如果连requests 或者ftplib都木有的话我也不好说什么是吧。pymysql这个库链接MySQL还是不错的

## 使用本程序问答手册

1. 我现在有一到两万公众号的获取需求你的程序能够满足么
**答：可以。如果有更大的量，可以考虑用虚拟机 然后运行电脑版微信批量用脚本模拟点击获取key。如果需求很强烈的话我会考虑改写
里面的ftp获取方法。**

2. 我想了解一下本程序批量获取微信公众号文章的方法
**答：通过fiddler获取电脑版的微信公众号访问请求以及response，然后本程序解析resopnse里面的msglist 然后批量获取文章的链接 
描述 发布时间 名称等 然后批量插入数据库 记得自己改数据库信息哦 值得注意的是：目前key算法换成一个公众号一个key
 key有效30min  我觉得用key获取文章历史的没啥意义，当然大家可以只用key来拼出来，获取文章历史列表只需要frommsgid和count
 就行，我这里就不写我怎么拼了。**
 
3. 我该如何使用本程序，能达到我的效果
**答：本程序仅作一个demo，运行new_crawl_wechat他会从response.txt转换为new_response.txt 这个response怎么来的呢是你fiddler截获
报文来的，生成的一个txt文本。至于fiddler怎么设置可以截获微信报文 怎么样修改rules可以生成你想要的response.txt尽在我的博客**
[fiddler教程地址](http://www.songluyi.com/%E5%88%A9%E7%94%A8fiddler-%E6%88%AA%E8%8E%B7%E5%BE%AE%E4%BF%A1%E4%BC%A0%E8%BE%93%E6%95%B0%E6%8D%AE-%EF%BC%88%E6%96%B9%E4%BE%BF%E6%8A%93%E5%8F%96%E5%85%AC%E4%BC%97%E5%8F%B7%E4%BF%A1%E6%81%AF%EF%BC%89/)
4. 我觉得你的思路很傻比，完全没有Python精神，我该如何找到你的联系方式喷你呢？
**答：见左边博客或者gmail谢谢 (请带上自己牛逼的方法和代码哦）**

5. 你这个傻吊程序靠谱不，有人fork然后成功了么？
**答：有人测试成功，已经为公司进行运作，满足实验室或者小规模使用**
 
## 文件介绍
1. prepare_request.py这个文件是以前版本，当时key没有和公众号关联一个key可以获取多个公众号文章列表，后来结果是大家都知道了
你可以借鉴这里面对key的拼接或者其他思想。
2. new_crawl_wechet.py这个是最新的，运行它你可以立刻看到他在做什么：主要就是将fiddler4获取到mp.weixin.qq.com的request的
response获取到的txt解析然后获取其中内容并放置到mysql中.
3. 其他的txt文件是fiddler获取下来的，new_response是我的程序生成的，具体为什么这么做我有写明.

## 技术含量
1. 恩，爬取微信除了让我比较难受以外没什么卵技术含量.

## 已经更新
1. 1.1版本更新 修复了如果拉取多章历史文章，不能获取的问题。

## 日后跟新
1. 在爬取的过程中，多进程导致微信有时候会有connection_error爆出，我准备写一个批量代理的轮子，方便切换IP。

3. 如果有任何问题可以在issue里面提出，或者直接mail我。如果看到我会解决你的一些问题。

## 本文转载  

[King-slayer](https://github.com/King-slayer/crawl_wechat)