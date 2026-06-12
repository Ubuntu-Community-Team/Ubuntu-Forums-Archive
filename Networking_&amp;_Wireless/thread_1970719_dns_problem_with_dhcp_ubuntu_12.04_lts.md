---
title: "dns problem with dhcp ubuntu 12.04 lts"
date: 2012-05-01
forum: Networking &amp; Wireless
---

### Post by flox12 on 2012-05-01
i had had a problem with my dhcp but i manged to fix my problem now the network start but i have a problem with DNS my clients in the network don't get any dns from my dhcp.
my network works as follow my i connect to wireless device then i share it throw out my Ethernet cable.
my configuration:
/etc/dhcp/dhcpd.conf```
 
#/etc/dhcp3/dhcpd.conf option subnet-mask 255.255.255.0; default-lease-time 600; max-lease-time 7200;  subnet 192.168.27.0 netmask 255.255.255.0 {   range 192.168.27.10 192.168.27.20;   option broadcast-address 192.168.27.255;   option routers 192.168.27.1; }
``` 

in /etc/default/dhcp-server i added  

```
 INTERFACES="eth0" 
```

/etc/network/interfaces  

```
 
iface wlan0 inet dhcp wireless-essid default  iface eth0 inet static address 192.168.27.1 netmask 255.255.255.0 gateway 192.168.0.100 pre-up /sbin/iptables-restore /etc/network/iptables
```


in /etc/resolv.conf 
i have two nameservers for dns but my clients in the network don't get them and even if i give them static ones no INTERNET does work.

any help will b appreciated. :)

---

