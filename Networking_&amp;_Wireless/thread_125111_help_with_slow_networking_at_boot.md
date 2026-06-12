---
title: "help with slow networking at boot"
date: 2006-02-03
forum: Networking &amp; Wireless
---

### Post by vorsia on 2006-02-03
Hi all,

Just a small annoyance... Networking is very slow to start when my computer starts. I can work around this each boot by pressing ctrl+c to skip it, however i would prefer a fix. I modified the /etc/network/interfaces file and commented out the "auto eth0" and "atho eth1" (wired and wireless interfaces). However it appears that whenever these lines are removed the system writes them back into the file when it starts up again.

How can I stop the system from adding the "auto eth0" and "auto eth1" lines to the /etc/network/interfaces file???

---

