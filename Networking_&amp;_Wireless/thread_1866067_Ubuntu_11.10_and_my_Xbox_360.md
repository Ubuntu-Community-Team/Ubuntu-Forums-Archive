---
title: "Ubuntu 11.10 and my Xbox 360"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by 484 on 2011-10-20
I just upgraded to Ubuntu 11.10 (don't know the name) and I can no longer access XboxLive.

My Xbox is connected like this

******  ************  *************  **********
|xbox|--|ubuntu box|--|home router|--|internet|
******  ************  *************  **********
The Ubuntu box is a dhcp server for the Xbox

According to the Xbox's network test tool the DNS are failing to resolve the Xbox live servers, but the same name servers work fine when I connect directly to our home router.

---

### Post by 484 on 2011-10-21
Here is a shameless self bump and some more info. My Xbox is connected to eth1.

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:19:66:cd:ff:c7  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:66ff:fecd:ffc7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:502243 errors:0 dropped:0 overruns:0 frame:0
          TX packets:340976 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:685631915 (685.6 MB)  TX bytes:35986743 (35.9 MB)
          Interrupt:47 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:e0:52:9a:32:e8  
          inet addr:10.42.43.1  Bcast:0.0.0.0  Mask:255.255.255.0
          inet6 addr: fe80::2e0:52ff:fe9a:32e8/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:799 errors:0 dropped:1 overruns:0 frame:0
          TX packets:723 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:167967 (167.9 KB)  TX bytes:272934 (272.9 KB)
          Interrupt:19 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1236 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1236 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70850 (70.8 KB)  TX bytes:70850 (70.8 KB)

/etc/resolv.conf
nameserver 24.196.64.53
nameserver 68.113.206.10
nameserver 24.178.162.3

/etc/dhcp/dhcpd.conf
authoritative;

ddns-update-style interim;
DHCPDARGS=eth1;
default-lease-time 600;
max-lease-time 7200;

subnet 10.42.43.0 netmask 255.255.255.0
{
 range 10.42.43.2 10.42.43.10;
 ignore client-updates;
 option routers 10.42.43.1;
 option broadcast-address 10.42.53.255;
 option subnet-mask 255.255.255.0;
 option domain-name-servers 24.196.64.53,68.113.206.10;
 #8.8.8.8,8.8.4.4; 24.196.64.53,68.113.206.10,68.113.206.10;
 option ip-forwarding on;
}

host debian
{
 hardware ethernet 00:0E:A6:53:CB:C7;
 fixed-address 10.42.43.3;
}
host xbox
{
 hardware ethernet 00:1D:D8:87:90:F7;
 fixed-address 10.42.43.2;
}

/etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 10.42.43.1
netmask 255.255.255.0

---

### Post by madjr on 2011-10-21
sorry i dont know how to fix it, but might be worth reporting in the meantime, till someone more knowledgeable can look into this

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by Pazzaisere on 2012-01-18
To get Xbox live up in Ubuntu 11.10 do exactly this!!!!

In eth0 under IPv6 change "method" to IGNORE!!!!! then take the tick from the box that says requires IPv6 for this connection to complete, this should stop the connection connecting then dropping again and again!

change the IPv4 to "shared to another computer"

Turn Xbox on at this point!!!!!

then in the terminal screen run

$ sudo killall dnsmasq

then do connection check on xbox and you should be up and running :P

hope this helps you all

Pazza

---

### Post by deadlittlepuppy on 2012-01-22
> **Pazzaisere said:**
> To get Xbox live up in Ubuntu 11.10 do exactly this!!!!

In eth0 under IPv6 change "method" to IGNORE!!!!! then take the tick from the box that says requires IPv6 for this connection to complete, this should stop the connection connecting then dropping again and again!

change the IPv4 to "shared to another computer"

Turn Xbox on at this point!!!!!

then in the terminal screen run

$ sudo killall dnsmasq

then do connection check on xbox and you should be up and running :P

hope this helps you all

Pazza

You are my hero!
I've been searching and trying for hours, and it was just that easy.

---

