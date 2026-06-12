---
title: "Ubuntu intrepid....sound just seems to &quot;die&quot;"
date: 2009-02-07
forum: Multimedia Software
---

### Post by robfindlay on 2009-02-07
Here is my lspci (please forgive the non-relevent parts) 

00:00.0 Host bridge: ALi Corporation M1647 Northbridge [MAGiK 1 / MobileMAGiK 1] (rev b0)
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:0a.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
00:0b.0 Multimedia audio controller: Ensoniq 5880B [AudioPCI] (rev 02)
00:0c.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0c.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:0d.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
00:0e.0 RAID bus controller: HighPoint Technologies, Inc. HPT366/368/370/370A/372/372N (rev 05)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3 Ti 200] (rev a3)

I'm not sure what is hanging up where, but this seems to happen randomly and the only fix that seems to work is a reboot.

Does someone know a command line sequence I can run to reinitialize or reboot the sound card / sound server? 

TIA

Rob

---

### Post by robfindlay on 2009-02-07
Bump?

---

### Post by kostkon on 2009-02-07
There are two possibilities. Either some application blocks the card and so *PulseAudio* can't continue to work and you lose sound on your desktop or *PulseAudio* is crashing, and again obviously you lose your sound. In both cases a reboot of corrects the problem.

To check if *PulseAudio* crashes, the next time you lose your sound check in your *syslog* for any error messages from *PulseAudio*. To access it, go to *System &#8594; Administration &#8594; System Log*. If you don't see it in the list of logs, add it by selecting *File &#8594; Open* and go to the */var/log* folder.

If you think an application blocks the sound card, then when this happens, check what applications you are running (the ones that produce sound, obviously). One of them must be the culprit.

---

### Post by robfindlay on 2009-02-07
> **kostkon said:**
> There are two possibilities. Either some application blocks the card and so *PulseAudio* can't continue to work and you lose sound on your desktop or *PulseAudio* is crashing, and again obviously you lose your sound. In both cases a reboot of corrects the problem.

To check if *PulseAudio* crashes, the next time you lose your sound check in your *syslog* for any error messages from *PulseAudio*. To access it, go to *System &#8594; Administration &#8594; System Log*. If you don't see it in the list of logs, add it by selecting *File &#8594; Open* and go to the */var/log* folder.

If you think an application blocks the sound card, then when this happens, check what applications you are running (the ones that produce sound, obviously). One of them must be the culprit.


I'm thinking it's crappy web embedded sound aps that stay running when firefox crashes.

---

