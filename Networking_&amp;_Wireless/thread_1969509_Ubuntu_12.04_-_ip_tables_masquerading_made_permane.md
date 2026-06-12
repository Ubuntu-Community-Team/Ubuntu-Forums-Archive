---
title: "Ubuntu 12.04 - ip tables masquerading made permanent"
date: 2012-04-30
forum: Networking &amp; Wireless
---

### Post by User#32423 on 2012-04-30
How do I make the following ip tables rule permanent on 12.04? It looses the rule when I reboot.

sudo iptables -t nat -A POSTROUTING -s 10.10.0.0/16 -o ppp0 -j MASQUERADE

Thanks

I have tried:

sudo iptables-save > /etc/iptables.up.rules

with the result:

bash: /etc/iptables.up.rules: Permission denied

---

### Post by User#32423 on 2012-04-30
What I have done, that seems to work for now is enter the rule into /etc/rc.local

Is there a better way?:confused:

---

