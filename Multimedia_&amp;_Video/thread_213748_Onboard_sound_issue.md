---
title: "Onboard sound issue"
date: 2006-07-11
forum: Multimedia &amp; Video
---

### Post by orbish on 2006-07-11
Running: Ubuntu Dapper Drake 6.06, kernel 2.6.15-23-386

Okay, I've downloaded a test audio file (ogg) that seems to be playing in XMMS, but with no sound. Well by playing, I mean, it's decoding the file. My current setup is SPDIF out to my reciever to 5.1 surround sound. I have tried using the line out jacks as well, they aren't working either. When I open XMMS through terminal (root) I get the following error:

Message: device: hw:0,0

I've tried Rhythmbox and it doesn't work either.

Here's my lspci output:

[SIZE="1"]0000:00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
0000:00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridge (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4600] (rev a3)
0000:02:01.0 Ethernet controller: Intel Corporation 82547GI Gigabit Ethernet Controller
0000:03:03.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
0000:03:04.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
0000:03:05.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)
0000:03:06.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
0000:03:06.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
0000:03:06.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)[/SIZE]

I've tried the help file with sound in this forum, but I don't have alsa-source nor can I find it in my package manager, it's really frustrating.](*,) 

Any help/suggestions would be deeply appreciated... getting sound is one step closer to me completely switched over. Next would be my tuner cards =P

---

### Post by orbish on 2006-07-11
oh here my system specs if it will help

Stock 350W PSU | ABIT IC7-MAX3 Mobo | P4 2.8 Prescott | 2GB DDR400 Corsair RAM | GeForce4 Ti4600 | 1x120GB WD IDE HDD 8MB cache | 1x300GB WD SATA HDD 8MB cache | Hauppaguge WinTV-PVR-150 | ATI HDTV Wonder | Logitech 3000 Webcam | 16x DVD-RW


I should have added that to a signature, but this was my first post on the forum

---

