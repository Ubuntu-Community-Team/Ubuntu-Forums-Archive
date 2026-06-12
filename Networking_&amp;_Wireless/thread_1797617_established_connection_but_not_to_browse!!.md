---
title: "established connection but not to browse!!"
date: 2011-07-05
forum: Networking &amp; Wireless
---

### Post by intelligence storm on 2011-07-05
hello,
there is an open wireless i can connect it -in ubuntu- but can not browse anything !!](*,)](*,)
we tried to connect via mobile it's working fine ,in addition via Windows XP it's fine ,but not in ubuntu why???!!:sad:

---

### Post by varunendra on 2011-07-07
Make sure it is getting a dhcp reply:
```
sudo dhclient
```

Else configure the connection manually through network manager, providing IP, Gateway and DNS addresses.

If unsure, connect to the wifi and post outputs of **sudo dhclient**, and:

```
ifconfig -a
```
```
route -n
```

---

