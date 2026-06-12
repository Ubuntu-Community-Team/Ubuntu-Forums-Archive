---
title: "Force video mode (?Modeline) to specific values"
date: 2017-05-14
forum: Multimedia Software
---

### Post by paul-norbealun on 2017-05-14
I have Mythbuntu running on a dedicated Intel NUC 5CPYH box.  Everything is good, except for the HDMI output to the TV.  VGA works fine.

The display when I use HDMI is granulated with lots of display effects as illustrated in the attached picture.  The picture is also jittery and has lots of flicker.  Every 10-20 seconds it blanks before reappearing 5-15s later.

I have attached the output from 
```
get-edid | parse-edid >/tmp/edid.txt
```

The EDID configuration appears to be being ignored by the system: the initial mode being selected is 1920x1080@60Hz, not the "Preferred mode" of "Mode 18".  I don't want the preferred mode anyway, but it's indicative.  Also when I run ```
xrandr --output HDMI2 --mode "Mode 0"
``` I get an error saying "Mode 0" is not known.

I don't know enough about xrandr to use --newmode and make it work.

A bit of reading suggested I could adding a Modeline to xorg.conf or XF86Conf but I can't find either of these... :(

I did find a file called > ~/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml which seems to relate to my TV.  It has the manufacturer as XXX and it's the right HDMI output.  But it just has the resolution and refresh rate.  I'm happy with these... it's the more technical parameters relating to the... stuff... that I want to see if I can fix.

Does anybody have any suggestions?  Or a solution even??

Thanks in advance.

---

### Post by walterav on 2017-05-14
Are you sure the HDMI output (hardware) works fine on different Television models, or during bios/uefi POST startup of the NUC or even in Windows X (software)?

What version of ubuntu / graphics stack are you running and what is your exact cpu/gpu, the output of the following commands might give more info?

```

lsb_release -a
uname -a
lspci -nn
glxinfo|egrep "OpenGL vendor|OpenGL renderer*"
xrandr #show how many outputs there are since you call hdmi2 but is there hdmi0/1?

```

What happens if you add kernel boot parameter "nomodeset i915.modeset=0", it will give less optimal resolution but is the picture stable? This can be done during boot in grub bootloader, select your boot option but press "e" instead of "enter". Than before the word "quiet" in the row that starts with "linux" type the "nomodeset i915.modeset=0". 

You might try other video modes as kernel boot parameters, since these will be gone on the next boot vs fiddling with xorg.conf which is permanent and might get you stuck.

---

### Post by paul-norbealun on 2017-05-15
Thanks for your response.
I have no trouble getting HDMI output to display on my Viewsonic monitor.

We have two HDMI televisions in the house, and I have not been able to get any HDMI output on either one.  The one that I'm struggling with, the one in the lounge room, is an Akai VJ6015FHD.  The other is a LG, which is fractionally worse in that I'm not getting any visual output at all.  I believe that if I can solve the first one I'll have the key to the second one... for when I get around to it.

Incidentally, if ***anybody*** can come up with a link to the latest software update for this television I would be inexpressibly grateful (but would still attempt to express my gratitude).  But back to the issue at hand...

I can't play with the boot parameters using 'e' because the HDMI output from the NUC is "unsupported" until after Mythbuntu has loaded and displayed the desktop.

However, as long as I'm not risking hanging the machine entirely, I can play with config files and not have to worry about whether the display shows at all.  I'm doing most of the work through SSH on my laptop anyway.

