---
title: "allow-hotplug eth0 not working"
date: 2012-01-06
forum: Networking &amp; Wireless
---

### Post by jasonlfunk on 2012-01-06
Hello,

I'm running a minimal server Natty install and am having trouble with my networking.

I am trying to configure my ethernet device to fetch an IP address when an ethernet cable is plugged in. Currently, if a cable is plugged in when the machine boots it gets the IP address or if I manually run dhclient then it works. However, if it boots without a cable plugged in and I plug it in after it boots, it does not grab an IP address automatically.

Currently, my /etc/network/interfaces looks like this:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The ethernet network interface
auto eth0
iface eth0 inet dhcp
```

I tried changing it to this:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The ethernet network interface
allow-hotplug eth0
iface eth0 inet dhcp
``` 
but it isn't working. When I plug in the cable, nothing happens. I don't see any messages in my syslog about the link coming up and the lights do not come on on the interface. (If I add "auto eth0" in addition to "allow-hotplug eth0", it acts just like the "allow-hotplug" isn't there.)

I'm thinking that there must be a problem with "hotplug" on the system. I think I read that Natty doesn't use hotplug anymore but uses udev instead. Is this correct? Am I chasing the wrong rabbit?

---

### Post by jasonlfunk on 2012-01-07
bump

---

### Post by Nicster on 2012-02-04
This is a serious problem for headless servers.

I've installed three machines with Unbuntu Server 11.10 with the intent of running them headless. If they are booted before the network is available, they never connect and must either be hard reset or a keyboard/monitor plugged in to restart them.

Does anyone know how to get network hotplugging working on Unbuntu Server 11.10? This problem effectively renders the distro useless for headless servers.

---

