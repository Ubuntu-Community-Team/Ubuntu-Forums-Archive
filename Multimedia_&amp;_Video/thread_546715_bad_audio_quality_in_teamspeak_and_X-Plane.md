---
title: "bad audio quality in teamspeak and X-Plane"
date: 2007-09-09
forum: Multimedia &amp; Video
---

### Post by sblanzio on 2007-09-09
HI!
I usually get good sound quality using software like XMMS, totem, VLC... and even games like SecondLife.

I cannot understand why I get very poor sound quality using applications for gaming like "TeamSpeak" or "X-Plane 8.60".

When I launch them (even separately) I always get chopping noise like "clicks" that sometiems are really hard to stand at.
I noticed that maybe these "clicks" get better when, for instance, X-plane is playing since 10 mins.

I tried to change sound driver in gnome (tried ALSA, OSS, ESD) but teamspeak works only if "oss /dev/dsp/" is seleceted in options. So i tried to use "aoss" before launching both Teamspeak and X-plane but I cannot get audio improvements.

I remember that with a previous pc maybe I did it, but I can't remember how.

For info, my MB card is a asus MVA-MVP and i had to add this line to /etc/modprobe.d/alsa-base
```
options snd-hda-intel model=3stack
```
in order to make it work. In fact this card audio doesn't work out of the box.

thank you very much for any help

---

### Post by sblanzio on 2008-06-12
i finally solved my problems using the info i found in this post:

[http://ubuntuforums.org/showpost.php?p=4869171&postcount=16](http://ubuntuforums.org/showpost.php?p=4869171&postcount=16)

then i start both teamspeak and xplane with aoss and works great!!

hope this can help

---

