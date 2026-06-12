---
title: "audio auto-mute not working"
date: 2013-11-09
forum: Multimedia Software
---

### Post by fube00 on 2013-11-09
Hi, 
I normally output audio to my TV speakers through HDMI. 
When I connect headphones, the TV speakers still output audio, and no sound coming from headphones. They work only if I manually select headphones in "Sound Settings - play sound through".

in alsamixer auto-mute function is enabled.

My audio device is integrated in the mobo (gigabyte h61m-usb3h), and  command:
     cat /proc/asound/card0/codec* | grep Codec
produces:
     Codec: Realtek _**ALC887-VD**_
     Codec: Intel CougarPoint HDMI

Since no corresponding model is present in file HD-Audio-Models.txt.gz, I selected model=auto in file audio.conf

alsa infos:
[http://www.alsa-project.org/db/?f=22...ded1c32d8c2dd7]("http://www.alsa-project.org/db/?f=224a44745ba412433fbcde7cc8ded1c32d8c2dd7")

Any suggestion is very welcome! Thank you!

fube00

---

### Post by oldos2er on 2013-11-09
Moved to Multimedia & Video.

---

### Post by fube00 on 2013-11-10
Sorry for posting in the wrong place...
But wow... away from "absolute beginner"... :D

---

