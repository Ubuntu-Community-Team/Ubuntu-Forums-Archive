---
title: "Low resolution on dual head with Intel graphic card"
date: 2010-07-18
forum: Multimedia Software
---

### Post by pulpfiction on 2010-07-18
Hello,

I've a Inspiron 1545 with a Intel 4500 graphic card on dual head with a 23" LG screen. I want the resolution of this external screen to be 1920x1080, but it seems I can't get it to be higher than 1360x768 (which is the same of the laptop screen). I'm using Ubuntu 10.4 Lucid Lynx.

Here's some output which may help:

```
chico@chico:/$ lspci | grep VGA
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

chico@chico:/$ xrandr -q
Screen 0: minimum 320 x 200, current 2726 x 768, maximum 8192 x 8192
VGA1 connected 1360x768+1366+0 (normal left inverted right x axis y axis) 510mm x 290mm
   1360x768       59.8* 
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.1*+
   1360x768       59.8  
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
DP1 disconnected (normal left inverted right x axis y axis)

```

Also, it seems I already have the proper drivers (at least from what I read):

```
chico@chico:/$ sudo apt-get install xserver-xorg-video-intel
[sudo] password for chico: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

The odd thing is I have an older Inspiron 1525 with a lower Intel 3100 graphic card which works just fine with Ubuntu Lucid Lynx. I can get a 1280x800 + 1920x1080 resolution there. :(

---

### Post by pulpfiction on 2010-07-24
Can any moderator please move this topic to the Multimidia & Video category? I guess I'd rather get more replies there as the category seems more appropriated. Thanks.

---

### Post by Iowan on 2010-07-24
Moved to Multimedia & Video (by request).

---

