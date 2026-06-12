---
title: "Audio problems"
date: 2007-03-10
forum: Multimedia &amp; Video
---

### Post by think13 on 2007-03-10
Audio used to work for me in Ubuntu Edgy, but just a couple days ago it stopped working.  I get no sound when I attempt to play CD 's and ogg vorbis files, but sound did work for a java applet in my browser that just played a midi sort of file.  Do I need new drivers, and how would I get new drivers?

By the way, I am running on a Thinkpad R52 laptop.

---

### Post by drpaul on 2007-03-10
I've got very similar problems. Totem and gxine [and ff] still play audio fine. Mplayer and xmms refuse to play like they were. Mplayer will now play if I set it to use oss. 

I have tried recompiling my alsa driver [upgraded to .13-rc3] but that didn't change anything.

I'm running Edgy on a HP dv6150us notebook.

No one has chimed in about potential solutions.

????

PAUL

---

### Post by think13 on 2007-03-10
update:
aplay -l lists

**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by drpaul on 2007-03-10
What does that mean?

This is what I have

 aplay -l lists
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Paul

---

