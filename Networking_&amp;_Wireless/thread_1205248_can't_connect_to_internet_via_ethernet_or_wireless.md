---
title: "can't connect to internet via ethernet or wireless"
date: 2009-07-05
forum: Networking &amp; Wireless
---

### Post by astroshaw on 2009-07-05
Hi, I'm running Ubuntu off a live CD and wanted to make sure I could connect to the internet before I installed it, but I can't connect via either wireless or wired connection, I was hoping someone could help me:
I plug in the ethernet cord and the green and orange indicator lights light up normally. Then I do System --> Administration --> Networking and deactivate all other connections except eth0, which I activate. I don't get any error messages through any of this. But then when I open Firefox, I still can't connect to any websites.
 
Thanks for your help!!
~astroshaw

---

### Post by Boondoklife on 2009-07-05
plug in the ethernet cable and boot the cd. then post the output of
```
ifconfig
tracepath www.google.com
```

---

### Post by astroshaw on 2009-07-06
Hi Boondoklife,
 
Here's the output:
 
ubuntu@ubuntu:~$ ifconfig
ath0 Link encap:Ethernet HWaddr 00:14:A4:08:31:6A
inet6 addr: fe80::214:a4ff:fe08:316a/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:2825 dropped:0 overruns:0 frame:2825
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:200
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:11 Memory:e0be0000-e0bf0000
 
eth1 Link encap:Ethernet HWaddr 00:20:E0:89:F6:7B
inet6 addr: fe80::220:e0ff:fe89:f67b/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:2772 (2.7 KiB)
Interrupt:11 Memory:f8000000-f8000fff
 
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:53 errors:0 dropped:0 overruns:0 frame:0
TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:3824 (3.7 KiB) TX bytes:3824 (3.7 KiB)
 
ubuntu@ubuntu:~$ tracepath [www.google.com](www.google.com)
gethostbyname2: Host name lookup failure
ubuntu@ubuntu:~$
 
Thanks!
-astroshaw

---

### Post by Boondoklife on 2009-07-06
Hmm well that is odd that there is not an eth0, how many network cards do you have in the system
Post the output of```
sudo lshw -class Network

```

---

### Post by superprash2003 on 2009-07-06
post output of **sudo dhclient eth1** when connected via wired

---

### Post by astroshaw on 2009-07-06
Hi boondoklife,
 
I got the output:
 
ubuntu@ubuntu:~$ sudo lshw -class Network
*-network:0
description: Wireless interface
product: Prism 2.5 Wavelan chipset
vendor: Intersil Corporation
physical id: 7
bus info: pci@02:07.0
logical name: eth1
version: 01
serial: 00:20:e0:89:f6:7b
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=orinoco driverversion=0.15rc3 firmware=Intersil 1.3.3 link=yes multicast=yes wireless=IEEE 802.11b
resources: iomemory:f8000000-f8000fff irq:11
*-network:1 DISABLED
description: Ethernet interface
product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
vendor: Intel Corporation
physical id: 8
bus info: pci@02:08.0
logical name: eth0
version: 42
serial: 00:0a:e4:41:bc:31
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
configuration: autonegociation=off broadcast=yes driver=e100 driverversion=3.4.14-k4-NAPI duplex=half firmware=N/A link=no multicast=yes port=MII speed=10MB/s
resources: iomemory:d0200000-d0200fff ioport:8000-803f irq:11
*-network
description: AR5001-0000-0000
product: Wireless LAN Reference Card
vendor: Atheros Communications, Inc.
physical id: 0
version: 00
slot: Socket 0
resources: irq:11
*-network
description: Wireless interface
product: AR5212 802.11abg NIC
vendor: Atheros Communications, Inc.
physical id: 1
bus info: pci@03:00.0
logical name: ath0
version: 01
serial: 00:14:a4:08:31:6a
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ath_pci driverversion=0.9.6.0 (EXPERIMENTAL) multicast=yes wireless=IEEE 802.11
resources: iomemory:d2000000-d200ffff irq:11
ubuntu@ubuntu:~$
 
 It looks like eth1 is actually a wireless interface.  And I'm having difficulty enabling eth0.  It shows up in the Network Settings dialog and I don't get any errors when I click the "activate" button, but I don't think it actually gets activated.
 
Thanks for helping me out with this!
-astroshaw

---

