---
title: "webcam orite RN 3500 driver"
date: 2008-01-24
forum: Multimedia &amp; Video
---

### Post by krmsgm on 2008-01-24
Hi everyone,

I am a newbie and trying to use my webcam in ubuntu 7.10 but with camorama keeps saying could not connect to video device (/dev/video0) even though it is connected. I've tried with easycam but didn't work. Here is the results when I type lsusb in terminal;

Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0c45:612a Microdia 
Bus 001 Device 001: ID 0000:0000

---

### Post by linuxwizard on 2008-01-24
For Microdia webcams you can get driver here > [http://www.linux-projects.org/modules/news/](http://www.linux-projects.org/modules/news/)

---

### Post by intel on 2008-01-27
**Microdia** 
(Webcam Support group for all Microdia chipsets under Linux)
Q) Is my webcam a "microdia"? 
A) Execute the following command 
    #lsusb
If you see any of the following numbers, you have a "microdia" webcam
0c45:6027, 0c45:608f, 0c45:60ec, 0c45:60fe, 0c45:6242, 0c45:6253, 0c45:6260, 0c45:6270, 0c45:60c0, 0c45:613b, 0c45:613c, 0c45:624f, 0c45:627b, 0c45:62c0, 0c45:8105
(basically 0c45:<xxxy> above is enough to conclude you have a microdia webcam) 

All of the above webcams are unsupported under Linux

https://groups.google.com/group/microdia

Please join this Group, to help each other get better support for these webcams from Linux.

---

### Post by vivalant on 2008-01-27
krmsgm, you can get the binary SN9CXXX driver here [http://www.linux-projects.org](http://www.linux-projects.org) . So far it's the only thing really working with these cheap Microdia webcams.

---

