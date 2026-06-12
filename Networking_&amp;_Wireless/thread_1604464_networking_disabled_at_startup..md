---
title: "networking disabled at startup."
date: 2010-10-24
forum: Networking &amp; Wireless
---

### Post by BrokenFishCake on 2010-10-24
for some reason, since i switched to a static ip configuration my wired nic is disabled at startup.  in order for it to work i have to manually start it with ifup. i am not using a network manager of any kind.




```
$ cat /etc/network/interfaces

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
iface eth0 inet static
address 192.168.2.40
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255
gateway 192.168.2.1
```
```
$ dmesg | grep eth0
[    1.717814] eth0: SiS 900 PCI Fast Ethernet at 0xe800, IRQ 19, 00:01:6c:35:39:18
.....................
[  259.656959] eth0: Media Link On 100mbps full-duplex 
[  268.080013] eth0: no IPv6 routers present

```i have tried removing the startup scripts and re-adding them, still the same issue. card disabled. any ideas?

thanks.

---

### Post by BrokenFishCake on 2010-10-24
for the time being i have just created a boot script to start the device. can anyone explain why could have happened?

---

