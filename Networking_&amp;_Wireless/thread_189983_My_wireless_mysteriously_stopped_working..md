---
title: "My wireless mysteriously stopped working."
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by Amablue on 2006-06-05
I have a Broadcom wireless card in my Dell insperion 2200. After reading through the other threads, I was able to get it working for a while. 

Today I was on the computer using the internet. Then I went to do some other non-internet stuff, and when I opened up FireFox the next time it didn't work. The connection was lost or something. I reset (which worked one other time when this happened) but it still wouldn't connect. 

It seems really inconsistant too. Sometimes it's able to detect the networks in my area (But it can't connect). Other times, it doesn't see any at all. Once it even said <hidden> which I've never see before.

Edit:

And now it's working again after playing with it some more, even though I just repeated the same thing I've been doing. I hope this behavior doesn't keep up. ](*,)

---

### Post by tkoster on 2006-06-06
I struggled with a similar problem (Dell 8600 with Truemobile 1300). After trying oodles of other things including dumping bcm43xx for ndiswrapper, it turned out I could fix it with this simple command:

sudo iwconfig eth1 essid on

I'm not sure if it will solve your problem but it can't hurt.

---

### Post by Amablue on 2006-06-07
I typed that in, but I don't see any immediate change in anything. I suppose that's to be expected though since it's currently working. What, exactly, does that command do?

I think I've found my problem. For some reason, my wireless card changes names. Sometimes it's eth1 and sometimes it's eth2, and I manually have to go to connection properties and switch it to the correct connection. I have no idea what's causing the wireless card's name to change.

---

