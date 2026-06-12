---
title: "Connection is slow, with packet loss to router"
date: 2010-12-06
forum: Networking &amp; Wireless
---

### Post by Ozeuss on 2010-12-06
In the past week or so, I'm experiencing connection problems-
The connection is there, but very slow, and usually i need to refresh pages once or twice before it fully loads. This symptoms is on a desktop connected directly to the router, and on two laptops.
Now, this happens on a windows-running laptop, so this might not be an ubuntu issue (unless there's a culprit process running on my machine or something).

Thing is, when i sometimes try to connect to/ping the router (192.168.1.1) it times out / there's a packet loss.
I tried a factory reset, which seemed to help for a couple of hours.
Any suggestions?

---

### Post by stlsaint on 2010-12-06
Sounds like a router issue if its on all computers on the network.  For starters try checking out bandwidth usage on the router or even try to make a some vlans to test each port usage.
If you plug directly into the modem do you still get the same network issues?

---

### Post by endotherm on 2010-12-06
do you have bittorrent or another app that opens a large number of small connections? some routers can't deal with the shear number of partially opened connections, and start responding to everything as though it were a syn attack.

---

### Post by Ozeuss on 2010-12-07
stlsaint:
What tool should I use to check bandwidth usage on  the router? the one I looked (bmon, tcpdump)- don't seem to tell that, but I might be missing something.
I'll read up on vlans.
The connection is good directly through the modem, although I tested it only for a couple of minutes.

endotherm:
That's possible.. I'll close that app and see if there's any improvement.

Thank you both.

---

### Post by Ozeuss on 2010-12-08
Turns out it was due to ktorrent- I switched to Transmission on another port, and connection is great...
Thanks again.

---

