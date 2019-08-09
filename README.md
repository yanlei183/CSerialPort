# CSerialPort

a lightweight library of serial port, which can easy to read and write serical port on windows and linux with C++

一个使用C++实现的轻量级串口类库，可以轻松在windows和linux下进行串口读写

# License 开源协议
since V3.0.0.171216 use LGPL v3 License

自 V3.0.0.171216版本后采用LGPL v3协议

---
# Last Modify 最新版本
## Version: 4.0.1.190728 beta
by itas109 on 2019-07-28

# Design Principles 设计原则

* Cross-platform 跨平台
* Easy use 简单易用
* higher efficiency 高效

# Todo List 待处理事项

- [x] 1.support windows and linux first
- [ ] 2.add communicating protocol
- [ ] 3.support hot swap
- [ ] 4.use new notify module
- [ ] 5.support other language,such as C, C#, Python, Java, Golang
- [x] 6.sync serial port communication
- [ ] 7.new cross-platform gui serial port tool
- [ ] 8.add a video description of this class

# Tested Machine 测试机器
* VS2013 update 5 - Win7 Ultimate 64bit CN - 2019-07-28
* VS2015 update 3 - Win7 Ultimate 64bit CN - 2019-02-27
* VS2015 update 3 - Win10 Enterprise 64bit CN - 2019-02-28
* GCC 5.4.0 20160609 - Ubuntu 16.04 64bit En  - 2019-07-28
* VS2013 update 5 - Win7 Ultimate 64bit En - 2019-03-07

# directory List 目录列表

update : 2019-08-10

```
|-- CSerialPort # root
    |-- .gitattributes
    |-- .gitignore
    |-- LICENSE # LGPL3.0 license
    |-- README.md 
    |-- VERSION # version 版本号
    |-- Demo # example 示例目录
    |   |-- Comm # CSerialPort MFC Demo use source code win32直接调用源码MFC程序示例
    |   |   |-- Comm
    |   |   |-- Release # CSerialPort Release Application 可以直接运行的Release程序
    |   |       |-- Comm.exe
    |   |-- CommDLL # CSerialPort MFC Demo use Win32 Dll win32动态库MFC程序示例
    |   |   |-- Comm
    |   |-- CommQT # CSerialPort QT win/linux Demo QT win/linux 程序示例
    |   |-- CommNoGui # CSerialPort No Gui win/linux Demo win/linux无界面程序示例
    |   |-- CSerialPortDemoWin32Console # CSerialPort Demo for Win32 Console win32控制台程序示例
    |       |-- CSerialPortDemoWin32Console
    |-- doc # document 文档目录
    |   |-- common_problems.md # common problems 问答文档
    |   |-- CSerialPort_doc_cn.chm # Chinese documnet 简体中文说明书
    |   |-- CSerialPort_doc_en.chm # English documnet 英文说明书
    |   |-- error_guide.md # error guide 错误指南文档
    |   |-- How To Use.txt
    |   |-- suspending.txt
    |-- lib # lib 库目录
    |   |-- Linux # windows lib windows库目录
    |       |-- compile.sh # sh compile 命令编译
    |       |-- Makefile # Makefile compile Makefile编译
    |   |-- Windows # windows lib windows库目录
    |       |-- VC12 # windows lib for vs2013 windows vs2013库目录
    |           |-- libcserialport
    |               |-- libcserialport
    |-- pic # picture 图片
    |-- src # source 源代码
        |-- osplatformutil.h # os platform define 操作系统定义
        |-- SerialPort.cpp
        |-- SerialPort.h # Lightweight library of serial port, which can easy to read and write serical port on windows and linux with C++ 轻量级跨平台串口读写类库
        |-- SerialPortBase.cpp
        |-- SerialPortBase.h # CSerialPort Base class 串口基类 
        |-- SerialPortInfo.cpp
        |-- SerialPortInfo.h # CSerialPortInfo class 串口信息辅助类 
        |-- SerialPortInfoBase.cpp
        |-- SerialPortInfoBase.h # CSerialPortInfo Base class 串口信息辅助类基类 
        |-- SerialPortInfoUnixBase.cpp
        |-- SerialPortInfoUnixBase.h # CSerialPortInfo unix class unix串口信息辅助类基类 
        |-- SerialPortInfoWinBase.cpp
        |-- SerialPortInfoWinBase.h # CSerialPortInfo windows class windows串口信息辅助类基类 
        |-- SerialPortUnixBase.cpp
        |-- SerialPortUnixBase.h # CSerialPort unix Base class unix串口基类 
        |-- SerialPortWinBase.cpp
        |-- SerialPortWinBase.h # CSerialPort Windows Base class windows串口基类 
        |-- SerialPort_global.h # Global difine of CSerialPort 串口全局定义 
        |-- sigslot.h # signal and slot 信号与槽
```

