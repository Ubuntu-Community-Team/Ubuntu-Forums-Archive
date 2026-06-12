---
title: "vkeybd --&gt; timidity"
date: 2006-11-10
forum: Multimedia &amp; Video
---

### Post by musther on 2006-11-10
I'm trying to get vkeybd to output to timidity (which is working fine as I have other apps, such as GNU Solfege using it).  The issue I'm having is that I don't know how to tell vkeybd to connect to timidity, I've googled and can't find any info on how to do this.

Anyone know, or can figure it out?

---

### Post by Syock on 2006-12-06
Use aconnect.
For example, if vkeybd`s output port is 129 and timidity`s input port is 128, you connect them by
```
aconnect 129 128
```
Of course there are other options for aconnect, maybe you can try out for yourself, since I`m no expert in this matter.

---

