---
title: "blank/corrupted windows, then black screen on 64-bit 10.04 Lucid Ubuntu"
date: 2010-07-12
forum: Multimedia Software
---

### Post by TrombaMarina on 2010-07-12
I'm attaching a screenshot of the kind of corruption I see before the Black Screen of Death.  Shortly after a few non-fatal display issues, the whole screen goes blank except for a single underscore in the upper left-hand corner (presumably it's a cursor in a character display mode).  After 2.5 seconds, the mouse pointer appears in the center.  A half-second later, I can move the mouse.  After 4 seconds (total), I sometimes see a flicker of what looks like startup messages.  I was able (after about 50 tries) to catch it with my camera before they disappeared (see the second attachment).  Here is the text:

```
* Speech-dispatcher configured for user sessions
* Starting VirtualBox kernel module
* done
* Starting Common Unix Printing System: cupsd
* PulseAudio configured for per-user sessions
* Enabling additional executable formats binf
* Checking battery state...
```

Then the screen blanks and the process repeats with the single solid underscore in the upper-left-hand corner for 2.5 seconds.  I'm not sure if this is an issue with the video driver or window manager, or what.  I have an on-the-motherboard Intel graphics card, no choice of drivers (that I can see), so I must be using the open-source driver.  Under 64-bit linux, I can see my 8GB of memory, but I get the Black Screen of Death after some interactive use, especially when invoking 2-D graphics (resizing windows, typing, etc.).  Under 32-bit 10.04 Lucid, everything seems pretty good (though I can only see 3 GB of memory) - that's what I used to write this report.  I was able to see a little corruption here and there, but no crash.  I think this is a display issue, more than a 64-bit issue, but in 32-bits it doesn't seem to crash.

My video card is an Intel:

```
desktop:/var/log$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
desktop:/var/log$ sudo lshw -C video
  *-display:0             
       description: VGA compatible controller
       product: 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:27 memory:fe400000-fe7fffff memory:d0000000-dfffffff(prefetchable) ioport:cc00(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:fe800000-fe8fffff
```


```
desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:04.0 IDE interface: Integrated Technology Express, Inc. IT8213 IDE Controller
03:08.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
```

---

### Post by TrombaMarina on 2010-07-13
I was able to completely fix this issue by adding the following to the "Device" section of my xorg.conf:

Option    "DRI"    "False"

DRI stands for Direct Rendering Infrastructure:
[http://en.wikipedia.org/wiki/Direct_Rendering_Infrastructure](http://en.wikipedia.org/wiki/Direct_Rendering_Infrastructure)

I think that disabling DRI disables direct graphics acceleration, but I'm not sure if that means it's using all software rendering or just passing all the commands through the X-window system before getting to the graphics hardware.  In any case, the load on my CPU seems much higher when dragging/resizing windows.

The latest 10.04 doesn't have an xorg.conf by default so you have to make one if you want to disable DRI:

[LIST]
[*]close all your windows
[*]press Ctrl-Alt-F1 to go to a text console
[*]sudo stop gdm
[*]Xorg -configure
[*]sudo cp /home/myname/xorg.conf.new /etc/X11/xorg.conf
[*]sudo start gdm
[/LIST]

Thanks to Marvin Wu for this!

This looks most similar to this bug:
[https://bugs.freedesktop.org/show_bug.cgi?id=26569](https://bugs.freedesktop.org/show_bug.cgi?id=26569)

Once again: Ubuntu 10.04, amd64/64-bit, Intel i915 driver

---

### Post by TrombaMarina on 2010-07-13
I entered a bug:
[https://bugs.freedesktop.org/show_bug.cgi?id=29046](https://bugs.freedesktop.org/show_bug.cgi?id=29046)

---