# Error Guide 错误指南文档

[Error Guide Document](https://github.com/itas109/CSerialPort/tree/master/doc/error_guide.md)

# Common Problems 问答文档

[Common Problems Document](https://github.com/itas109/CSerialPort/tree/master/doc/common_problems.md)


# Result 结果

## linux：

## Gui 界面

Demo Path: CSerialPort/Demo/CommQT

![image](https://github.com/itas109/CSerialPort/raw/master/pic/linux.jpg)

## No Gui 无界面

Demo Path 1: CSerialPort/Demo/CommNoGui

![image](https://github.com/itas109/CSerialPort/raw/master/pic/linux_no_gui.jpg)

Demo 2 is as follows :

![image](https://github.com/itas109/CSerialPort/raw/master/pic/linux_no_gui_2.jpg)

* code

```
//sp.cpp

#include <iostream>
#include "SerialPort.h"

int main()
{
        itas109::CSerialPort sp;
        std::cout << "Version : " << sp.getVersion() << std::endl;
	sp.init("/dev/ttyS0");
	sp.open();
	std::cout << " open status : " << sp.isOpened() << std::endl;
	
	return 0;
}
```

* compile

```
Linux compile 1
g++ sp.cpp SerialPort.cpp SerialPortBase.cpp SerialPortUnixBase.cpp -lpthread -o sp
./sp

Linux compile 2 with .so library
g++ SerialPort.cpp SerialPortBase.cpp SerialPortUnixBase.cpp -fPIC -lpthread -shared -o libsp.so
g++ sp.cpp -o sp -L. -lsp
export LD_LIBRARY_PATH=./
./sp
```

## windows:

## Gui 界面

Demo Path: CSerialPort/Demo/CommQT

![image](https://github.com/itas109/CSerialPort/raw/master/pic/win.jpg)

## No Gui 无界面

Demo Path 1: CSerialPort/Demo/CSerialPortDemoWin32Console

Demo Path 2: CSerialPort/Demo/CommNoGui

![image](https://github.com/itas109/CSerialPort/raw/master/pic/win_no_gui.jpg)

# Contacting 联系方式

* Email : itas109@qq.com

* QQ Group : [129518033](http://shang.qq.com/wpa/qunwpa?idkey=2888fa15c4513e6bfb9347052f36e437d919b2377161862948b2a49576679fc6)

# Links 链接

* [CSDN Blog](http://blog.csdn.net/itas109)
* [Github](https://github.com/itas109/CSerialPort)
* [Gitee](https://gitee.com/itas109/CSerialPort)

---
# Other branches 其他分支

Remon Spekreijse's serial library has had a profound impact on me, thanks again to Remon Spekreijse
http://www.codeguru.com/cpp/i-n/network/serialcommunications/article.php/c2483/A-communication-class-for-serial-port.htm


only for windows branches : 
https://github.com/itas109/CSerialPort/tree/CSerialPort_win_3.0.3

仅支持windows版本分支 : 
https://github.com/itas109/CSerialPort/tree/CSerialPort_win_3.0.3

---