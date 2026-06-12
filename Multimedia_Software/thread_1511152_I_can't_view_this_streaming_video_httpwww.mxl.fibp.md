---
title: "I can't view this streaming video http://www.mxl.fi/bpfeeds2/"
date: 2010-06-16
forum: Multimedia Software
---

### Post by Skipnaz on 2010-06-16
If you can see all the videos tell us how you did it. Thank You

---

### Post by ron999 on 2010-06-16
Hi
I just pasted the URL into Firefox's URL window and the videos played, but they took a while to load.

It's possible to watch those feeds using VLC or mPlayer.
These are the links:-
> mms://a246.l9789246245.c97892.g.lm.akamaistream.net/D/246/97892/v0001/reflector:46245
mms://a288.l9789244287.c97892.g.lm.akamaistream.net/D/288/97892/v0001/reflector:44287
mms://a839.l9789244838.c97892.g.lm.akamaistream.net/D/839/97892/v0001/reflector:44838
mms://a567.l9789246566.c97892.g.lm.akamaistream.net/D/567/97892/v0001/reflector:46566
mms://a1031.l9789255030.c97892.g.lm.akamaistream.net/D/1031/97892/v0001/reflector:55030
mms://a1500.l9789231499.c97892.g.lm.akamaistream.net/D/1500/97892/v0001/reflector:31499
mms://a459.l9789222458.c97892.g.lm.akamaistream.net/D/459/97892/v0001/reflector:22458
mms://a1686.l9789245685.c97892.g.lm.akamaistream.net/D/1686/97892/v0001/reflector:45685
mms://a1684.l9789245683.c97892.g.lm.akamaistream.net/D/1684/97892/v0001/reflector:45683
mms://a1176.l9789247175.c97892.g.lm.akamaistream.net/D/1176/97892/v0001/reflector:47175
mms://a1146.l9789221145.c97892.g.lm.akamaistream.net/D/1146/97892/v0001/reflector:21145
mms://a1236.l9789237235.c97892.g.lm.akamaistream.net/D/1236/97892/v0001/reflector:37235
mms://a1524.l9789235523.c97892.g.lm.akamaistream.net/D/1524/97892/v0001/reflector:35523

If you paste this command into the monitor they all play together:-
```
vlc mms://a246.l9789246245.c97892.g.lm.akamaistream.net/D/246/97892/v0001/reflector:46245 &
vlc mms://a288.l9789244287.c97892.g.lm.akamaistream.net/D/288/97892/v0001/reflector:44287 &
vlc mms://a839.l9789244838.c97892.g.lm.akamaistream.net/D/839/97892/v0001/reflector:44838 &
vlc mms://a567.l9789246566.c97892.g.lm.akamaistream.net/D/567/97892/v0001/reflector:46566 &
vlc mms://a1031.l9789255030.c97892.g.lm.akamaistream.net/D/1031/97892/v0001/reflector:55030 &
vlc mms://a1500.l9789231499.c97892.g.lm.akamaistream.net/D/1500/97892/v0001/reflector:31499 &
vlc mms://a459.l9789222458.c97892.g.lm.akamaistream.net/D/459/97892/v0001/reflector:22458 &
vlc mms://a1686.l9789245685.c97892.g.lm.akamaistream.net/D/1686/97892/v0001/reflector:45685 &
vlc mms://a1684.l9789245683.c97892.g.lm.akamaistream.net/D/1684/97892/v0001/reflector:45683 &
vlc mms://a1176.l9789247175.c97892.g.lm.akamaistream.net/D/1176/97892/v0001/reflector:47175 &
vlc mms://a1146.l9789221145.c97892.g.lm.akamaistream.net/D/1146/97892/v0001/reflector:21145 &
vlc mms://a1236.l9789237235.c97892.g.lm.akamaistream.net/D/1236/97892/v0001/reflector:37235 &
vlc mms://a1524.l9789235523.c97892.g.lm.akamaistream.net/D/1524/97892/v0001/reflector:35523
```

---

### Post by Skipnaz on 2010-06-16
ron999 thanks I got it to work. I could only get one at a time to work in VLC. Got an error mass pasting but thats OK. I pasted the mass in Terminal and a bunch of VLC opened up and I was able to delete the test pattern ones and resize/move the others. Im a happy camper thanks. 
How did you get those links?

---

### Post by ron999 on 2010-06-16
> **Skipnaz said:**
>  
How did you get those links?

Ok
I opened each feed from the BP website here:-
[http://www.bp.com/genericarticle.do?categoryId=9033572&contentId=7062605]("http://www.bp.com/genericarticle.do?categoryId=9033572&contentId=7062605")
As each video played in the browser, right-click and 'Copy location'.
Then I pasted the location into VLC, then look in VLC Tools > Codec information.
In the 'Location' window at the bottom it shows the true feed.

---

### Post by Skipnaz on 2010-06-16
thanks ron999 for all the help

---

