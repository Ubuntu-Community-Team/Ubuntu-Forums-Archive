---
title: "Wireless connection problems to Airport Express"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by John Azelvandre on 2009-03-22
I've set up an Airport Express as a wireless hub.

I'm having great difficulty getting my Ubuntu laptop to connect to it.  It sees it listed in the choice of wireless networks, and signal is strong (it's only a few feet away at the moment), but it absolutely refuses to pick up the connection.  The little connecting icon just keeps whirling.  Doesn't time out or anything.  Doesn't get to the asking for password stage either, which is should, right away.

UPDATE: hovering over the swirling icon, it says "Waiting for Network Key for the wireless network 'Hedgewizard Express'"  (that's the name I gave the network in Airport Express).

The weird thing is that when I first tried this last night it DID get to the password stage, and picked up the signal, but no internet.  Now it just spins.  Is there some cache that needs to be dumped?

The Airport seems to be working fine.

Any suggestions?

---

### Post by John Azelvandre on 2009-03-23
An update on this problem:  I had to further refine settings on the Airport Express base station: now it's working properly, and I get a connection on my Ubuntu laptop (Running 8.04).

I'm having a slightly different problem on the Ubuntu side.  I suspect it has something to do with security on the wireless network.

The base station is set up with WPA/WPA2 security.  A password is required to join the network.

If I have just restarted the wireless base station, or just rebooted the Ubuntu box, the wireless service is detected, requests a password, and then connects normally.  Everything is fine for a long time, until it comes time to reconnect to the wireless network (say, after the laptop has been asleep for a while).  

Then, when attempting to connect to the network, it asks for the password, but times out and rejects the connection before I've even had time to enter the password!  Rebooting Ubuntu fixes this problem.  Something is not resetting or being properly cleared.  Anyone have any ideas?

---

