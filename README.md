## branch
* 使用 ffmpeg 命令来下载和转换 m3u8 格式视频
```sh
ffmpeg -acodec copy -vcodec copy -threads 32 "/sdcard/Download/`date +%Y-%m-%d_%H-%M-%S`_m3u8.mp4" -i "https://www.hfyrw.com/Cache/68f72049e32321f85ce506431caddfe6.m3u8"
```
* -i 参数指定了输入文件的位置，在这里是一个网络地址。
* -acodec copy 和 -vcodec copy 参数分别指定音频和视频的编码格式，这里都是 copy，意味着不进行编码转换，而是直接拷贝原始编码。
* -threads 参数指定线程数。如果不指定线程数，ffmpeg 默认会使用单线程。注意，多线程下载可能会增加带宽占用和服务器负载，请注意使用线程数的限制。
* 上面的命令使用了 /path/to/save/ 来指定下载路径，并将文件保存在该路径下。请确保该路径存在且有写入权限。
* 上面的命令使用了 date +%Y-%m-%d_%H-%M-%S 来获取当前日期和时间，并将其作为文件名的一部分。这里的 %Y表示年份，%m表示月份，%d表示日期，%H表示小时,%M表示分钟，%S表示秒。
* 请注意，这只是在linux系统下的写法，对于其他系统的命令可能会有不同。

## 软连接
```sh
ln -s /sdcard/Download Download
ln -s /sdcard storage
```

## 脚本
* 下面是一个示例脚本，它接受一个参数，即输入文件的网络地址，并使用该地址下载文件。
```bash
#!/bin/bash

input_url=$1
output_path="/path/to/save/"

ffmpeg -i "$input_url" -acodec copy -vcodec copy -threads 4 "$output_path`date +%Y-%m-%d_%H-%M-%S`_m3u8.mp4"
```
* 使用这个脚本时，可以将网络地址作为第一个参数传入，如下所示：
```bash
./script.sh "https://www.hfyrw.com/Cache/68f72049e32321f85ce506431caddfe6.m3u8"
```
```bash
sh script.sh https://www.hfyrw.com/Cache/68f72049e32321f85ce506431caddfe6.m3u8
```
* 请注意，需要给这个脚本加上可执行权限（例如 chmod +x script.sh）

## start
* 由于Python以及ffmpeg的强大，此脚本可以跨平台Windows、Mac OS、Linux、Android等
* 依赖 ffmpeg Python3.6+ requests库
* 在termux下安装三个依赖
```sh
pkg install ffmpeg
```
```sh
pkg install python
```
```sh
pip install requests
```

## HELLO
    我想要🌟🌟，你可以给我点亮它吗


## 用处

1. 支持`m3u8`类型流媒体，能播放就能下载
2. 多线程下载
3. 批量任务、一次性下载一部电视剧都没问题  
4. 它不是万能的，有些m3u8文件乱得离谱，没有规律，我只能见一个改一下，也许你可以反馈一下

## 依赖

1. `python3.6+` ![img](img/1610781483234.jpg) 
2. `requests`库,使用`pip install requests`安装![img](img/1610781483232.jpg)  
3. [ffmpeg](http://www.ffmpeg.org)![img](img/1610781483229.jpg)
   对于Windows用户，需要将ffmpeg添加进环境变量中,直到你可以在CMD中使用ffmpeg命令   
    termux: `pkg install ffmpeg`  
    centos: `yum install ffmpeg`  
    mac os: `brew install ffmpeg`  
   

## 使用

1. 命令行敲入`python M3u8Download.py`
2. 输入 `url` `name` 即可使用  
   `完整的m3u8文件链接: url`  
   `保存m3u8的文件名: name`
   

## 演示

![img](img/1610781483225.jpg)
![img](img/1610781483227.jpg)


## 参数说明

![img](img/1610781483220.jpg)
