---
title: "working network but not internet access from one machine"
date: 2013-05-19
forum: Networking &amp; Wireless
---

### Post by black-beard on 2013-05-19
I have a macmini 6,2 (2012) running 12.04 which I use a mythtv frontend. I have just been setting up apache and as soon as i got it working I could no longer connect out to the internet.

I am using a fixed ipaddress on eth2
(eth1 is wifi and disabled etho has never been there)
 
I am able to connect via ssh, also to apache web pages, mythtv connects to the backend and I can ping the gateway

ifconfig is as follows.

> eth2      Link encap:Ethernet  HWaddr a8:20:66:1e:3c:f5  
          inet addr:192.168.1.148  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::aa20:66ff:fe1e:3cf5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:127 errors:0 dropped:20 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22026 (22.0 KB)  TX bytes:9416 (9.4 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13074 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13074 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:907147 (907.1 KB)  TX bytes:907147 (907.1 KB


when i restart the network interface i get

> c@mcf:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                              ssh stop/waiting
ssh start/running, process 3338

  any thoughts?

thanks in advance

---

### Post by daanvbaal on 2013-05-19
This is probably because you have a fixed ip-address. The computer doesn't ask for an ip-address with dhcp, so it doesn't get any information about which gateway to use.

To solve this, edit you're /etc/network/interfaces file:
```

auto eth2
iface eth2 inet static
        address 192.168.1.148
        netmask 255.255.255.0
        gateway 192.168.1.1

```

Restart the network with:
```

user@yourhost$ sudo service networking restart

```

To check if the gateway is used, check the routes in use:
```

user@yourhost$ route

```

It should include this:
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth2

```

---

### Post by black-beard on 2013-05-19
/etc/network/interfaces is currently 

>     auto eth2
    iface eth2 inet static
    address 192.168.1.148
    netmask 255.255.255.0
    gateway 192.168.1.1
    network 192.168.1.0
    broadcast 192.168.1.255


tried removing network and broadcast but still the same

route gives me 

> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth2
link-local      *               255.255.0.0     U     1000   0        0 eth2
192.168.1.0     *               255.255.255.0   U     0      0        0 eth2

---

### Post by prodigy_ on 2013-05-19
> **black-beard said:**
> tried removing network and broadcast
Those are optional but can't hurt so no need to remove them. Instead you should add dns-nameservers option (e.g. **dns-nameservers 8.8.8.8 8.8.4.4**) and reboot because this looks like a name resolutions issue.

Then try: ```
cat /etc/resolv.conf
dig iana.org
```

---

### Post by black-beard on 2013-05-19
> **prodigy_ said:**
> Those are optional but can't hurt so no need to remove them. Instead you should add dns-nameservers option (e.g. **dns-nameservers 8.8.8.8 8.8.4.4**) and reboot because this looks like a name resolutions issue.

Then try: ```
cat /etc/resolv.conf
dig iana.org
```

thats fixed it thank you!!!
:)

---

