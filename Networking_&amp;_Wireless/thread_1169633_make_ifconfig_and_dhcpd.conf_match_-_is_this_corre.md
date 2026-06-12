---
title: "make ifconfig and dhcpd.conf match - is this correct?"
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by peterpanandthenws on 2009-05-25
I've been trying to boot from pxe, but get stuck all the time.

I suspect its because my eth0 is somehow set up wrong. Any tips, thoughts or help will be appreciated.


This is what I've got so far.
```
$ sudo ifconfig eth0 10.0.0.1 netmask 255.255.255.0 broadcast 10.0.0.255

$ sudo ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:1c:25:76:9f:a7  
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fe000000-fe020000 

# dhcpd.conf

ddns-update-style none;

option domain-name "instantretard.eu";
option domain-name-servers 193.162.153.164;
option subnet-mask 255.255.255.0;
option broadcast-address 10.0.0.255;

default-lease-time 604800;
max-lease-time 604800;
authoritative;

subnet 10.0.0.0 netmask 255.255.255.0
{
range 10.0.0.100 10.0.0.254;
filename "pxelinux.0";
option broadcast-address 10.0.0.255;
option routers 10.0.0.1;
}
```Thanks in advance

---

### Post by puppywhacker on 2009-05-25
what you are showing is the server right? what is the client showing, is it "looking for ip-address" or something similar?

your dhcpd.conf doesn't look wrong on first sight, your interface has 0 bytes sent and received, make sure the dhcp server is started after your interface has an address, otherwise it doesn't know where to start handing out addresses.

```
sudo /etc/init.d/dhcp3-server restart
 * Stopping DHCP server dhcpd3                                           [ OK ] 
 * Starting DHCP server dhcpd3                                           [ OK 
```

especially the last one should show an OK. otherwise look at the log to see what dhcp is complaining about
```
tail -50 /var/log/messages
```

after that make sure you have a TFTP server setup and ready to serve the pxelinux.0 file

---

