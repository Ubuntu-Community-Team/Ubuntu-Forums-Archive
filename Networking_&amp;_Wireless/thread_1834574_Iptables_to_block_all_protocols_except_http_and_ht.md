---
title: "Iptables to block all protocols except http and https"
date: 2011-08-27
forum: Networking &amp; Wireless
---

### Post by sky5564 on 2011-08-27
I am trying to block all protocols except http and https, im not sure what the proper command would be to do this?

I tried this - 

```
iptables -I FORWARD 1 -p tcp -m multiport --dports 21,80,443 -j ACCEPT
iptables -I FORWARD 2 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -I FORWARD 3 -j DROP
```

But this blocks everything including http and https.

---

