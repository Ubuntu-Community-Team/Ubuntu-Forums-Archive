---
title: "TP-Link TL-MR3420 router problems..."
date: 2012-03-03
forum: Networking &amp; Wireless
---

### Post by omelette on 2012-03-03
Hi.  This is my first ever router, with a rated speed of 300Mb/s (bgn). While I have no problem with the internet speed it delivers, transferring files between computers connected by it is a real let-down.  For instance, with a 'direct' AP connection, my old Dell laptop with an Intel 54Meg wireless (abg) chipset was able to transfer files to & from my other computer (which has bgn wireless) at about 2Mb/s.  But despite the routers rated 300Mb/s transfer speed, the best I can achieve when the computers are transferring through it is about 1Mb/s - it's acting like a real bottle-neck!

My question, is this 'typical' for most routers?

---

### Post by gordintoronto on 2012-03-03
If you have any 802.11abg devices, the router will drop back to "g" speed.

I suspect you are getting 1 MB/s (bytes) speed, which is 8 times 1 Mb/s (bits). For every packet of data, there must be handshaking between the two computers, and the router is slower than a direct connection.

Even so, your old laptop must be brutally slow. It's the biggest bottleneck.

---

### Post by omelette on 2012-03-04
Hi, thanks for the reply.  Yes that should have been bytes, (a big 'B'!) which I was aware of.  I've just timed a 200meg file transfer and it averages out at around 1.1MB/s - which is about half the transfer rate I can get between the two same machines with a 'direct' connection, ie. with one of them set up as an AP.  The laptop although over 6 years old is actually faster that my much newer mini-pc (quad-core Atom) - it's a 1.8Ghz ProDuo dual-core, which on tests seems quite a bit faster at CPU-intensive stuff such as video-converting.

So as far as I'm concerned, the router is definitely acting as a bottle-neck.  I emailed TP-Link a few days ago about this through their email-support but have yet to receive a reply which isn't encouraging.  As it's brand-new & from Amazon I'm seriously thinking of returning it.

I'd love if someone could give me some idea as to what kind of transfer-speed-between-pc's they achieve with a similar setup - just two pc's connected via a router.

---

### Post by gordintoronto on 2012-03-04
I just ran file transfers between two machines connected to a Wireless G router, with files larger than 600 MB. In both directions, the transfer rate was about 1.9 MB/sec. Mind you, both machines are faster than your computers, and have faster hard drives.

---

### Post by lisanels47 on 2012-03-04
Are any of these computers windows?  If so, a IT friend of mine did an experiment on a wired net, and found that the windows TCPIP stack was the issue... 

He used the exact same setup after formatting both systems with linux, and got the 100M speed he expected.  Wired setup through a switch.  I'm sure MS would have fixed that by now.

---

### Post by gordintoronto on 2012-03-05
Yes, one of the systems was Windows.

I tried wireless Ubuntu to Ubuntu, but my wife and stepson were both making heavy use of the router, so it wasn't a valid test.

---

### Post by omelette on 2012-03-05
Aha, so about 2M/s would seem to be the figure I'm looking for, and what I'm also seeing - thanks for that!  I also made another discovery - the 'slowdown' only happens when the slow 54Mb/s abg-wireless pc is receiving data - when the fast bgn-wireless pc is receiving data, it does so at 2MB/s, twice as fast!

I actually got a reply from TP-Link today, requesting for some more information on my setup, so there may be some hope yet.  Incidently, while googling for information on this I came across someone with similar problems with slow wireless where the problem was causing by using TKIP with WPA2.  Switching to AES solved the problem.  This was with 300Mb/s bng-wireless though. Unfortunately Gnome & NetworkManager don't provide GUI-access to those.  Time for some more googling maybe...

---

### Post by gordintoronto on 2012-03-06
As a comment, I have the same security setup, plus MAC Address filtering.

---

