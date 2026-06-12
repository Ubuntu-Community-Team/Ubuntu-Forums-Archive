---
title: "Ubuntu 5.10  no sound"
date: 2005-11-23
forum: Multimedia &amp; Video
---

### Post by oldman on 2005-11-23
Hi !
I have Creative Audigy v2 .  When I do a lspci I got:

0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS 645xx (rev 02)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 04)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:06.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:00:07.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:00:07.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0000:00:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
0000:00:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
0000:00:09.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 04)
0000:00:09.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
0000:00:0b.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
0000:00:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]
0000:01:00.1 Display controller: ATI Technologies Inc Radeon R300 [Radeon 9500 Pro] (Secondary)


As you se the sound card is found. When I look in System - User - Sound no cards are detected as default card. Also when I am running test on system sound nothing happends. No sound - no messages. The card did work on Ubuntu 5.04 .
Anybody has any tips ?

Thank you!

---

### Post by oldman on 2005-11-23
Hi !

I found out! It was all a question of authorisation. Probably I have answered too restrictive under install. I did not solve before I restartet the PC so I am not sure which of the groups I assigned my user that did the trick, but noe it is working...

---

### Post by Teroedni on 2005-11-23
Hey Great that you were able to get it work:) could you mark your thread as [Solved]
Thank you

---

