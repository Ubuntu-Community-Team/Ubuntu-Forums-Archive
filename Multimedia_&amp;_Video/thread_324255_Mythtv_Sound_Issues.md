---
title: "Mythtv Sound Issues"
date: 2006-12-23
forum: Multimedia &amp; Video
---

### Post by crazedgremlin on 2006-12-23
Hi, I've installed mythtv and I have everything working as I want it to, with a few exceptions:

[INDENT]1) When I record a show, the audio from it plays through the speakers.  After the show is over, the audio from that channel will continue to play through my speakers.  If I reboot, the sound from that channel is not playing any more and I can watch what I recorded.
[/INDENT]
[INDENT]2) When I play back a show, I get crackly audio.[/INDENT]

I followed[ this guide ]("http://www.animewine.com/index.php?entry=entry060720-151531"), but around halfway through I upgraded to edgy.  I'm running mythtv .20

:-k

---

### Post by AusIV4 on 2006-12-24
1) Mute the line in. 
2) Play with the line in and capture controls until you get something that well.

---

### Post by crazedgremlin on 2006-12-25
thankyou!  I'll try this when I get home from Christmas vacation :)

---

### Post by crazedgremlin on 2006-12-28
OK, I figured out that I'm only getting sound in the left.  If I'm watching tv, it comes only from the left, but if I play a cd it comes out of both speakers.

My conclusion: It's a tv card problem (I have the ATI TV WONDER PRO).

---

### Post by superm1 on 2006-12-29
> **crazedgremlin said:**
> OK, I figured out that I'm only getting sound in the left.  If I'm watching tv, it comes only from the left, but if I play a cd it comes out of both speakers.

My conclusion: It's a tv card problem (I have the ATI TV WONDER PRO).

There is a little wire that comes from the card to your line in on these cards.  Have you tried replacing just that wire?

---

### Post by crazedgremlin on 2006-12-29
mmk I've fixed my sound problems!

I ran
```
# amixer set Master,0 100%,100% unmute
# amixer set PCM,0 100%,100% unmute
# amixer set Line,0 75%,75% mute captur
# amixer set Capture,0 100%,100% captur
```
from [here]("http://www.animewine.com/index.php?entry=entry060720-151531") and it worked!

---

