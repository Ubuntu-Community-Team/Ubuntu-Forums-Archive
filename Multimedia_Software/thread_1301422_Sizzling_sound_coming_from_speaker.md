---
title: "Sizzling sound coming from speaker"
date: 2009-10-26
forum: Multimedia Software
---

### Post by Superdarion on 2009-10-26
Hi everyone.

The problem is simple. When I'm listening to audio I hear a sizzling sound coming from the left speaker. This happens with all audio formats, as well as video. Even when it comes from youtube and other sites.

The first idea was to blame the speaker itself, but that's not the problem. The same thing happens if I plug my earphones to the line. Also, when I change to Windows, the problem is not present, so it's gotta be something to do with Linux.

Now, I've had this problem for a few years now, ever since Ubuntu 6 was the new release, which is when I first tried linux, but only now have I bothered to really try to fix it.

The sizzling sound is usually present, but sometimes it disappears. I don't know why it goes away; I haven't been able to reproduce the no-sizzling. It just randomly occurs.

As for my hardware, I don't remember the exact model of the internal sound card, but it's a 3 years old Intel HDA.

I would really appreciate any help with this. The higher the volume of the music, the louder the snake in my left speaker and sometimes it gets really annoying.

---

### Post by AutoStatic on 2009-10-26
Hello Superdarion, if possible could you post the output of the following command in a terminal?
```
aplay -l && lspci | grep -i audio && cat /proc/asound/card*/codec#* | grep -i codec
```
You can paste the command in the terminal with ctrl+shift+v.

---

### Post by Superdarion on 2009-10-26
Yes, of course. Here it is:

```
d*/codec#* | grep -i codec
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: STAC92xx Analog [STAC92xx Analog]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
Codec: SigmaTel STAC9221 A1

```

---

### Post by Superdarion on 2009-11-03
So... no one has any idea? I still can't find anything on the web about it.

---

### Post by Griz054 on 2009-11-04
I found this post and it solved my hissing problem.

[http://swiss.ubuntuforums.org/showpost.php?p=8233782&postcount=6](http://swiss.ubuntuforums.org/showpost.php?p=8233782&postcount=6)

---

### Post by Superdarion on 2009-11-04
Thanks, Griz054, but I found no such line in my alsa-base.conf file.

---

