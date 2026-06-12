---
title: "Nvidia Driver is freezing my System under edgy"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by splashi on 2007-05-03
Hi There!

I have the following problem on my Ubuntu 6.10 (edgy):

If I acivate the original nvidia driver, my whole system freezes for a few time, if there is a minimal Usage of the Graphics Adaptor.

Aftera few minutes the System runs again, but sometimes It needs a reboot.

This problem is even on only-Text Websites, Forums, etc, If I'll scroll down, there appear mome small horzontal lines on the screen, then it freezes.

If I'll change the driver to nv, this problem doesn't appear, but my system slows down.

How can I fix this problem, I think this is even a small problem in my xorg.conf.

If You need any other Logs or configurations, please let me know.

Thanks In advance
Wolfgang

-----

cut from my xorg.conf:

Section "Device"
Identifier "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
Driver "nvidia"
BusID "PCI:1:5:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 31-82
VertRefresh 56-75
EndSection

Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection

---

### Post by splashi on 2007-05-08
The same Problem also appears under ubuntu 7.04 (feisty fawn)

---

