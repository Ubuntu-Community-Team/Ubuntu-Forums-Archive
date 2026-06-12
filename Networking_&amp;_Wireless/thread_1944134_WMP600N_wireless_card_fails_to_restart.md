---
title: "WMP600N wireless card fails to restart"
date: 2012-03-20
forum: Networking &amp; Wireless
---

### Post by FreeWillzyx on 2012-03-20
[LEFT]Here is my current wireless card 
[IMG]http://i43.tinypic.com/2ebv9s7.jpg[/IMG]

My system is **ubuntu 10.04.2 LTS**
kernel [B]2.6.38 64 bit

[/B]When my system boots the card shows up as wlan0 when i run **ifconfig**, and will connect to my network (WPA2). 

However, if i turn the interface off by doing **ifconfig wlan0 down** I am not able to turn it back on. 

As far I can tell I have the right driver installed as well as the latest firmware. 

running **etc/init.d/networking restart** does not fix the problem. It ends up saying the same thing as when I run **ifconfig wlan0 up**:

SIOCSIFFLAGS: Input/output error

My only solution so far has been to restart the computer, however that is very impractical because there are a lot of things that require turning the interface off. 

Any suggestions would be appreciated. Thanks in advance. 


[/LEFT]

---

