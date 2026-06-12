---
title: "Network Manager"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by suda on 2009-02-01
[SOLVED]I'm a newbie to Ubuntu. Just installed 8.10 on Acer Aspire laptop using Wubi. Good install, but where is Network Manager? I see Network Configuration, Network Proxy, Network Tools and have gone into each but no luck. Help, please. :p

---

### Post by 73ckn797 on 2009-02-01
> **suda said:**
> I'm a newbie to Ubuntu. Just installed 8.10 on Acer Aspire laptop using Wubi. Good install, but where is Network Manager? I see Network Configuration, Network Proxy, Network Tools and have gone into each but no luck. Help, please. :p

Network Manager is installed by default. Right click on the network icon on top right panel (TV screen looking icon). Select edit connections and work with that.

---

### Post by suda on 2009-02-01
Thanks! Didn't know about that right click on the icon.

---

### Post by minsf on 2009-02-02
> **suda said:**
> Thanks! Didn't know about that right click on the icon.
if it ever disappear, in command line type
```
sudo /etc/init.d/NetworkManager restart
```
and hit enter. you may be asked for your administrative password

---

