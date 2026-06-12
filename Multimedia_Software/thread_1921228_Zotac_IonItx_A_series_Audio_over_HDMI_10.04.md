---
title: "Zotac IonItx A series Audio over HDMI 10.04"
date: 2012-02-06
forum: Multimedia Software
---

### Post by WannabeFantasma on 2012-02-06
Hi all

Since a couple of years I have an HTPC where I play audio and movies on.
It's a Zotac ionitx A board (Atom 330 + Ion)

But I never got HDMI audio to work.

did this: [http://ubuntuforums.org/showthread.php?t=1332261](http://ubuntuforums.org/showthread.php?t=1332261)

```
In a terminal type

Code:

alsamixer

if alsamixer is not installed it can be with the follwing command

Code:

sudo apt-get install alsamixer

once you have the alsa mixer open in the terminal use the arrow keys to move across to the IE958 1 switch, which in my case was muted
```

But there is no IE958 switch when I search for it?
I only see these:
            
[B]  Master Headphon   PCM     Front   Front Mi Front Mi   Line     Mic    Mic Boos   S/PDIF  S/PDIF D S/PDIF 1   Beep    
[/B]

my aplay -l info:

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


My main goal would be that it would work with HDMI if I want to when selected in the sound preferences, and otherwise just analog.

Hope you guys can help me!

---

### Post by WannabeFantasma on 2012-02-09
no one? :(

---

