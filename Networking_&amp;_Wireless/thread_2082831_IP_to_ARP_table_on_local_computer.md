---
title: "IP to ARP table on local computer ?"
date: 2012-11-10
forum: Networking &amp; Wireless
---

### Post by zozza on 2012-11-10
I'm not sure exactly how to ask this question but here goes.

What I am looking for is a file which records the IP - ARP address.

For example, I connect to my router.  It assigns me 192.168.1.33 and knows my ARP.  Where is this information stored?

Thanks.

---

### Post by Doug S on 2012-11-10
Do you mean /proc/net/arp ? See also "man arp".

---

### Post by zozza on 2012-11-11
/proc/net/arp is shows my routers IP and ARP.

I want a file that shows my IP and ARP.  In other words the file (if it exists) which shows the router the relationship between my IP and my ARP.

Thanks.

---

### Post by Doug S on 2012-11-11
I only know of "ifconfig" to show your MAC (Media Access Control) hardware address and your IP address.
ARP means Address Resolution Protocol.

---

### Post by bab1 on 2012-11-11
> **zozza said:**
> /proc/net/arp is shows my routers IP and ARP.

I want a file that shows my IP and ARP.  In other words the file (if it exists) which shows the router the relationship between my IP and my ARP.

Thanks.

The kernel itself keeps the ARP cache.  The /proc/net/arp file is the useland access to the current cache.  The ARP cache is always changing so there is no fixed file as such.

What to you mean by "my ARP"?  ARP is a process to resolve the IP address to the MAC address.  All non-routed (local link) communication is utimatly completed via MAC address.

To activate all devices that respond to ICMP pings attatched to the local segment of a LAN you can use ping broadcasts.  If I ping the broadcast address of my LAN like this ```
ping -b 192.168.1.255
```
I get all my active devices to respond like this```
 ping -b 192.168.1.255
WARNING: pinging broadcast address
PING 192.168.1.255 (192.168.1.255) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=2.33 ms
64 bytes from 192.168.1.245: icmp_req=1 ttl=64 time=113 ms (DUP!)
64 bytes from 192.168.1.200: icmp_req=1 ttl=64 time=114 ms (DUP!)

```
Then I can check the MAC addresses with this```
arp -a
bb-gw1 (192.168.1.1) at 00:0f:db:xx:xx:xx [ether] on wlan0
bb-ap1 (192.168.1.245) at 00:14:bf:xx:xx:xx [ether] on wlan0
bb-hp1 (192.168.1.200) at 00:01:e6:6b:xx:xx:xx [ether] on wlan0
```
After some time the cache will be updated keeping only active devices.  I end up with only my gateway (router) active ```
arp -a
bb-gw1 (192.168.1.1) at 00:0f:db:xx:xx:xx [ether] on wlan0
```

What are you trying to achieve?  Maybe it is already available in another format.

---

