---
title: "IPW promisc mode"
date: 2006-04-19
forum: Networking &amp; Wireless
---

### Post by bin2hex on 2006-04-19
I recently bought a Samsung q30. I firstly put Breezy on it (everything worked, except widescreen but I found a workaround) but while networking works a treat, the wireless card (an Intel Pro Wireless) will not go into promiscuous mode. 

It will go into monitor mode but not promicuous mode.

To get monitor mode I use 

```
sudo iwconfig mode monitor
```

To get proiscuous mode I use ```
sudo ifconfig eth1 promisc
```

I was wondering if anyone else has this problem and if there is a fix

Its also worth mentioning that I dist-upgraded to Dapper (again no issues) but still have the same issue

Thanks, Ade

---

