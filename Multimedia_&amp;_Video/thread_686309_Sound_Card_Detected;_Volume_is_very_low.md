---
title: "Sound Card Detected; Volume is very low"
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by shankarganesh on 2008-02-03
Hi all,

I recently installed Feisty here, and all went well. My sound card got detected, but the volume is very low. How can I fix this?

Here's the output I got when I ran the hwinfo --sound command on my system:

```
12: PCI 1b.0: 0403 Audio device
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_8086_2668
  Unique ID: u1Nb.2HWUYaI85QD
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Hewlett-Packard Company 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2668 "82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x2a29 
  Revision: 0x04
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xffa3c000-0xffa3ffff (rw,non-prefetchable)
  IRQ: 19 (1054262 events)
  Module Alias: "pci:v00008086d00002668sv0000103Csd00002A29bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```

Please help me out, Thank You!

---

### Post by jan quark on 2008-02-03
stupid question

did you check the volume control ?

go to system > preferences > sound there you can check your sound configuration
and when you right click on the volume control and select open volume control you can also increase the sound volume

I hope it is that easy if not please tell us

---

### Post by shankarganesh on 2008-02-03
Hey, I'm not stupid.
In volume control, the level is UP and maximum, but still the volume is low.
Please help, thanks.

---

### Post by Toet on 2008-02-03
Have you tried alsamixer from a terminal?

---

### Post by prelude on 2008-02-03
I have the same problem as OP has

everything is turned up to the max volume but when I play some video or music the outputted sound is so low I can barely hear it. I have to get up close and personal with my speakers to hear what's being played.

```

23: PCI 1d.0: 0403 Audio device                                 
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_10b9_5461
  Unique ID: 1GTX.6BS8+jqTkd4
  SysFS ID: /devices/pci0000:00/0000:00:1d.0
  SysFS BusID: 0000:00:1d.0
  Hardware Class: sound
  Model: "ASUSTeK High Definition Audio/AC'97 Host Controller"
  Vendor: pci 0x10b9 "ALi Corporation"
  Device: pci 0x5461 "High Definition Audio/AC'97 Host Controller"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x817f 
  Revision: 0x02
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xdbcf4000-0xdbcf7fff (rw,non-prefetchable)
  IRQ: 22 (40944 events)
  Module Alias: "pci:v000010B9d00005461sv00001043sd0000817Fbc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

From the looks of hwinfo it seems me and shankarganesh is using the same audio driver


Edit: I should learn to search more.. ;)
I found a solution to my problem. in a console I entered ```
alsamixer
``` and got access to all the channels. turned out that the "side" channel adjusted my main output volume.

OP, I believe you might have the same problem, what's line out in windows is not line out in ubuntu ;)

---

### Post by Romanovzky on 2008-02-03
I had the same problem, this worked for me:

[http://ubuntuforums.org/showthread.php?t=373287&page=3](http://ubuntuforums.org/showthread.php?t=373287&page=3)

---

### Post by shankarganesh on 2008-02-03
> **prelude said:**
> I have the same problem as OP has

everything is turned up to the max volume but when I play some video or music the outputted sound is so low I can barely hear it. I have to get up close and personal with my speakers to hear what's being played.

```

23: PCI 1d.0: 0403 Audio device                                 
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_10b9_5461
  Unique ID: 1GTX.6BS8+jqTkd4
  SysFS ID: /devices/pci0000:00/0000:00:1d.0
  SysFS BusID: 0000:00:1d.0
  Hardware Class: sound
  Model: "ASUSTeK High Definition Audio/AC'97 Host Controller"
  Vendor: pci 0x10b9 "ALi Corporation"
  Device: pci 0x5461 "High Definition Audio/AC'97 Host Controller"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x817f 
  Revision: 0x02
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xdbcf4000-0xdbcf7fff (rw,non-prefetchable)
  IRQ: 22 (40944 events)
  Module Alias: "pci:v000010B9d00005461sv00001043sd0000817Fbc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

From the looks of hwinfo it seems me and shankarganesh is using the same audio driver


Edit: I should learn to search more.. ;)
I found a solution to my problem. in a console I entered ```
alsamixer
``` and got access to all the channels. turned out that the "side" channel adjusted my main output volume.

OP, I believe you might have the same problem, what's line out in windows is not line out in ubuntu ;)

this did not solve my problem.

edited /etc/modprobe.d/alsa-base, tried alsamixer, all volume is up but i still hear the sound in the same level of volume. it's still low.

---

### Post by prelude on 2008-02-03
alsamixer did the trick for me, it's to bad it didn't for you and I'm sorry but I can't help you any further.

---

