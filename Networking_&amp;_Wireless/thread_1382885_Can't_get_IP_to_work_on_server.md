---
title: "Can't get IP to work on server"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by Blogem on 2010-01-16
Hello,

I consider myself to be fairly good at managing Ubuntu servers, but apparently I'm having loads of trouble with the following issue. Hope you guys can help!

I'm running a server which hosts several virtual machines, two of which are Ubuntu machines (both 8.04 LTS). Right now I have to move an IP from one VM to another. On VM1 the IP used to work just fine, but on VM2 there's no way I can get it to work. No errors or any other indications what so ever. When switching back to VM1 it works again (but that's not what I want ;) ). I removed the IP first on VM1, before configuring it on VM2.

When running ifconfig it shows the IP and I can ping it from the box itself. From other hosts it's impossible to reach it.

iptables is not running, UFW is disabled.

The IP is configured on eth2 like this:

```

#tunnel
auto eth2
iface eth2 inet static
        address 85.92.145.63
        netmask 255.255.255.0
        network 85.92.145.0
        broadcast 85.92.145.255
        gateway 85.92.145.4

```

Routetable looks fine to me as well:

```

root@smtp:/etc# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth1
85.92.145.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
85.92.145.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2
0.0.0.0         85.92.145.4     0.0.0.0         UG    100    0        0 eth2
0.0.0.0         85.92.145.4     0.0.0.0         UG    100    0        0 eth0

```

So I'm kind of stuck right now on debugging this further. Any tips on how to figure out what is going wrong?

---

### Post by DGortze380 on 2010-01-16
> **Blogem said:**
> Hello,

I consider myself to be fairly good at managing Ubuntu servers, but apparently I'm having loads of trouble with the following issue. Hope you guys can help!

I'm running a server which hosts several virtual machines, two of which are Ubuntu machines (both 8.04 LTS). Right now I have to move an IP from one VM to another. On VM1 the IP used to work just fine, but on VM2 there's no way I can get it to work. No errors or any other indications what so ever. When switching back to VM1 it works again (but that's not what I want ;) ). I removed the IP first on VM1, before configuring it on VM2.

When running ifconfig it shows the IP and I can ping it from the box itself. From other hosts it's impossible to reach it.

iptables is not running, UFW is disabled.

The IP is configured on eth2 like this:

```

#tunnel
auto eth2
iface eth2 inet static
        address 85.92.145.63
        netmask 255.255.255.0
        network 85.92.145.0
        broadcast 85.92.145.255
        gateway 85.92.145.4

```

Routetable looks fine to me as well:

```

root@smtp:/etc# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth1
85.92.145.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
85.92.145.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2
0.0.0.0         85.92.145.4     0.0.0.0         UG    100    0        0 eth2
0.0.0.0         85.92.145.4     0.0.0.0         UG    100    0        0 eth0

```

So I'm kind of stuck right now on debugging this further. Any tips on how to figure out what is going wrong?

What does the rest of the network look like?

---

### Post by Blogem on 2010-01-16
It bridged on the host server (physical server) and from there on it's to switches and routers and such. But because both Ubuntu VM's are on the same host and in the same network (same bridge, etc), I'm suspecting that it is some weird config on the Ubuntu box.

---

### Post by gombadi on 2010-01-16
> 
Routetable looks fine to me as well:
```

Code:

root@smtp:/etc# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth1
85.92.145.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
85.92.145.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2
0.0.0.0         85.92.145.4     0.0.0.0         UG    100    0        0 eth2
0.0.0.0         85.92.145.4     0.0.0.0         UG    100    0        0 eth0

```


It looks like you have both eth0 and eth2 configured the same. Both seem to be on the 85.92.145.0/24 network and both have been configured as a default gateway to get to 85.92.145.4.


Can you post the output of ifconfig inside the VM?

---

### Post by Blogem on 2010-01-29
Thank you for your answer. I didn't have time to reply in this thread and fixed my problem with a work-around (different IP, different server).

Somehow the problem got fixed by itself. I left the IP configured, changed nothing on the server (not even a reboot) but apparently the IP is working. I did do a whole lot of updates on the server yesterday (concerning separate packages, no kernel updates included), so that might have fixed it somehow.

Thank you both for your time.

---

