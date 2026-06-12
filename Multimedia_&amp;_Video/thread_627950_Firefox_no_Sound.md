---
title: "Firefox no Sound"
date: 2007-11-30
forum: Multimedia &amp; Video
---

### Post by ziofil on 2007-11-30
hello everybody! :KS

I have a strange problem: I'm running gutsy with no problems at all, but if i try to watch a video on youtube with firefox I can't hear any sound (nor from any flash animation)
rithmbox works great, i use skype, too, only firefox gives me problems...
how can i fix this? :confused:
anyone has/had the same problem?

thank you in advance!

---

### Post by ziofil on 2007-11-30
solved! :guitar:

I did a ```
gksudo asoundconf set-default-card Audigy2
```
and then i modified the string FIREFOX_DSP="none" to FIREFOX_DSP="alsa" in the /etc/firefox/firefoxrc file.

---

### Post by wonk-o-matic on 2007-11-30
Thanks so much for posting the solution!  I fixed my problem with a single search on this site.

---

### Post by Fredrik_b on 2007-12-01
Worked but now rythembox cant play music

---

