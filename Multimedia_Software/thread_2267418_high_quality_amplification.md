---
title: "high quality amplification"
date: 2015-03-01
forum: Multimedia Software
---

### Post by CkDGTAT on 2015-03-01
Hi,

How can I obtain a high quality amplification? This one leads to the production of lots of noise while amplifying voices.

```
mp3_scale () {	lame --scale $1 $2 ${2%%.mp3}out.mp3
}



```

---

### Post by tgalati4 on 2015-03-01
You can set the Replay Gain in the ID3 tag so that it plays back louder, without re-encoding.  Taking an mp3 and applying a gain and then recompressing to mp3 will add noise.  You need to use *audacity* and apply an EQ to raise the frequencies of voices and supress the  background noise using one of several different techniques that exist within *audacity*.

---

### Post by CkDGTAT on 2015-03-04
Do you have a magical cmd?

Audacity won't work due to the number of file I have

---

### Post by tgalati4 on 2015-03-04
Install *sox* and read about its features.  Try one file in audacity with the EQ and gain that gives you the best results, then use that knowledge to apply the same filter settings in a batch file.

[http://forum.audacityteam.org/viewtopic.php?f=21&t=74944](http://forum.audacityteam.org/viewtopic.php?f=21&t=74944)

[http://forum.audacityteam.org/viewtopic.php?f=14&t=52068](http://forum.audacityteam.org/viewtopic.php?f=14&t=52068)

[http://comments.gmane.org/gmane.comp.audio.sox/3931](http://comments.gmane.org/gmane.comp.audio.sox/3931)

[https://github.com/srikantpatnaik/noNoise](https://github.com/srikantpatnaik/noNoise)

---

