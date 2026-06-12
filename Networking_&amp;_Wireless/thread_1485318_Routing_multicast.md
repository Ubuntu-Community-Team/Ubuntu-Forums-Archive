---
title: "Routing multicast"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by squaregoldfish on 2010-05-16
Here's a nice question for a Sunday evening:

I've just set up an LTSP server, with all its clients on a separate subnet to my main network - the main network is 192.168.1.x, and the LTSP clients are all 192.168.2.x. My LTSP server has 2 NICs, one on each network, and is merrily forwarding normal IP traffic from the clients to the rest of the network.

Now for the problem: I have a client/server application that has a server on one machine, and clients locate and attach to it using multicast protocols. The server is on the main network, and any other machines on the network can locate and talk to the server quite happily. The LTSP clients, however, cannot - I assume because the multicast communications aren't being forwarded by the LTSP server.

I've spent a bit of time wandering around looking for answers with no luck. Does anyone have a clue as to how I can get this working?

(By the way, as may be apparent, I don't know an awful lot about this multicast thing. Ignorance is bliss only until you find out you need the information.)

TIA,
Steve.

---

### Post by malom on 2010-05-16
Hi goldfish. 

Multicast traffic should have no trouble being routed from one network to another. Is your server (terminal server?) configured to route traffic? Can you ping the 192.168.2.x network from the 192.168.1.x network?

---

### Post by squaregoldfish on 2010-05-17
Thanks for the suggestion.

Yes, I can ping between subnets in either direction (192.168.1.x -> 192.168.2.x and vice versa).

Steve.

---

