---
title: "Two network interfaces, two IPs in diferent networks"
date: 2009-09-04
forum: Networking &amp; Wireless
---

### Post by luismpedro on 2009-09-04
Dear all,
   I've a machine with two distinct ehternet adapters that I want to use for different purposes. I've configured them as follows:
```

auto eth0
iface eth0 inet static
    address 192.168.3.4
    netmask 255.255.255.0
    network 192.168.3.0
    broadcast 192.168.3.255
    gateway 192.168.3.9
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 192.168.3.2


# The DMZ network interface
auto eth2
iface eth2 inet static
        address 192.168.2.12
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 195.186.4.111 

```My ifconfig output:

```
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:1a:96:e3  
          inet addr:192.168.3.4  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:c6ff:fe1a:96e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7823 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8737 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1188446 (1.1 MB)  TX bytes:12797756 (12.7 MB)
          Interrupt:254 


eth2      Link encap:Ethernet  HWaddr 00:19:cb:54:f3:c6  
          inet addr:192.168.2.12  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::219:cbff:fe54:f3c6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:210 errors:0 dropped:0 overruns:0 frame:0
          TX packets:119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23164 (23.1 KB)  TX bytes:11040 (11.0 KB)
          Interrupt:16 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:55041 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55041 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7163112 (7.1 MB)  TX bytes:7163112 (7.1 MB)


```Each one of the network addapters is connected to a different port in my router. One allowing 192.168.3 connections and the other allowing 192.168.2  connections. 

I can successfully connect (ssh) to the machine using the 192.168.3.4 IP but I cannot connect using the 192.168.2.12 IP. 

While connected to the machine:

```
ping google.com -I eth0
PING google.com (74.125.45.100) from 192.168.2.12 eth0: 56(84) bytes of data.
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=1 ttl=49 time=124 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=2 ttl=49 time=131 ms


```But 
```
ping google.com -I eth2
PING google.com (74.125.127.100) from 192.168.3.4 eth2: 56(84) bytes of data.
^C
--- google.com ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 5007ms
```Do I need to make any other configuration in order to be able to use both network adapters to accept all IN and OUT connections? 

Thank you very much in advance for your time and answer.

Luis Pedro

---

### Post by Iowan on 2009-09-04
Are you attempting to SSH (or **ping**) from a 192.168.2.0 machine (ie. you're sure the router configuration is working for the 192.168.2.0 port?)

---

### Post by gombadi on 2009-09-04
The problem is each interface has a default gateway configured.

When you configure an interface the kernel then knows it can reach that network via that interface.
In your case it knows it can get to the 192.168.3.0/24 network via eth0 and to the 192.168.2.0/24 network via eth2. All packets for the rest of the world then get sent to the default gateway. In your case you have configured two default gateways and packets are being sent in the wrong direction.

For all packets to the rest of the world you need to decide which interface will be used. For example if you decide to use eth0 then remove the gateway line from the eth2 config, restart networking and all should work.

You can check the routing with this command -
```

route -n

```

Of course if you are wanting to be able to make connections to the world via either interface then you are looking at something else altogether :-)

---

### Post by luismpedro on 2009-09-07
Hi...
   Thank you for the answers. Indeed, adding only one default gateway solved the problem.

   Again many thanks.

   Luis Pedro

> **gombadi said:**
> The problem is each interface has a default gateway configured.

When you configure an interface the kernel then knows it can reach that network via that interface.
In your case it knows it can get to the 192.168.3.0/24 network via eth0 and to the 192.168.2.0/24 network via eth2. All packets for the rest of the world then get sent to the default gateway. In your case you have configured two default gateways and packets are being sent in the wrong direction.

For all packets to the rest of the world you need to decide which interface will be used. For example if you decide to use eth0 then remove the gateway line from the eth2 config, restart networking and all should work.

You can check the routing with this command -
```

route -n

```Of course if you are wanting to be able to make connections to the world via either interface then you are looking at something else altogether :-)

---

