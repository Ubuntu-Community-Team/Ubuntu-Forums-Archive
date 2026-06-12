---
title: "Ethernet recognized but not connecting."
date: 2012-11-11
forum: Networking &amp; Wireless
---

### Post by smithy545 on 2012-11-11
I set up ubuntu 12.04 server edition on an old computer and the ethernet is not connecting. It is recognized by ifconfig as eth0, and I think it worked during installation.

The driver is supported(SiS 900) and was recognized by lspci so the computer knows that it's there. When I run dhclient it hangs for a while and then passes through with no errors but anytime I ping anything I get "Destination Host Unreachable" whether it's a an ip address or a domain name.

I've installed the drivers for a wifi adapter and it's connected to the internet on my home router with no issues so the computer can connect to the internet and so can the router just not the ethernet.

Any advice would be helpful (I've turned it on and off multiple times and even reinstalled ubuntu).

---

### Post by gerowen on 2012-11-12
Do you have IP address left available in your DHCP pool?  Have you tried assigning a static IP and seeing if it works that way?

---

### Post by smithy545 on 2012-11-12
I'm pretty sure I've got dhcp addresses left as my router dhcp pool goes from 192.168.15.2 - 192.168.15.254 if that's what you mean. As for static ip I've already tried that with no luck.

---

### Post by chuck_theobald on 2012-11-12
If "ifconfig eth0" shows that an address has been assigned, try running the "route" command to see if your routing is correctly set up. It would be helpful if you posted the results of both these commands.

---

### Post by smithy545 on 2012-11-12
Ok route returns:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.15.1    0.0.0.0         UG    100    0        0 eth0
localnet        *               255.255.255.0   U     0      0        0 eth0
```

And ifconfig returns:
```
eth0      Link encap:Ethernet  HWaddr 00:0a:e6:28:47:5a  
          inet addr:192.168.15.205  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e6ff:fe28:475a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:1 dropped:1 overruns:0 frame:1
          TX packets:34 errors:0 dropped:4 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2056 (2.0 KB)  TX bytes:2120 (2.1 KB)
          Interrupt:11 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:115 errors:0 dropped:0 overruns:0 frame:0
          TX packets:115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11256 (11.2 KB)  TX bytes:11256 (11.2 KB)
```

---

### Post by chuck_theobald on 2012-11-12
Your routing table looks right, routing out of your box through 0.0.0.0, and elsewhere through your router, 192.168.15.1.
What happens if you try "ping 192.168.15.1"?
I am suspecting possible problems with your cable or NIC. Not sure what could cause an error on RX, but could be indicative of hardware failure.

---

### Post by chuck_theobald on 2012-11-12
And, since you have an IP address and netmask, it appears that dhcp is working.

---

### Post by smithy545 on 2012-11-12
This is what happens when I ping 192.168.15.1(I changed my static ip from 192.168.15.55 to 192.168.15.205 but this was before that):
```

PING 192.168.15.1 (192.168.15.1) 56(84) bytes of data.
From 192.168.15.55 icmp_seq=1 Destination Host Unreachable
From 192.168.15.55 icmp_seq=2 Destination Host Unreachable
From 192.168.15.55 icmp_seq=3 Destination Host Unreachable
From 192.168.15.55 icmp_seq=4 Destination Host Unreachable
From 192.168.15.55 icmp_seq=5 Destination Host Unreachable
 
--- 192.168.15.1 ping statistics ---
 
5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 4024ms
pipe 3
```

---

### Post by smithy545 on 2012-11-12
I'm just going to buy an ethernet card. Thanks for the help though guys.

---

