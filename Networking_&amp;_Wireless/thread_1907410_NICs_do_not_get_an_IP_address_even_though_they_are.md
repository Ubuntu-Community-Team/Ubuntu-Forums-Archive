---
title: "NICs do not get an IP address even though they are defined in /etc/network/interfaces"
date: 2012-01-11
forum: Networking &amp; Wireless
---

### Post by dmt0 on 2012-01-11
Hi All!

It's pretty hard to google an issue like this because it gives a lot of noise results, so I'm posting it here.
Using Ubuntu 10.04.
Some but not all of my NICs don't get IPs assigned at boot even though they are defined in /etc/network/interfaces:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual
        address 172.16.1.3
        netmask 255.0.0.0
    gateway 172.16.1.255

auto tap0
iface tap0 inet static
        address 172.16.1.1
        netmask 255.0.0.0
    gateway 172.16.1.255
        pre-up vde_tunctl -t $IFACE
        post-up vde_switch -t $IFACE -s /tmp/vde-$IFACE \
                -d -g rhuser -m 664
        post-down vde_tunctl -d $IFACE

auto br0
iface br0 inet static
        address 172.16.1.2
        netmask 255.0.0.0
        gateway 172.16.1.255
        bridge_ports eth0 tap0

```Note that network-manager was apt-get purged from the system and is not in the way.
Here's my output from ifconfig:

```

$ ifconfig
br0       Link encap:Ethernet  HWaddr 78:e3:b5:90:88:df  
          inet addr:**172.16.1.2**  Bcast:172.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::7ae3:b5ff:fe90:88df/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:36414 (36.4 KB)  TX bytes:3317 (3.3 KB)

eth0      Link encap:Ethernet  HWaddr 78:e3:b5:90:88:df  
          inet6 addr: fe80::7ae3:b5ff:fe90:88df/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38598 (38.5 KB)  TX bytes:3317 (3.3 KB)
          Interrupt:32 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1408 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1408 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:113404 (113.4 KB)  TX bytes:113404 (113.4 KB)

tap0      Link encap:Ethernet  HWaddr c2:e3:c8:17:69:0f  
          inet6 addr: fe80::c0e3:c8ff:fe17:690f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:173 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```Note: only br0 is assigned IP for some reason.
Also, if I use ifconfig command to assign IPs temporarily, it works fine. assignment at boot is the issue.

There must be something very simple that I'm missing here. Any suggestions are very much appreciated!

(In case you're wondering where I'm going with all this - I'm trying to have a configuration with several virtual machines talking to each other, to the host, and to the outside network. The host will not be connected to the internet - it's only on the local network.)

---

### Post by jonobr on 2012-01-11
Your formatting of /etc/network/interfaces looks kind of quirky

This is just a wild guess.

With stuff like this
```
  
        address 172.16.1.3
        netmask 255.0.0.0
    gateway 172.16.1.255
```

try changing to 

```
       
address 172.16.1.3
netmask 255.0.0.0
gateway 172.16.1.255
```

Again, just a guess that your copy paste (if thats what you did)
has inserted hidden control characters and non blank spaces

---

### Post by drdos2006 on 2012-01-11
You might have to switch off IPv6.


cat /proc/sys/net/ipv6/conf/*/disable_ipv6
They should all be 1.

Disabling IPV6 is best done via sysctl. In ubuntu, add the following to /etc/sysctl.conf

# Disable IPV6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1


regards

---

### Post by dmt0 on 2012-01-11
jonobr: thanks, i replaced tabs with spaces and stuff, and there are no windows CRs in the file. Good thing to do, but didn't solve the issue...

---

### Post by dmt0 on 2012-01-11
> **drdos2006 said:**
> You might have to switch off IPv6.


cat /proc/sys/net/ipv6/conf/*/disable_ipv6
They should all be 1.

Disabling IPV6 is best done via sysctl. In ubuntu, add the following to /etc/sysctl.conf

# Disable IPV6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1


regards

I've seen this advice of yours is another post, used it and it was part of the solution.
The other part (workaround really, not a solution) was to put a bunch of 
"post-up ifconfig eth0 172... netmask 255..."
into each stanza. Each time I would add a line like that to one interface, another interface would stop getting IP on boot.
Got a configuration that is stable for now, but keeping my fingers crossed!
Not solved by worked around...

---

### Post by jonobr on 2012-01-11
Should
```
iface eth0 inet manual
```
not be
```
iface eth0 inet static
```


I thought the manual command was to allow other external  programs configure the ethernet interface.

I would have also thought that the tap0 should be set from static to manual as that is being configured elsewhere

Just a guess though (that should be another guess)

---

### Post by dmt0 on 2012-01-12
If I make eth0 static, than tap0 doesn't get IP assigned. Does it make any sense to you?

I'm posting the only interfaces file so far that works as intended:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual
        address 172.16.1.1
        netmask 255.0.0.0
        gateway 172.16.1.255
        post-up ifconfig eth0 172.16.1.1 netmask 255.0.0.0

auto tap0
iface tap0 inet static
        address 172.16.1.2
        netmask 255.0.0.0
        gateway 172.16.1.255
        pre-up vde_tunctl -t $IFACE
        post-up ifconfig tap0 172.16.1.2 netmask 255.0.0.0
        post-up vde_switch -t $IFACE -s /tmp/vde-$IFACE -d -g rhuser -m 664
        post-down vde_tunctl -d $IFACE

auto br0
iface br0 inet static
        address 172.16.1.3
        netmask 255.0.0.0
        gateway 172.16.1.255
        post-up ifconfig br0 172.16.1.3 netmask 255.0.0.0
        post-up ifconfig br0:1 172.16.1.4 netmask 255.0.0.0
        bridge_ports eth0 tap0

```

---

