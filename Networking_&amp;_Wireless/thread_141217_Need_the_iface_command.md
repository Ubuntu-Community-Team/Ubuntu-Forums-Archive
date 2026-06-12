---
title: "Need the iface command"
date: 2006-03-07
forum: Networking &amp; Wireless
---

### Post by racsw on 2006-03-07
Hi guys,
  Not sure why, but my wireless boot-up problem might be because I have no "iface" executable anywhere on my 5.10 system.  This is needed in the /etc/network/interfaces script to bring up ath0.

  Where do I get this?

Thanks,
Robert

---

### Post by ssam on 2006-03-08
/etc/network/interfaces is not an executable script just a config file.

the comand to bring up an interface is
```
sudo ifup ath0
```
and to bring it down
```
sudo ifdown ath0
```

ifup and ifdown read /etc/network/interfaces to find out what settings to use

---

