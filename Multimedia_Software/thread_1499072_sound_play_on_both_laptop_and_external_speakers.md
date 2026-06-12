---
title: "sound play on both laptop and external speakers"
date: 2010-06-01
forum: Multimedia Software
---

### Post by faelken on 2010-06-01
I looked around the settings on Ubuntu and I cannot prevent sound from being played on my laptop speakers when external (more powerful) speakers are plugged in. Windows automatically defers all sound output to the external ones as soon as it is plugged in.
 
How can I fix this?

---

### Post by faelken on 2010-06-01
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Codec: Motorola Si3054
Codec: Realtek ALC880

---

### Post by lidex on 2010-06-01
Sounds like a jack-sense issue. What is the make/model of the PC?

---

### Post by faelken on 2010-06-02
Its an old Alienware M17. Basically it has 3 jacks - two outputs and one mic. input. I've seen the other post but what should I put into the command lines?

---

### Post by lidex on 2010-06-02
That's a tough one. Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=3stack 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

Other options to try:
```
options snd-hda-intel model=w810
options snd-hda-intel model=uniwill
options snd-hda-intel model=auto
```
Only one line at a time!

---

### Post by faelken on 2010-06-03
Thanks it worked for 3stack not w810

---

### Post by lidex on 2010-06-04
Great. Please mark the thread as solved using 'Thread Tools' up top.

---

