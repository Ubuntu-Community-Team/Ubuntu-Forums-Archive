---
title: "can't play media"
date: 2008-08-09
forum: Multimedia Software
---

### Post by JoshLacey on 2008-08-09
I just downloaded a few mp3 and wanted to hear them and for some reason amarok would not play them. I have all of the appropriate codecs and what not. I've actually was able to play the same songs yesterday, but for some reason today it's deciding not to work... I tried downloading other media players (kaffeine, banshee, and I even tried using xgine) none of these worked. Something seems to be freezing them up because each would attempt to play and then freeze. I also tried a dvd, which I have played before on gxine, and it too froze and I had to force quite the application. I don't even know where to start with this problem. I've tried restarting thinking that might help, but it didn't...

please help me :confused:

---

### Post by wdaniels on 2008-08-09
I suggest you try launching amarok or whatever from a terminal to see if there are any revealing error messages.

---

### Post by T_W on 2008-08-10
Is this the standard pulseaudio hang?

Is a web browser (with flash plugin installed) running?

If so, kill the browser, kill the media player and try again.

Or you could try a 'sudo pkill pulseaudio', which in my case solves most of my media playback problems.

---

### Post by JoshLacey on 2008-08-10
I actually had a bunch of youtube videos open, lol. yeah closing them helped. all working now. thanks a ton!

---

