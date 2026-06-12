---
title: "No HDMI video output"
date: 2011-02-17
forum: Multimedia Software
---

### Post by racitup on 2011-02-17
Hi guys,

Hardware: HP dv3505ea laptop
Ubuntu: 10.04 LTS
uname -a: Linux adventure 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 23:42:43 UTC 2011 x86_64 GNU/Linux
HDTV: Panasonic TX-L37D28BSA

I'm having trouble getting any output from my laptop's HDMI socket. I've had a search and can only find sound problems, mine is no visible output whatsoever.

Let me describe the setup: Laptop has a HDMI socket which I have never used before, HDTV has 4 HDMI inputs, I just bought a HDMI cable to connect the two to try it.

After connection I go to System->Preferences->Monitors and the TV is detected fine with the correct description and offers me 3 different resolutions. xrandr also works and gives me the same thing:
```
rich@adventure:~$ xrandr -q
Screen 0: minimum 320 x 200, current 2560 x 800, maximum 8192 x 8192
LVDS-1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 286mm x 178mm
   1280x800       60.0*+
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  
   720x400        59.6  
   640x400        60.0  
   640x350        59.8  
VGA-1 disconnected (normal left inverted right x axis y axis)
DVI-D-1 connected 1280x720+1280+0 (normal left inverted right x axis y axis) 698mm x 392mm
   1920x1080      50.0 +   60.0  
   1280x720       60.0     50.0* 
   720x576        50.0  

```However none of the options display ANYTHING on the TV. The screen remains black, not even a flicker.

I have connected the laptop to the TV before using an analogue VGA (monitor) cable which worked in the same way with no problems.

Could this be an encryption/DRM/DVI problem?
I have suspicions about the cable too because it is new and I haven't seen it work, but it wouldn't detect the correct TV description and resolutions would it? It was sold as an XBOX360/PS3 HDMI cable, is there a difference? It looks like a standard HDMI male-male cable.

Other things I've tried:

[LIST]
[*]Log off and log back on to restart the X server
[*]reboot
[/LIST]
Some more stuff:
```

rich@adventure:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9300M GS] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection

```Any help is much appreciated!
Richard

EDIT: Actually having double checked it doesn't quite give the right TV description:
"Panasonic Industry Company 32""
Whereas it's actually a 37"

EDIT2: Also I don't get the option to have "Same image in all monitors" either if that makes a difference?

---

### Post by racitup on 2011-02-17
**Bump** anyone?

---

