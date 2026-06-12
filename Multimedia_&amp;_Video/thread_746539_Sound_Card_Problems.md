---
title: "Sound Card Problems"
date: 2008-04-05
forum: Multimedia &amp; Video
---

### Post by offramp13 on 2008-04-05
I have been using ubuntu for a very long time. Up until a few days ago i was using 7.10, which worked great but i decided to try out 8.04. I have two soundcards, one is native to my motherboard, and the other is PCI. I prefer to use the PCI one because, of course, it is better quality. My issue is, since i started using 8.04 the sound coming out of my computer has been switching between the two cards, each time i restart it is on the other card. Does anyone know how to force ubuntu to use only one of the cards? Thanks.

---

### Post by Dave Otter on 2008-04-05
Applications-Accessories -Terminal

   type      asoundconf set-default -cardCARD

   replacing CARD with the soundcard you wish to use

---

### Post by offramp13 on 2008-04-06
> **Dave Otter said:**
> Applications-Accessories -Terminal

   type      asoundconf set-default -cardCARD

   replacing CARD with the soundcard you wish to use

what exactly do i replace CARD with though? i dont just write "Sound Blaster Live!" there. It probably has an ID or something right? how do i find that out?


I got it. First I did:
```
asoundconf list
```

---

