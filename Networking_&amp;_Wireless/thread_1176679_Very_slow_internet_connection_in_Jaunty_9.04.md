---
title: "Very slow internet connection? in Jaunty 9.04"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by monty593 on 2009-06-02
Hi, this my first thread and post here though I've used these forums for along time for help on Ubuntu Jaunty, my final problem is the slow internet connection, the speed is very low I'm using wireless network and when I've upgraded to Jaunty and had to turn on the proprietary driver , I need to fix this problem because this is the only thing that has been annoying me in jaunty.... my chipset 

Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
    Subsystem: AMBIT Microsystem Corp. Device 0422
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f8000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl, ssb


thks...:)

---

### Post by laloruelas on 2009-06-04
do you know how to disable iPV6? it sometimes makes ubuntu's internet slow.

---

### Post by NETWORKsolutions on 2009-07-27
Hi I have a slow connection to internet with ubuntu 9.04. Before install this great OS I was using windows vista and the internet connection was fast, but now with ubuntu I do not know why is slow. After I red some posts I typed this command and get some of this info:

sudo lshw -C network
*-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:95:0f:67
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1f:e1:89:55:b5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.0.65 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 66:58:f0:3f:0d:5b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Can somebody help me to know how to get a faster connection?? please

---

### Post by simon@syd on 2009-07-30
dont know if it is the same problem, but i posted a solution to my problem here:
[http://ubuntuforums.org/showthread.php?t=1227509](http://ubuntuforums.org/showthread.php?t=1227509)

---

### Post by ub-newbie on 2009-08-02
In response to laloruelas's comment.  It is my understanding that IPV6 is now built into the kernel in Jaunty.  

[https://bugs.launchpad.net/ubuntu/jaunty/+source/glibc/+bug/313218]("https://bugs.launchpad.net/ubuntu/jaunty/+source/glibc/+bug/313218")

---

### Post by ArmenianLeader4 on 2009-08-02
First, I'd disable your IPV6, and then check that you have at least 56Mbps internet connection. I can't see any reason why it shouldn't work from there.

---

### Post by elnur on 2009-08-12
I solved this problem by setting **OpenDNS** as DNS.

Open the file:
```
sudo nano /etc/dhcp3/dhclient.conf
```
And add this to the end of the file:
```
prepend domain-name-servers 208.67.222.222, 208.67.220.220;
```

More info [here]("http://ubuntuforums.org/showthread.php?t=878694").

---

