---
title: "Router crashing with my eee"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by Mitch_Toledo on 2009-01-09
Hey, I'm completely new to ubuntu and after one day with it I can't believe I've been using XP for seven years. 
A really annoying problem I'm experiencing: Ubuntu's download/installation for new software is running fine on an executable level, but the action of downloading is crashing my router, or the way my router and cable modem exchange data.
This is not a completely new problem - the router crashes with heavy download speeds maintained over 5-10 minutes and needs to be reset (unplug and replug), and just randomly crashes other times.
The router is a Netgear WPN824.
My problem is mostly that it crashes instantaneously when trying to download new programs with Ubuntu's Add/Remove program.
Any ideas, suggestions, or experience with this sort of issue?
Thanks!

---

### Post by mikewhatever on 2009-01-10
Check for the firmware upgrade for your router on the manufacturer's website. Besides that, your configuration settings may be wrong.

---

### Post by Daveth on 2009-01-10
with any reasonable supplier that might be so, but this

[http://kbserver.netgear.com/products/WPN824.asp](http://kbserver.netgear.com/products/WPN824.asp)

rather rules out an upgrade!

---

### Post by dtakamori on 2009-06-21
I experienced something similar with my wpn824.  I ended up going with the following command to reduce my laptop's wifi bandwidth usage.  Hope it helps someone.

iwconfig eth1 rate 2M auto

---

