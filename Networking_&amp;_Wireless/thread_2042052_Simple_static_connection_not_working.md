---
title: "Simple static connection not working?"
date: 2012-08-13
forum: Networking &amp; Wireless
---

### Post by yang on 2012-08-13
System A has Wi-Fi Internet access and an Ethernet port, while System B has just an Ethernet port.  I connected the ports directly to each other.  Both are fairly modern desktop PCs running Ubuntu 10.04.

On A I ran:

```

$ sudo ip addr add 192.168.0.1/24 dev eth0

$ ip route
10.66.225.0/24 dev ra0  proto kernel  scope link  src 10.66.225.153  metric 2 
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.1 
169.254.0.0/16 dev ra0  scope link  metric 1000 
default via 10.66.225.1 dev ra0  proto static 

```

On B I ran:

```

$ sudo ip addr add 192.168.0.2/24 dev eth0

```

However, when I now try to ping 192.168.0.2 from .1, I get:

```

$ ping 192.168.0.2
PING 192.168.0.2 (192.168.0.2) 56(84) bytes of data.
From 192.168.0.1 icmp_seq=1 Destination Port Unreachable
From 192.168.0.1 icmp_seq=2 Destination Port Unreachable

```

Any hints?  TIA.

---

### Post by yang on 2012-08-13
And like magic, I just pressed up enter to retry the same command again some 10m later, and it works. Any ideas why this happened?

---

### Post by yang on 2012-08-14
Just tried doing the same thing again, and once more I'm getting Destination Host Unreachable errors, except this time it's been hours and the problem hasn't gone away.

---

### Post by Bucky Ball on 2012-08-14
Check the cable and if you have another try it.

Also, if you have wireless and cable running (or actively attempting to connect) on one of the computers you could be creating some confusion.

You may be attempting to learn more about how to do this through a terminal but I would personally just set up the static IPs in Network Manager (right click, edit connections) on each machine so you KNOW you have it right and they are there, disable wireless on the machine that has it, then try the ping. If you have it right, those IPs should appear in Network Manager when you check, anyhow.

---

### Post by papibe on 2012-08-14
Hi yang.

The kernel keeps a routing cache that is looked before the static rules. Eventually, the cache is drop, or expired, and the new rules will take effect.

In order to avoid "lag" between the introduction of a new rule and its effective use, it would be required to 'flush' the kernel's routing cache:
```
sudo ip route flush cache
```
Hope that helps. Let us know how it goes.
Regards.

---

