---
title: "Sound problem: Laptop speaker and microphone not working"
date: 2010-08-29
forum: Multimedia Software
---

### Post by Rehd on 2010-08-29
Dear community,

its complicated, and I googled it and locked up the forum for similar problems, without avail.

A) My laptop (Lenovo Thinkpad X61s) speakers are not working after installing Xubuntu Lucid 10.04 amd64, but the headphone does! They did function with 9.10.

B) The microphone does not work, neither the internal nor an external, when trying skype or google talk. I have to specify this:
- When I unmute the microphone and set the microphone boost I hear the internal microphone in the headphones *very*clearly and the external one very low.

As you might imagine the soundcard is recognized:
```
rforge@rforge:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I also added 
```
options snd-hda-intel model=thinkpad
```
with
```
sudo nano /etc/modprobe.d/alsa-base.conf
```

I added my user name 'rforge' with
```
sudo nano /etc/group
```
from
```
audio:x:29:pulse
```
to
```
audio:x:29:pulse:rforge
```

I also used
```
alsamixer
```
and
```
pavucontrol
```
and played with the configuration options, enabling everything setting levels to 100% and activating microphone boost.

No success.

Any ideas? Any help appreciated!

Reinhard


PS.: I love Lucid both X- and Ubuntu. The HP Elitebook of my girlfriend workes like a charm with Ubunut Lucid 10.04-i386 and even her beloved MacBook looks like crap compared to it :D ..and she admits it :KS

---

