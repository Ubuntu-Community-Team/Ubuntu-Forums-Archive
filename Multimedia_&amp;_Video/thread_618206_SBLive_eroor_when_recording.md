---
title: "SBLive eroor when recording"
date: 2007-11-20
forum: Multimedia &amp; Video
---

### Post by Ashrael on 2007-11-20
When i try to test sound recording in system/preferences/sound, i get this error:

gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Resource busy or not available.

When i blow in the mic, i hear myself on my speakers, so somehow it's working, but not?
I am not logged in in any chat client, and in soundmixer my mic is muted??? when i switch mute off nothing changes.

I read a lot of posts with the same error, but none of them seams to either aply to me, or work for me...

anybody ](*,)](*,)](*,)??

---

### Post by Ashrael on 2007-11-20
well, i have tried:

1) replacing my ct4760 (emu10k1-sef) for a ct4700 (creative 5507).

SAME PROBLEM, okay, now for something completely different: take it out completely and enabled my onboard soundthingy: same problem: i have sound out, but as soon as i try to record i get this message again in various versions... it seems to be more an ubuntu bug to me,than a real soundcard problem...

anyone??
____________

---

### Post by Ashrael on 2007-11-20
Still at it.....So, I decided to (take my work back underground #-o ) startup from the livecd....

here it does work!!?? If you got the same problem, please try this and post....

So what has gone wrong when i installed gutsy from scratch? Gonna post this elsewhere too, not sure where yet.. Seems to me it's a bug in the installer. But who am i, said the fool.

to be continued...

---

### Post by Ashrael on 2007-11-28
removed pulseaudio, it doesn't seem to be necessary for any of my appss, it works now!

see what it does for you...

---

