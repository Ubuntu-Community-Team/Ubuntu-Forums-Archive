---
title: "Java won't share audio with ANYTHING!"
date: 2008-12-11
forum: Multimedia Software
---

### Post by Truckerpunk on 2008-12-11
Hey.I have yet another sound problem with Ubuntu 8.10. I have audio playback working (finally). And I can play multiple audio-streams, like music and video playback simultaneously, the only thing that wont play nice is java. I can't listen to music while having a java application running, because it won't share the output. But at the same time, if I have a music-player playing and open a java-applet there won't be any sound in the java-applet. Any one have an idea how to solve this little problem?

---

### Post by Truckerpunk on 2008-12-12
I found a work-around for this problem that, at least worked for me. If I launch firefox with the "aoss firefox" command in the terminal, I will let me run the java-applet and share the sound with everything else. Hope this helps any one else who have this problem as well.

---

### Post by dagoth_pie on 2009-09-21
Just to add to the helpfulness, this needs alsa-oss installed.
```
sudo apt-get install alsa-oss
```

---

