---
title: "Sound does not work with headphones, but works otherwise"
date: 2010-03-17
forum: Multimedia Software
---

### Post by jrtayloriv on 2010-03-17
I am using Ubuntu 9.10.

My sound works fine unless I have headphones plugged in. I've tried 2 sets of headphones, and it doesn't work with either set, so it's not the headphones. The volume is not muted (it's at 100%) for the headphones either in alsamixer.  How can I diagnose and fix this?

lspci -v
01:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]
    Subsystem: Gateway 2000 Device 0562
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f3010000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
    Subsystem: Gateway 2000 Device 0562
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at f3300000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

---

### Post by jrtayloriv on 2010-03-18
bump

---

### Post by Yellow Pasque on 2010-03-18
You probably need to specify a model=keyword in /etc/modprobe.d/alsa-base.conf to get the jacks set up correctly.

What model laptop or system do you have and what is the output of:
```
aplay -l
```

---

### Post by jrtayloriv on 2010-03-18
I have a Gateway m6888u laptop.

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Thanks for answering
--Jesse

---

### Post by Yellow Pasque on 2010-03-18
You can try some of the models for Gateway laptops based on this:
[http://ubuntuforums.org/showpost.php?p=8571901&postcount=6](http://ubuntuforums.org/showpost.php?p=8571901&postcount=6)

Unfortunately, the codec info was not very specific :\

You could also try upgrading to the latest ALSA via this script: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by wiebe de haas on 2010-03-31
GATEWAY laptop
Model: m6823

LinuxMint 8 Helena (Karmic)
ALSA 1.0.20
codec: SigmaTel STAC9205  

I HAD no audio from Headphone-out.[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]  Everything else worked correctly 
after initial installation. 

I dug through these forums.
(I am very impressed with the persistence
of many contributors to this forum.)

ADDED to: /etc/modprobe.d/alsa-base.conf

options snd-hda-intel model=eapd enable=1 index=0
options snd-hda-intel enable_msi=1

rebooted, WORKS!!    [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