The output from your suggested diagnostic commands is here (sorry, couldn't get attachment windowlet to work):

```
=====================================================================
lsb_release -a
---------------------------------------------------------------------
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial
---------------------------------------------------------------------
 
=====================================================================
uname -a
---------------------------------------------------------------------
Linux mythbase 4.4.0-77-generic #98-Ubuntu SMP Wed Apr 26 08:34:02 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
---------------------------------------------------------------------
 
=====================================================================
lspci -nn
---------------------------------------------------------------------
00:00.0 Host bridge [0600]: Intel Corporation Device [8086:2280] (rev 21)
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:22b1] (rev 21)
00:13.0 SATA controller [0106]: Intel Corporation Device [8086:22a3] (rev 21)
00:14.0 USB controller [0c03]: Intel Corporation Device [8086:22b5] (rev 21)
00:1a.0 Encryption controller [1080]: Intel Corporation Device [8086:2298] (rev 21)
00:1b.0 Audio device [0403]: Intel Corporation Device [8086:2284] (rev 21)
00:1c.0 PCI bridge [0604]: Intel Corporation Device [8086:22c8] (rev 21)
00:1c.1 PCI bridge [0604]: Intel Corporation Device [8086:22ca] (rev 21)
00:1c.2 PCI bridge [0604]: Intel Corporation Device [8086:22cc] (rev 21)
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:229c] (rev 21)
00:1f.3 SMBus [0c05]: Intel Corporation Device [8086:2292] (rev 21)
02:00.0 Network controller [0280]: Intel Corporation Wireless 3165 [8086:3165] (rev 81)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
---------------------------------------------------------------------
 
=====================================================================
glxinfo|egrep "OpenGL vendor|OpenGL renderer*"
---------------------------------------------------------------------
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) HD Graphics 400 (Braswell) 
---------------------------------------------------------------------
 
=====================================================================
xrandr
---------------------------------------------------------------------
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
HDMI2 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 575mm x 323mm
   1920x1080     60.00*+  60.00    50.00    59.94    24.00    23.98  
   1920x1080i    60.00    50.00    59.94  
   1680x1050     59.88  
   1280x1024     60.02  
   1280x960      60.00  
   1360x768      60.02  
   1280x800      59.91  
   1280x720      60.00    50.00    59.94  
   1024x768      60.00  
   800x600       60.32    56.25  
   720x576       50.00  
   720x576i      50.00  
   720x480       60.00    59.94  
   720x480i      60.00    59.94  
   640x480       60.00    59.94  
   720x400       70.08  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
---------------------------------------------------------------------
```

---

### Post by walterav on 2017-05-15
HDMI can handle both RGB and YUV video signals, the viewsonic monitor probably use RGB signal (DVI compatible?) and the televisions in your house probably YUV. My guess is that the opensource intel driver doesn't do correct YUV signal.

Have you tried a different hdmi cable, maybe there are bios settings to force the HDMI in a certain mode?

Please try newest ubuntu 17.04 or even alpha/beta or daily build on a USB stick to see if the graphic stack improves, the other option is to test Windows 10 which can be download and tested in trial period without the need for registration. Than you are sure if its hardware or software related.

---

### Post by paul-norbealun on 2017-05-16
Alright, those are ideas for me to follow up.  I hadn't thought of Windows evaluation version and I'd wondered whether Windows would work...

In the meantime, just in case I get reckless, do you have any pointers on where the Mythbuntu equivalents of xorg.conf or XF86Conf might live?

---

### Post by walterav on 2017-06-13
I'm having a similar issue on a Intel Baytrail based nuc from Zotac CI320NANO-P, it will only display HDMI output on television (50/60hz only, no 23.976 nor 24p) from Windows10 not in Ubuntu. During BIOS/UEFI and in Ubuntu there is just no signal on the television(which is forced to ycbcr 422 tv broadcast standard instead of RGB). 

This might be the cause, libdrm version 2.4.7x will fix "HDMI YCBCR output handling in DRM layer" will try a ubuntu 17.10 daily iso with libdrm 2.4.80 and kernel 4.11 and let you know:
[https://lwn.net/Articles/719729/](https://lwn.net/Articles/719729/)

Does your television has a PC/RGB-mode setting for the HDMI input being used, that might work as a workarond?

---

### Post by walterav on 2017-07-08
Using a other HDMI cable and a other input on the HDMI receiver fixed correct output for me, both during POST and in Ubuntu Linux although being RGB only.

---

