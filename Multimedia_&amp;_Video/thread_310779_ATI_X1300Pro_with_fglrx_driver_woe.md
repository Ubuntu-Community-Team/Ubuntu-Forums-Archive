---
title: "ATI X1300Pro with fglrx driver woe"
date: 2006-12-01
forum: Multimedia &amp; Video
---

### Post by JAW on 2006-12-01
So i decided to install Ubuntu (6.10) Edgy onto my latest machine which is a Dell Dimension E520, Intel Core Duo 2 E6300 with an ATI X1300PRO gfx card and an 19" Ultrasharp 1907FP LCD Display. All installed fine except i noticed that X Windows redraw was terribly slow. I took a peek at the xorg.conf file and sure enough it was using the "vesa" driver... arghh...

So i decided to try the binary "fglrx" driver, which i got using apt-get. I edited my xorg.conf file to use the "fglrx" instead of "vesa", restart and.... damn!!!!  the monitor goes into standby mode after the inital Ubuntu boot screen :( 

After *alot* of messing about with various options, i have found out the following;

1) Connecting the display via DVI doesn't work, switching cables to analogue VGA and it magically works. For some reason it seems that the driver is trying to use modes which are totally invalid for my LCD panel when connected with DVI...

2) When using DVI i could get it to display something if i used the "ForceMonitor" option to "tdms1", although it seemed to display 1024x768 even though it was supposed to be 1280x1024. But i gave up on this and switched to Analogue VGA as mentioned above.

3) I will *never* purchase or recommend another ATI board to anybody! I had grief with their drivers in my laptop a year ago, and stuck with nVidia on my desktops since. I thought they (ati) would have got their act together by now but obviously not...](*,) 

Hope my time wasted saves other ubuntu-ites some of theirs...

James
jigsawdezign.com

---

### Post by hotspear on 2006-12-04
Have you checked this out?
[http://www.ubuntuforums.org/showthread.php?t=143283](http://www.ubuntuforums.org/showthread.php?t=143283)

I have an X1300pro with nVidia chipset on motherboard. Never had any problems getting fglrx installed on both 6.06 and 6.10.

However I do have a question myself and hope to get some insight from here.

I ran 
x11perf -deepcopyplane500
on different machines to compare their video performance.

On a sempron 1.6G with nVidia FX5200(very entry level card) I got 700+/sec. But on an AMD64 3200+ with ATI x1300pro, I  got 264/sec. The ati driver doesn't show any improvement in that regard comparing to the mesa version. Can anyone tell me what's wrong? The bottom end nVidia seems to beat a reasonable ATI entry level card. I wonder if I have done anything wrong. My fglrxinfo shows:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 Series Generic
OpenGL version string: 2.0.6011 (8.28.8)

So I am sure fglrx is properly installed and
direct rendering: yes
according to glxinfo.

By the way, what's the best free tool to benchmark 2D/3D performance on linux?

---

