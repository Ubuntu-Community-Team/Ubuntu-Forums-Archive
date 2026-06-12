---
title: "Alsa driver- loud crackle from speakers on start-up"
date: 2010-11-04
forum: Multimedia Software
---

### Post by przemekispolish on 2010-11-04
I am experiencing a loud crackle sound coming from my speakers at startup. It appears to be the alsa driver because when I disable it the crackle/pop stops. Sound works when playing back music and videos however. Has anyone else experienced this problem? I reported the issue to launchpad, and was told the issue would be fixed in the latest kernel; 2.6.35.2. I upgraded to 10.10 and am still experiencing the same problems. :( Any ideas?

---

### Post by cojoda on 2010-11-04
I've noticed this problem as well.  I've noticed that usually the "crackle" isn't quite as loud unless I have my headphones plugins in.  Using Intel HD Audio.  Yeah, I'm pretty sure it's alsa too.

---

### Post by Sylos on 2010-11-04
I get the same at time using both Karmic normal flavour and lucid studio flavour. I have an M-audio delta soundcard. I also get some random stuff from time to time like the splash audio sample playing too fast or skipping. Kinda weird but I just ignored it. Would like to know why though?

---

### Post by przemekispolish on 2010-11-05
Its definitely a problem with the alsa driver. Its kinda annoying. Is there a comprehensive guide to installing OSS4 instead? Maybe I'll have better luck with my particular graphics card.

---

### Post by randumnumber on 2010-11-05
Have you tried muting the microphone on the sound board? I had this problem in 9.04 and had to do it at command line but you should just be able to right click the speaker and do properties. Mute the microphone input and presto. If you cant find a way to do it by right clicking try 
```


hbaw@hbaw:~$ alsamixer


```
for a command line interactive mixer

@cojoda  This should def fix your problem because you dont notice the crackle interference when its through your speakers. The microphone jack is picking up noise from your system fans, etc.

You can also look here [http://www.theopenhelp.com/2010/10/how-to-fix-crackling-sound-problem-in.html](http://www.theopenhelp.com/2010/10/how-to-fix-crackling-sound-problem-in.html) this might be a possible fix for your problem. but make sure you backup anything your going to change because i cannot test this so i dont know if it works

---

