---
title: "Volume decreased"
date: 2009-03-25
forum: Multimedia Software
---

### Post by single.coil on 2009-03-25
Hello all, recently switched to ubuntu from windows vista, but i have a question. When i play my mp3s, they play a lot quieter than they do in windows, even at full volume its like half of what it would be within windows, any ideas?

---

### Post by lovinglinux on 2009-03-25
Click the volume icon in the panel then raise "Master", "PCM" and "Front" volumes.

---

### Post by rdumas on 2009-03-25
I have the same issue, and I have adjusted all valume levels to 100%
even video is very quiet.
any thoughts?

---

### Post by lovinglinux on 2009-03-25
> **rdumas said:**
> I have the same issue, and I have adjusted all valume levels to 100%
even video is very quiet.
any thoughts?

Depending on the application you use to play the media, there is the possibility of configuring volume gain. For example, I use the following option in mplayer config (~/.mplayer) to raise the volume a little bit:

```
af=volume=5:0
```

This will boost mplayer volume by 5 db, which is more than enough in my opinion.

---

### Post by single.coil on 2009-03-25
ya mine is better now that i raised the front and such. Works nicely. The more i use this ubuntu, the more i consider getting rid of windows lol

---

### Post by lovinglinux on 2009-03-25
> **single.coil said:**
> ya mine is better now that i raised the front and such. Works nicely. The more i use this ubuntu, the more i consider getting rid of windows lol

Yeah. The transition can be difficult sometimes, but with patience you will get there. I started using Ubuntu just 7 moths ago, after 15 years using only Windows. I'm 100% Ubuntu now and very happy with it. Go for it.

---

### Post by rdumas on 2009-03-26
> **lovinglinux said:**
> Click the volume icon in the panel then raise "Master", "PCM" and "Front" volumes.

This may sound dumb but what is "PCM" and I am assuming Front volumes is the volume dial in the front of my lap top.  Oh I hope I don't sound stupid.

---

### Post by lovinglinux on 2009-03-26
> **rdumas said:**
> This may sound dumb but what is "PCM" and I am assuming Front volumes is the volume dial in the front of my lap top.  Oh I hope I don't sound stupid.

[http://en.wikipedia.org/wiki/PCM](http://en.wikipedia.org/wiki/PCM)

I guess "Front" refers to the main speakers.

---

