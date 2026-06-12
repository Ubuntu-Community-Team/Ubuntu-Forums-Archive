---
title: "The Dreaded Conexant CX20549 (Venice)"
date: 2013-08-09
forum: Multimedia Software
---

### Post by fxkrait-1 on 2013-08-09
I recently acquired a Toshiba Satellite P105-S6197, which features the above chipset. It originally had Vista on it, but i put 12.04 32bit on it. After some preliminary tinkering with settings and removing the OSS4 i was tinkering with, i finally got the audio to a usable quality, and not the muddiness it was. This was fixed with the Alsa Mixer PCM slider. 

So now everything about the audio works, except when i suspend the laptop. I get absolutely no audio whatsoever. I have tried to restart pulse, with commands like pulseaudio -k..etc, but to no avail. The only way to fix this is to restart the computer, then it works great. I have tried a few articles and posts here and there, but still no luck. If anyone has a solution to this is issue it would be greatly appreciated. Thanks!

[Here]("http://ubuntuforums.org/showthread.php?t=1313274") is a link to a forums post with my same model, with the same issue. There is also a link to the bug report, which to the best of my knowledge shows it still unfixed...:(

---

### Post by Yellow Pasque on 2013-08-10
You could try this as a workaround (much better than restarting completely):
```
sudo alsa force-reload
```
If that works, you should probably script it so that it runs on resume.

---

### Post by kurt18947 on 2013-08-10
I know nothing about audio but this problem sounds a little like a problem some wireless chipsets have.  They work great, suspend, resume and nothing.  The problem is that the devices don't suspend properly so can't resume.  The fix for some wifi adapters is pretty simple.  

"gksu gedit /etc/pm/config.d/config"

A new empty file will open.  Add this line:

"SUSPEND_MODULES='module_name'

and save.  I have no idea if this will help your audio problem or not but it might be something to investigate.

---

