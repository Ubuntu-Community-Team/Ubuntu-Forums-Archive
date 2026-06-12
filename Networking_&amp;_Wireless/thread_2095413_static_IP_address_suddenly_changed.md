---
title: "static IP address suddenly changed"
date: 2012-12-16
forum: Networking &amp; Wireless
---

### Post by petru.marginean on 2012-12-16
Hi,

I was  using static IP address, and it worked fine for weeks.
I noticed today the IP address has changed, not sure why.
(192.168.1.2 => 192.168.1.3)

How can I find out why this happened?
I probably can restart the networking, but I need to fix it so this doesn't happen again.

Below are the interfaces file, and the IP address.

Many thanks,
PM

```
$> cat /etc/network/interfaces
auto eth0

#iface eth0 inet dhcp
iface eth0 inet static
address 192.168.1.2

netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

auto lo
iface lo inet loopback

$> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:9b:01:30:0a  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:9bff:fe01:300a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69302478 errors:4 dropped:14 overruns:0 frame:2
          TX packets:37908696 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:100378086503 (100.3 GB)  TX bytes:3202809897 (3.2 GB)
          Interrupt:20 Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:126765 errors:0 dropped:0 overruns:0 frame:0
          TX packets:126765 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:329481384 (329.4 MB)  TX bytes:329481384 (329.4 MB)


```

---

### Post by ahallubuntu on 2012-12-16
Are you also using network manager?  If so, your interfaces file may be ignored.  Better to set the static IP in the GUI.  ("Network Connections" I believe.)

Better yet - if you have access to your router, make a DHCP reservation there so your IP never changes and set your computer back to DHCP/automatic.  That makes managing your network easier: you can do it all in your router and not worry about the IP addresses of individually-connected computers.

---

