---
title: "ATI 9700 Mobility TV out only black n white"
date: 2006-11-13
forum: Multimedia &amp; Video
---

### Post by lassegs on 2006-11-13
Hi

We dont have cable in my our apartement (moving out on wedensday :D), so we've created the most kick *** media center, using 6.10 and Mythtv. Great OS, great software. 

The computer we have got this running on is a laptop(compal cl56), with a ATI Radeon 9700 mobility with s-video out. Everything is set up and nice and dandy, except the s-video tv out. After playing around with aticonfig --tvf and --tvs a bit we only get it to show black and white (no colors!). This is really a hassle and we really dont want to use an alternative solution (Windows MCE [-( ).

We live in Norway, so we assume that we have a PAL-B tv.
Also, the tv-out is a s-video cable from the graphics card to  a SCART plug in the tv. (Ive drawn some art to illustrate this, see attachement)

BTW: this works (with color) on MS Windows.

Now please, help us get in living color. What to do!?

Cheers
Knut-Egil, Mari and Lasse

---

### Post by armandg on 2006-11-13
sounds to me like the driver doesn't like you very much... ;)

---

### Post by lassegs on 2006-11-13
That doesnt say that much. You know how to make this driver like me?

---

### Post by armandg on 2006-11-13
> **lassegs said:**
> That doesnt say that much. You know how to make this driver like me?
Have you checked with ATI that the recent driver actually supports this feature in Linux? Does this problem exist with previous drivers?

---

### Post by lassegs on 2006-11-13
The driver actually supports this feature in Linux. What we obviously need is help with confiuguring the driver.

---

### Post by lassegs on 2006-11-13
What i didnt write in the problem description above, is that i  havent tryed this hardware (same laptop, same cables and TV, on a windows computer, only the the same cables and TV on a different computer(with nvidia card). 

After some heavy googling I've found out that some people have had the same problem as me. It seems that a possible solution is to just buy a s-video to composite cable. Maybe that'll work, at least its worth a try since the cable only costs 44kr (7$)

---

### Post by lassegs on 2006-11-13
This is beginning to look more like a journal than a forum post but what the hell:

Is it really possible that the same cables and TV work with  the right configuration with one graphics card, but not with another? Is it really possible that the xorg.conf has been configured correct, but the ATI card doesnt manage to send color signals through the s-video to the TV, even though the NVIDIA card does?

---

### Post by lassegs on 2006-11-13
hmm, i had no composit cables at home and I wont be able to buy them until tomorrow. Guess ill have to tweak the xorg.conf a bit more...

---

### Post by SpanishFranks on 2007-06-14
*bump*

What happened? How did you solve?
I have the same problem.

---

