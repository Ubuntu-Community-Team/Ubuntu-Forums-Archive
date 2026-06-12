---
title: "Sound card issues"
date: 2010-08-11
forum: Multimedia Software
---

### Post by Justasic on 2010-08-11
well I probably should be posting this in the Backtrack forums but I didn't want to deal with hackers and drivers.

I have Backtrack 4 RC1 and I have gone through 3 sound cards so far. none have worked and I am starting to get frustrated.

I have tried so far a PCI card, On-board audio, and a usb audio card.

PCI: C-Media CM8738
USB: M-Audio Mobile PRE
On-board: ATI IXP SB400 AC'97 Audio controller

Alsamixer says "alsamixer: function snd_ctl_open failed for default: no such device", any other mixer doesn't show the device or gives similar errors.

lspci -v says:
Multimedia audio controller: C-Media Electronics Inc CM8738 (rev ff) (prog-if ff)
!!! Unknown header type 7f
Kernal modules: snd-cmipci

I don't care what I have to do to get this to work, I just want a solution to my audio problem.
Even if I have to install a new kernal or rip apart this linux distro to get it to work.

rest of my hardware
CPU: AMD Athlon 64 Processor 3200+
Ram: 1004 mb ddr
Motherboard: E-machines MS-7145
Graphics card: Nvidia GeForce 8600 GT
HDD: 40GB Maxtor 6E040L0
WIFI: BCM4318 [AirForce One 54g] 802.11 Wireless LAN controller
Ethernet: RTL-8139/8139C/8139C+
USB mouse and PS2 Keyboard

---

