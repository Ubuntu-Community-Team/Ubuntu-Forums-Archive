---
title: "Centrino N-1030 has a hard time to connect in Ubuntu 11.10"
date: 2012-01-03
forum: Networking &amp; Wireless
---

### Post by bj44 on 2012-01-03
Hi all,

I have an ASUS laptop, When I try to "Enable Wireless" it goes right back off. It takes more than several times connecting and disconnecting within the Network Manager to get it to work. Sometimes never connects and I have to use wired connection.
The driver is iwlagn and problem started when I upgraded to Ubuntu 11.10.
uname -a:
Linux ASUS 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

Any help you can provide is appreciated.

Update: The problem was solved by updating the Kernel.

uname -a:
Linux ASUS 3.1.0-030100rc10-generic #201110200610 SMP Thu Oct 20 10:11:32 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

See ==>> [http://thelinuxexperiment.com/guinea-pigs/tyler-b/ubuntu-11-10s-wifi-crashes-my-router/](http://thelinuxexperiment.com/guinea-pigs/tyler-b/ubuntu-11-10s-wifi-crashes-my-router/)

---

