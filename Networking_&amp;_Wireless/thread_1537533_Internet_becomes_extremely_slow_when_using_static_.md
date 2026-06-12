---
title: "Internet becomes extremely slow when using static ip!"
date: 2010-07-23
forum: Networking &amp; Wireless
---

### Post by Anxious Nut on 2010-07-23
Hello there, I am currently facing a weird problem, It's that the internet connection becomes extremely slow when using static IP instead of DHCP when Im connected through a cable! The local network seems okay with both, but differs when using the internet!

I've ran a ping test and got the following results!

**using static IP**
```

$ ping -c 3 google.com
PING google.com (209.85.153.104) 56(84) bytes of data.
64 bytes from 209.85.153.104: icmp_seq=1 ttl=42 time=343 ms

--- google.com ping statistics ---
3 packets transmitted, 1 received, 66% packet loss, time 16351ms

```

**using DHCP**
```

ping -c 3 google.com
PING google.com (209.85.153.104) 56(84) bytes of data.
64 bytes from bom01s01-in-f104.1e100.net (209.85.153.104): icmp_seq=1 ttl=42 time=307 ms
64 bytes from bom01s01-in-f104.1e100.net (209.85.153.104): icmp_seq=2 ttl=43 time=324 ms
64 bytes from bom01s01-in-f104.1e100.net (209.85.153.104): icmp_seq=3 ttl=42 time=334 ms

--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms

```

**Summery**
When I used static IP i received only one packet while when using DHCP i received all three!! Also I lost 66% of the packets when using the Static IP connection!! And most importantly, the speed, DHCP connection was 8 times faster than Static IP connection!!!

I dont think this is normal, so i wish for your help! Thanks in advance!

AnxiousNut

---

### Post by Anxious Nut on 2010-07-23
Okay after doing some researches and checks, i found that i've mistaken in the DNS servers field! Thats one bad mistake! Anyways, the ping test is now

```
$ ping -c 3 google.com
PING google.com (209.85.153.104) 56(84) bytes of data.
64 bytes from bom01s01-in-f104.1e100.net (209.85.153.104): icmp_seq=1 ttl=42 time=301 ms
64 bytes from bom01s01-in-f104.1e100.net (209.85.153.104): icmp_seq=2 ttl=43 time=309 ms
64 bytes from bom01s01-in-f104.1e100.net (209.85.153.104): icmp_seq=3 ttl=42 time=294 ms

--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2033ms
rtt min/avg/max/mdev = 294.164/302.022/309.942/6.441 ms
```

as fast as the DHCP!! Im glad! though i should be ashamed of such a mistake!

---

### Post by Iowan on 2010-07-23
Everything else is the same (nameservers, routing, etc.)?


(edit) Sorry about that - apparently you "sneaked" a post in under me. ;) Had I seen it, I probably wouldn't have posted.

And you _even_ marked the thread [SOLVED] - THANK YOU!

---

### Post by Anxious Nut on 2010-07-23
yes, corrected only the DNS servers!

---

