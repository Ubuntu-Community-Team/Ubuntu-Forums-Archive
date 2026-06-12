---
title: "Trying to get Belkin wireless card working with 10.04"
date: 2010-06-30
forum: Networking &amp; Wireless
---

### Post by chkneater on 2010-06-30
I have a Compaq AMD64 that has ubuntu 9.04 on one HD that works great.  I've installed 10.04 on a separate HD and had problems installing it.  I have 10.04 running now but I can't get my wireless card to work.

During installation I skipped setting up the wireless network.  Now when I boot into the 10.04 partition I cannot get the nm-applet to work.  I can't get it onto the task bar and I don't see it anywhere else.  I checked to see what drivers are installed, and since I have no connection with that OS I can't update or DL drivers for it.

I'm pretty sure that it is because I skipped setting it up during installation.  What do I need to do to get the wireless working now?  I checked other threads and none seem to pertain to my situation.  Thanx for any help in advance.

P.S. Since I have to log into the 9.04 partition, I can't copy/paste outputs very easily.

---

### Post by ReginaldPerrin3 on 2010-07-01
Open a terminal and type "nm-applet"
This should start the network manager.

If this does not work at all, then you can try installing a different manager program, like Wicd.
Works in a similar fashion to Network Manager.

If you can still not get connected, then there might be a conflict with drivers. This may be preventing Network Manager from starting up properly.

---

### Post by chkneater on 2010-07-01
nm-applet doesn't even exist.  That is why I'm pretty sure the problem is related to the problem I had installing it.  I skipped the wireless setup during installation altogether.  

Without any connection there is no way to get driver updates.

---

### Post by chkneater on 2010-07-01
I have used wicd on a different comp. and it worked good with this belkin wireless card.  I would use that if I could figure out a way to install it to that HD while logged on to the other HD.

---

