---
title: "PXE remote boot isn't given an IP by dnsmasq"
date: 2011-03-18
forum: Networking &amp; Wireless
---

### Post by EricSR on 2011-03-18
I'm trying to boot an old server via PXE. The server starts up just fine, the monitor reads that it's looking for a DHCP server to give it an IP. 

The server is connected to my laptop via ethernet. A wireshark capture confirms that the server is indeed asking for a lease.

Running dnsmasq with the following:
```
dnsmasq  --enable-tftp=eth0 --tftp-root=/var/lib/tftpboot/ --dhcp-range=192.168.1.20,192.168.1.30,12h --dhcp-boot=pxelinux.0 -d  --interface=eth0 --dhcp-option=3,192.168.1.1 --dhcp-option=6,192.168.1.1  --dhcp-authoritative --log-queries 
```

Not sure how much of the above is necessary.
When dnsmasq is running and the server is attempting to get an ip, the output of dnsmasq is as follows:
```
dnsmasq: started, version 2.55 cachesize 150
dnsmasq: compile time options: IPv6 GNU-getopt DBus I18N DHCP TFTP
dnsmasq-dhcp: DHCP, IP range 192.168.1.20 -- 192.168.1.30, lease time 12h
dnsmasq-tftp: TFTP root is /var/lib/tftpboot/ 
dnsmasq: reading /etc/resolv.conf
dnsmasq: using nameserver 192.168.0.1#53
dnsmasq: read /etc/hosts - 10 addresses
dnsmasq-dhcp: DHCP packet received on eth0 which has no address
dnsmasq-dhcp: DHCP packet received on eth0 which has no address
dnsmasq-dhcp: DHCP packet received on eth0 which has no address
dnsmasq-dhcp: DHCP packet received on eth0 which has no address
dnsmasq-dhcp: DHCP packet received on eth0 which has no address
dnsmasq-dhcp: DHCP packet received on eth0 which has no address
dnsmasq-dhcp: DHCP packet received on eth0 which has no address
dnsmasq-dhcp: DHCP packet received on eth0 which has no address
dnsmasq-dhcp: DHCP packet received on eth0 which has no address
dnsmasq-dhcp: DHCP packet received on eth0 which has no address
dnsmasq-dhcp: DHCP packet received on eth0 which has no address
dnsmasq-dhcp: DHCP packet received on eth0 which has no address
 
```

Wireshark merely shows a bunch of ignored requests from the server 
```
Internet Protocol, Src: 0.0.0.0 (0.0.0.0), Dst: 255.255.255.255 (255.255.255.255)
User Datagram Protocol, Src Port: bootpc (68), Dst Port: bootps (67)
```

Any ideas what's going wrong? Everything seems like it's set up correctly, nestat says dnsmasq is listening
```
udp        0      0 0.0.0.0:53              0.0.0.0:*                           -               
udp        0      0 0.0.0.0:67              0.0.0.0:*                           -               
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -               
udp        0      0 0.0.0.0:69              0.0.0.0:*                           -               
u
```
but for the life of me I can't figure out what's going wrong.

---

### Post by BkkBonanza on 2011-03-18
Sounds like maybe a cabling problem. Check that first as a bad cable will set you running around in circles for days.

---

### Post by EricSR on 2011-03-18
Assuming cabling as in the ethernet connection between the two. It has worked just fine before, so I don't believe that's it. 
The laptop I'm using as a dnsmasq server hasn't any problems with networking before.
As for the old server? From what I can tell, there aren't any *obvious* problems with the network card and cabling inside.

---

