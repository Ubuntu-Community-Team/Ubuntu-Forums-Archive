---
title: "Ethernet configuration"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by dineshs on 2010-03-15
If I configure my ethernet as in step-1 in the following link
[https://store.opendns.com/setup/device/ubuntu/](https://store.opendns.com/setup/device/ubuntu/)
In which file the details are written?Because I dont find any difference in /etc/network/interfaces.In older versions of ubuntu I used to configure ethernet via system-admin-networking and there was no confusion

---

### Post by dineshs on 2010-03-15
pl help

---

### Post by Iowan on 2010-03-15
> **dineshs said:**
> 
In which file the details are written? There is a */etc/NetworkManager* directory... but seems like the information is buried under (alt-F2)- gconf-editor >System>networking on my Jaunty laptop...

---

### Post by dineshs on 2010-03-16
> **Iowan said:**
> There is a */etc/NetworkManager* directory... but seems like the information is buried under (alt-F2)- gconf-editor >System>networking on my Jaunty laptop...

I dont find networking under system.Can we edit the file in the same manner as editing /etc/network/interfaces, to avoid configuration via GUI ?

---

### Post by dineshs on 2010-03-24
It is in
/etc/NetworkManager/system-connections
I find the contents as under
```
[connection]
id=Wired connection 1
uuid=7b588ed0-0acc-4314-b710-71c86c01e18c
type=802-3-ethernet
autoconnect=true
timestamp=0

[ipv4]
method=manual
dns=8.8.8.8;
addresses1=192.168.1.100;24;192.168.1.1;
ignore-auto-routes=false
ignore-auto-dns=false
never-default=false

[802-3-ethernet]
speed=0
duplex=full
auto-negotiate=true
mtu=0
```

---

### Post by Iowan on 2010-03-24
I'll check my Karmic machine when I get home - curious that it would be in such a different place...

---

