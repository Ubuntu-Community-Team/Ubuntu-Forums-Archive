---
title: "Firefox lowers sound on Feisty"
date: 2007-06-13
forum: Multimedia &amp; Video
---

### Post by HalNineThousand on 2007-06-13
I've seen posts about problems with Flash and Firefox, but this is not at all like that.  I'm using Kubuntu Feisty and, as you'd expect from that, I use KDE.  I keep several apps open all the time, including Firefox.  I use Amarok for music.  There are times when I try to play music and I hear nothing.  Then I crank the volume on my mixer -- not the computer one, but by hand on the mixer for several inputs to my speakers, and when I pull it all the way up, I can hear my music. 

Amarok is not the only program effected.  Kaffeine is effected, which I suspect is because they both use the Xine engine for sound.  There are times, though, when I pull up the KDE control center  and play a test sound and that's so low I don't hear it without cranking up the physical mixer.

Many times when this happens, if I stop Firefox, the sound returns to normal, which is why I think Firefox is creating the problem.  As best I know, the sites I have loaded in my default tabs are not using Flash.  I guess it's possible one of them does, but I don't think they do.

Many times if I go to KControl->Sound & Multimedia -> Sound System and change to alsa, restart the sound, then change back to autodetect and restart again, it is fixed, but not every time.

There have been a few times that it turns out some rude app has turned the PCM volume on the KDE mixer down, but the over all problem of some program (likely Firefox) dropping the volume output until Firefox is stopped and I can restart the sound system is not the same as the PCM volume sometimes being lowered.

Is anyone else having a similar problem?  Any ideas or suggestions?

Thanks!

---

### Post by muximus on 2007-06-14
woah... never hrd somethin like this happen... do the volumes on alsamixer remain the same and still your volume goes down??

---

