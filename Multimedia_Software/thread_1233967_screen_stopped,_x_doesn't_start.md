---
title: "screen stopped, x doesn't start"
date: 2009-08-07
forum: Multimedia Software
---

### Post by jmmmp on 2009-08-07
Hi,

just installed jaunty on my thinkcentre yesterday. I was working fine, and using my Radeon with dual screen with the open driver (didn't allow for the closed driver, because couldn't even acess the display settings with it).

After an x-hour work session, when I rebooted the ubuntu splash screen + progress bar came. But instead of X starting, the screen looks just weird (with a strange montage of bits that are probably still in memory), and nothing happens. Also ctrl-alt-del or other key combinations do nothing. The only thing I can do is switch the computer down. (the only way to get to a terminal is to boot with repair)
Booting with repair or with another kernel doesn't do anything. But, booting with live cd works. I compared xorg.conf from my partition with the one from live cd, and they match.

I guess something went wrong with the video setup, but have no idea what. After the sucessful work session there were no changed settings, and everything shut down ok.

Here is the output of lspci, and xorg.conf:

```
00:00.0 Host bridge: Intel Corporation 82946GZ/PL/GL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82946GZ/PL/GL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3450
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5786 Gigabit Ethernet PCI Express (rev 02)
0a:09.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 81)
```

(I removed the comments - haven't edited this file before)
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

Anyone has any ideas?

- - 
PS: A related subject, but not so urgent: When I choose the proprietary video driver, I can't open the settings->display window (and change the screen to dual, etc). The frame of the window opens, but the content doesn't. Also, one cpu starts working at 100%, and only stops when I reboot.

---

