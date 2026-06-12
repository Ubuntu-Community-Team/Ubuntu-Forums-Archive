---
title: "ATI X200 compiz problems"
date: 2007-11-21
forum: Multimedia &amp; Video
---

### Post by abds on 2007-11-21
hello, 

I have an ATI X200, I installed the ATI drivers using the howto. Everything seems to be fine, except its not. When I enable desktop effects, my performance goes to hell. Even with the basic effects. Should this be happening? I mean I know that the video card is not that great, but it should be able to handle this? Any way I can fix this? Any help would be appreciated.

---

### Post by Stemp on 2007-11-21
Hi,

What howto did you follow and what driver are you using ?

---

### Post by abds on 2007-11-21
Used this howto:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Driver version:
8.42.3

---

### Post by Stemp on 2007-11-21
So you have accelerated graphics without compiz ? 
What **fglrxinfo** give you ? 
Next question are you using a xgl-server ?

---

### Post by abds on 2007-11-21
Output of fglrxinfo:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6958 Release


and no i am not using xgl-server

---

### Post by Stemp on 2007-11-21
> **abds said:**
> 
and no i am not using xgl-server

I'm pretty sure you'll have to with this version of fglrx and this video card.
If you're using gutsy just install it, quit your session, restart X (ctrl+alt+backspace) and login.
if you're using a prior version : [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

---

### Post by abds on 2007-11-21
That fixed the problem. Thanks a lot!! Really appreciate the help.

---

### Post by Stemp on 2007-11-21
You're welcome. Have fun ;)

---

### Post by abds on 2007-11-21
OK. Now I have another problem. When I start to play videos, the xgl process starts taking up A LOT of cpu time, and the videos dont play properly. There is this green bar across the top of most videos.   This happened after I installed the xgl-server, before everything was fine.

---

### Post by Stemp on 2007-11-21
For that I can't help you, I don't know much about fglrx and xgl ;)

---

### Post by abds on 2007-11-21
OK. Thanks anyway.

Anyone has any ideas?

---

