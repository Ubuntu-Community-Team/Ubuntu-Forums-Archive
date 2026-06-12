---
title: "Cannot compile Poldhu wireless driver for 3CRWE62092A X-Jack card"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by sjnovick on 2009-04-28
I have an old laptop (Pentium 2) with an 3CRWE62092A X-Jack wireless card.  Back in the day, I compiled the poldhu wireless driver ([http://poldhu.sourceforge.net/](http://poldhu.sourceforge.net/)) for it, and all was well.  Unfortunately, the code will not compile with the last few Ubuntu releases.  Has anyone had any luck?  If so, what did you do?

If I can compile the wireless driver, I will be able to give a 100% working laptop away to a friend.  Please help if you can.  Thanks!

By the way, ndiswrapper does not work with the windows driver.

---

### Post by Crafty Kisses on 2009-04-28
Do you have build-essentials installed?

---

### Post by sjnovick on 2009-04-29
Yes, of course.  There are compilation errors when I type "sudo make".

---

### Post by sjnovick on 2009-05-10
Solved, but not being fixed.  From the Poldhu driver developer:

The poldhu driver development is kinda dead these days...
I think that my board broke down, and it is quite difficult these days to find
a laptop with PCMCIA...

As far as I remember the last kernel I have seen it alive was 2.6.21, and I
made some blind fixes for 2.6.24, and then it become pointless...

The wireless code is changing a lot from kernel version to kernel version, so
it would be necessary to go in small steps - 2.6.25...26.......30
It has nothing to do with gcc - the API
 is changing...

Woody


-- Woody Suwalski, Xandros, Ottawa, Canada, 1-613-842-3498 x414

---

