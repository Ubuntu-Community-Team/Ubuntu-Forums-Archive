---
title: "One machine out of 5 inacessible"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by dmwyatt on 2010-03-14
I have 4 PC's:

1. Ubuntu 9.10 with wireless.
2. Windows 7 Machine 1
3. Windows 7 Machine 2
4. Windows Vista
5. Windows Server 2003

All machines can ping each other by ip and hostname except for the fact that the Ubuntu machine cannot ping or connect in any useful way to one of the Windows 7 machines.

An attempt to ping it by name:
```
therms@tc4200:~$ ping -c 5 Sampson
PING Sampson (192.168.1.3) 56(84) bytes of data.
From tc4200 (192.168.1.117) icmp_seq=1 Destination Host Unreachable
From tc4200 (192.168.1.117) icmp_seq=2 Destination Host Unreachable
From tc4200 (192.168.1.117) icmp_seq=3 Destination Host Unreachable
From tc4200 (192.168.1.117) icmp_seq=4 Destination Host Unreachable
From tc4200 (192.168.1.117) icmp_seq=5 Destination Host Unreachable
```

As you can see, it knows the correct IP address of Sampson.

If I attempt to browse it's network share with Nautilus I get a dialog that says:

```
Unable to mount location
Failed to retrieve share list from server
```

The machine DOES show up when I open the Network file browser, I just can't access it.  I can browse all my other windows machines just fine.

Suggestions for troubleshooting?

---

### Post by Iowan on 2010-03-15
I doubt **route -n** will provide any earth-shattering information - but verify the Ubuntu machine knows how to get to the W7 box (you mentioned that it can ping all the others...). You hinted that tc4200 cannot ping 192.168.1.3 either?

---

### Post by dmwyatt on 2010-03-15
```
therms@tc4200:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
```

192.168.1.117 is tc4200's own IP, but yeah it can ping itself.  It can't ping Sampson by name or IP (192.168.1.3).

---

