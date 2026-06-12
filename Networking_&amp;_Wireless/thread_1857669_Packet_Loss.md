---
title: "Packet Loss"
date: 2011-10-10
forum: Networking &amp; Wireless
---

### Post by borgward on 2011-10-10
I am getting a lot of packet loss w/wireless on Dell Inspiron 1520 Ubuntu 10.04 Linksys BEFW1154. 
wireless B router

The laptop is about 30 inches from the router.

I am not getting packet loss with Ethernet.

Could the wireless router be getting "tired"?

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=150 time=4.15 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=150 time=4.25 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=150 time=2.51 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=150 time=4.17 ms

--- 192.168.1.1 ping statistics ---
5 packets transmitted, 4 received, 20% packet loss, time 4005ms
rtt min/avg/max/mdev = 2.511/3.772/4.251/0.730 ms

I set ping to run 500 times. I got several results that took a lot of time:

64 bytes from 192.168.1.1: icmp_seq=64 ttl=150 time=126 ms

4 bytes from 192.168.1.1: icmp_seq=184 ttl=150 time=126 ms

$ sudo lshw -C network
               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:3a:b1:f0:eb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.100 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:fe8fc000-fe8fffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:d7:0c:79
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.102 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:17 memory:fe5fe000-fe5fffff

 rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by praseodym on 2011-10-10
Hi,

check the mtu-value of your ISP and add it as a number instead of "automatic" in the NM applet.

---

### Post by borgward on 2011-10-10
Hi

First, problem solved, at least on the laptop end.

Just connected to a different wireless router while at my neighbors house. No Packet loss.

ping -c5 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=127 time=2.64 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=127 time=2.63 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=127 time=2.66 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=127 time=2.81 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=127 time=2.64 ms

--- 192.168.0.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4007ms
rtt min/avg/max/mdev = 2.637/2.680/2.816/0.082 ms


Looks like my wireless router is at fault. What to do?

I am on dialup. The topography is as follows:

Laptop -> Linksys wireless router -> DLink router -> USR external MODEM -> phone line
                 /\
Desktop computer /\ (via cable) to Linksys router

Both routers are set for DHCP could that slow things down? They have been set that way for years. I have only recently began to have problem downloading.

That said, what is mtu value. how do I check it? What is NM applet?

---

### Post by praseodym on 2011-10-11
Router firmware is up-to-date? The mtu value is explained here:

[http://en.wikipedia.org/wiki/Maximum_transmission_unit](http://en.wikipedia.org/wiki/Maximum_transmission_unit)

If it is wrong it will cause package loss. NM applet is the network-manager. Which mode does the router send? (b+g or b+g+n or ...)

---

### Post by borgward on 2011-10-11
I just replaced the wireless router and broadband modem. No packet loss.

I used a Linksys Wireless-G  Model WRT54G Ver 2.2 (I think It is one that can be loaded w/Linux). It had been sitting around for a long time. I found another DLink Dl 705 broadband MODEM, just like the one I had for $4.99. Also picked up another USR external Faxmodem  for a spare $3. Not a bad day.

The DLink broadband modem was working, but gave up the ghost last night. Has done it before, but would operate again if left unplugged overnight, and reset. Wonder whats with that? Never seemed hot. Will keep it for a while to see if it works again.

Tom

---

### Post by borgward on 2011-10-11
I just replaced the wireless router and broadband modem. No packet loss.

I used a Linksys Wireless-G  Model WRT54G Ver 2.2 (I think It is one that can be loaded w/Linux). It had been sitting around for a long time. I found another DLink Dl 704 broadband MODEM, just like the one I had for $4.99. Also picked up another USR external Faxmodem  for a spare $3. Not a bad day.

The DLink broadband modem was working, but gave up the ghost last night. Has done it before, but would operate again if left unplugged overnight, and reset. Wonder whats with that? Never seemed hot. Will keep it for a while to see if it works again.

---

