---
title: "Sound system killed itself"
date: 2006-06-24
forum: Multimedia &amp; Video
---

### Post by Timokl on 2006-06-24
Hi everybody,

I think around yesterday, I killed my soundsystem. :-#  There is no sound playback of any kind, not even the Gnome start-up sound. It might have happened while I was ripping a dvd with dvdrip - or to be precise: That was the first time I remarked something strange.

I try to give you as many details as possible - but I am relatively new to linux, and I don't know too much about the soundsystem, so if you need some more info, just tell me how I could get it. ;) 

I run Ubuntu Dapper on an Acer Aspire 5021NWLCi notebook. I use the newest kernel from the repos for AMD K7 cpu's - 2.6.15-25-k7.

The soundhardware is from ATI. See:

```
timo@ubuntu:~$ lspci
0000:00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
0000:00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
0000:00:06.0 PCI bridge: ATI Technologies Inc: Unknown device 5a38
0000:00:07.0 PCI bridge: ATI Technologies Inc: Unknown device 5a39
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
0000:00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
0000:06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0000:06:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:06:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0000:06:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0000:06:06.4 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
0000:06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
```

I also tried different media players (xmms, Mplayer, vlc, ...) and different sound drivers (ALSA, SDL, eSound, ...) -- no playback.

However, if I boot WinXP, then the sound works. So it should be a software problem. But how to solve it?

Any ideas on this???

Bye,
Timo

---

### Post by trorion on 2006-06-24
Try opening your volume control (on gnome just double-click the speaker on the control bar) and un-muting PCM.  The update appears to have muted this.

---

### Post by irv on 2006-06-24
Here is a link on sound in Linux: It might be overkill, but this how to tells you everthing you want to know about sound in Linux.
[[COLOR="Red"]http://tldp.org/HOWTO/Sound-HOWTO/index.html[/COLOR]]("http://tldp.org/HOWTO/Sound-HOWTO/index.html")

---

### Post by Timokl on 2006-06-25
[QUOTE=trorion]Try opening your volume control (on gnome just double-click the speaker on the control bar) and un-muting PCM.  The update appears to have muted this.[/QUOTE]

Thanks a lot, that did it!!! 

I am just surprised that right after updating it was not muted, but it works now!

Thanks!!!

Bye,
Timo

---

### Post by Timokl on 2006-06-25
[QUOTE=irv]Here is a link on sound in Linux: It might be overkill, but this how to tells you everthing you want to know about sound in Linux.
[[COLOR="Red"]http://tldp.org/HOWTO/Sound-HOWTO/index.html[/COLOR]]("http://tldp.org/HOWTO/Sound-HOWTO/index.html")[/QUOTE]

Thank you, too! Indeed, it's a little bit overkill, but next time I have a problem, I will look there first. ;) 

Bye,
Timo

---

