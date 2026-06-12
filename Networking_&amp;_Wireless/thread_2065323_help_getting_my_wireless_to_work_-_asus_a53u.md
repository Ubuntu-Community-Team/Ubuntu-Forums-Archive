---
title: "help getting my wireless to work - asus a53u"
date: 2012-10-01
forum: Networking &amp; Wireless
---

### Post by jensenguy on 2012-10-01
I've read many related threads to this, but I'm coming up empty on a solution that works for me. 

This is a asus a53u, with the Atheros AR9485 wireless card. I'm running a fresh install of 12.04 64bit alongside windows 7. All recommended updates installed. 

Network manager has no problem seeing my network, but never connects. 

I've tried disabling encryption and power management per other threads but no change. I've also installed 'linux-backports-modules-cw-3.3-precise-generic'. Somewhere I read someone blaming IPv6 for issues, when I set IPv6 to 'link local only' as per the suggestion, I immediately show a connection, but without any internet access. 

Any suggestions?

---

### Post by jensenguy on 2012-10-01
Well, I just tried upgrading the kernel to 3.5.0, system works fine but no change for the wireless connectivity. 

And also, the system has connected 2 times in the hundreds of tries. No rhyme or reason that I can tell, but both times once it connected it was nice and fast, and stayed connected until I shut it off.

---

### Post by jensenguy on 2012-10-02
Still trying to sort this out, It seems like if I keep trying to connect it will eventually connect, then the connection is crystal clear for good once it's up. Almost seemed like it connects to wireless a little easier when also connected to a hard line, but I can't see how that makes sense.

Appreciate any ideas!

---

### Post by bjballar41 on 2012-10-02
this worked for me just cant get it to permanently work i have to always enter it in still working on it

[http://ubuntuforums.org/showthread.php?t=1929304](http://ubuntuforums.org/showthread.php?t=1929304)

---

### Post by jensenguy on 2012-10-03
bjballar, I have tried the solution from that thread, doesn't do the trick for me, thanks though

But I believe I found a solution for me that does work (so far, 3 restarts and multiple connect/disconnects by me, its been flawless) I was in my router playing with settings, and I disabled WMM QOS. As soon as I did that and restarted the router its been perfect since. I guess my laptop/ubuntu combo was having trouble connecting with that option?

I'd still love to hear some opinion on why this is, or maybe a workaround in case im connecting to another network with this enabled.

---

