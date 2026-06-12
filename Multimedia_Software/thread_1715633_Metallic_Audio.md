---
title: "Metallic Audio"
date: 2011-03-27
forum: Multimedia Software
---

### Post by agentsmith23 on 2011-03-27
I'm running Ubuntu 10.10 and for some reason my audio sounds very high pitched or metallic. The only way I can get rid of it is by using VLC and mythtv all other players and streaming internet content sound horrible. What would be causing this and how do I fix it?

I also just tried this and it played back fine.
```
aplay -Dplughw:0,9 /usr/share/sounds/alsa/Side_Right.wav 
```

I am using a Nvidia GT240 video card with HDMI audio.

Please let me know if any other info is needed.

*RESOLVED*

I looked back at a previous post from when I was having a different issue with audio and Usererror posted a fix for no audio which actually fixed my metallic sounding audio also.

[http://ubuntuforums.org/showthread.php?t=1571942&page=4]("http://ubuntuforums.org/showthread.php?t=1571942&page=4")

---

