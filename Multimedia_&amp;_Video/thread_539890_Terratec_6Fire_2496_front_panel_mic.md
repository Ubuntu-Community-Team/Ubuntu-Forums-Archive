---
title: "Terratec 6Fire 24/96 front panel mic"
date: 2007-08-31
forum: Multimedia &amp; Video
---

### Post by Bobba on 2007-08-31
I'm having trouble with my front panel mic/phono input on my terratec soundcard. Ideally I'd have my keyboard plugged into the mic socket and jam away to music that I'm listening to on Rhythmbox, all coming out of the same soundcard, This works on dare i say it windows but i was hoping i could get it working on ubuntu. I suppose this also applies to anyone wanting to voip etc. 

Using Envy24Control I can hear the mic input by selecting Phono/Mic L and R under H/W Out 1 (L) and (R). However, this means that I can't hear anything from anything but the mic socket. I've had a look at qjackctl but haven't had much luck and don't know what im doing.

Has anyone else got their front mic sockets working at the same time as software produced sound?

Thanks for your help

---

### Post by Bobba on 2007-09-01
Another complication is that upon booting my computer today I appear unable to get any sound out at all :confused: even by testing all the options in 'sound preferences'
Help would be very much apprecitated!!!

---

### Post by Bobba on 2007-09-01
lspci

00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
01:05.0 Network controller: RaLink Wireless PCI Adapter RT2400 / RT2460
01:07.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
01:09.0 Communication controller: Rockwell International HCF 56k Data/Fax/Voice/Spkp (w/Handset) Modem (rev 01)
01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
03:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 315PRO PCI/AGP VGA Display Adapter

i.e. Terratec card isn't listed now and has changed to my motherboard soundcard

---

