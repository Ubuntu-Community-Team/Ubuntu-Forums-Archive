---
title: "How to set up the WLAN Hard- and -Software?"
date: 2009-03-10
forum: Networking &amp; Wireless
---

### Post by Cotopaxi on 2009-03-10
After reading through the forums, I found out that many users are having problems with logging into WLANS or WIFI networks or public access points.

The goal of this thread is to set up a kind of a &#8220;guideline&#8221; which will help other users to set up their hardware and software.

The first logical point is, of course a description of the hardware and software installed, as well as a description of the problem.

So, in my case:

Hardware: Lenovo 3000 N200 Laptop with an INTEL WLAN PCI card.

Software: (K)UBUNTU Intrepid Ibex

The problem: The (K)Network Manager (an icon with the form of the world globe) DOES display the available WLANS, differentiating between protected and &#8220;free&#8221; WLANS but, when I select a &#8220;free&#8221; WLAN to log into, the Network Manager starts building up the connection, but never finishes establishing this connection.

As soon, as I plug in an Ethernet cable, I can access the internet without any problem.

I also had exactly the same problem with Kubuntu Hardy Heron, I made a clean install of Kubuntu Intrepid, hoping to have more luck.

So the question is now:

Which are the correct steps to take, what should be checked out, and in which chronological order should these steps and checks be performed?

I hope that with your feedback you will not only help me but also many others.

Thank you very much in advance for your help!! :D

---

### Post by Cotopaxi on 2009-03-11
One thing i found out:

The WLAN device is an Intel PRO/Wireless 3945 ABG.

I am located in Spain, I do not know if this is important.

---

### Post by Cotopaxi on 2009-03-12
Bump ;)

---

### Post by Cotopaxi on 2009-03-12
Bump ;)

---

### Post by Cotopaxi on 2009-03-12
Here comes the output of: "lshw -C network"

>  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:98:49:45
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:0b:36:0a
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 5e:ca:20:27:ea:7d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


---

### Post by Cotopaxi on 2009-03-12
Bump;)

---

### Post by Cotopaxi on 2009-03-12
Bump;)

---

### Post by Cotopaxi on 2009-03-12
Bump

---

### Post by Cotopaxi on 2009-03-12
I installed "wicd" (which eliminated the network manager). 

Wicd actually DOES FIND the available networks, differentiating between protected and free networks. Once you choose to connect to a free network, wicd just connects to the selected network, WITHOUT INDICATING that the connection is established! You only know that the connection was successful, because the button &#8220;Connect&#8221; changes to &#8220;Disconnect&#8221;!

Besides that, wicd works great! :guitar::mrgreen:

The following link describes how to install wicd:

[http://kubuntuforums.net/forums/index.php?topic=3099106.0]("http://kubuntuforums.net/forums/index.php?topic=3099106.0")

It is actually a Kubuntu forum, but the procedure is exactly the same for Kubuntu or Ubuntu.

I hope, this helps other people! ;)

---

