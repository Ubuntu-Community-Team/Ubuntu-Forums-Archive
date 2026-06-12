---
title: "screen resolution with widescreen LCD  tv"
date: 2010-02-19
forum: Multimedia Software
---

### Post by Jeztastic on 2010-02-19
Hi

I am setting up a computer for pre-school kids to use. I have a Toshiba Regza 26wlt66s which I am using via SVGA (may attempt DVI later). Using edubuntu 9.10.

I have been using xrandr to try and get the right resolution - listed as 1366x768 - for ages now, but with little success. I have successfully set up a variety of resolutions, but they are always a bit too large for the screen - half the menu bars are obscured. 

I have extensively googled and read the manual, tried setting up xorg.conf, but getting nowhere. 

Please help - think of the children!

```
littlehands@happyapple:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:04.0 PCI bridge: Hint Corp HB6 Universal PCI-PCI bridge (non-transparent mode) (rev 15)
04:04.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
04:04.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
04:05.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
04:05.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
04:06.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
04:06.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
04:07.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
04:07.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
```

Thanks again.

---

### Post by Jeztastic on 2010-02-20
I would like to re-iterate that I have searched these forums and tried a variety of different fixes, nothing has worked, please don't let the thread die!

---

### Post by efflandt on 2010-02-20
Many screens advertised as 1366x768 might not be exactly.  For my 40" Polaroid HDTV **cvt** would not come up with a 1366 mode, it either ended up 1360 or 1368 for numbers between that.

Look through /var/log/Xorg.0.log to see what resolutions X finds, even if it does not use them.  In my case X seemed to think 768 was too many lines.  And since WinXP used 1360x764, it looked like 1360x765 was the closest to ideal.  This is an example of script I use to switch resolution of the external VGA and turn off the laptop display with Intel video.  You might try this mode (make sure you copy the entire line through +vsync).

```
#!/bin/bash
xrandr --newmode "1360x765_60.00"   84.50  1360 1432 1568 1776  765 768 773 795 -hsync +vsync
xrandr --addmode VGA1 1360x765_60.00
xrandr --output VGA1 --mode 1360x765_60.00
# turn off laptop display
xrandr --output LVDS1 --off
exit
```

---

### Post by Jeztastic on 2010-02-20
Great, thanks I will try that. It's not a laptop, I take it I just remove the lines relating to turning off the laptop screen?

---

