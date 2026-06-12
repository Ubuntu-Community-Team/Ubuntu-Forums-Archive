---
title: "Unstable internet connection..cutting off"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by hoboy on 2009-11-02
since I have upgrade to 9.10 I am experiencing that the internet connection unexpected cut off, and it is slow to load sites.
I use vista dual booting, I don't experienced the same in windows so it has to be because of the upgrade.
I use NetGear router
I really don't where to look for a solution.

---

### Post by jmlm-1970 on 2012-10-24
It can be several things:

1. disk hardware failure, like I/O errors, can cause net to go off because it fails to store data from browser.

2. firewall blocking traffic, should have a rule to allow out tcp 25,53,80,110,443 and also allow out udp 53.

3. if you have multiple firewalls programs, running simultaneous, that can also became a problem, like ufw and gufw, it is better to use only gufw...

---

