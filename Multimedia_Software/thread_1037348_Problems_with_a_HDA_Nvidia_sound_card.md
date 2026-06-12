---
title: "Problems with a HDA Nvidia sound card"
date: 2009-01-11
forum: Multimedia Software
---

### Post by melinko2003 on 2009-01-11
So here's the issue I've ran into and some solution's i've been able to cook up on my own. 

While using ANY voip software mic will drop or sound will drop all together making it so we have to shutdown the machine let it sit for 10s and then start it. Using the Reboot function wont fix the problem.

Next solution which works every once in awhile is, we go into terminal and kill GDM , then restart it and sound starts again. 

This is highly frustrating because these problems are common amongst other machines, but the machine with the HDA Nvidia has the problems ever 4 to 6 hours. Any recommendations? I've been fighting with this one for a week now. 

What i've concluded is something in GDM is causing the conflict after several hours, but restarting pulseaudio does nothing. Anyone have a clue whats going on here?

Kind Regards,

Llew

---

### Post by melinko2003 on 2009-01-11
bump

---

### Post by J1m on 2009-05-15
Hi,

I just solved my HDA Nvidia sound card woes by upgrading ALSA.

[http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/)

Good Luck!

Jim

---

