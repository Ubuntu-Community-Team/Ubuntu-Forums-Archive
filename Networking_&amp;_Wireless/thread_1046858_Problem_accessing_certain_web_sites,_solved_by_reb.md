---
title: "Problem accessing certain web sites, solved by reboot"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by elecnix on 2009-01-21
I have a weird problem accessing certain web sites. They are usually always the same. For example, google.com, google.ca, gmail.com, google-analytics.com, and my bank's web site bnc.ca. Firefox finds the site, but says "connecting" until it times out.

He're what happens according to strace:

```

nicolas@cortex:~$ strace -f wget http://www.google.com
[...]
write(2, "Connexion vers www.google.com|66"..., 51Connexion vers www.google.com|66.249.91.104|:80... ) = 51
socket(PF_INET, SOCK_STREAM, IPPROTO_IP) = 3
connect(3, {sa_family=AF_INET, sin_port=htons(80), sin_addr=inet_addr("66.249.91.104")}, 16^C <unfinished ...>
```

tcpdump -i eth2 shows the name resolution, then nothing.

At the same time, Pidgin connects to my gmail.com account with no problems. Maybe the problem is only for the web? HTTPS shows the same behavior:

```

write(2, "Connexion vers www.google.com|66"..., 52Connexion vers www.google.com|66.249.91.147|:443... ) = 52
socket(PF_INET, SOCK_STREAM, IPPROTO_IP) = 3
connect(3, {sa_family=AF_INET, sin_port=htons(443), sin_addr=inet_addr("66.249.91.147")}, 16
```

I have tried renewing my DHCP lease (ifdown eth2, ifup eth2) with no results. I have tried rebooting my TP-Link WR340G v5 08118989 router and upgrading its firmware to 3.8.2 Build 080628 Rel.36171n with no more results.

The only thing that works is rebooting my Ubuntu desktop. It will work for few days, then hang again. I've even seen it unblock by itself after few hours.

There's an other Ubuntu PC (a laptop) on the same network and it never had this problem.

This is driving me nuts. At least I can access ubuntuforums.org!

Interface info:

```

nicolas@cortex:~$ ifconfig eth2
eth2      Link encap:Ethernet  HWaddr 00:11:2f:49:f4:25  
          inet adr:192.168.3.50  Bcast:255.255.255.255  Masque:255.255.255.0
          adr inet6: fe80::211:2fff:fe49:f425/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:1382 erreurs:0 :0 overruns:0 frame:0
          TX packets:1416 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:281119 (281.1 KB) Octets transmis:296677 (296.6 KB)
          Interruption:17 
```

Routing table:

```

$ route -n
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
192.168.3.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth2
0.0.0.0         192.168.3.1     0.0.0.0         UG    100    0        0 eth2
```

This all started around the time I switched ISPs. One thing I did to my Ubuntu desktop was connect directly to my modem and dialing PPPoE. Maybe that screwed some config? What else could I check?

```

$ ps aux|grep ppp
nicolas  17497  0.0  0.0   3244   812 pts/1    S+   20:37   0:00 grep ppp
```

Update: Note that I get a response from a ping.

---

### Post by freegnu on 2009-01-21
Take a look at your /etc/resolv.conf when you are having these problems.  Also try pinging yahoo.com my ISP, Verizon, has DNS hiccups that confound me sometimes.  Also I had to seriously restrict the number of simultaneous connections per a torrent download and the number of torrent uploads and downloads to keep my DD-WRT Linksys from rebooting several times a day and making the Internet seem sluggish and unresponsive.  Check the uptime on your router.  If it's less than a week it may be the router.  Even if your router has been up and running fine for months you may find that rebooting your router once a week saves you from a lot of headaches.

---

### Post by damis648 on 2009-01-21
When does this happen? After resuming from suspend?

---

### Post by elecnix on 2009-01-22
> **freegnu said:**
> Take a look at your /etc/resolv.conf when you are having these problems.  Also try pinging yahoo.com my ISP, Verizon, has DNS hiccups that confound me sometimes.


It's not a DNS issue. According to strace, the DNS lookup was made.

> **freegnu said:**
> Also I had to seriously restrict the number of simultaneous connections per a torrent download and the number of torrent uploads and downloads to keep my DD-WRT Linksys from rebooting several times a day and making the Internet seem sluggish and unresponsive.  Check the uptime on your router.  If it's less than a week it may be the router.  Even if your router has been up and running fine for months you may find that rebooting your router once a week saves you from a lot of headaches.

The router is fine. According to tcpdump, packets are not even going out of my PC after the name resolution.

---

### Post by elecnix on 2009-01-22
> **damis648 said:**
> When does this happen? After resuming from suspend?

That PC never suspends.

---

### Post by freegnu on 2009-01-23
Check for the device with ifconfig -a when you are having the problem.  It may be a hotplug issue.  The device may be disappearing and reappearing periodically.  I had this problem with my wifi network device interface.  I had to go into /etc/network/interfaces and make sure the wifi interface was not considered a hotplug interface.  This required that I also set up the whole roaming configuration thing.  I eventually got to the root of the problem by changing the beacon interval on my access point to 101 to avoid being dropped from the access point after too many missed beacons because of all the overlapping wifi networks, wireless phones, and cell phones in use in my neighborhood.

---

### Post by freegnu on 2009-01-23
If you are having a problem with a wired connection then the problem can be hotplug but the underlying problem is probably either a bad ethernet cable or port.  Hotplug is just doing it's job correctly when it detects that the network connection has gone away.  But hotplug isn't great at always bringing the network back up when there is an underlying network connectivity problem.

If all else fails try sudo ifdown ethx.  Then watch to output after the command completes to see if the network interface ethx comes back up on it's own.  If not follow up with a sudo ifup ethx

---

