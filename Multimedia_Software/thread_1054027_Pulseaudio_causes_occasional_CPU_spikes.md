---
title: "Pulseaudio causes occasional CPU spikes"
date: 2009-01-29
forum: Multimedia Software
---

### Post by Zhatan on 2009-01-29
Hi, I am a new user of Ubuntu and Linux and so far I like it but I don't know muc habout how it works or how to fix problems so I'd like some help.

I noticed the problem while listening to a mp3, the sound would stop for about 2-3 sec once or twice during a 3 min song. I then tried youtube and found that the issue was not related to mp3's since both the audio and video stopped on youtube in the same manner.

I then used the system monitor to see if the problem was caused by cpu usage and I detected a cpu spike from pulseaudio when the sound stopped. The cpu spiked to about 90% and then went back down but since the refresh on system monitor is one sec it is possible it spiked to 100% and went back down before the next refresh.

Anyway it seems that pulseaudio is the culprit. Any input and suggestions are welcome!

Also I forgot to say im using Ubuntu 8.10!

EDIT
Also I have tried the sound problem solution guide but nothing in there seems to help

---

### Post by Zhatan on 2009-01-30
Update

I have tried to use my usb-headset instead of pulseaudio in the sound options and that made the problem go away but instead I get a more frequent split second stuttering. I'm not sure if the problems are related or not. Any input would be welcome.

---

### Post by halovivek on 2009-01-30
Could you please post this output ?
In terminal type

lspci

---

### Post by Zhatan on 2009-01-30
Right, here it is:

00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
00:08.0 RAID bus controller: Promise Technology, Inc. PDC20378 (FastTrak 378/SATA 378) (rev 02)
00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X850Pro]
01:00.1 Display controller: ATI Technologies Inc R480 [Radeon X850Pro] (Secondary)

---

### Post by Zhatan on 2009-01-31
Following this advice solved the problem by removing pulseaudio and using esound instead. 

[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)

---

