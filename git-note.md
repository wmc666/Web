# git学习笔记

## 一、创建本地仓库
* 1.配置用户名：
>  git config --global user.name "Your Name"
* 2.配置邮箱：
> git config --global user.email "email@example.com"
* 3.创建目录（此目录就是本地仓库）：mkdir xxx 跳转目录：cd xxx
* 4.初始化一个Git仓库：
> git init
* 5.添加文件到Git仓库：
* （1）将文件从工作区添加到缓存）
> git add <file>   //添加一个文件   
> git add .       //添加当前目录下所有文件
* （2）将文件从缓冲区上传到本地库
> git commit -m "xxx"

## 二、本地仓库关联远程仓库（GitHub）
* 1.创建SSH key：
> ssh-keygen -t rsa -C "youremail@example.com" 
* 在本地仓库生成一个ssh目录，里面有id_rsa和id_rsa.pub两个文件，其中id_rsa.pub是公钥，id_rsa是私钥。
* 2.添加SSH,在giuhub页面Account settings/SSH Keys里添加id_rsa.pub公钥
* 3.与本地仓库关联：
> git remote add origin git@server-name:path/repo-name.git
* git@xxx 为自己GitHub申请的仓库地址（网址）
* 4.首次推送内容到远程仓库：
> git push -u origin master
* 其中origin是远程仓库默认名，master是仓库分支
* 5.每次本地提交后，远程推送命令：
> git push origin master

## 三、查看修改文件
要随时掌握工作区的状态：
> git status
如果文件被修改过，查看修改内容：
> git diff

## 四、版本回退
* git会记录每次提交修改的版本，并用HEAD指针指向当前版本最新，每个版本有唯一版本号，上一个版本是HEAD^，恢复到任意版本命令：
> git reset --hard commit_id
* 查看版本号/提交日志：
> git log，
* 查看命令历史：
> git reflog

## 五、管理撤销、修改、删除
* 1.当你修改了工作区某个文件的内容，想放弃工作区的修改时：
> git checkout -- file
* 2.当你不但修改了工作区某个文件的内容，还添加到了暂存区时（git add），想丢弃修改，先取消暂存区里的文件，再按1操作：
> git reset HEAD <file>
* 3.当你已经提交修改到仓库时，想要撤销本次提交，先恢复到上一次版本（参考第四点）：再按2，1操作。
* 4.删除文件命令：
> git rm 
> git commit