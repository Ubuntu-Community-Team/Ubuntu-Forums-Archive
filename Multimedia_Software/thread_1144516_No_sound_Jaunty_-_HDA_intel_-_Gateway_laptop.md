---
title: "No sound Jaunty - HDA intel - Gateway laptop"
date: 2009-04-30
forum: Multimedia Software
---

### Post by arturhoo on 2009-04-30
I've done a fresh install of Jaunty on my laptop, and sound worked only in the headphone jack for 2 days.

Suddenly it stopped working, and neither the laptop speakers nor the headphone jack are working.

I have followed several tutorials and howtos but none have managed to work for me.

I have Gateway 6860FX Laptop and I'm running 32 bit version of ubuntu.
My alsa stats are available at [http://www.alsa-project.org/db/?f=2894b30c9f2dfaab5f4a765c5280c1c02d96782c](http://www.alsa-project.org/db/?f=2894b30c9f2dfaab5f4a765c5280c1c02d96782c)

I have also added different combinations to my /etc/modprobe.d/alsa-base.conf file including:

```
options snd-hda-intel model=laptop

options snd-hda-intel model=gateway

options snd-hda-intel model=laptop enable=1 index=0
options snd-hda-intel enable_msi=1
```

My aplay -l shows

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


I have also followed this extensive guide:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

My System->Sound has everything marked as Autodetect, and if I play the test sound nothing comes out (neither from speakers nor from headset).

I also checked if everything in alsamixer and gnome-alsamixer is UNmuted. 

The only thing left to do for me I think is reinstalling ubuntu.

---

### Post by arturhoo on 2009-04-30
Insert the following in /etc/modprobe.d/alsa-base.conf:
```

options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel
```

made the trick. Thanks to
mourngrym1969
from:
[http://ubuntuforums.org/showthread.php?t=1137610&highlight=gateway](http://ubuntuforums.org/showthread.php?t=1137610&highlight=gateway)

---

### Post by BigZed on 2009-05-01
Hey everyone,

I'm having this problem also but im also an extremely new Ubuntu user (about 1 hour worth of usage).

I have /etc/modprobe.d/alsa-base.conf up in the terminal but I have no clue where to paste

options snd-hda-intel model=5stack

within that file

I followed this guideline 

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

any help would be appreciated!!

Just an update: played a video and could hear sound but it was very faint/almost inaudible.

---

### Post by tommah04 on 2009-05-29
I didn't look at the page you mentioned... but if it doesn't say where to put, you usual just put it at the end of the document

---

