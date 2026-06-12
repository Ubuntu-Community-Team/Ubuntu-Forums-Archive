---
title: "ubuntu server gateway configuration doesn't work"
date: 2010-07-13
forum: Networking &amp; Wireless
---

### Post by chaiwei on 2010-07-13
Hi,

My office internet infrastructure:

Internet->modem-> wireless router -> Wireless connection (A5)
                                                    Internet->modem-> wireless router -> Gateway (gate01) -> 192.168.2.2 (web server)
                                                                                   Internet->modem-> wireless router -> Gateway (gate01) -> wireless connection ( GA1 )

1 internet, 1 modem, 1 wireless router.
wireless router connect to 
a) A5
b) Gate01

Gate01 connect to 
a) 192.168.2.2 webserver
b) GA1
                              
when using "GA1", I only can access to certain website, many website can't access, if I switch it to "A5", I can access to mostly websites as usual. 
Is it because of the ubuntu gateway configuration DNS problems?

modem configuration page = 192.168.0.1
gate01 IP eth0 = 192.168.0.3 (dynamic DHCP IP) modem connect tk
gate01 IP eth1 = 192.168.2.1 (fixed IP) in /etc/network/interfaces

here is my interfaces file
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
iface lo inet loopback

# The primary network interface
auto eth0 eth1
iface eth0 inet dhcp  
    
iface eth1 inet static
    address 192.168.2.1
    netmask 255.255.255.0
    network 192.168.2.0
    broadcast 192.168.2.255
    post-up iptables-restore < /etc/iptables.up.rules

```Gate01 can ping to google, and access to other website where "GA1" can't access 
I use "GA1" also can connect/ping to google, but I try most website, it can't access,
example using GA1 connect/ping [www.pentrac.com]("http://www.pentrac.com"), it show me unable to "resolve target name", but using gate01 can connect/ping

Is it because of the eth1 firewall?

Another strange thing was if I set the modem configuration page to "192.168.2.150"
and modem DHCP range in 192.168.2.151 -> 192.168.2.254 , 

A5 still can access to internet but "GA1" can't access/ping to all websites.

Please advise.

---

