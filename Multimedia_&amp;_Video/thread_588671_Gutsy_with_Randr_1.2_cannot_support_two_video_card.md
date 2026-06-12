---
title: "Gutsy with Randr 1.2 cannot support two video cards"
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by Craigus on 2007-10-23
Shouldn't this be in the release notes ?

If the information here is correct: [http://wiki.debian.org/XStrikeForce/HowToRandR12]("http://wiki.debian.org/XStrikeForce/HowToRandR12")

> VI.4. Multi-board support broken

RandR 1.2 does not support multiple boards yet (it's planned for RandR 1.3). It means that any RandR 1.2 aware driver will crash the server if you have 2 boards. Even one board with a RandR 1.2 driver and another board with a classic driver does not work. It just crashes the X server.


That means that it is impossible to use two cards with Gutsy with xrandr aware drivers. The release notes mention that you can't mix cards with and without xrandr aware drivers, but there is no mention that you can't have two cards *at all* (without reverting both to legacy drivers).

---

### Post by Sergeantfour on 2008-01-21
If this is the cause of me not being able to install Ubuntu because of the monitor falling asleep issue relating to me having sli (and I'm not sure I understand the post well enough to say it is) then do I just have to wait for the next version of Ubuntu and hope that is has a better version of RandR?

---

### Post by Craigus on 2008-01-21
I'm not actually sure, and am hoping that someone who knows a bit more about this might help out ...

---

### Post by nonewmsgs on 2008-04-14
is this resolved for hardy????

---

