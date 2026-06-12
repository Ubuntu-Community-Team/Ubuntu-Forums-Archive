---
title: "Help with forwarding packets from a Tun to an Eth interface"
date: 2012-08-30
forum: Networking &amp; Wireless
---

### Post by ChristopherJO on 2012-08-30
[********SOLVED*********]

Good Morning all,

I have a C-Program that currently creates a Tun (tun0) and writes to it.  This part works fine, but I then want the packets to be forwarded over eth0 (different network), this unfortunately is not working.

If I force a ping with a src of the tun0 then this successfully exits via eth0 - so I am happy my routes are correct.

Any additional information that you can provide to help me resolve this would be much appreciated - see below the interfaces information.

TUN is setup with these flags:

```
IFF_UP | IFF_RUNNING | IFF_NOARP | IFF_PROMISC
```

after the program sets them up I then set the ip addresses.  The network resembles this:

```

MACHINE1:
      tun0      |   |     eth0    |
 192.168.1.1/28 | - | 10.1.1.1/16 |---|
                                      |
MACHINE2:                             |
      tun0      |   |     eth0    |   |
 192.168.2.1/28 | - | 10.1.2.1/16 |---|

```

IP forwarding is on via:

```

sysctl -w net.ipv4.ip_forward=1

```

ifconfig gives me this:

```

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:192.168.1.1  P-t-P:192.168.1.1  Mask:255.255.255.240
          UP POINTOPOINT RUNNING NOARP PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:694 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:80504 (80.5 KB)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 52:54:00:9a:bc:9a  
          inet addr:10.1.1.1  Bcast:10.1.255.255  Mask:255.255.0.0
          inet6 addr: fe80::5054:ff:fe9a:bc9a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18076 errors:0 dropped:65 overruns:0 frame:0
          TX packets:537 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2017435 (2.0 MB)  TX bytes:74778 (74.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3450 (3.4 KB)  TX bytes:3450 (3.4 KB)

```

(it is worth noting that I am setting the IP addresses manually, after the program has set up the tun.  I am using this as *ifconfig tun0 192.168.1.1/28*.

and my routing table:

```

default via 10.1.2.1 dev eth0  metric 100 
10.1.0.0/16 dev eth0  proto kernel  scope link  src 10.1.1.1 
192.168.0.0/16 dev eth0  scope link  src 192.168.14.1 
192.168.1.0/28 dev tun0  proto kernel  scope link  src 192.168.1.1 

```

I've been pulling my hair out a bit about this, and have tried several solutions that I have found while researching this on the internet.  Including iptables forwarding but I am having no luck with this.

If I tcpdump tun0 I see:

```

11:43:00.847394 IP 192.168.1.1 > 192.168.2.1

```

but nothing of the sorts while tcpdump is on eth0

Any help is greatly appreciated.

Many thanks,

Chris.

---

### Post by ChristopherJO on 2012-08-31
Follow Up:

I have come up with a solution.  It appears that a TUN will only route to user space and other TUN/TAPs.

I have now re-coded my program to read in on my TUN, but for the read out I complete a sendto() to a RAW socket (IPPROTO_RAW with IPHDR_INCL), which just drops my packet into the stack and lets it sort it out!

This has allowed me to achieve what I want, and now my packets are being routed out of the machine correctly.

Regards,

Chris.

Edit: I am not sure how to set this to 'SOLVED', could a Mod do the honours - Thank you.

---

