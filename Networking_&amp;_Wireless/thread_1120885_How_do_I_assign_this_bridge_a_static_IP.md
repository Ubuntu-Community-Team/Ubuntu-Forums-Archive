---
title: "How do I assign this bridge a static IP?"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by Underpants on 2009-04-09
I followed this guide: 
[https://help.ubuntu.com/community/NetworkMonitoringBridge](https://help.ubuntu.com/community/NetworkMonitoringBridge)

Everything is working great, except I would like to assign a static IP to the bridge interface instead of it getting DHCP. 

The document says to use the line 
```
iface bridge01 192.168.1.2 netmask 255.255.255.0 up
```
but that results in an error about too many or the incorrect number of arguments when the networking service is restarted. 

This is what my config looks like now:

```
# The loopback network interface
auto lo
iface lo inet loopback

auto bridge01
iface bridge01 inet dhcp
  pre-up ifconfig eth0 down
  pre-up ifconfig eth2 down
  pre-up brctl addbr bridge01
  pre-up brctl addif bridge01 eth0
  pre-up brctl addif bridge01 eth2
  pre-up ifconfig eth0 0.0.0.0
  pre-up ifconfig eth2 0.0.0.0
  post-down ifconfig eth0 down
  post-down ifconfig eth2 down
  post-down ifconfig bridge01 down
  post-down brctl delif bridge01 eth0
  post-down brctl delif bridge01 eth2
  post-down brctl delbr bridge01
```

---

### Post by Underpants on 2009-04-14
bump for help.

---

