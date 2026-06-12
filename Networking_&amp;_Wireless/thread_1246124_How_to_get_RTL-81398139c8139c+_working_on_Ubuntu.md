---
title: "How to get RTL-8139/8139c/8139c+ working on Ubuntu"
date: 2009-08-21
forum: Networking &amp; Wireless
---

### Post by fernandoc1 on 2009-08-21
I'm trying to solve a problem with this network card for a friend.
He is using Ubuntu Intrepid Ibex (8.10), and having troubles with networking. I've read in many places that this card seems to have a bug.
These are the links to the places that I read:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/22575](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/22575)
[http://ubuntuforums.org/archive/index.php/t-607953.html](http://ubuntuforums.org/archive/index.php/t-607953.html)
[http://ubuntuforums.org/showthread.php?t=1032143](http://ubuntuforums.org/showthread.php?t=1032143)

Do someone knows a solution to this?
An upgrade to Jaunty Jackalope will solve the problem?

---

### Post by jamest09 on 2009-08-21
Think I have that card at home and it works fine on karmic

---

### Post by fernandoc1 on 2009-08-21
But Karmic hasn't been released yet.
Is there an other option to get this working?

---

### Post by cascade9 on 2009-08-21
I've used a RTL-8139 on a few distros, and never seem to have had any problems, apart from DHCP. Probably more of a router problem than anything else, but still very annoying. 

If your friend is havign the same issues I was (cant get an adress from DHCP etc) what works for me is to turn the router and modem off, let it sit for a while (I find 5 minutes works), then turn everything back on.

---

### Post by fernandoc1 on 2009-08-21
As you can see, in the links I posted before, it seems to be a bug in Ubuntu that prevents the card's modules to be properly loaded.

---

