---
title: "Sound coming out of both headphones and speakers in ubuntu 9.04"
date: 2009-09-28
forum: Multimedia Software
---

### Post by su4232 on 2009-09-28
I just installed Ubuntu 9.04 on Dell Vostro 1014
i am having trouble with sound
laptop speakers still make sound after plugging in the headphone.
any help will be appreciated.
am gone through various posts made earlier but no success.
plz help
thanks in advance

"aplay -l" output-
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

"head -n 1 /proc/asound/card0/codec*"
Codec: Conexant ID 5067

---

### Post by bogdan.veringioiu on 2009-09-28
Hi.
You can try this, maybe it works:

Add this line in /etc/modprobe.d/alsa-base

options snd-hda-intel model=laptop

and then issue sudo /etc/init.d/alsasound restart 

Better, take a look at this post:
[http://ubuntuforums.org/showthread.php?t=314383](http://ubuntuforums.org/showthread.php?t=314383)
It shows different variations of the above syntax, depending on your laptop mode.

Bogdan

---

