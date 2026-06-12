---
title: "Incrising network interface and problems with router"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by augustosantos on 2008-12-19
Hi guys,
I´m new here and I need help, please!!!

I have a motherboard Gigabyte GA-M61PM-S2 and my problem is:
Always when I reboot my system, in my case an Ubuntu 8.10 32bits, a new network card is recognized, and the number oh the ethernet controller is increasing like eth1, eth3, now it´s on "eth19". Can you help me with this problem? Nobody on other forums ever saw this problem.
The other problem is: I have an ADSL modem which used to work as a bridge and when I wanted to login is the internet I had to do the follow command: "sudo pppoeconfig", it recognized my ethernet controller, I had to put login and my password, but happened all the things that I said already, that is, my ethernet controller was always increasing after reboot. But now, I turned the modem to work as an ADSL router modem, and my ubuntu didn´t recognized again.
What I have to do guys?

Since now, thanks a lot!

Augusto Cesar.

---

### Post by Iowan on 2008-12-19
I remember seeing another thread (maybe a couple) with a similar problem (eth# keeps climbing).  I'll see if I can find it.
[This one]("http://ubuntuforums.org/showthread.php?t=941466") is similar. [ Another one.]("http://ubuntuforums.org/showthread.php?t=964105") Something unusual in /etc/udev/rules.d/70-persistent-net.rules.  I thought I found a thread with more of a solution - still looking...
Might be weirdness with forcedeth - check that file to see if you're using forcedeth.

---

