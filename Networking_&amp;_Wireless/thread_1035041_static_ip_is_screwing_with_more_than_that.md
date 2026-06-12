---
title: "static ip is screwing with more than that"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by hwttdz on 2009-01-09
Using a static ip address seems to really bog down my connection.  And I have no ideas why.  

Static ip ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:18:f3:b7:08:12  
          inet addr:192.168.1.136  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:feb7:812/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:666927 errors:0 dropped:0 overruns:0 frame:0
          TX packets:495628 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:417076836 (417.0 MB)  TX bytes:608357852 (608.3 MB)
          Interrupt:22 Base address:0x2000 
```

DHCP ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:18:f3:b7:08:12  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:feb7:812/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:669605 errors:0 dropped:0 overruns:0 frame:0
          TX packets:497876 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:417298596 (417.2 MB)  TX bytes:612843965 (612.8 MB)
          Interrupt:22 Base address:0x2000
```

ping switching connection type in the middle, note that the time jumps from about 80 ms to about 1580 ms.  

```
PING ubuntuforums.org (91.189.94.12) 56(84) bytes of data.
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=18 ttl=49 time=79.2 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=19 ttl=49 time=93.0 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=20 ttl=49 time=81.1 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=21 ttl=49 time=79.7 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=22 ttl=49 time=82.2 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=23 ttl=49 time=81.5 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=24 ttl=49 time=83.5 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=25 ttl=49 time=81.4 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=26 ttl=49 time=81.5 ms
ping: sendmsg: Network is unreachable
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=29 ttl=49 time=177 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=30 ttl=49 time=413 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=31 ttl=49 time=1106 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=32 ttl=49 time=1537 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=33 ttl=49 time=1580 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=34 ttl=49 time=1571 ms
```

I also experience an extreme perceived slowdown in page loading times.  i.e. forum homepage loads instantly to 15 seconds.  Can someone suggest a possible cause.  I need to have a static ip so that I can use port forwarding and access my machine remotely.

---

### Post by superprash2003 on 2009-01-09
possibly a DNS issue.. cause once you set static ip.. you need to manually enter dns addresses..

---

### Post by hwttdz on 2009-01-09
The dns lookup is clearly succeeding, as it's finding the ip address of the site.  Second I think the ip lookup only happens once, because it says pinging numericip rather than pinging hostname.  Finally I believe (hard to check as logging in is taking forever) I have specified dns servers on my router (linksys) so it assigns the same dns servers to dhcp leases as this static ip configuration gets.

---

### Post by hwttdz on 2009-01-09
I should also say that it was working fine up to yesterday.  Though I did just change dns servers a few days ago (namely because I found a faster free one than opendns).  I also tried the same static ip with the opendns dns servers and got the same result.  

There were a bunch of updates having to do with connectivity pushed over the last few days, might have been one of those?

Does the connection have to deal with port forwarding on the way out?  I should try resetting my router and cable box this evening.

Update: magically resolved (no action on my part), not marking as solved because I never found a solution (or the cause of the problem)

---

