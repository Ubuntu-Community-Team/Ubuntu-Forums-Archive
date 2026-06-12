---
title: "static routing question"
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by methodtwo on 2009-11-22
Hi there
I'm sorry to ask a general question about routing on this forum but I've googled my question and could find no answer where a short answer would suffice.So here goes: In static routing when a link goes down and then comes back up how does TCP detect that the link is back up.Does it just send new segments with the SYN flag set, to original destination, and when it gets a SYN/ACK it knows that the link is back up?So what type of TCP segment is sent to probe whether the link is back up or not?.
Thankyou for your time
regards

---

### Post by puppywhacker on 2009-11-22
TCP (layer 4)knows nothing about the link (layer 2) or route (layer 3). There are timers in the TCP stack that wait for the ack's from the previous packets, if it doesn't receive them it will, drop the connection. It's up to the application to establish a new TCP connection, so sending a new SYN.

---

