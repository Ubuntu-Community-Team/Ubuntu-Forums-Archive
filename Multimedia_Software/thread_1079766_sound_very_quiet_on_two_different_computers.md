---
title: "sound very quiet on two different computers"
date: 2009-02-24
forum: Multimedia Software
---

### Post by bobdobbs on 2009-02-24
Hi guys.
I have ubuntu 8.10 installed on a laptop and a desktop.
On both of them, the sound is very quiet.
I have to turn all the volume controls right up to hear anything.

Mute is off. The settings in alsamixer are maxed. The volume control on the gnome panel is maxed.
Still, the sound on both systems is quiet.

Here is info on the laptop:
```

Linux endorra 2.6.27-11-generic

```

```

aplay  -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


...and my desktop
```

Linux endorra 2.6.27-12-generic

```
```

card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I'd like to know what the possible causes of this problem are.
I'd also like to know how I can get normal sound levels.


Thanks

---

### Post by bobdobbs on 2009-02-24
Partial success:

I found some instructions that were applicable to Feisty. I followed the procedure, and got fuller volume and a working headphone jack on the laptop:

I enabled backports:
```

apt-get install linux-backports-modules-intrepid

```

Then edited /etc/modprobe.d/alsa-base

I added
```

options snd-hda-intel model=acer

```

Can I do something similair for my desktop ?

---

