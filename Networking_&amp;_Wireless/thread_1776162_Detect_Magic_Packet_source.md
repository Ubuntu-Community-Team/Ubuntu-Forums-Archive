---
title: "Detect Magic Packet source"
date: 2011-06-05
forum: Networking &amp; Wireless
---

### Post by VoyezScout on 2011-06-05
Hi,

I have a computer, running Ubuntu server, with WakeOnLan properly configured, and with several users which may awake it both from the local LAN or from the internet.
However, at the moment anyone who got the MAC address could just send a Magic Packet and awake the server, so I would like to add some security checks in order to "control" the situation.
So, is it possible for the server to be awaken only on Magic Packets coming from a known origin?
If not (I guest it is not..), would it be possible to detect this origin once the server is up and act consecuently? For example: I'd like to check the origin against a users list, and if the source is not in the list, notify me with an e-mail and halt the server.

Thank you in advance!

---

