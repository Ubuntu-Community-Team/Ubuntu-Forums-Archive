---
title: "MythTV and EMU USB soundcard"
date: 2010-10-25
forum: Multimedia Software
---

### Post by bluetomgold on 2010-10-25
I can't get MythTV to work with my EMU Tracker Pre. The card works for everything else and is set as the default device under system>preferences>sound.

Myth is set to ALSA-default. I've tried all the other settings but it will only output through the PC's crappy on-board card. I did once manage to get it to work (don't ask me how) but following a reboot, nothing...

Hm.

---

### Post by bluetomgold on 2010-10-31
Any ideas?

---

### Post by bance on 2010-11-04
I don't know if it;ll work for you, but when I had problems with sound (different hardware) I did this;-

in a terminal type

```
aplay -l
```


This gives an output of your sound devices, make a note of the one you want to use, then in your myth set-up use "alsa:default:Card=N" obviously substituting N for the appropriate number.

Good luck Steve,

---

### Post by bluetomgold on 2010-11-05
Nice idea...

I got this answer:

```
tom@tom-shuttle:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: USB [E-MU Tracker Pre | USB], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
tom@tom-shuttle:~$ 
```

So set it audio output device and mixer device to:

"alsa:default:Card=1"

But still not a squeak out of the EMU.

---

### Post by bance on 2010-11-08
maybe try Alsa:Default:CARD=1

---

