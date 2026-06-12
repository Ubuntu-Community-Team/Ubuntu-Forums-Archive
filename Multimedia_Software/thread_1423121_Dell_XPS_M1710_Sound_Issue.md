---
title: "Dell XPS M1710 Sound Issue"
date: 2010-03-06
forum: Multimedia Software
---

### Post by Arex Bawrin on 2010-03-06
I have a few problems with my laptop sound in Ubuntu that I do not get in Windows. I've tried searching for this issue, but I just ended up more confused and frustrated. 

Problems:
[LIST=1]
[*]Volume is way too high to begin with.
[*]Music and other sounds tend to muffle through my laptop at a reasonable volume.
[/LIST]

Here's the codec information:
```
Codec: SigmaTel STAC9200
Codec: Conexant ID 2bfa

```

---

### Post by RedSingularity on 2010-03-06
In a terminal type

alsamixer

and check you mixer levels.

---

### Post by Arex Bawrin on 2010-03-07
I opened up alsa mixer and messed around with the levels and got a pretty good set. The problem is once I adjusted the volume through the buttons on my laptop the volume would just start blasting again and the levels in alsa mixer would go back to their default levels (the original bad sound). Any ideas?

---

### Post by RedSingularity on 2010-03-07
After you adjust the levels are you pressing "esc" to exit?

---

### Post by Arex Bawrin on 2010-03-07
Yes I did hit esc to exit. The problem is the second I hit the volume up button the PCM and LFE levels jump to the maximum levels, while the master is at a 6. This creates a very loud noise for such a "low" volume level. And then I will hit volume down on my laptop and the music will just go mute.

---

### Post by RedSingularity on 2010-03-07
Look in System>Prefs>Keyboard shortcuts.  Assign the proper key to volume UP and DOWN.

---

### Post by Arex Bawrin on 2010-03-07
I appreciate all of the replies from everyone. This is a great commmunity:) @RedSingulrity - The keyboard shortcuts are working properly. The volume slider appears like it should when I hit the up/down volume buttons.

I noticed something interesting though. When I plug in my headphones I get a MUCH better sound. The up/down volume levels work just as they did in Windows. So why is this not so when coming out of my laptop speakers? I know it's not a problem with the hardware since it works fine in Itunes/Windows. Once again, I really do appreciate the suggestions and I hope we can find a solution!

---

### Post by RedSingularity on 2010-03-07
Interesting, does your speakers and headphones use the same port?

---

### Post by Arex Bawrin on 2010-03-08
I found a pretty good solution to this problem:

[http://ubuntuforums.org/showthread.php?t=1317562](http://ubuntuforums.org/showthread.php?t=1317562)

Hope that helps the people who were as frustrated with this issue as I was.

---

