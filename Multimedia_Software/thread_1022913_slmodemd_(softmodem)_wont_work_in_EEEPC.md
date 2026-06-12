---
title: "slmodemd (softmodem) wont work in EEEPC"
date: 2008-12-27
forum: Multimedia Software
---

### Post by weblordpepe on 2008-12-27
Hi guys
I'm trying to get the software modem **slmodemd** (smartlink softmodem) working on my EEEPC but I'm running into troubles relating to the intel audio chip. 

* Note this is a 100% software only modem that woks via the soundcard. 

The software installs & creates a modem however I get no noise out of the speakers.

When **slmodemd** is set to use ALSA device **hw:0** the 'modem' returns an error when I send an ATA (answer string):
```
NO CARRIER
ERROR
```
It also shows in the slmodemd console window:
```
error: cannot set channels for playback: Invalid argument
```

When I type **slmodemd -a** to use the default ALSA device I get the following:
```
error: mixer setup: attach hw:1 error: No such file or directory
ALSA lib confmisc.c:768:(parse_card) cannot find card '1'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline:CARD=1,DEV=0
error: alsa setup: cannot open playback device 'modem:1': No such file or directory
error: cannot setup device `modem:1'

```

The software can work completely in ALSA mode with no special hardware. I have the following hardware:
```
pepe@weee:~$ hwinfo --sound
22: PCI 1b.0: 0403 Audio device                                 
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_8086_2668
  Unique ID: u1Nb.PHGlf707Hc8
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "ASUSTeK 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2668 "82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x82a1 
  Revision: 0x04
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xf7eb8000-0xf7ebbfff (rw,non-prefetchable)
  IRQ: 5 (1409 events)
  Module Alias: "pci:v00008086d00002668sv00001043sd000082A1bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

I have another box with a SoundBlaster Live, and it works flawlessly. However my EEEPC with an intel sound chip doesn't want to go.

I've tried both the latest source/compiled version of soundmodem and the ubuntu deb, and they both give me the same trouble.

* How do I find out my version of ALSA, and do I need the latest version?
* Which kernel module should I load / have loaded?
* Which ALSA device should I specify?
[INDENT]I have tried hw:0 hw:0,0 hw:1 modem:0 modem:1 and all sorts[/INDENT]

---

