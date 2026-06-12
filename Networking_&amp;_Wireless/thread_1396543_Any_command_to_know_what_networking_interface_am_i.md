---
title: "Any command to know what networking interface am i using to connect to internet"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by tirengarfio on 2010-02-02
Hi,

is there any command to know what networking interface (eth0, eth1, ..) am i using to connect to internet my PC at the moment?

Regards

Javi

---

### Post by lotharmat on 2010-02-02
```
ifconfig
```

look at the TX and RX bytes

(There is probably a better way though!)

---

### Post by bogdan.veringioiu on 2010-02-02
Try:
> route | grep default
You will see the eth device in the last column.
The command is displaying your default route, which most probably is used for internet access.
Bogdan

---

