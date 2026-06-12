---
title: "Dual monitor resolution issues with 9.10"
date: 2010-01-11
forum: Multimedia Software
---

### Post by roboa1983 on 2010-01-11
Hello:
I recently upgraded to 9.10 after a pretty happy time under 9.04. I use an Dell Inspiron 1420 laptop and often use a 20" Acer X203H as dual monitor. Under the previous distribution I had no problem loading the appropriate resolution (1600x900 if I remember correctly).

However, with the most recent upgrade, I cannot access that resolution. It is possible that I need to play with xorg.conf, but I want to avoid it since ubuntu does so as well. Moreover, this is a laptop and I will not use the dual monitor all the time. 

I have looked around for the solution to this problem to no avail. 

The lspci output I obtain is:
> 
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)


Thank you for the help,

Roberto

---

### Post by roboa1983 on 2010-01-30
*bump*

---

### Post by rogue_0111 on 2010-01-30
For dual screens I use:
  
[FONT=DejaVu Sans]lxrandr[/FONT]

[FONT=DejaVu Sans]I installed from Terminal with:

 apt-get install lxrandr

--
[/FONT]

---

### Post by roboa1983 on 2010-01-31
Rogue_0111:
Thanks for your reply.
What do you mean with the prefix to lxrandr? What is its function?

> **rogue_0111 said:**
> For dual screens I use:

 p, li { white-space: pre-wrap; }  [FONT=DejaVu Sans]lxrandr[/FONT]

[FONT=DejaVu Sans][/FONT]

[/FONT]

On another note, I just tried lxrandr. The problem is that the resolution I work with, 1600x900, does not show up...

Thanks again!

---

### Post by Kixtosh on 2010-01-31
Piggyback please, since I have the same issue:

- Toshiba Portégé 3490CT
- HP f1905 external LCD monitor sometimes used

I won't give any extra details just yet, since that might derail the thread for the OP, I'm just hoping his solution might help me out too.

---

### Post by roboa1983 on 2010-02-10
I have not been able to solve this problem, but as an update, a slightly smaller monitor (18") does display a dual monitor. Then, it seems the problem is related to the 1600x900 resolution for this 20" monitor...

Any ideas?

---

### Post by Kixtosh on 2010-02-10
I never found a solution for my case. If I set the BIOS to "simultaneous" display, the 19" LCD got the same 1024x768 resolution as the Portégé's internal monitor. If I set the BIOS to "auto-select", the 19" external display only would come on, but with just 800x600. Either way, it was useless to me, so I've given up until I have enough time to research the issue more thoroughly ... ugh!

No matter what I did, I could never get the display settings menu to display more than one screen, even when both were working together. Nor could I switch from the laptop screen to the external screen or vice versa.

I wish I had better news to report.

---

### Post by roboa1983 on 2010-02-10
Kixtosh:

Thanks for the reply. So you're setting the changes directly from BIOS? I suppose you've tried it inside 
System -> Preferences -> Display
right?

---

### Post by Kixtosh on 2010-02-10
I only played with the preferences from BIOS when I couldn't get the second screen to come up at all from inside Ubuntu (now using Xubuntu). 
 
When using a Windows O.S. (W2K or XP) I 've never had to fiddle with the BIOS at all. After starting up with a second monitor attached, I can just use the Fn+F5 key combination to toggle between either the internal or external display,s no displays (blank screen), or both displays at the same time. I can also use the usual Windows menus for selecting if I want identical display content or an extended desktop (I think this is not possible with W2K or earlier), etc. ...
 
Anyway, with Ubuntu, if I start up with the external monitor connected, all I get is that crappy resolution mentioned already. Toshiba BIOS settings allow the user to choose between "auto-selected" and "simultaneous". The only way to get both working in any way at all was to change the BIOS setting, but 1024x768 for 19" really isn't very useful to me, and none of the other advantages of dual monitors can be activated either, so I'll wait until I find a solution before using it again. 
 
As for the settings menu, currently, it doesn't matter if I select "clone" or whatever, the laptop's internal screen never comes on, and none of the higher resolutions for the external monitor are available to select when it is the only one in use (using the default BIOS, "auto-select" mode). 
 
I should probably have another try with this, now that I'm using Xubuntu instead, since some things have worked differently than they did with a regular Ubuntu install (and mostly better, perhaps because this is an older, "technically challenged" laptop).

---

### Post by Kixtosh on 2010-02-10
Tried connecting the external monitor with Xubuntu (also Karmic Koala). Exact same result as Ubuntu. Oh well, it was worth a shot, and at least it makes sense ... I think ... !

---

### Post by roboa1983 on 2010-02-21
Hello:

Indeed, for Intel graphics, we need to revert to the previous version of the intel drivers.

This page:
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Fix_Intel_graphics_resolution_problems](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Fix_Intel_graphics_resolution_problems)

led me to the solution in this page:
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

I hope it helps someone else. Thanks for the help!

---

### Post by efflandt on 2010-02-21
lxrandr apparently does not show you any more resolutions than System > Preferences > Display would show you in gnome.  So you would need to add the modeline(s) or mode(s) you want in xorg.conf (which I have not tried, since it does not exist) or with **xrandr**.

See [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

I am just using standard modules in Ubuntu 9.10.  **xrandr** shows that my VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) can be set to maximum 4096 x 4096.  So it should have no trouble adding a 1600x900 mode.

If you booted with the external display on with PC input selected (or re-logged into X after connecting it) you may be able to find a resolution that was recognized in /var/log/Xorg.0.log, but not active (even if it would work with proper timings).

For example, HDTV says it is 1366x768, but its closest mode in Xor.0.log is 1360x765 (WinXP uses 1360x764):

(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)

Apparently because the laptop display does not have such a mode (larger than its 1280x800), X does not offer that mode.  If I give it a **cvt** like name, it works for xrandr in a script (which also turns off laptop display):

```
#!/bin/bash
xrandr --newmode "1360x765_60.00"   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync
xrandr --addmode VGA1 1360x765_60.00
xrandr --output VGA1 --mode 1360x765_60.00
xrandr --output LVDS1 --off
exit
```For a 1080p HDTV, cvt was not even close (off center pillar boxed), so I got a 1920x1080 mode from Xorg.0.log of a DVI to HDMI connected desktop to use in a similar script when connecting VGA to that (picture perfect).

---

### Post by roboa1983 on 2010-02-21
Hello:

Thanks! It makes sense to try this with the most recent packages, though I have always been hesitant to manipulate xorg.conf due to previous disastrous and time-consuming results.

> 
```
#!/bin/bash
xrandr --newmode "1360x765_60.00"   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync
xrandr --addmode VGA1 1360x765_60.00
xrandr --output VGA1 --mode 1360x765_60.00
xrandr --output LVDS1 --off
exit
```For a 1080p HDTV, cvt was not even close (off center pillar boxed), so I got a 1920x1080 mode from Xorg.0.log of a DVI to HDMI connected desktop to use in a similar script when connecting VGA to that (picture perfect).

---

