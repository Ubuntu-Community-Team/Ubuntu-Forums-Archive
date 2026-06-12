---
title: "ssh -X user@machine (already running program)"
date: 2010-08-02
forum: Networking &amp; Wireless
---

### Post by FiVAL on 2010-08-02
He Hi Hello!!

ssh between 2 machines is no problem. And start (for example)
firefox over ssh by X-Forwarding is also no problem.

BUT is it possible to "take over" an already running program?

My situation: I alway leave my (ubuntu) computer on, logedin
and locked when I leave the office. Also my Thunderbird is then
still running... From home I easily can login by ssh (and RSA)
to this computer, but can I "take over" the running Thunderbird?
OR can I get a "copy" of this thunderbird-screen?

ThX in advanced!

---

### Post by Iowan on 2010-08-02
I don't have an answer, but "taking over" an existing connection sounds generically "dangerous".

---

### Post by CharlesA on 2010-08-02
You'd need to use VNC or something like that to view yer desktop. I do not believe you can "take over" control of programs already running.

---

### Post by FiVAL on 2010-08-03
I also can imagine that it can be dangerous to "take-over"...

But something like VNC takes copies the whole screen.
And in my situation that's a resolution of 2560 x 1024!!
It's so sssslllloooowwww on the remote (10") laptop :-)

Is it maybe possible for VNC to take only 1 application over?

---

### Post by CharlesA on 2010-08-03
I know you can set VNC in Windows to do that, but I don't know how you can do that in VNC for Linux, since as far as I know, it will only grab the desktop.

---

