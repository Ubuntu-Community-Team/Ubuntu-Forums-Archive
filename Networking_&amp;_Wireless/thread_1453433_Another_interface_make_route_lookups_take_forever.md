---
title: "Another interface make route lookups take forever"
date: 2010-04-13
forum: Networking &amp; Wireless
---

### Post by schoel on 2010-04-13
Hello,

I recently added a new network card to my computer to have access to a LAN. After adding this, I've had several problems.

1. When I reboot my computer the LAN card becomes the default route:
```

joel@joel-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway      Genmask         Flags Metric Ref    Use Iface
192.168.10.0    0.0.0.0      255.255.255.0   U     1      0        0 eth2
130.238.8.0     0.0.0.0      255.255.255.0   U     1      0        0 eth0
0.0.0.0         192.168.10.1 0.0.0.0         UG    0      0        0 eth2

```
How do I make eth0's gateway the default one permanently?

2. If I alter the routing table so that eth0's gateway is the default one, like this:
```

joel@joel-desktop:~$ sudo route del default gw 192.168.10.1
joel@joel-desktop:~$ sudo route add default gw 130.238.8.1

```
All lookups seem to be painfully slow whenever I want to access anything outside my own network. For example, if I ping [www.google.com](www.google.com), 4 pings take around 20 seconds even though the response time is always within a few milliseconds.
The routing table then looks like this:
```

joel@joel-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.10.0    0.0.0.0      255.255.255.0   U     1      0        0 eth2
130.238.8.0     0.0.0.0      255.255.255.0   U     1      0        0 eth0
0.0.0.0         130.238.8.1  0.0.0.0         UG    0      0        0 eth0

```

I am certain that the problem isn't my connection, because it works fine if I do:
```

joel@joel-desktop:~$ sudo ifconfig eth2 down

```

Do you have any idea what to do about this?


Thanks for any help,
Schoel

---

### Post by Iowan on 2010-04-13
In olden days, I'd have suggested setting up eth2 in */etc/network/interfaces* - dunno if Network Manager plays nice with that file anymore, but NM *should* have a way to set up routes (Edit>Manual). You can also use **man route** for information on using **route delete** and **route add** to "have it your way". Making the results permanent will be next step.

---

### Post by schoel on 2010-04-14
2. I found a solution to this. Turns out 192.168.10.1 was listed as my primary DNS and since that doesn't have any internet connection, it fails. This failing takes a few seconds. Putting 130.238.8.1 as my primary DNS made the lookups much faster.
However, I'd still like to know an answer to 1.

---

### Post by Iowan on 2010-04-14
The secret may lie in Network Manager's configuration files. The secret also seems to be where to find them... Before I upgraded a machine to Lucid, it had Karmic's NM files in */etc/NetworkManager/system-connections*. I installed Karmic on another machine - but */etc/NetworkManager/system-connections* is a directory - not a file :confused:
The information wass buried under (alt-F2)- gconf-editor >System>networking on my Jaunty laptop.

---

