---
title: "forwarding VNC ports through a remote LAN?"
date: 2010-08-26
forum: Networking &amp; Wireless
---

### Post by potat on 2010-08-26
At my home I have a headless Ubuntu machine running as a server. On the local network are multiple other machines running VNC servers (on port 5900) with static local IPs. What I'd like to be able to do is run a VNC client across the Internet from my school and access these machines directly.

My router port-forwards 5900 to the server. Is there a way to get the server to forward incoming connections on 5900 to one of the other machines on its LAN? I would like to be able to change which machine is accessed by changing something on the server rather than reconfiguring the router. Can this be accomplished through the port-forwarding features of openssh? This seems simple enough but I haven't been able to find anything like it online.

Any help is greatly appreciated.

---

