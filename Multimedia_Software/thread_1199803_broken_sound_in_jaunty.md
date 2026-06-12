---
title: "broken sound in jaunty"
date: 2009-06-29
forum: Multimedia Software
---

### Post by mateuszzz on 2009-06-29
hello
After fresh install of kubuntu jaunty, sound seemed to work ok. Sadly, every time after some playing (say 1 minute) sound goes extremely... wrong. It's as it were trying to repeat itself and start again multiple times.
Search (google & forums) gives lots of output about sound not playing at all (for me works for short time after reboot) with intel sound cards (not my case as well). I though it's PulseAudio's fault, but kubu doesn't have it. I tried to install gnome-desktop, but that doesn't give new options in systemsettings/multimedia. BTW sound doesn't seem to work in gnome at all, but that doesn't worry me.
My card is:
```
mateuszzz@mateuszzz-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
**00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)**
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```
It's Asus A6R laptop. I had to (as always with ubu) to mute external amplifier to have sound work at all.
What can I do to fix the sound?

---

### Post by hhhumbert on 2009-07-04
Hi,
These guys ([http://ubuntuforums.org/archive/index.php/t-1033041.html) ]("http://ubuntuforums.org/archive/index.php/t-1033041.html")recommend using OpenSound[ (]("http://ubuntuforums.org/archive/index.php/t-1033041.html")[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)) instead of ALSA on Ubuntu. Installed it 5 minutes ago, and still working :) Guess you should do some additional tinkering to get it work on KDE (I am _very_ newbie), but it well may be worth the effort.
Cheers,
hhhumbert

---

