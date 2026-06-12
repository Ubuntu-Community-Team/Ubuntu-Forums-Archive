---
title: "Unable to connect to the Internet [10.04]"
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by vlamnire on 2010-08-18
I have a problem with my Ubuntu installation on my laptop.  I have never experienced this problem before but suddenly after a reinstall I am.  My desktop is running Windows 7 and has no problems.

My connection is DSL (modem and router) via wireless connection.

Router IP: 192.168.1.1
Desktop IP: 192.168.1.2
DNS servers: 8.8.8.8 and 8.8.4.4

My current desktop settings are below in this image:
[IMG]http://i421.photobucket.com/albums/pp296/vlamnire/network.jpg[/IMG]

I can open Firefox and enter 192.168.1.1 and connect to my routers configuration page.  Could anyone help me out here?

---

### Post by dineshs on 2010-08-18
How do you connect to the internet ?Using the DSL tab in Network manager (Modem in bridge mode) or modem configured for always on (modem in PPPoE mode)?

---

### Post by vlamnire on 2010-08-18
I do not have PPoe and my router is set to bridged.  Currently I am using the default network manager for Ubuntu and I'm using the Wireless tab.

---

### Post by dineshs on 2010-08-18
In windows do you have a PPPoE dialler?Where do you enter  your username and password?

---

### Post by vlamnire on 2010-08-18
I don't use ppoe and I do not use a username and password.  I just have phone line to modem then yellow ethernet cable to router then laptop connected wirelessly.

---

### Post by dineshs on 2010-08-18
Can you post the output of(ubuntu)```
sudo lshw -C network
```and
```
route -n
```

---

### Post by vlamnire on 2010-08-18
> **dineshs said:**
> Can you post the output of(ubuntu)```
sudo lshw -C network
```and
```
route -n
```

output of sudo lshw -c network
```
*-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:16:36:d0:5b:40
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:27 memory:44000000-44003fff ioport:2000(size=256)
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:0a:03.0
       logical name: wlan0
       version: 01
       serial: 00:19:7d:4c:dc:6a
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.1.3 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:d0000000-d000ffff
```

output of route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
```

---

### Post by dineshs on 2010-08-18
Wireless interface shows IP 192.168.1.3 
Did you configure Network Manager for static IP 192.168.1.3?Did you give gateway?

---

### Post by vlamnire on 2010-08-18
I believe I have

[IMG]http://i421.photobucket.com/albums/pp296/vlamnire/network2.jpg[/IMG]

---

### Post by dineshs on 2010-08-18
Your gateway is not set
You should assign 192.168.1.1 as gateway then[COLOR="Blue"] hit enter[/COLOR] (do not forget to hit enter)

---

### Post by vlamnire on 2010-08-18
Thank you so much it works now.  Who knew a little thing like pressing enter would make so much of a difference.

---

### Post by dineshs on 2010-08-18
I also had the same problem and took a week to solve it.Kindly mark the thread as solved via thread tools

---

