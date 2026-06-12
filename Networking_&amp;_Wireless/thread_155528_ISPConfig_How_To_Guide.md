---
title: "ISPConfig How To Guide"
date: 2006-04-05
forum: Networking &amp; Wireless
---

### Post by caffine_fizz on 2006-04-05
Hi,

I have recently followed the Ubuntu 5.10 guide to installing ISPConfig on my system, it was great; considering i've just come from the dark side of the force (MS Windows), it was good to have a guide like that to work through for beginers.

Anyway the install went without a hitch using putty i just copied and pasted, makeing some minor changes where sugested, for running the server web based instead of localy as the guides intended. logging into the system locally doesn't seem to present a problem either using [http://www.domain.com](http://www.domain.com) or [https://www.domain.com:81](https://www.domain.com:81) . But when you try to access the system from Web side [http://www.domain.com](http://www.domain.com) sends me to the root /www directory and when using [https://www.domain.com:81](https://www.domain.com:81), all i get is a white/blank page with no errors.

The server is set up on DMZ through the router so to my understanding i shouldn't need to worry about port forwarding from that end.

There isn't any fire wall running on the server either, running iptables -L produces the following:

Chain INPUT (policy ACCEPT)
target prot opt source destination

Chain FORWARD (policy ACCEPT)
target prot opt source destination

Chain OUTPUT (policy ACCEPT)
target prot opt source destination

I have worked through the forums and a few people seem to have problems similar but none seem to fix my problem. REINSTALL don't even suggest it, been there done that, three times and don't want to do it again.

Could any one with experience of the How to tuts, or ISPConfig please help me try and fix this?

---

