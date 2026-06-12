---
title: "Can't get front audio ports to work"
date: 2010-05-30
forum: Multimedia Software
---

### Post by ashfame on 2010-05-30
Hi,

I am using Ubuntu 10.04 64bit edition and I can't get my front audio ports to work.

I am running the latest alsa drivers 1.0.23 and my alsa-base.conf file is at [http://pastebin.com/3wLCpznm](http://pastebin.com/3wLCpznm)

I am using Intel D965 motherboard and ATI HD 4850 graphics card.

I have added 
```
options snd-hda-intel model=5stack
```at the end of my alsa-base.conf file

I earlier found out my model to be STAC9227 but now by using this command

```
cat /proc/asound/card0/codec#* | grep Codec
```it says Codec: ATI R6xx HDMI

Any suggestions on getting my front audio ports to work?

---

