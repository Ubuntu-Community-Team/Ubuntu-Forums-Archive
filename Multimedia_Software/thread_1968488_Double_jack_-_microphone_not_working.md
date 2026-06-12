---
title: "Double jack - microphone not working"
date: 2012-04-29
forum: Multimedia Software
---

### Post by zcout on 2012-04-29
Hello,

I have a netbook with some kind of "double" jack - you can connect both audio output and input there. And while the audio output is working, I can't seem to configure the input after several attempts with ALSA.

Testing with my headphones - if I connect them to my iPhone, they work as expected, so I guess the problem is in my ALSA configuration as it probably doesn't recognize the microphone correctly.

I'm using Lubuntu Oneiric x86 on netbook: Asus Eee PC 1015BX-BLK165S.

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

```
$ hwinfo --sound
09: PCI 01.1: 0403 Audio device                                 
  [Created at pci.318]
  Unique ID: mnDB.t33_nio85b3
  SysFS ID: /devices/pci0000:00/0000:00:01.1
  SysFS BusID: 0000:00:01.1
  Hardware Class: sound
  Model: "ATI Audio device"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x1314 
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x84a4 
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfeb44000-0xfeb47fff (rw,non-prefetchable)
  IRQ: 40 (54 events)
  Module Alias: "pci:v00001002d00001314sv00001043sd000084A4bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

18: PCI 14.2: 0403 Audio device
  [Created at pci.318]
  Unique ID: 5Dex.flNwR3gtgu9
  SysFS ID: /devices/pci0000:00/0000:00:14.2
  SysFS BusID: 0000:00:14.2
  Hardware Class: sound
  Model: "ATI SBx00 Azalia (Intel HDA)"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4383 "SBx00 Azalia (Intel HDA)"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x8437 
  Revision: 0x40
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfeb40000-0xfeb43fff (rw,non-prefetchable)
  IRQ: 16 (98726 events)
  Module Alias: "pci:v00001002d00004383sv00001043sd00008437bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```

How am I supposed to configure ALSA correctly?

---

### Post by Rodney9 on 2012-04-29
sudo apt-get install pavucontrol

PulseAudio, previously known as Polypaudio, is a sound server for POSIX and WIN32 systems. It is a drop in replacement for the ESD sound server with much better latency, mixing/re-sampling quality and overall architecture.

PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume control tool (mixer) for the PulseAudio sound server. In contrast to classic mixer tools this one allows you to control both the volume of hardware devices and of each playback stream separately. It also allows you to redirect a playback stream to another output device without interrupting playback.

Thanks To ZekeGraal

---

### Post by zcout on 2012-04-29
And what am I actually supposed to do, except installing the app?

---

