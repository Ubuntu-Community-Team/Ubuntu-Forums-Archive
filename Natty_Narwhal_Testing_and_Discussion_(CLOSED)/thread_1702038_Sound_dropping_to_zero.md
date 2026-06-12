---
title: "Sound dropping to zero"
date: 2011-03-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by CaptainMark on 2011-03-07
Just started trialling natty, (i gave alpha one a shot but unity was all over the place) my sound keeps dropping to zero every now and again, i cant find a common link between instances either. its not muting as such but the volume level will drop to zero just randomly??
Anyone else had this?

---

### Post by icek on 2011-03-07
Same problem here...

---

### Post by rapiertg on 2011-03-07
This happen for me every time i start rhythmbox...

Not sure for other situations.

---

### Post by CaptainMark on 2011-03-07
hmm, i may log it on launchpad, im not sure yet i dont want to bother them with something that will probaly be fixed by the beta or full release

---

### Post by cariboo on 2011-03-07
I noticed the same thing using banshee on a fresh install last night, the only reason I noticed, it, is when the album art popped up when it went to the next track. At the time I only wanted to play the first track, so I wasn't really paying it any attention.

---

### Post by CaptainMark on 2011-03-08
Ive noticed its seems okay most of the time but goes to zero on login, is there a way to pass arguments to the alsamixer program? as a workaround you could make a script to run on login which starts alsamixer and passes it a 5 for 50% volume?? any thoughts?

---

### Post by CaptainMark on 2011-03-08
this should work,```
amixer set Master 60%
```but it doesnt, its crazy it sometimes works in a terminal, sometimes doesnt, weird, i think the sound mixer is a bit tempermental yet, 51days left so my phone tells me

---

### Post by mc4man on 2011-03-08
A couple of things have gone south w/ the updates of last couple of days or so, this being one.
it's been bugged and confirmed so will be fixed at some point.
[https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/730925](https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/730925)

---

