### 项目介绍

Video-subtitle-generator (vsg) 是一款基于语音识别，将音频/视频生成外挂字幕文件(srt格式)的软件。 

- 支持中文、英文、韩文、日文、越南语、俄语、西班牙语、葡萄语等语言的字幕生成

<img src="https://github.com/sgpublic-forks/video-subtitle-generator/blob/main/design/gui.png?raw=true" alt="gui" border="1px" >

### DEMO

<img src="https://github.com/sgpublic-forks/video-subtitle-generator/blob/main/design/demo.gif?raw=true" alt="demo">

## 源码使用说明

> 运行要求：需要Nvidia GPU显卡（显存大于1G可使用base模型，大于5G可使用medium模型，大于10G可使用large模型）

#### 1. 安装 pixi

https://pixi.sh/latest/installation/

#### 2. 创建并激活虚机环境

（1）切换到源码所在目录：

```shell
cd <源码所在目录>
```

> 例如：如果你的源代码放在D盘的tools文件下，并且源代码的文件夹名为video-subtitle-generator，就输入 ```cd D:/tools/video-subtitle-generator-main```

（2）使用 pixi 恢复环境：

```shell
pixi install
```

#### 3. 运行程序

- 运行图形化界面版本(GUI)

```SHELL
pixi run gui
```

- 运行命令行版本(CLI)

```SHELL
pixi run main
```

```SHELL
coder@dev-container:~/video-subtitle-generator$ pixi run help
Pixi task (help in default): python backend/main.py -h
usage: main.py [-h]
               [-l {auto,en,zh-cn,zh-tw,zh-hk,zh-sg,zh-hans,zh-hant,de,es,ru,ko,fr,ja,pt,tr,pl,ca,nl,ar,sv,it,id,hi,fi,vi,he,uk,el,ms,cs,ro,da,hu,ta,no,th,ur,hr,bg,lt,la,ml,cy,sk,te,fa,lv,bn,sr,az,sl,kn,et,mk,br,eu,is,hy,ne,mn,bs,kk,sq,sw,gl,mr,pa,si,km,sn,yo,so,af,oc,ka,be,tg,sd}]
               [filename]

Subtitle Generator

positional arguments:
  filename              请输入文件完整路径：

options:
  -h, --help            show this help message and exit
  -l {auto,en,zh-cn,zh-tw,zh-hk,zh-sg,zh-hans,zh-hant,de,es,ru,ko,fr,ja,pt,tr,pl,ca,nl,ar,sv,it,id,hi,fi,vi,he,uk,el,ms,cs,ro,da,hu,ta,no,th,ur,hr,bg,lt,la,ml,cy,sk,te,fa,lv,bn,sr,az,sl,kn,et,mk,br,eu,is,hy,ne,mn,bs,kk,sq,sw,gl,mr,pa,si,km,sn,yo,so,af,oc,ka,be,tg,sd}, --language {auto,en,zh-cn,zh-tw,zh-hk,zh-sg,zh-hans,zh-hant,de,es,ru,ko,fr,ja,pt,tr,pl,ca,nl,ar,sv,it,id,hi,fi,vi,he,uk,el,ms,cs,ro,da,hu,ta,no,th,ur,hr,bg,lt,la,ml,cy,sk,te,fa,lv,bn,sr,az,sl,kn,et,mk,br,eu,is,hy,ne,mn,bs,kk,sq,sw,gl,mr,pa,si,km,sn,yo,so,af,oc,ka,be,tg,sd}
                        选择识别的语言:
```

- 代码调用：

```shell
    # 1.指定音视频文件路径
    wav_path = './test/test.flv'
    # 2. 新建字幕生成对象，指定语言
    sg = SubtitleGenerator(video_path, language='zh-cn')
    # 3. 运行字幕生成
    ret = sg.run()
```

#### 4. 程序配置

- 设置模型文件

修改settings.ini中的Mode，取值为：base, medium, large，即可使用对应的识别模型

|  Mode  |  要求显存   |  速度  |
|:------:|:-------:|:----:|
|  base  | 大于1 GB  | ~16x |
| medium | 大于5 GB  | ~2x  |
| large  | 大于10 GB |  1x  |
