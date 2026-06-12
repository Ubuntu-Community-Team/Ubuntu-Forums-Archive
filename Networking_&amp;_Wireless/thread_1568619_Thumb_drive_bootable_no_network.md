---
title: "Thumb drive bootable no network"
date: 2010-09-05
forum: Networking &amp; Wireless
---

### Post by MooPi on 2010-09-05
I have a thumb drive with a minimal Ubuntu install. The etho interface functions on the original machine it was setup on but if it travels to a new machine to boot from no ethernet connection. I've tried ```
sudo ifconfig eth0 -dynamic
``````
sudo ifconfig eth0 up
```Nothing happens, I'm sure it works just can't get it to connect on another machine. Much needed connection because I'm using this to diagnose problems on other computers.
Okay I edited the /etc/network/interfaces
basically when the device was booting from another machine it recognized the device as eth1 instead of eth0. I added the lines to interfaces ```
# The secondary network interface
auto eth1
iface eth1 inet dhcp
```

---

