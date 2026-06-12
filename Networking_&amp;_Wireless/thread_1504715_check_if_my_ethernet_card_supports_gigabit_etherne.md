---
title: "check if my ethernet card supports gigabit ethernet"
date: 2010-06-08
forum: Networking &amp; Wireless
---

### Post by infestor on 2010-06-08
with what command i can check whether my ethernet card supports gigabit speed ethernet or not?

---

### Post by chili555 on 2010-06-08
```
sudo ethtool eth0
```Here is a sample:> Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        [COLOR="Red"]1000baseT/Full [/COLOR]
--- snip ---

---

