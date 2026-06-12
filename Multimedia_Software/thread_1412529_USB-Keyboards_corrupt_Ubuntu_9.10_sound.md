---
title: "USB-Keyboards corrupt Ubuntu 9.10 sound?"
date: 2010-02-21
forum: Multimedia Software
---

### Post by yyann on 2010-02-21
Hello friends,

 again I have come across a rather odd "bug" (is it one?). This time I might even fail in describing it properly. Let's start off with my observation.

[B]Problem:
[/B]After the latest kernel update of Ubuntu 9.10 Karmic Koala, the sound device couldn't be loaded. This showed in the fact, that the volume control wasn't shown in the notification field and a click on "System -> Administration -> Sound" prompted the error "Waiting for connection to sound device". 
Funny thing: exactly the same thing happened after I had upgraded from 9.04 to 9.10. I tried everything to sort it back out again, but to no good cause.

Funny thing number two: I just rebooted the machine to get a fresh start on the issue.. and it was gone! So now for my...

[B]Assumption:
[/B]Since my two M-Audio USB-Keyboards were switched off when I started up the computer, they were of course not loaded as audio devices (cat proc/... usually lists them as "USB-Audio Device") - so Ubuntu didn't try to route any sound to them, failing miserably since they are merely able to send MIDI commands...

**Question:**
Could this be the case? And how can I leave my USB-Keyboards on when using Ubuntu without having problems? 

Thanks to everyone for looking into this. I'd really appreciate all your help here!

Best wishes,
yyann.



[B]Hardware setup:
[/B]My soundcard is an M-Audio Delta 1010LT... yay, I know... M-Audio geek I am ;)

---

