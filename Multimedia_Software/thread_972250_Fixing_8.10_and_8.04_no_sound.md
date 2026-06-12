---
title: "Fixing 8.10 and 8.04 no sound"
date: 2008-11-05
forum: Multimedia Software
---

### Post by Airfoot on 2008-11-05
If you recently updated your 8.04 kernel version or if you installed 8.10 and you have problems with your sound here is a brief tutorial of how to fix it(tested to work with dell inspiron 1525 and 1526):

first (in terminal) terminate pulse audio:  $ pulseaudio -k
(you should not have to sudo)

next (in terminal) reload ALSA:   $ sudo alsa force-reload
(enter your password when prompted)

then go to "system > preferences > sound" and set all options to ALSA (if they are not already) 

then got to "system > preferences > volume" and make sure your sound volume is turned up (reloading ALSA may have turned some channels down)

then test your sound by running a file with sound (video, song, ect.)

if your sound is now working correctly then all you have to do is go to "system > preferences > sessions" and unselect pulse audio (so it won't run agian when you restart).

and that's it, with any luck you should have sound.

---

### Post by Stephen Bruington on 2009-02-14
Thanks for the post, but this didn't work for me.  I have a Dell Inspiron 1526 that came pre-loaded with Vista.  I don't know much about Linux, but thought I'd give it a try.  I'm running 8.10, dual-booted with Vista.  Everything works but the sound!  I tried this in the past and finally got it working, but can't remember what I did to fix it.  Any help is much appreciated!

---

