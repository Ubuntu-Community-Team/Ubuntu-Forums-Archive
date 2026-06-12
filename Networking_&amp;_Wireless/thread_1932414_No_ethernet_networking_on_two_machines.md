---
title: "No ethernet networking on two machines"
date: 2012-02-27
forum: Networking &amp; Wireless
---

### Post by richfaraone on 2012-02-27
Hi Everyone,

I recently acquired a dell PowerEdge 2650 server from a friend and decided to install Ubuntu 11.10 on it to use as a customer computer in my shop's waiting area. Everything went just fine on the install but there is no Ethernet connection to the Internet. I turned it off and plugged up an ativa USB wireless to connect and post here, that worked fine, but I have a weak signal and I would rather plug this into the Ethernet connection.

Here are my network connections:
```
[sudo] password for user: 
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5703X Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 02
       serial: 00:11:43:d7:43:f9
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 firmware=5703-v2.25a latency=64 link=no mingnt=64 multicast=yes port=twisted pair
       resources: irq:28 memory:fcf10000-fcf1ffff
  *-network:1
       description: Ethernet interface
       product: NetXtreme BCM5703X Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:03:08.0
       logical name: eth1
       version: 02
       serial: 00:11:43:d7:43:fa
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 duplex=half firmware=5703-v2.25a latency=64 link=yes mingnt=64 multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:29 memory:fcf00000-fcf0ffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlan0
       serial: 00:17:3f:6c:6b:e9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=zd1211rw driverversion=3.0.0-12-generic firmware=4725 ip=192.168.2.14 link=yes multicast=yes wireless=IEEE 802.11bg
user@user-PowerEdge-2650:~$ 

```

The Ethernet connection is plugged into eth1. Funny thing is, the IP shows up in the router and I was able to add the network printer, it saw and added the printer, but I can't communicate with it on a wired connection, nor can I access the Internet.

If it matters, we have a CenterCOM 18 port hub --> Belkin Router --> Scientific Atlanta modem, cable connection.

I also got out an old Gateway laptop and installed 11.10 on it as well. It has the same exact problem, cannot connect via Ethernet only. We have customers bring in their own laptops to the waiting area occasionally and they plug right up with no problems... I'm stumped! 

Any ideas would be greatly appreciated!

---

### Post by richfaraone on 2012-02-27
Stranger yet, take a look at the network info:

[IMG]http://i898.photobucket.com/albums/ac183/richfaraone/ubuntu/connections.jpg[/IMG]

I have the BIOS on this machine set to: 192.168.2.14, however, the machine is grabbing 192.168.0.102? If I change the IP to static at 2.14 it looses all connectivity, and the printer offline message pops up??

---

### Post by richfaraone on 2012-02-27
Anyone???

---

### Post by richfaraone on 2012-02-28
Anyone??

---

### Post by richfaraone on 2012-02-29
So... after 2 days, does anyone have any ideas??

---

### Post by dandnsmith on 2012-02-29
That one is a bit tricky.
What you need to do now is elaborate on what the wired and wireless ports are connecting to - is it a router (if so what sort)?
It could be something as simple as an oddball setup in a router, or might need some other info.

---

### Post by richfaraone on 2012-03-01
I did...
> **richfaraone said:**
> If it matters, we have a CenterCOM 18 port hub --> Belkin Router --> Scientific Atlanta modem, cable connection.

---

### Post by dandnsmith on 2012-03-01
I understand your post, but I don't think you understand mine.
What does the wired port connect to, and what the wireless?
These bits of hardware can vary quite a bit in capability.
Does the router supply all the IP addresses?

---

### Post by richfaraone on 2012-03-01
> **dandnsmith said:**
> I understand your post, but I don't think you understand mine.
What does the wired port connect to, and what the wireless?
These bits of hardware can vary quite a bit in capability.
Does the router supply all the IP addresses?
The connection is to a RS718TXL CenterCOM 18 port hub. The hub connects to a Belkin F5D8230-4 Pre n Router which supplies the IP addresses via DHCP. The router is connected to a Scientific Atlanta, WebStar DPC2100 modem, which connects to the high speed Internet via Cox cable on a static IP.

The wireless connection works fine, and pulls an IP address from the pool I have configured in the router (192.168.2.2 - 2.100). It's just the ethernet connection that's not working. Yesterday I tested the ethernet connection by plugging up a Mac and a Windows laptop, both connected fine. 

It's only when I plug in the Ubuntu machine to the wired connection that there is a problem. It pulls an address of 192.168.**0**.100 when on DHCP, but it CAN see my network printers, and it says it's connected. If I manually configure an IP address on the machine in the 2.2 - 2.100 range, it looses all connectivity.

---

### Post by dandnsmith on 2012-03-02
Thanks for the detail.
Is there any chance you can take interaction with the hub out of the equation by plugging directly into one of the router's ethernet ports?
Did you look to see what IP addresses the Mac and Windows machines were allocated when they worked plugged to the hub?
Have you tried different hub ports and different cables?
Do you have any evidence that that ethernet port on your PC is working?

---

