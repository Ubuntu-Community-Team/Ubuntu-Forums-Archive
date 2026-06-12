---
title: "Finding the IP of a network device"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by WitchCraft on 2009-05-24
OK, everybody knows this: you get a new network device with a hugh manual for computer-illiterates, which you don't want to read through, but you need the default IP.

So how do you do this in Linux? 

It's easy. First, install nmap:
```

apt-get install nmap

```

Then, scan the probable IP range.
Usually, internal default IP's are in the range 192.168.0.<something> or 192.168.1.<something>

To query 192.168.0.* and 192.168.1.* with nmap:
```

nmap -sP 192.168.0.*
nmap -sP 192.168.1.*

```


> 
nmap -sP 192.168.0.*

Starting Nmap 4.68 ( [http://nmap.org](http://nmap.org) ) at 2009-05-24 12:17 CEST
Nmap done: 256 IP addresses (0 hosts up) scanned in 104.167 seconds


nmap -sP 192.168.1.*

Starting Nmap 4.68 ( [http://nmap.org](http://nmap.org) ) at 2009-05-24 12:23 CEST
Host 192.168.1.1 appears to be up.
MAC Address: 00:25:F3:A8:70:AE (Netgear)
Host 192.168.1.2 appears to be up.
MAC Address: 00:EF:0A:C8:85:5E (Giga-Byte Technology Co.)
Host 192.168.1.4 appears to be up.
Host 192.168.1.5 appears to be up.
MAC Address: 9B:10:A4:EA:6D:E0 (Askey  Computer )
Nmap done: 256 IP addresses (4 hosts up) scanned in 4.902 seconds


---

