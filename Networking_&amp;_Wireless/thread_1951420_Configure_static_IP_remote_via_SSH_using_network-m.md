---
title: "Configure static IP remote via SSH using network-manager"
date: 2012-04-02
forum: Networking &amp; Wireless
---

### Post by koma77 on 2012-04-02
I have a headless server running ubuntu 11.10 and network-manager.

I want to disable dhcp for eth0 and configure the IP-address statically.

How can I do that via ssh?

I can't seem to run any network-manager related software through SSH...

Can I create connection files myself in /etc/NetworkManager/system-connections? If so, how should they look?

---

### Post by chili555 on 2012-04-02
Isn't Network Manager a GUI? How are you able to run a GUI on a headless system; i.e. with no windowing manager running? Are you sure it is running?```
ps aux | grep etwork
```The usual tried-and-true method is to amend /etc/network/interfaces and ifdown/ifup the interface and be done with it.

---

