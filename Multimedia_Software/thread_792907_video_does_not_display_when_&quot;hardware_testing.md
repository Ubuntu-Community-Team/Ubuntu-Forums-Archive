---
title: "video does not display when &quot;hardware testing&quot; after upgrade"
date: 2008-05-13
forum: Multimedia Software
---

### Post by hotpinkflamingo on 2008-05-13
Hello,After I upgraded to 8.04 when I go through the "hardware testing" wizard the video no longer displays. 
(on the "Did you see color bars and static?" screen)
It worked with 7.10.  What would cause that to happen?  
I would say what video card I have, but don't know how to find out.

---

### Post by hermes0710 on 2008-05-13
```
lspci
```

---

### Post by hotpinkflamingo on 2008-05-13
This is what I get when I run that code in terminal:

00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by hotpinkflamingo on 2008-05-26
I have Ubuntu installed, and I also have the kubuntu desktop which I prefer to use as of late.
The video test wasn't working on either the KDE or Gnome desktops.  I reconfigured the xserver, and now in Gnome the video test works.  In the hardware drivers section, the ATI proprietary driver is unchecked.  When I try to turn on any desktop effects, the screen goes all white and I have to restart-and the effects are turned off when I do so.

When I try to log into the KDE desktop, I just get a blank white screen.  I had the effects turned on there, and they were working.  Has it suddenly decided it doesn't like them?  I don't know how to get to the KDE settings to turn them off where the screen is white......

Should I be using the proprietary driver?  What makes the screens go white?  I'm assuming it has something to do with my video card.
Would appreciate any advise.

---

