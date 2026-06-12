---
title: "Setting up network between two laptops"
date: 2010-04-28
forum: Networking &amp; Wireless
---

### Post by kent a on 2010-04-28
Hello ..

I have two laptops with Ubuntu 9.10

I want to connect them with a wireless router. phillips snb5600 router.

So I can go online and share files with both laptops

My LG E500 laptop to function as a modem with a connection to the internet with a 3g usb modem.

There are built-in wireless LG E500.

My other laptop is an old webtech without wireless built in, but I have a wireless USB thing fully with snb5600 Router.
Ubuntu can find the wireless USB thing. so it's not a problem.

Both laptops can also connect with the router with cable.

This is written with google translation because I'm from Denmark ..

---

### Post by Iowan on 2010-04-28
The double-connection(s) might be a problem if wired and wireless connections have addresses in the same subnet.

---

### Post by lindsay7 on 2010-04-28
This may help you.

[http://my.opera.com/ubuntunerd1/blog/share-files-between-two-ubuntu-computers-via-ssh](http://my.opera.com/ubuntunerd1/blog/share-files-between-two-ubuntu-computers-via-ssh)

---

### Post by jukzh on 2010-06-27
What about without router? Just two laptops with wifi cards.
I managed to connect them via usb0, and share ethernet wan connection of one with another. Why not wireless?
Well, another wasn't actually a laptop, tablet to be precise n900, links followed:
[http://wiki.maemo.org/N900_USB_networking](http://wiki.maemo.org/N900_USB_networking), i got them ping each other.
And here, i got internet on tablet:
[https://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing)
If to set up a wifi in same way, would be so cool!

---

### Post by jukzh on 2010-06-27
Just hooked up them via wifi, they are pinging each other!
Remains to enable wan in client, server iptable rules:
```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  gjjline.bta.net.cn   anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  gjjline.bta.net.cn   anywhere            
ACCEPT     tcp  --  dialdns.bta.net.cn   anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  dialdns.bta.net.cn   anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             localhost           
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
INBOUND    all  --  anywhere             localhost           
INBOUND    all  --  anywhere             localhost           
INBOUND    all  --  anywhere             localhost           
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN TCPMSS clamp to PMTU 
OUTBOUND   all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             localhost/24        state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             localhost/24        state RELATED,ESTABLISHED 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 
ACCEPT     all  --  localhost/24         anywhere            ctstate NEW 
ACCEPT     all  --  anywhere             anywhere            ctstate RELATED,ESTABLISHED 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  localhost            gjjline.bta.net.cn  tcp dpt:domain 
ACCEPT     udp  --  localhost            gjjline.bta.net.cn  udp dpt:domain 
ACCEPT     tcp  --  localhost            dialdns.bta.net.cn  tcp dpt:domain 
ACCEPT     udp  --  localhost            dialdns.bta.net.cn  udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (4 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (3 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere 
```

And in resolv.conf of client I added google's DNS 8.8.8.8
Help me, anyone!

---

### Post by jukzh on 2010-06-30
Easy Wireless Ad-hoc:
[http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html](http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html)
Why routers when Ubuntu, at home?

---

