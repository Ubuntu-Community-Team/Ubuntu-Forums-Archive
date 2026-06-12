---
title: "Dual monitor - Karmic - i915G"
date: 2009-12-22
forum: Multimedia Software
---

### Post by sbrbot on 2009-12-22
I have older machine Dell GX280 with built in Intel i915G graphic card. On this machine I connected two monitors: first monitor Dell 22" (model=E2209W, screen=1680x1050@60) monitor on digital DVI output and second monitor Dell 19" (model=1905FP, screen=1280x1024@60) on analog VGA output. (Dual monitor works on Windows XP but not on Ubuntu 9.10)

Ubuntu recognized my two monitors in Display Preferences (see attached pictures) but when I turn on second (by default it is off) and try to Apply settings my machine freezes.

kernel:

```
sbrbot@hoto:~$ uname -a
Linux hoto 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux
```

intel video driver (v2.9.0):

```
sbrbot@hoto:~$ grep -A2 intel_drv /var/log/Xorg.0.log
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.9.0

```

lspci output:

```
sbrbot@hoto:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation 82915G Integrated Graphics Controller (rev 04)
...
```

xrandr ouput:

```
sbrbot@hoto:~$ xrandr
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 4096 x 4096
VGA1 connected (normal left inverted right x axis y axis)
   1280x1024      60.0 +   75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
DVI1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 473mm x 296mm
   1680x1050      60.0*+
   1280x1024      75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  

```

At the moment only bigger Dell 22" works on DVI output while smaller Dell 19" does not work at all.

How to configure them in dual monitor mode. I tried many xorg.conf files without any success.

---

### Post by sbrbot on 2009-12-22
I solved my problem using instructions from this site:

[http://www.gir.me.uk/computers/xorg_dual-head.html]("http://www.gir.me.uk/computers/xorg_dual-head.html")

I had to setup KMS

---

