---
title: "Waiting 60 more seconds for network Configuration"
date: 2012-04-14
forum: Networking &amp; Wireless
---

### Post by jbowen7 on 2012-04-14
Very long time to boot after defining a bridged interface. Before reaching lightgdm login, I get:

"Waiting for network Configuration"

Then a while later:

"Waiting 60 more seconds for network Configuration"

This bug seems to be posted all over, but with no real fixes, other than some hacks like editing /etc/init/failsafe.conf to sleep less.

The problem only persists when my ethernet cable isn't plugged in.

/etc/network/interfaces
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet dhcp
bridge_ports eth0
bridge_stp off
bridge_fd 0
bridge_maxwait 0
```


Some various messages at syslog:
```
NetworkManager[1121]: <warn> /sys/devices/virtual/net/br0: couldn't determine device driver; ignoring
udevd[418]: timeout: killing 'bridge-network-interface' [494]
NetworkManager[1121]: <info> Unmanaged Device found, state CONNECTED forced. ( see http://bugs.launchpad.net/bugs/191889

```



Affects 11.10, and 12.04 final beta.

---

### Post by krishnamohan on 2012-06-30
Hi...

I had the above problem as well as the problem of Network Manager not starting on startup...

Commenting out the following lines in /etc/network/interfaces fixed both problems for me..

```
auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet dhcp
```


You may have to comment out something different..

---

