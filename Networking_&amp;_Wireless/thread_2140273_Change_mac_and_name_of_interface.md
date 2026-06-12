---
title: "Change mac and name of interface"
date: 2013-04-29
forum: Networking &amp; Wireless
---

### Post by sakishrist on 2013-04-29
Hello *

I have a pc that I would like to use as a router and I am facing some difficulties.

First of all I would like to do the following two changes on one of the interfaces (let's say eth0):

[LIST]
[*]Change the name from "eth0" to "WAN"
[*]Change the mac address so that it matches the one registered with my ISP
[/LIST]
The problem here is that I am not really sure how linux handles these changes. For instance, in the /etc/network/interfaces I have set: ```
auto eth0
iface eth0 inet dhcp
       hwaddress ether 01:02:03:04:05:06
```And then in /etc/udev/rules.d/ I have a file with```
KERNEL=="eth*", ATTR{address}=="00:56:78:98:76:54", NAME="WAN"
```So my confusion comes from the fact that to change the mac I do it based on the name, to change the name I do it based on the mac. Is this correct, is there some better way to do this?

---

### Post by sakishrist on 2013-04-30
I found a solution, using a single udev rule:```
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="08:00:27:d9:ea:b0", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="WAN", RUN="/sbin/ip link set dev %k address 08:00:27:d9:ea:b1"
```

---

