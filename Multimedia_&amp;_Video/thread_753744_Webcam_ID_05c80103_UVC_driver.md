---
title: "Webcam ID 05c8:0103 UVC driver"
date: 2008-04-13
forum: Multimedia &amp; Video
---

### Post by zasten on 2008-04-13
Hello,

I have a LG R400 laptop and would very much like to get the webcam up and running.

lsusb gives the following output

Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 004: ID 05c8:0103 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 005 Device 002: ID 0cf2:6220 ENE Technology, Inc. 
Bus 005 Device 001: ID 0000:0000  

I believe that Bus 005 Device 004: ID 05c8:0103 Cheng Uei Precision Industry Co., Ltd (Foxlink) is the webcam and that it is supported by the UVC driver. Unfortunately the website seems to be down ([http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)).

Can anyone help me out?

Thanks

---

### Post by xc3RnbFO8P on 2008-04-13
If the server is down at the moment, I think you should wait.
But there is a **luvcview** package here, I dont know if it helps:
[http://packages.debian.org/testing/x11/luvcview]("http://packages.debian.org/testing/x11/luvcview")
I found it in this Howto:
[http://ubuntuforums.org/showthread.php?t=280121&page=3]("http://ubuntuforums.org/showthread.php?t=280121&page=3")
Here is another Howto:
[http://ubuntuforums.org/showthread.php?t=593231]("http://ubuntuforums.org/showthread.php?t=593231")

---

