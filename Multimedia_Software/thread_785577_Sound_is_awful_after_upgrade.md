---
title: "Sound is awful after upgrade"
date: 2008-05-07
forum: Multimedia Software
---

### Post by web250 on 2008-05-07
I never had problems ever with gutsy and sound.

Now, I have problems galore with Hardy. Flash often kills sound, mplayer often kills sound.

I hate how I have to walk on eggshells constantly when viewing multiples flash videos, or playing music in amarok while i play a flash video in Firefox.

I need to pgrep and kill processes extremely often after things crash.

How can I make my sound right again?

---

### Post by billgoldberg on 2008-05-07
In a terminal (application -> accessories) copy paste this:

```
sudo apt-get install libflashsupport
```

That should fix things.

---

### Post by ThrashJazzAssassin on 2008-05-07
I had the same problem till I installed the package and followed the instructions here

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888/comments/39](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888/comments/39)

---

### Post by web250 on 2008-05-07
Tried both of those...I'll see how it works!

---

