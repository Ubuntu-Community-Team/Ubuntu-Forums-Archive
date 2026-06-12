---
title: "qjackctl only as sudo"
date: 2011-09-21
forum: Multimedia Software
---

### Post by drumanart on 2011-09-21
Hello.
After successfully installing a realtime kernel in my ubuntu I can run qjackctl only as super user.
After googling I found that I have to be member of the audio group so:

I write: **sudo usermod -a -G audio (myusername)**

and I put:

@audio - rtprio 99
@audio - memlock unlimited
#@audio - nice -19

to my /etc//security/limits.conf


Yeep, it works, but after rebooting the computer tha qjackmessage tells me that **jackd** was not found (or something simmilar).

And now???
Chears

---

### Post by drumanart on 2011-09-22
OK resolved.
I reinstalled qjackctl and now it works.

---

