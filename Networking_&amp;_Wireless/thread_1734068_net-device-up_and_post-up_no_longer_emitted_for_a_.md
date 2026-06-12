---
title: "net-device-up and post-up no longer emitted for a bridge"
date: 2011-04-19
forum: Networking &amp; Wireless
---

### Post by radarman on 2011-04-19
Hello,

After recent automatic package updates my networking setup no longer works. I had a few upstart jobs listening for net-device-up of a bridge br0, but that seems to longer be emitted. When I do a manual emit of the signal everything works:

```
initctl emit net-interface-up IFACE=br0
```

I didn't have to do this before. The signal was automatically emitted based on my /etc/network/interfaces configuration:

```
auto br0
iface br0 inet static
  address 192.168.10.1
  netmask 255.255.255.0
  gateway 192.168.10.1
  bridge_ports eth1 eth2 eth3

```

I also tried adding the manual emit as a post-up of the bridge in the /etc/network/interfaces configuration, but that did nothing.

Do any of you wonderful linux gurus have any ideas on this?

---

