---
title: "Grey video in totem and green in VLC"
date: 2008-02-13
forum: Multimedia &amp; Video
---

### Post by kaar3l on 2008-02-13
Hello

I have problem watching this live video: mms://video.eenet.ee/siga . At the beginning it worked, with both VLC and totem, but it doesn't anymore. I tried with mplayer, it worked like charm. I would like to get it working in totem. :(

Thanks, Kaarel

---

### Post by hyperair on 2008-02-13
Try installing the ubuntu-restricted-extras package from Synaptic, or just use this command line for it: ```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by kaar3l on 2008-02-13
ubuntu-restricted-extras is already the newest version.

---

### Post by Nerdriot on 2008-03-08
Why type of video card do you have, just out of curiosity?

I was having a similar issue, and I ended up having to disable glx and dri in xorg to correct the problem (I have a crappy onboard VIA).

---

