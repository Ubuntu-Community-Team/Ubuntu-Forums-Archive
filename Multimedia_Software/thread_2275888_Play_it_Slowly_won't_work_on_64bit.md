---
title: "Play it Slowly won't work on 64bit"
date: 2015-04-29
forum: Multimedia Software
---

### Post by Lagbehind on 2015-04-29
I too have problems with Play it Slowly. It works well on my desktop (32bit U14.04) but fails to play on my laptop (64bit U14.04).  Both werre downloaded from the software centre. Anyone able to offer a suggestion to help solve this mystery please?

---

### Post by v3.xx on 2015-04-29
Try opening it up with the terminal and look for error message.
```
playitslowly
```

---

### Post by Rob Sayer on 2015-04-29
You can't assume that the problem is caused by it being 64 bit.  WHat's your audio config?

POst result of:

sudo aplay -l

Paste into terminal and post o/p here with [CODE] tags.

---

### Post by Lagbehind on 2015-04-30
Hello I opened in terminal and got the following.  Any ideas?:
Zoo:~$ playitslowly
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, mpegaudioversion=(int)1, layer=(int)3, rate=(int)44100, channels=(int)2, parsed=(boolean)true

---

### Post by Lagbehind on 2015-04-30
I typed this   sudo aplay -l    into terminal and got the following:


**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
Zoo:~$

---

### Post by v3.xx on 2015-04-30
The only thing I came up with is to check to be sure all dependencies are loaded.

[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=775698](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=775698)

---

### Post by mc4man on 2015-04-30
playitslowly is a gstreamer 0.10 app (and will shortly be obsoleted)
For mp3 support install the ugly plugin  in 14.04, after that some of these 0.10 plugins could cause issue..
```
sudo apt-get install gstreamer0.10-plugins-ugly
```

---

