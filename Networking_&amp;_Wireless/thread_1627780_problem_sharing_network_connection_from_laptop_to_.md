---
title: "problem sharing network connection from laptop to desktops"
date: 2010-11-21
forum: Networking &amp; Wireless
---

### Post by KFwLsKvVAs on 2010-11-21
Hello,

I'm having this networking issue.  

Here's the deal.  I got a laptop with wireless.  Next to it I got 2 desktops, neither of which have a wireless card and I don't have any usb wireless adapters or anything.  I do however have an ethernet cord.  In the past I was able to set my eth0 connection to be "shared to other computers", then from my laptop I could run the patch cable to the desktop and voila, internet to the desktops.  

For some reason though, now whenever I try to connect from the desktops, there are 2 green circles and a little blue circley thing going around them.  it spins for a while and then says disconnected.  

Also, now if (on my laptop) I connect to the wired network, my wireless stops working.  

I'm kind of stumped here, I tried deleting both connections from both computers, setting everything up again, and connecting, and I get the same problem.  Also seeing as how I'm trying to troubleshoot this from my laptop and watch this thread, I can't exactly mess around with it much right now or I won't see any replies.  

So if anyone has some ideas of how to get this fixed, or at least how to start, I'm all ears.

---

### Post by KFwLsKvVAs on 2010-11-22
anybody at all?

Is there some setting that would prohibit me from using both network interfaces simultaneously?  

I really don't know what to try next.

---

### Post by Iowan on 2010-11-22
It's been awhile since I played with connection sharing. You didn't mention which version you use - but you *should* still be able to share eth0 as you did in the past. I presume [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") method should still work.

---

### Post by KFwLsKvVAs on 2010-11-30
That's the guide I originally used when I first had it working.  

I followed the steps again, exactly (I had forgot to restart after changing the setting to "shared to other computers" before), and attempted to connect the desktop to the laptop again.  

The network status icon has two green balls and a blue thing that goes around them for a long time, way longer than it usually took when the connection was working.  Then it says connected, but there is no connectivity aside from being able to ping the laptop, but nowhere outside of the local network.  

Also, and I experimented with this a  few times, as soon as the laptop connects to the wired network (the desktop), the wireless stops working.  It says i'm still connected, but I can't reach anything on the internet.  As soon as I click disconnect from the wired network, the wireless starts working again.

---

### Post by KFwLsKvVAs on 2010-11-30
as far as which version, I'm not sure I follow you.  What version of Network Manager?  Or of Ubuntu?  I'm using NetworkManager Applet 0.8.1 and Ubuntu 10.10 with all the current updates.

---

### Post by Iowan on 2010-12-01
Ubuntu 10.10 is the answer I was seeking. Unfortunately, my 10.10 box doesn't have 2 NIC's, so I can't see if it'll share one (although I could probably plug one to try...) You might check **route -n**. It's possible the routing gets messed up when the wired connects...

---

