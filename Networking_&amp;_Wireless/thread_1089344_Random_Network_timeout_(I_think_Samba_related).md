---
title: "Random Network timeout (I think Samba related)"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by thelamer on 2009-03-07
Hello, 

I am experiencing a random timeout from my new raid 5 fileserver running Intrepid 8.10.

The timeout only seems to occur when steaming movies from the server over a Samba share. The timeout occurs every 20-30 minutes for about 20 seconds and locks up movie playback and all other network connections to the machine. I am not able to remote desktop  in or ping the machine during this 20 second window. (edit: connected the machine to a monitor and found out it is losing networking alltogether during this period)

But after this time period the server runs completely normal. 

At first I thought it was an issue with smbfs mount so I tried cfis with the same results. And the error occurs when connecting to it with windows clients. So I have ruled out client issues and think it is something wrong with the Samba server on the server. 

Has anyone experienced these timeouts and is their a solution for it? 

A media fileserver is pretty useless if it cannot stream media. 

Any tips are appreciated :)

Here is a ping log from the timeout occuring while I am streaming a movie; 

```
64 bytes from 192.168.1.132: icmp_seq=65 ttl=64 time=0.289 ms
64 bytes from 192.168.1.132: icmp_seq=66 ttl=64 time=0.305 ms
64 bytes from 192.168.1.132: icmp_seq=67 ttl=64 time=0.305 ms
64 bytes from 192.168.1.132: icmp_seq=68 ttl=64 time=0.171 ms
64 bytes from 192.168.1.132: icmp_seq=69 ttl=64 time=36487 ms
64 bytes from 192.168.1.132: icmp_seq=70 ttl=64 time=35486 ms
64 bytes from 192.168.1.132: icmp_seq=71 ttl=64 time=34465 ms
64 bytes from 192.168.1.132: icmp_seq=72 ttl=64 time=33440 ms
64 bytes from 192.168.1.132: icmp_seq=73 ttl=64 time=32439 ms
64 bytes from 192.168.1.132: icmp_seq=74 ttl=64 time=31437 ms
64 bytes from 192.168.1.132: icmp_seq=75 ttl=64 time=30429 ms
64 bytes from 192.168.1.132: icmp_seq=76 ttl=64 time=29429 ms
64 bytes from 192.168.1.132: icmp_seq=77 ttl=64 time=28426 ms
64 bytes from 192.168.1.132: icmp_seq=78 ttl=64 time=27426 ms
64 bytes from 192.168.1.132: icmp_seq=79 ttl=64 time=26405 ms
64 bytes from 192.168.1.132: icmp_seq=80 ttl=64 time=25387 ms
64 bytes from 192.168.1.132: icmp_seq=81 ttl=64 time=24386 ms
64 bytes from 192.168.1.132: icmp_seq=82 ttl=64 time=23386 ms
64 bytes from 192.168.1.132: icmp_seq=84 ttl=64 time=21366 ms
64 bytes from 192.168.1.132: icmp_seq=86 ttl=64 time=19349 ms
64 bytes from 192.168.1.132: icmp_seq=87 ttl=64 time=18349 ms
64 bytes from 192.168.1.132: icmp_seq=89 ttl=64 time=16349 ms
64 bytes from 192.168.1.132: icmp_seq=94 ttl=64 time=11328 ms
64 bytes from 192.168.1.132: icmp_seq=98 ttl=64 time=7289 ms
64 bytes from 192.168.1.132: icmp_seq=100 ttl=64 time=5279 ms
64 bytes from 192.168.1.132: icmp_seq=102 ttl=64 time=3275 ms
64 bytes from 192.168.1.132: icmp_seq=106 ttl=64 time=2.46 ms
64 bytes from 192.168.1.132: icmp_seq=107 ttl=64 time=2.45 ms
64 bytes from 192.168.1.132: icmp_seq=108 ttl=64 time=0.152 ms
64 bytes from 192.168.1.132: icmp_seq=109 ttl=64 time=3.32 ms
64 bytes from 192.168.1.132: icmp_seq=110 ttl=64 time=5.24 ms
64 bytes from 192.168.1.132: icmp_seq=111 ttl=64 time=3.67 ms
64 bytes from 192.168.1.132: icmp_seq=112 ttl=64 time=3.88 ms
64 bytes from 192.168.1.132: icmp_seq=113 ttl=64 time=2.92 ms
64 bytes from 192.168.1.132: icmp_seq=114 ttl=64 time=0.146 ms
64 bytes from 192.168.1.132: icmp_seq=115 ttl=64 time=0.167 ms
64 bytes from 192.168.1.132: icmp_seq=116 ttl=64 time=0.132 ms
64 bytes from 192.168.1.132: icmp_seq=117 ttl=64 time=0.125 ms
64 bytes from 192.168.1.132: icmp_seq=118 ttl=64 time=0.414 ms
64 bytes from 192.168.1.132: icmp_seq=119 ttl=64 time=0.150 ms
64 bytes from 192.168.1.132: icmp_seq=120 ttl=64 time=0.314 ms
64 bytes from 192.168.1.132: icmp_seq=121 ttl=64 time=0.312 ms
64 bytes from 192.168.1.132: icmp_seq=122 ttl=64 time=0.128 ms
64 bytes from 192.168.1.132: icmp_seq=123 ttl=64 time=0.123 ms

```

---

### Post by thelamer on 2009-03-08
Please can anyone point me in the right direction?

---

### Post by thelamer on 2009-03-10
Ok it turns out Ubuntu wasn't playing nice with my; 

"ASUSTek Computer RT8111/8168B PCI Express Gigabit Ethernet Controller"

I thought it might be the actual hardware, but sadly it is not. SMB streaming from this NIC under windows works just fine and doesn't lock the computer up. 

Threw another NIC in there and everything is working great. 

Should I file a bug report for this? 

On the surface the ASUSTek NIC seems to work fine especially if someone was just testing a driver, but if you start streaming from it or initiate a large file transfer for about 30 minutes it will time out and shut down all connections on the machine. In some cases it completely locked up my machine.

---

### Post by buck2825 on 2009-04-07
Very interesting, I have been having a similar issue streaming to my xbox, with XBMC over samba from my mdadm raid 1.  I will give this a look see as right now i'm using my onboard NIC, and i have a spare to slap in one of my PCI slots.  I was thinking it might me a raid "idle" issue, because I can stream from a hard disk on my machine that is not in a RAID just fine.

---

### Post by buck2825 on 2009-04-13
not the same issue.  thanks

---

