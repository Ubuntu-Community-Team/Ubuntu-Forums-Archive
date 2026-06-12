---
title: "Need Urgent help regarding NICs' config (two-week old problem)"
date: 2006-06-18
forum: Networking &amp; Wireless
---

### Post by simn on 2006-06-18
Hi, i've been using ubuntu since breezy- Once i upgraded to dapper, I decided to run my own ftp/web server. 

Problem is, although I have the servers up and running, I cannot access them over the Internet. Often users who try to do that get a 'too many users on server' error msg for ftp or 'no route to host' msg.

If i run [ftp://localhost](ftp://localhost) or [http://localhost](http://localhost) the servers do fine- I figured that this has something to do with my NICs' configuration. Since I am using a usb-ADSL modem (aztech 208U) I have had to compile the drivers using the most recent sources from the developers' website. Once the modem is up and running, it creates another ethernet device eth1 (in addition to the onboard ethernet card - eth0).

Even after using pppoeconf to configure the network interfaces, my network script at boot time seems to fail. Can someone please verify for me whether the interface configuration is correct as shown here?

The problem, I've been told is of routing- I should make configure the network interfaces so that the eth0 card can directly access the eth1 (virtual?) device created by eagleusb modem on ppp0.


```
# /usr/share/doc/ifupdown/examples for more information.

auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.1
netmask 255.255.255.0
gateway 192.168.1.1

iface eth1 inet dhcp


auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider



auto eth0


```

Here's the output of ifconfig -a (in case it is needed)

```
eth0      Link encap:Ethernet  HWaddr 00:11:D8:5E:54:70
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201

eth1      Link encap:Ethernet  HWaddr 00:30:0A:56:DF:AF
          inet6 addr: fe80::230:aff:fe56:dfaf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41009 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36339 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:39727917 (37.8 MiB)  TX bytes:4136910 (3.9 MiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2063 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2063 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1700631 (1.6 MiB)  TX bytes:1700631 (1.6 MiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:202.1.194.162  P-t-P:202.1.194.229  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:4963 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5295 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:4618185 (4.4 MiB)  TX bytes:463309 (452.4 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

Many thanks in advance](*,)

---

### Post by erimar77 on 2006-06-18
> Problem is, although I have the servers up and running, I cannot access them over the Internet.

How are you trying to access them when you're using internal IP addresses.  Are you doing port forwarding through a router?

---

