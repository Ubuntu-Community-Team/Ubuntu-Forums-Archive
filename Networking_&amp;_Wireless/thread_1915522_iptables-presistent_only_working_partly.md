---
title: "iptables-presistent only working partly"
date: 2012-01-26
forum: Networking &amp; Wireless
---

### Post by Empire-Phoenix on 2012-01-26
well i have the problem, taht I want to automatically apply a ruleset on startup.
I installed iptables-persistent to do so, and it works partly.

if I do iptables-save after a startup everything looks fine, however the rules are somehow not applied untill i do a iptables --flush manually. 
(I tried to just add it to the script after the restore, but it does not make a difference there)

I have a kvm installed and running if that changes anything, not sure.

---

