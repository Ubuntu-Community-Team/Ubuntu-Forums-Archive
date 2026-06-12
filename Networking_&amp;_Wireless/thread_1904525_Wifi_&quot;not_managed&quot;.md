---
title: "Wifi &quot;not managed&quot;???"
date: 2012-01-04
forum: Networking &amp; Wireless
---

### Post by Danny1977 on 2012-01-04
Hello everyone, I have a Lenovo j3000 amd dektop running ubuntu 11.1 that I just installed, with a dlink wda 1320 wireless card. when I do the troubleshooting steps in the help section everything comes up ok. The PCI card is recognized, drivers are loaded and that is where the help stops. I checked the file NetworkManager.conf and it was 

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

so I tried to change the statement to true and looged out and back in and it did not change, while I installed the system it was getting it's files wirelessly. previously had posted the same issue, and was moved to ubuntu+1 the same issue with ver 12 unknowingly that it was under development.. Am I stuck to a wired connection? thanks for your help.

---

