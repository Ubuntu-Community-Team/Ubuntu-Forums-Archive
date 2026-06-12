---
title: "firestarter help, ports don't appear to be open"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by piusvelte on 2009-04-01
I've set up a new, clean install of 8.10 and added lighttpd, squid, openssh-server, and firestarter. This is my home network's internet gateway. In firestarter, ICS works fine, but I can't seem to open or forward ports on the external interface. At first, I had lighttpd and ssh running on ports 80 an 22, respectively, and I tried to add policies forwarding 8080->127.0.0.1:80, and 2222->127.0.0.1:22. No go. Then I configured both services to run on ports 8080 and 2222, and just opened those ports for the external interface. No go. Internally, this all worked fine and I can get to the services.

I've preferences set to apply policy immediately, though restarted networking just to be sure.

I've checked that my dhclient exit hook script is updating my dynamic dns records with zone edit.

Any ideas what I'm missing? I'm at work and obviously can't reach my machines to troubleshoot, so I'll have to wait until tonight to work more on this. I really appreciate any helpful suggestions  or ideas. I plan to get more familiar with iptables, but was in a bit of a hurry to replace my old machine and have read good things about firestarter. Thank you!

---

### Post by piusvelte on 2009-04-02
Nevermind. I removed all of my rules, triple checked dyndns and re-added the rules and it's all fine now.

---

