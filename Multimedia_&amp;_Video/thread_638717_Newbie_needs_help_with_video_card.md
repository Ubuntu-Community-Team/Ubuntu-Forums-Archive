---
title: "Newbie needs help with video card"
date: 2007-12-12
forum: Multimedia &amp; Video
---

### Post by 2005fz1 on 2007-12-12
Hi guys, Great forum...
I need help with a fresh install of ubuntu. I have a radeon 9250 agp card installed on my system and I'm having a problem with the display, it is painfully slow. What can I do to speed it up? here are my specs...
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x x86/MMX+/3DNow!+/SSE TCL
OpenGL version string: 1.3 Mesa 7.0.1

Thanks
Mike

---

### Post by flamelab on 2007-12-12
Go to System -->Administration --> Restricted Drivers Manager and choose (it has a "tick" ) your graphics card .
It will automatically install your driver from the internet .
Reboot or restart Xorg (better - you can do that by pressing ctrl + alt + backspace ) and you have finished !!!!

---

### Post by 2005fz1 on 2007-12-12
Thanks flamlab but the message I get is _Your hardware does not need any restricted drivers._

Mike

---

### Post by 2005fz1 on 2007-12-12
This is my output from lspci if it helps someone find my problem.
Thanks
Mike



lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-760 [IGD4-1P] System Controller (rev 13)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-760 [IGD4-1P] AGP Bridge
00:04.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:04.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:04.4 Non-VGA unclassified device: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:09.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:0a.0 Multimedia audio controller: Ensoniq ES1370 [AudioPCI] (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
01:05.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)

---

### Post by steefjeqv on 2007-12-13
Hi,

Use the following line in terminal :

sudo gedit /etc/X11/xorg.conf

You'll notice a line like this :

Section "device"
driver "radeon"

Make sure that the driver says "radeon".

Save the file and pres Ctrl-Alt-Backspace to restart X.

This should speed things up a bit.

Greetings,
Steven

---

### Post by vanadium on 2007-12-13
There is a chance that you won't be able to reboot after editing your /etc/X11/xorg.conf. To make sure you can recover in case it goes wrong, make sure you make a backup copy of your current /etc/X11/xorg.conf:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

If you find that after the previous post, you cannot bot graphically, then boot to the command prompt and copy the old file back:

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf 

Then restart the system, and the previous situation will be restored.

sudo reboot

(oops, tried this and the system reboots immediately: fortunately Firefox can restore the session, including my typing for this post! )

---

### Post by 2005fz1 on 2007-12-13
Thanks guys!
Solved!


Mike

---

