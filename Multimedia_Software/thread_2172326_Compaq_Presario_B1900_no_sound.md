---
title: "Compaq Presario B1900: no sound"
date: 2013-09-04
forum: Multimedia Software
---

### Post by raicho on 2013-09-04
I've seen a couple of other threads regarding getting sound working on  the B1900 but as of yet have yet to find one that provides a concise  answer.  As the title would suggest, I can't get any sound out of my  B1900 running Lubuntu.  I've initially gone over items that people have  suggested to check across a number of threads and so far have done this  but found nothing that would suggest a solution:
[B]
lsusb[/B]
```
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

**lspci**
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI Device 5a31 (rev 01)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:04.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:05.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:12.0 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80)
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80)
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RC410M [Mobility Radeon Xpress 200M]
02:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 01)
08:07.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
08:07.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:07.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

**aplay -l**
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

**aplay -L**
```
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=SB
    HDA ATI SB, ALC260 Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, ALC260 Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC260 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC260 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC260 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC260 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC260 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=SB,DEV=0
    HDA ATI SB, ALC260 Analog
    Direct sample mixing device
dsnoop:CARD=SB,DEV=0
    HDA ATI SB, ALC260 Analog
    Direct sample snooping device
hw:CARD=SB,DEV=0
    HDA ATI SB, ALC260 Analog
    Direct hardware device without any conversions
plughw:CARD=SB,DEV=0
    HDA ATI SB, ALC260 Analog
    Hardware device with all software conversions
```

This is the output I got from alsa-info.sh
[www.alsa-project.org/db/?f=b18aa859e6496a31a6ead154fd37c2541586e41a]("http://www.alsa-project.org/db/?f=b18aa859e6496a31a6ead154fd37c2541586e41a")

As suggested by many threads, alsamixer indicates that the sound has definitely not been muted.

And I've also tried appending the following entry in my alsa-base.conf with no luck:
```
options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1
```

Having taken a look in the xfce4-mixer and the alsa mixer gui I can see only PulseAudio listed.

The  most recent activity I've seen on this problem was in January, and it  yielded no solution - perhaps some good folk out there can re-invigorate  the discussion a little!

---

### Post by raicho on 2013-09-04
It seems patience really is a virtue, after a little searching I found that Joey Jiao had already solved the problem: [https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/186698](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/186698)

The solution for me was simply to remove any additions I had made to **/etc/modprobe.d/alsa-base.conf **and use this one line instead:
```
options snd-hda-intel model=will
```

---

