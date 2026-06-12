---
title: "ALSA troubles - device is busy"
date: 2006-11-28
forum: Multimedia &amp; Video
---

### Post by GolerGkA on 2006-11-28
Recently I had a minor sound trouble - for some reason I couldn't play sound through flash - I mean, like YouTube and such. Video went OK, but there were no sound. But just today I booted the system, installed some updates (never paid attention to it), started firefox - Oh! It Works! Amazing.
But then I wanted some music. BTW - the player is BMPx (may be that is it's bug?). But when I wanted to play things, all I've got was the message about the device 'default' being busy.
I use ALSA, all configuration (OK, all ALSA-related configuration) unchanged - so, what is wrong?

---

### Post by richardward101 on 2006-11-28
It sounds like whats happening is this: the thing is alsa and oss can't output sound at the same time. The video sound didn't work because something was using alsa, and then one time you tried when the device was free, but then it was locked up by oss (flash uses oss), so now your alsa media player won't work. Firstly, go to systm->preferneces->multimedia selector and make sure its on alsa, and then follow [these]("http://planet-geek.com/archives/003048.html") instructions, then maybe at least restart your desktop for good measure. Hopefully all the sound should work then.

---

### Post by GolerGkA on 2006-11-28
Thanks a lot, but it appears that all I have to do was to restart the computer - now all works properly :)

---

