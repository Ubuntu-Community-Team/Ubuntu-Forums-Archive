---
title: "Hardy sound problem"
date: 2008-05-19
forum: Multimedia Software
---

### Post by beckols on 2008-05-19
Ok, so I actually had this problem when I had gutsy, but I solved it by removing and purging then installing linux-sound-base as well as a couple other things (per the comprehensive sound guide sticky)... the problem was that this also removed gdm, and that caused many more problems than it solved (although the sound did work after that).

So now I upgraded to Hardy, and the problem is back.  I have a Creative Sound Blaster Audigy.  Here is the output of aplay -l:

```
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

A lot of people had a similar problem, and they fixed it by disabling Audigy Analog/Digital Output Jack in the alsamixer... but it doesn't appear in mine.

I should also say that I get the little sound when the login screen first appears, but nothing after that.

---

### Post by beckols on 2008-05-19
Also, if I type gstreamer-properties into terminal and set the plugin to ALSA and the device to Default, I here the test sound... other than that and the login screen sound, I can never get any other sound

Edit: New update, I tried PulseAudio because one of the guys on the IRC said there were conflicts after I showed him the output of "lsof | grep snd" and that made it so no sounds work... I have it back to where I get the logon screen drum, I hear pidgin sounds, and I hear most test sounds when testing with ALSA, but still no music playing from Amarok

second edit:
Ok so I can get sound working in anything that lets me change the audio to ALSA... but I still have the conflict... here is the output from lsof | grep snd:

```
gconf-hel  7855     colin  mem       REG        8,2    357520  4950267 /usr/lib/libsndfile.so.1.0.17
mixer_app  7954      colin   20w      CHR      116,0              12148 /dev/snd/controlC0

```

Does anyone know how I can eliminate this conflict????

---

### Post by beckols on 2008-05-20
bump

---

### Post by xc3RnbFO8P on 2008-05-20
Did you try :
> sudo modprobe snd-hda-intel

---

### Post by beckols on 2008-05-20
I just tried that, but the conflict is still there

---

### Post by beckols on 2008-05-21
bump

---

### Post by raulcarreras on 2008-05-21
I got _exactly_ the same problem. Had it before with 6.06. How can it be fixed? The bug has been around for some time!

---

### Post by Yellow Pasque on 2008-05-21
> Ok so I can get sound working in anything that lets me change the audio to ALSA...
Most apps are written natively for OSS (because it's a lot easier). Try:
```
sudo apt-get install alsa-oss
```

---

### Post by beckols on 2008-05-21
Ok, I did that.  Now what?

---

### Post by beckols on 2008-05-22
bump...

---

### Post by tich on 2008-05-22
has anyone got this working yet?

---

