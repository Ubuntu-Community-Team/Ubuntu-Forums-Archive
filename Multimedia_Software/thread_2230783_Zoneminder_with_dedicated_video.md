---
title: "Zoneminder with dedicated video"
date: 2014-06-21
forum: Multimedia Software
---

### Post by zrock2 on 2014-06-21
[COLOR=#000000]Hello Ubuntu forums,
[/COLOR][COLOR=#000000]I have installed and configured zoneminder to work with my 1 IP camera. I can view them from a web browser.



[/COLOR]Failed to stat video device /dev/video0: No such file or directory[COLOR=#000000]
[/COLOR]'zmc -d /dev/video0' exited abnormally, exit status 255

system Ubuntu 14.04
Dvr pico2000 
[h=3]conexant 878a[/h]

[COLOR=#DC143C][FONT=inherit][/dev/video0 (0)]("http://aitos.no-ip.info/zm/?view=monitor&mid=1") red
help to fix it

[/FONT][/COLOR]

---

### Post by Vladlenin5000 on 2014-06-21
Hi, welcome.

It seems Zoneminder - as it is configured right now - is expecting a video device physically connect to the machine, not some network stream. You need to configure it for the network camera.

[http://www.zoneminder.com/wiki/index.php/Hardware_Compatibility_List#Network_Cameras](http://www.zoneminder.com/wiki/index.php/Hardware_Compatibility_List#Network_Cameras)
[http://www.linux.com/learn/tutorials/762058-how-to-operate-your-spycams-with-zoneminder-on-linux-part-1-](http://www.linux.com/learn/tutorials/762058-how-to-operate-your-spycams-with-zoneminder-on-linux-part-1-)

---

