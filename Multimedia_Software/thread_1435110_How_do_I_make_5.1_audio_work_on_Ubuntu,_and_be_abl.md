---
title: "How do I make 5.1 audio work on Ubuntu, and be able to remap sound outputs"
date: 2010-03-21
forum: Multimedia Software
---

### Post by normankev on 2010-03-21
Hey,
I've been using ubuntu for well over a year now, and have loved every minute of it. I have lived with one single issue that has not really bothered me up until now, and that is 5.1 audio. The 5.1 set of speakers I have has 3 jacks, each corresponding to front two speakers, back two speakers, center/sub, and my motherboard only has 3 jacks. In windows, the drivers that came with it would let me remap these ports so that instead of having a microphone port i'd have a center/sub port etc. Is this possible to emulate in Ubuntu?
Output of aplay -l:

kn100@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
(it uses the Realtek HD audio driver in windows)

How would I go about getting this to work?

Kevin

---

### Post by normankev on 2010-03-21
bump :popcorn:

---

### Post by Christor on 2010-05-05
I am also looking for this feature!

---

### Post by lidex on 2010-05-05
Use the pulseaudio volume control=Alt+F2; enter:
```
pavucontrol
```
Select the correct profile on the configuration tab.

---

