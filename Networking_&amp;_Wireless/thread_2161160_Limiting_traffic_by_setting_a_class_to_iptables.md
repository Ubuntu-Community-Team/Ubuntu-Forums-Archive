---
title: "Limiting traffic by setting a class to iptables"
date: 2013-07-09
forum: Networking &amp; Wireless
---

### Post by sl3ax on 2013-07-09
I read many tutorials on the web, and after have setting up various rules with *nix "tc" command, i had to set up also iptables for limiting incoming traffic. Tutorials suggest to type this command: ```
 iptables -t mangle -A OUTPUT -j CLASSIFY --set-class 1:1 
``` So, assuming that class 1:1 is configured (with tc),  why should i define a rule in the OUTPUT chain  for incoming connections? I noticed that, once set, the limit apply both to oncoming and outcoming connections. Why is that?

---

