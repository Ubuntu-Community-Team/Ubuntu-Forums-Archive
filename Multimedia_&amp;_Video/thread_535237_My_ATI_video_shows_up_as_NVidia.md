---
title: "My ATI video shows up as NVidia?"
date: 2007-08-26
forum: Multimedia &amp; Video
---

### Post by TheGZeus on 2007-08-26
If there is a thread related to this already, feel free to direct me and delete, but I didn't find any.
Automatix detected NVidia, a command prompt identified the proper ATI video chipset(laptop) once I had my proper(proprietary) drivers installed OpenGL has worked fine.
However, when I tried to enable Compiz, even for a trial, once again, it showed that my Nvidia drivers weren't installed.

I'm confused...

Should I try switching to KDE from GNOME? Either one is fine by me. I'm confident I can configure either to work how I'd like.

I generally use FVWM-Crystal, but sometimes I want a little more 'complete' or 'pretty' environment.

---

### Post by Lord Illidan on 2007-08-26
I am confused now. Do you have an nvidia card or an ATI card?

What does lspci show please?

---

### Post by TheGZeus on 2007-08-26
HAHA. That's how I felt.

It's definitely an ATI card.
For some reason it seems that GNOME/XFCE apps, that look, see NVidia.

Here's the output VVVV Probably way more than you needed, but I figure better more than less...

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by TheGZeus on 2007-08-26
I'd like to note I've been considering removing GNOME entirely.
It's just not my speed.
I won't do anything until I hear otherwise, as I don't want to somehow make things worse.

---

### Post by tseliot on 2007-08-26
> **TheGZeus said:**
> If there is a thread related to this already, feel free to direct me and delete, but I didn't find any.
Automatix detected NVidia, a command prompt identified the proper ATI video chipset(laptop) once I had my proper(proprietary) drivers installed OpenGL has worked fine.
Automatix detected an Nvidia card but installed the ATI driver???

> **TheGZeus said:**
> However, when I tried to enable Compiz, even for a trial, once again, it showed that my Nvidia drivers weren't installed.
Who did show that Nvidia drivers weren't installed?

ATI+AIGLX+Compiz won't work. You will have to use XGL+Compiz.

---

### Post by Lord Illidan on 2007-08-26
Ah, ok, it is an ATI

01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)

I have the same kind of card on another AMD machine, and yes, you need to install XGL to use desktop effects. Try this howto : [http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)

---

### Post by TheGZeus on 2007-08-26
> **tseliot said:**
> Automatix detected an Nvidia card but installed the ATI driver???


Who did show that Nvidia drivers weren't installed?

ATI+AIGLX+Compiz won't work. You will have to use XGL+Compiz.

Nono, I installed tham with the command line. It was just an example of the weirdness.
I have the XGL drivers.
glxinfo |grep rendering
direct rendering: Yes

So it's not that I don't have hardware rendering, some programs are seeing the hardware as something else.

---

### Post by TheGZeus on 2007-08-27
Well, I followed that, and it failed miserably. Nautilus wouldn't launch, the desktop was buggy as hell...
Meh.  Eyecandy I can live without for now. I just wanted the option...
i've heard there are problems with my video chipset.
Well, if KDE doesn't somehow make it work, I might jsut wait for E17

---

