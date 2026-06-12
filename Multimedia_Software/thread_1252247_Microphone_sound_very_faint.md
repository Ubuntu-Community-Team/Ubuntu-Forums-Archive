---
title: "Microphone sound very faint"
date: 2009-08-28
forum: Multimedia Software
---

### Post by BramWillemsen on 2009-08-28
Hi,

The recordings from my microphone are very faint. I turned up the volume to the maximum in alsamixer, but it is still not enough. I always used 'i2s in' as digital source like the screenshot shows. After testing all the combinations i found out that the microphone is only loud enough when i use 'IEC958 out'. The problem with selecting this option is that all the sounds my computer plays are relayed to my microphone. For instance when I record something and turn on some music on the computer, this music will also be recorded. The music is relayed to the microphone. 

Is there a way to get rid of this feedback phenomenon while still using 'IEC958 out'? Or is this problem inherent to using 'IEC958 out'? It is the ONLY option that records my voice at a volume that is high enough. Or is there maybe a way to boost the microphone volume while using another 'digital source' like 'i2s in' that does not give the feedback phenomenon? I'm not knowledgable at all about the different sound systems in Linux, suggestions would be very welcome :)

---

### Post by BramWillemsen on 2009-08-28
changed the problem description

---

### Post by BramWillemsen on 2009-08-29
does anyone have an idea?

edit: it seems like Audigy SE has no mic boost option in Alsa.... That could be the core of the problem. I upgraded to version 1.0.20 but still no mic boost, at least skype records with this new version though. ** Is there any flashy way to get the mic boost option? **

(other people who want to upgrade alsa should use this link, very easy process! [http://webupd8.blogspot.com/2009/08/how-to-upgrade-to-alsa-1020-on-ubuntu.html](http://webupd8.blogspot.com/2009/08/how-to-upgrade-to-alsa-1020-on-ubuntu.html) )

---

