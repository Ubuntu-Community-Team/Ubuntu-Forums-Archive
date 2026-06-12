---
title: "Slow and hanging wireless on local network"
date: 2009-04-18
forum: Networking &amp; Wireless
---

### Post by jfacemyer on 2009-04-18
I've got a couple of boxes connected to a D-Link DIR-655.

Both boxes use the same wireless card to connect - Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (from lspci).

The network works - the router as internet gateway is fine, I can transfer files between locally connected boxes via ssh, nfs, http, etc.

The problem is that, when I try to transfer larger files (over 300Mb, in this case), after a short period of fairly quick transfer (~100-300k / s) the file transfer seems to "hang".  However, quite often both computers show data transfer still taking place as if the file were being transferred, but the file doesn't get bigger.

Eventually the file will start growing again (usually after a long period, like, say, 10 minutes or so).  But these file transfers should only take a short time anyway.

I'm pretty well versed on networking, less so on wireless (though I'm gaining confidence).  The only other thing I can think to tell you is that the wireless connection has wpa encryption.

Any help debugging this problem?  Thanks.

---

### Post by hesjnet on 2009-04-18
```
ping www.ubuntuforums.org
```
and
```
sudo apt-get install traceroute
traceroute www.ubuntuforums.org
```

---

### Post by jfacemyer on 2009-04-18
Thanks for the reply.

The problem isn't getting to the internet, though.

The problem only seems to be an intranet problem.  (Though I really haven't tested it much on the internet, but I haven't seen any problems.)

Here's a traceroute of the other box.

> traceroute to antonius (192.168.0.13), 30 hops max, 40 byte packets
 1  antonius (192.168.0.13)  1.269 ms  13.658 ms  14.233 ms

I have a feeling the problem is on the other box only, though I've just considered how to test that.  I'll report anything I find.

Again, thanks.

---

### Post by jfacemyer on 2009-04-18
Well, it's not at all an internet problem.  My internet speed (on sustained downloads for a major update of about 3 weeks or so) averaged ~700k very steadily, getting as fast as 1MB/sec (!!!!!)  I've never seen it so fast.

But the intranet problem is still there.

---

### Post by jfacemyer on 2009-05-19
So, apparently sometime after the upgrade to Jaunty, the connection really bombed.  It worked the same for a while after the update.  I've changed nothing (except by automatic updates).  The card connects just fine, seemingly, and I get intermittent activity on the network and outside the network.  (By intermittent I mean about once every 4-5 minutes I get a burst of connectivity for about 15 seconds.)  The network is completely unusable on this machine.

My other computers work fine on this network, and as far as I can tell all the settings for this computer are correct.

Where do I begin tracking down this problem?  I don't know much about monitoring and figuring out network traffic.

Help?

---

