---
title: "Separate X-Sessions without an N-Vidia card."
date: 2011-01-29
forum: Multimedia Software
---

### Post by Nillerz on 2011-01-29
I want to set up separate X-Sessions for my two monitors. One is an old CRT monitor which I will use as a TV due to it's size/resolution and the first is a laptop panel.

First off, I don't have an NVidia card, I am running Intel graphics.

Second, I have some general questions. First off would I need a separate desktop environment running on the second screen? How would I switch the focus between the screens? Is there anything else I should know about doing this?

And finally, how exactly do I do this?

This is my lspci readout:```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```

---

### Post by Nillerz on 2011-01-30
Nothin? Nobody?

---

### Post by BicyclerBoy on 2011-01-30
You need to create a /etc/X11/xorg.conf file..

AFAIK Xorg has a tool for this but it will only run if X server is stopped.
X -configure
[http://www.x.org/wiki/TitleIndex](http://www.x.org/wiki/TitleIndex)

But it is just as easy to find a simple intel xorg.conf file.
[http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html)

Then you need to add device monitor screen sections for your extra display.
If the display supports DDC EDID & is auto detected, then this will be easy.

The /var/log/Xorg.0.log file reveals lots of clues.
You will be able to find if display is auto-detected & the name of the wired port VGA-0 or VGA-2 etc..

---

### Post by Nillerz on 2011-01-30
Thanks for the reply.

So if I understand this correctly, I need to develop an xorg.conf file. I can do this if I shut down the X-server and use the command "Xorg -configure". Another way to accomplish this would be to find the contents of an already existing xorg.conf file, one specific to Intel, and put that there, modified slightly to support my purposes. Am I correct?

---

### Post by BicyclerBoy on 2011-01-30
Yes correct on both counts..

The intel dual head link should provide a starting point

Attached the simplest xorg.conf for use with intel driver.

This forum forces dos filename extension, so chop off the .txt bit...

---

### Post by Nillerz on 2011-01-30
I used the Xorg -configure command and it produced a xorg.conf file, which I've opened to view. I am comparing it to the one you provided and am trying to logic out exactly how it is set up. Do you have any info on where exactly I need to specify what goes where?

EDIT: I think I found something obvious and relevant...

```

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection
```

Would it be as simple as adding another "Monitor" section?

---

### Post by BicyclerBoy on 2011-01-30
No
As I said previous post..

Extra device screen & monitor sections (and a serverlayout section).

Just plug in external (2nd monitor) & reboot/restart.

The /var/log/Xorg.0.log  should reveal the wired port names..etc

The dual head link has a xorg.conf snippet that has clues..

The problem is finding out the wired port names LVDS TMDS VGA DVI HDMI etc..
(LVDS is internal panel)

---

### Post by Nillerz on 2011-01-30
I am trying to start them up as separate x-sessions, not as an extended desktop. I might have misunderstood you, but it sounds like you're trying to describe a way to add an extra monitor to the current x-session. At any rate, the monitors are LVDS1 and VGA1, if I remember correctly, because I needed to add a bizarre native resolution to the VGA monitor (2048x1536)

---

### Post by BicyclerBoy on 2011-01-30
Sorry
I should have realised you meant separate X sessions, multiple X servers..

No idea how to on that h/w.

AFAIK Need to determine if you need to use vesa or intel-free or intel closed driver.

---

### Post by Nillerz on 2011-01-31
I use the default Intel driver that comes with the OS. It seems to work out of the box and since it is included with the OS I'm guessing it's open.

---

### Post by Nillerz on 2011-02-11
:/

Nobody has done this before?

---

