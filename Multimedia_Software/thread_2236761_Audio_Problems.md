---
title: "Audio Problems"
date: 2014-07-28
forum: Multimedia Software
---

### Post by The_Foul_One on 2014-07-28
I am presently running Ubuntu 14.04 on a Medion laptop.
Internal speakers are working fine.
There is no signal to the headphone jack. Therefore I can not use external speakers.

Everything works fine with Microsoft windows.
I have tried several Linux distros such as Ubuntu, Linux Mint, Zorin, Kubuntu, etc.... I get the same results on all of them whether I have a full installation or running a "live" version from a USB drive. No headphone signal on any of them except microsoft windows. (mutes are off, volumes are up, etc...)
It seems to be a Linux thing.

After running lspci  in the terminal I get this;

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 Non-Raid-5 SATA
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI0)
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI1)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI2)
00:13.3 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI3)
00:13.4 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI4)
00:13.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB Controller (EHCI)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB600 IDE
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB600 PCI to LPC Bridge
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS690M [Radeon Xpress 1200/1250/1270]
01:05.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RS690 HDMI Audio [Radeon Xpress 1200 Series]
08:00.0 Network controller: Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

This has been bothering me for awhile now. Any ideas?
Thanks.

---

### Post by sp40140 on 2014-07-29
What drivers for video do you have installed. (go to launcher panel and search for "Additional drivers". You should see a list. take a screen shot and post it if you can. 
Take a screen shot of Audio settings and post.
What is the kernel version you are running (uname -r).

---

### Post by Bucky Ball on 2014-07-29
*Thread moved to **Multimedia & Video**.*

Welcome. You should have more luck here, and as you're new, we'll be gentle. ;) Anything you don't understand, just ask. 

Have you got Pulseaudio Volume Control installed? Should be in the Apps>Sound & Video (might be something else on your box). If you haven't, you can install via Software Centre. That will give you 'total control' over sound. Once installed, launch it and start an audio stream (play some music). You should see that in the 'Playback' tab of PAVC. Check the 'Output' make sure the stream is set to output to the headphone socket. You may need to experiment with the 'Output' tab also. 

Good luck.

---

### Post by Yellow Pasque on 2014-07-29
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by The_Foul_One on 2014-07-30
Thanks,
I have installed Lubuntu since the last post. Still the same problem.
The kernel version is (3.13.0-32-generic)
Here is a screen shot of the "additional drivers".. And, screen shot of audio settings while playing audio, both playback and output devices tabs.[IMG]http://www.fusiontunes.net/PAOD.png[/IMG][IMG]http://www.Fusiontunes.net/PAP.png[/IMG]
[IMG]http://www.Fusiontunes.net/AD.png[/IMG]

---

### Post by The_Foul_One on 2014-07-30
> **Temüjin said:**
> [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

ALSA information for my computer can be found here. [http://www.alsa-project.org/db/?f=22f1e7aa7516a4c152a33c77df5fc0ca3c683217](http://www.alsa-project.org/db/?f=22f1e7aa7516a4c152a33c77df5fc0ca3c683217)



Thanks

---

