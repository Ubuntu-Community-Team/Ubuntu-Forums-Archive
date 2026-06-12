---
title: "Popping sound"
date: 2009-11-22
forum: Multimedia Software
---

### Post by Gannin on 2009-11-22
In Karmic 9.10, if no program has generated any sound for a while, whenever something does generate a sound there's always a loud pop before the audio plays.  Once a program has played some audio, for a little while audio plays without the loud pop beforehand, but if the sound system sits quiet for a while, then when something finally does play audio once again, it's proceeded by that loud pop once again.  Why is that?

---

### Post by Tedward on 2009-11-26
I'm having that same problem... it's rather annoying.

---

### Post by kostkon on 2009-11-26
Check [this solution here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/442463/comments/4").

---

### Post by Gannin on 2009-11-26
Thanks for pointing that out.  It worked great :).

---

### Post by unkle1 on 2010-06-11
Hello,

Just wanted to confirm that this also worked for me :)
Thankyou very much for the tip !!

The "pop" usually happened when changing formats (ie listening to an mp3, exit musicplayer and then watch a video or a TV-recording triggered the pop) and if the box had been idling for some time (minutes/hours) it would make a pop regardless if I chose a video or some music.

Running 9.10 with homebuild mythtv 0.23 and ALSA 1.20 on an Asus AT3N7A-I motherboard
(using analogue audio, I havent tested if it also removes the pop from the hdmi-audio (but I guess it does)).

---

