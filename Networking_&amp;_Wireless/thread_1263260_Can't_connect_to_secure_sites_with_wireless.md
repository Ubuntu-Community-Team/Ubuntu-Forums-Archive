---
title: "Can't connect to secure sites with wireless"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by Mariane on 2009-09-10
Same problem. When I go to some secure websites I get the message "can't do that, ssh is disabled" even when in preferences it is written enabled. 

But only on wireless, when I'm connected via a wire it works fine. I thought it was due to some settings in the wireless network which I have no access to (because the wired and the wireless are not the same network, not in the same building even). 

about:config ipv6.disabled solution is not possible because I have no such variable in about:config and ifconfig -a doesn't speak about ipv6 aither. 

Mariane

---

### Post by Iowan on 2009-09-10
> **Mariane said:**
> Same problem. When I go to some secure websites I get the message "can't do that, [COLOR="Red"]ssh[/COLOR] is disabled" even when in preferences it is written enabled. SSH or SSL?
(Still, neither should be wire-dependent.)

---

### Post by Mariane on 2009-09-10
SSL, sorry. Well to be frank I don't know the difference. 

I have two options:
- Enable SSL version 3
- Enable TLS

I tried the 4 possible combinations. 

Mariane

---

