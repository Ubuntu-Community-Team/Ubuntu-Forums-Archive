---
title: "Which graphical driver(s) for hardware acceleration and dual displays ?"
date: 2014-06-23
forum: Multimedia Software
---

### Post by raphael-cohen on 2014-06-23
Hi all.
I have installed lately Ubuntu 14.04 LTS (64-bit) on a Dell Vostro 3560, and I am pretty happy with it.
I have used until now the default display driver Using X.Org X server - AMD/ATI display driver (open source) for this device: AMD/ATI Thames XT [Radeon HD 7670M].
This driver worked really well even with a secondary display plugged in HDMI port. The only problem I have is that I don't have hardware acceleration enabled. For instance, in Chrome if I type chrome://gpu, it says "Hardware acceleration unavailable", and I can't run anything in 3D.
So what I did is try the other recommended drivers in the "Additional Drivers" tab of "Software and Updates". I tried fglrx-updates and fglrx. When the secondary display is not plugged, it seems to work ok. But as soon as I plug the second display in HDMI port, the screen on both displays becomes completely messed up and flickery as I move the mouse, and the quicklaunch bar is in the middle of the screen. So I reverted to the open source drivers.

So now my question is: can I have 3D acceleration enabled with the open source drivers ? If so, how do I install step by step ?
If I need ton install the proprietary drivers, how can I make them work correctly with dual displays ?

Import Note: it seems that this computer has 2 VGA controllers. When I type "lspci -nn | grep VGA", I get 2 controllers:
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Thames [Radeon HD 7500M/7600M Series] [1002:6840] (rev ff)


Thanks for your advices.

---

### Post by monkeybrain20122 on 2014-06-24
Vdpau for open driver is not enabled in Ubuntu for the apparently ridiculous reason of saving space. [http://www.phoronix.com/scan.php?page=news_item&px=MTYwNzU](http://www.phoronix.com/scan.php?page=news_item&px=MTYwNzU)
To get vdpau for your AMD card with the open driver you need to update the driver with [https://launchpad.net/~oibaf/+archive/graphics-drivers](https://launchpad.net/~oibaf/+archive/graphics-drivers) and install the package mesa-vdpau-drivers

As for Chrome it just disables hd accel by default for open drivers (so disable for all Intel cards), you can turn it on by going to chrome://flags and enable "override software rendering" and then restart Chrome.

---

### Post by raphael-cohen on 2014-06-25
Thanks a million times, your answer was very helpful. I owe you a beer ;)

---

