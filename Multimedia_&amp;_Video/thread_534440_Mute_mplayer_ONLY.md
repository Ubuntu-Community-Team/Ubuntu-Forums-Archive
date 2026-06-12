---
title: "Mute mplayer ONLY"
date: 2007-08-25
forum: Multimedia &amp; Video
---

### Post by luckSpray on 2007-08-25
Hi there,

I'm running Feisty on my system with mplayer (2:1.0~rc1-0ubuntu9.1) and I want mplayer to mute only it's sound instead of muting the whole PCM channel (causing all the others, like amaroK to be silent too).

I have read somewhere (can't find the link anymore :( ) that the -aop option is/was capable of doing that, though when I followed the orders of the certain page, mplayer yielded that the -aop option is deprecated.

All in all, my question is: How can I mute mplayer without affecting other program's sounds?

Best regards
hiro

---

### Post by luckSpray on 2007-08-25
*bump*

---

### Post by shirilover on 2007-08-26
you could use the 'm' keyboard shortcut to mute mplayer or -ao null for no sound while maintaining video playback

---

### Post by Batuhan on 2007-08-26
-nosound option should work.

---

### Post by luckSpray on 2007-08-26
Isn't there a possibility to mute mplayer **during** playback and **without** the need of restarting it with another option?

---

### Post by luckSpray on 2007-08-28
Okay, for anyone who's interested in doing this, I've found a way to do it :popcorn::

```
mplayer -softvol <FILE>
```

This way mplayer uses the internal software mixer to mix the sound. You can use the keys [9] and [0] to crank the volume up/down.

Further reading: [[COLOR="DarkOrange"]MPlayer Documentation: 3.6.3. Software Volume adjustment[/COLOR]]("http://www.mplayerhq.hu/DOCS/HTML/en/advaudio.html#advaudio-volume")

---

