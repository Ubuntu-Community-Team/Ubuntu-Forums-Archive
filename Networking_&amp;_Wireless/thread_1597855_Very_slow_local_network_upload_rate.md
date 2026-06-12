---
title: "Very slow local network upload rate"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by Garugaga on 2010-10-15
I used to have a windows file server and after years of issues I decided to switch to a linux based one. I downloaded Ubuntu Server Edition 10.10 a couple days ago and installed it on my file server. I set up my raid array and samba file sharing to the best of my knowledge. I started copying data over with samba and everything was working fantastically, I could write to the drives at 80 MB/s while it was initializing. While I was copying I noticed that browsing my share was very slow. While I was figuring out the problem I tried copying a file over and the fastest that it would run was about 200 KB/s. To figure out whether it was a network issue I ran iperf, I included the results here

```
Client connecting to 192.168.1.112, TCP port 5001
TCP window size: 64.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.250 port 46944 connected with 192.168.1.112 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.2 sec    688 KBytes    555 Kbits/sec


Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.1.250 port 5001 connected with 192.168.1.112 port 59150
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec    321 MBytes    270 Mbits/sec

```

I'm pretty sure that this shows that this issue is not samba-bound but that there is something wrong with my network configuration.

Here is my ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:23:54:87:22:47
          inet addr:192.168.1.250  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:54ff:fe87:2247/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6319 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7913 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:481978 (481.9 KB)  TX bytes:10221402 (10.2 MB)
          Interrupt:20 Memory:fe8c0000-fe8e0000

```

And here is my lshw of my network card.

         ```
    description: Ethernet interface
             product: 82567LM-3 Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 02
             serial: 00:23:54:87:22:47
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k4 firmware=0.4-3 ip=192.168.1.250 latency=0 multicast=yes
             resources: irq:46 memory:fe8c0000-fe8dffff memory:fe8fa000-fe8fafff ioport:d880(size=32)
```



Here is my /etc/network/interfaces file
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
     address 192.168.1.250
     network 192.168.1.*
     netmask 255.255.255.0
     gateway 192.168.1.1


```



This is on a vanilla Ubuntu Server 10.10 install with the samba package installed. I don't have much else installed besides the stock packages so I don't think that there is any package incompatibilities. This is my first time actually using linux so I'm still learning everything. If you need more information just ask

---

