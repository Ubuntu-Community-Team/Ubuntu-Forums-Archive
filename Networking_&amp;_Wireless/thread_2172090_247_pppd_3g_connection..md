---
title: "24/7 pppd 3g connection."
date: 2013-09-03
forum: Networking &amp; Wireless
---

### Post by janis2 on 2013-09-03
Hi, I would like to set up persistant 3g connection manually using pppd daemon and chat scripts.
Everything works fine using persistant option - when network disappears, pppd tries to reconnect and it works flawlesly.
Problem is that my ISP wants that I reconnect every 24 hours - the IP address doesn't work next day - ping or anything.
I want it to reconnect automatically in case ISP has dropped support for current connection and I don't want to use any external scripts if possible.
Combination of 'persistant' and 'idle' seems like a great solution, BUT the connection isnt reestablished if it was terminted from 'idle' timer - at least as far as I have experimented.

So is there a way to configure pppd to have a persistant connection and in case there is no packet flow, then try to reconnect automatically?
Thank you

---

