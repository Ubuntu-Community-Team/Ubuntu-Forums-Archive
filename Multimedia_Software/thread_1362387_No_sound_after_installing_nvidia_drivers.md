---
title: "No sound after installing nvidia drivers"
date: 2009-12-23
forum: Multimedia Software
---

### Post by snowwolfau on 2009-12-23
I need help i have no sound when using the Nivida Drivers

I have a fresh install of Karmic 9.10. I ran update manager to get the lastest packages. I then went to the Hardware devices and enabled the Nvidia driver v185. On reboot the sound no longer works. I then went back to Hardware Devices and disabled the nvidia drivers and re-booted and the sounds works again.

My system is 
Motherboard Asus P5B-E Plus
Video Card:  Nvidia GT240

I am using my LCD tv as a monitor as this box was going to be set up as a mythtv. But i have not installed any of the myth packages yet. I connect to the tv using HDMI, also with a separate cable from the sound output jack on the back of them computer to the input jack on the TV.

I looked at alasmixer and nothing was muted.

```
media@HesterTv:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


```
media@HesterTv:~$ lspci -v
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 81ec
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at febf8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

01:00.1 Audio device: nVidia Corporation Device 0be4 (rev a1)
    Subsystem: Giga-byte Technology Device 34e5
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at fe77c000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
```

Thanks
Scott

---

### Post by byStanderone on 2009-12-23
...download and install the ubuntu-restricted-extras that suites your machine:

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=ubuntu-restricted-extras](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=ubuntu-restricted-extras)

---

### Post by RedSingularity on 2009-12-24
Ok.....first of all install the nvidia drivers and we will start there.

---

### Post by snowwolfau on 2009-12-26
> **byStanderone said:**
> ...download and install the ubuntu-restricted-extras that suites your machine:

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=ubuntu-restricted-extras](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=ubuntu-restricted-extras)

Done 

> **RedSingularity said:**
> Ok.....first of all install the nvidia drivers and we will start there.

and Done but no change.

---

### Post by RedSingularity on 2009-12-26
Ok first thing you do is check the alsa mixer and make sure your volume levels are up.

In a terminal type

alsamixer

---

