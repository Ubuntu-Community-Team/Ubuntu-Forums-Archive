---
title: "Milkytracker Sound driver initialization failed &lt;Solved&gt;"
date: 2008-12-06
forum: Multimedia Software
---

### Post by blumojo on 2008-12-06
When trying to use Milkytracker I got the following error;
```
Sound driver initialization failed.  Try different settings or driver.
```

On the console I got this message:
```
SDL: Failed to open audio device! (buffer = 8832 bytes)..
SDL: Try setting "Force 2^n sizes" in the config menu and restarting.
```
Checking the "Force 2^n sizes" option and restarting had no effect.

This probably my fault for changing the default libraries when trouble-shooting my original "no sound" issue, but I thought it would be useful to post if someone else made the same mistake that I did;

Install the libsdl1.2debian-alsa package;
```
sudo aptitude install libsdl1.2debian-alsa
```

(Note: you must agree to remove the libsdl1.2debian-pulse package.)

Restart Milkytracker, if the SDLAudio driver is not selected;
1.) Click "Config"
2.) On the "I/O" tab click the "SELECT DRIVER..." button
3.) Highlight SDLAudio and click "OK"
4.) Click "APPLY" and "OK"

---

### Post by greyfox1 on 2009-01-11
Thanks a million M8!  I came back to MilkyTracker after having not used it for several months and was horrified when I ran into this problem.  Fortunately a quick search on the forums turned up your post.  Thanks again!!

---

