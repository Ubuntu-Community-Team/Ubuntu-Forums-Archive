---
title: "UDP Hole Punching Help"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by statistic on 2009-07-01
So for interest's sake I've been trying to implement some direct connections through NAT's, and have had little success. I'm able to run torrent clients and various gaming applications from behind this NAT, so I don't think it's an issue of the NAT not being able to do it.

My model as of now is that I have an account on an external server, and am trying to punch a hole from inside my home NAT to be able to accept a connection from the external server.

So my home machine sends a UDP packet simply containing "Handshake\0" to the server which I thought should punch the hole. So immediately after sending the packet over port 1500, it switches to listening on port 1500 and as quick as I can (estimated time for me to hit alt+tab, enter: <0.5 seconds) I signal over SSH to send a UDP packet over port 1500 to my home. The packet never gets received.

When I switch the server/client roles it all works fine since the server isn't behind a NAT, so I don't think the implementation completely fails, just the NAT traversing part.

Anyways, if anyone could tell me what I'm doing horribly wrong, or point me to a library (preferably in C) that can implement it for me, or maybe explain another way to allow incoming connections through a NAT, I would be much obliged.

The final product I hope to have would be able to connect two machines behind two separate NATs using an external server as described in [http://www.brynosaurus.com/pub/net/p2pnat/index.html#SECTION00033000000000000000]("http://www.brynosaurus.com/pub/net/p2pnat/index.html#SECTION00033000000000000000")

---

