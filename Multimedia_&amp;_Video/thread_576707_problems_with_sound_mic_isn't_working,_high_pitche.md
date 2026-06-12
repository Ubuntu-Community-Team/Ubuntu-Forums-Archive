---
title: "problems with sound: mic isn't working, high pitched noise...i'm desperate!"
date: 2007-10-15
forum: Multimedia &amp; Video
---

### Post by solnik on 2007-10-15
I was trying to get my mic to work so I upgraded to the latest version of ALSA as shown at:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

But when everything was perfectly compiled and installed, my mic still wouldn't work and other 2 new problems appeared:

- high pitched noise on left speaker
- sound disappears when touching volume controls

Does anyone know what to do??

My sound card is AD1986A and I'm using Feisty Fawn.

Should I remove that upgrade? If yes, how can | do it?

I've already tried to set "options snd-hda-intel position_fix=1 model=3stack" to "/etc/modprobe.d/alsa-base" but it didn't work!

Thank you!

---

### Post by linuxwizard on 2007-10-15
Try these for getting your mic to work.

[https://help.ubuntu.com/community/AudioCapture](https://help.ubuntu.com/community/AudioCapture)

[http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone](http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone)

---

### Post by solnik on 2007-10-16
thanks, but it didn't work...:(

---

### Post by perixx on 2007-10-16
Hi solnik!

Read this thread: 
[http://ubuntuforums.org/showthread.php?t=310938&highlight=high+pitched]("http://ubuntuforums.org/showthread.php?t=310938&highlight=high+pitched")

perhaps that's just what you're looking for...


perixx

---

