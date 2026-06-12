---
title: "convert a from PCM to CCITT"
date: 2009-09-10
forum: Multimedia Software
---

### Post by kriom on 2009-09-10
Hello,

After some search on google, I ask to the Ubuntu forum.
Do you know a way to convert a .wav with format PCM
(8khz, 8 bit, mono, PCM)
to a wav with format CCITT A-law
(8khz, 8 bit, mono, loi A, CCITT)
I'm looking for a application to do it with a commande line

Thank in advance for your help

Kriom

---

### Post by kriom on 2009-10-07
I found a solution :KS :
```

sox input.wav -A -c 1 -r 8000 output.wav
```

I hope this could be helpful

Kriom

---

