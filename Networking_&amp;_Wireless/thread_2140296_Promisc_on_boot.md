---
title: "Promisc on boot"
date: 2013-04-29
forum: Networking &amp; Wireless
---

### Post by sakishrist on 2013-04-29
Hello all,

How do I set an interface to go in promisc mode on boot? I tried putting "up ifconfig wth0 promisc up" in /etc/network/interfaces but it did not work.

---

### Post by sakishrist on 2013-04-30
Here is the solution to my problem.

Since my main goal was to:


[LIST]
[*]Change the mac address of an interface
[*]Change the name of the interface
[*]Put the interface in promisc mode
[/LIST]

Here is how I did it with a udev rule:```
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="08:00:27:d9:ea:b0", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="WAN", RUN="/bin/bash -c '/sbin/ip link set dev %k address 08:00:27:d9:ea:b1;ifconfig %k promisc'"
```I am not entirely sure this is the best way to do it. I used bash so that I can use two commands instead of the just one that udev seems to allow. Then I used ip (here I think ifconfig would have done the same job) and then ifconfig to put WAN into promisc.

If you think something could be done better, please advise. :)

---

