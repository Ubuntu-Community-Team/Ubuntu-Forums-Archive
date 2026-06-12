---
title: "How to get 1366x768 with fglrx?"
date: 2011-05-07
forum: Multimedia Software
---

### Post by lonfucius on 2011-05-07
I'm using Ubuntu 11.04 and using the fglrx driver from repo, but i can't get 1366x768 resolution.
I generate xorg.conf with "sudo X -configure" and put in the Modeline that was copied from windows powerstrip, which works fine under windows with catalyst. and restart X, the lcd gets 1366x768 resolution as expected. but the "sudo X -configure" generated xorg.conf was using "radeon" driver, but blender won't work with it, etc...  I want to use "fglrx" driver. So I change the Driver section from "radeon" to "fglrx" and restart X, it wont start now, telling me that out of range or something. 

Section "Device"
	Identifier  "Card0"
	Driver      "radeon"
	BusID       "PCI:1:5:0"
EndSection

---

### Post by BicyclerBoy on 2011-05-08
This is not very helpful but any information could help..
1366x768 is not a standard video mode..
1360x768 is a std vesa built in video mode.

You should be able to use a custom modeline of 1366 but maybe the driver will not allow it (it does not integer divide by eight).

I don't have any ATI/AMD graphics to experiment with, sorry.

When I calculate the modeline for 1366x768 CVT returns these modelines with 1368 dots/line

# 1368x768 59.85 Hz (CVT) hsync: 47.28 kHz; pclk: 72.25 MHz
Modeline "1368x768R"   72.25  1368 1416 1448 1528  768 771 781 790 +hsync -vsync

# 1368x768 59.88 Hz (CVT) hsync: 47.79 kHz; pclk: 85.25 MHz
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync

---

### Post by lonfucius on 2011-05-12
Thanks for your reply BicyclerBoy!

I have solved this problem, I first try everything with xorg.conf, amdpcsdb, aticonfig, and nothing worked. fglrx keeps ignore my setting of custom modeline, randr disabling, etc. And it turns out that fglrx just IGNOREs Monitor setting from xorg.conf, and that Xrandr CANNOT be DISABLED. Finaly I add "Virtual 1366x768" Display SubSection, and add up the Modeline which works perfectly with open-sourced radeon driver. And it worked! Hope my experience is helpful to anyone who would encounter the same problem.

---

### Post by c@ssie on 2011-05-18
> **lonfucius said:**
> Thanks for your reply BicyclerBoy!

I have solved this problem, I first try everything with xorg.conf, amdpcsdb, aticonfig, and nothing worked. fglrx keeps ignore my setting of custom modeline, randr disabling, etc. And it turns out that fglrx just IGNOREs Monitor setting from xorg.conf, and that Xrandr CANNOT be DISABLED. Finaly I add "Virtual 1366x768" Display SubSection, and add up the Modeline which works perfectly with open-sourced radeon driver. And it worked! Hope my experience is helpful to anyone who would encounter the same problem.

Could you please paste your xorg.conf?  I'm not really following what goes where.

---

### Post by grindboy on 2011-05-29
I'll second this request. I can't seem to get 1366x768 working no matter what I do!

---

