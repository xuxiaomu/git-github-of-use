我使用的是win7版本的git（git安装略去，自行搜索）。   

本地git使用：   
1、在本地某个盘下新建一个文件夹，例：在E:盘创建gitProject文件夹，  
打开git命令窗口。  
2、git命令窗口进入gitProject文件夹，   
命令git init把这个文件夹变成Git可管理的仓库.   
3、把你需要上传的资料复制到创建gitProject文件夹中。使用git status命令    
可以查看当前git仓库文件状态   
4、通过git add . 命令把刚才复制过来的资料全部添加到仓库上(git add . 表示当前文件夹下所有资料)。   
使用git status查看，添加成功的文件名字是绿色的。   
5、用git commit -m "注释" 把项目提交到仓库。此处注意，需要注册下自己的邮箱及用户名，    
命令： git config user.email "xuxiaomu008@163.com"   
       git config user.name "xuxiaomu"    

（以上操作已经成功文件提交到git仓库了，接着是连接远程仓库（也就是连接Github））    


本地git连接Github提交资料    

1、创建SSH KEY。先看一下你C盘用户目录下有没有.ssh目录，有的话看下里面有没有id_rsa和id_rsa.pub这两个文件，有就跳到下一步，    
没有就通过下面命令创建    
   $ ssh-keygen -t rsa -C "youremail@example.com"    
（自行百度具体操作，因为只需要一次，以后就不用操作了）   
2、在Github上创建一个Git仓库，你可以直接点New repository来创建，我创建的地址是    
https://github.com/xuxiaomu/java-of-wsdl.git    
3、和本地git仓库进行关联，根据创建好的Git仓库页面的提示，可以在本地git仓库的命令行输入：   
$ git remote add origin ttps://github.com/xuxiaomu/java-of-wsdl.git    
4、关联好之后我们就可以把本地库的所有内容推送到远程仓库（也就是Github）上了，通过：     
$ git push -u origin master   
 由于新建的远程仓库是空的，所以要加上-u这个参数，等远程仓库里面有了内容之后，下次再从本地库上传内容的时候只需下面这样就可以了：    
$ git push origin master    

补充一点：如果你上传的github上的远程仓库中，已经有其他文件了，在第4步push就会报错了。这是由于你创建的那个仓库里面的文件不在本地仓库目录中。    
解决办法：  
通过以下命令先将内容合并以下：  
$ git pull --rebase origin master   
然后再执行第4步的push命令就好了。   
