---
title: "Broadcoam sta wirless not working"
date: 2010-12-26
forum: Networking &amp; Wireless
---

### Post by swissman on 2010-12-26
Hi, I have a hp dv2745se.
I recently installed ubuntu 10.10, everything works fine, I even installed all the update and repaired all broken packages. I installed additional drivers nvdia, but the STA broadcoam wireless wont work.... I keep spending sleepless nights trying to figure out what is wrong with my wireless, can anyone help????

---

### Post by dineshs on 2010-12-27
Is postcount#1 [here]("http://ubuntuforums.org/showthread.php?t=1604868") related?
> Solution: System > Administration > Synaptic Package Manager > Search: firmware-b43-lpphy-installer > Click Mark > Click install > Close

Kontza found the solution (post #3), so thank him for it.

---

### Post by swissman on 2010-12-27
I already installed it, still doesnt work/// please help

---

### Post by dineshs on 2010-12-27
What does ```
sudo lshw -C network
``` and ```
iwconfig
``` say?

---

### Post by swissman on 2010-12-27
sudo lshw -C network: shows

 *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:47:c5:f7
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=118.202.208.147 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:42 memory:fc488000-fc488fff ioport:30f8(size=8) memory:fc489c00-fc489cff memory:fc489800-fc48980f
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:73:e3:c2:3f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:20 memory:fc000000-fc003fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes



iwconfig shows :
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

vboxnet0  no wireless extensions.

thanks for fast reply btw

---

### Post by dineshs on 2010-12-27
Is wireless enabled?.Check
1)Rightclick Networkmanager icon and ensure that wireless is enabled 
OR
See postcount #7 [here]("http://ubuntuforums.org/showthread.php?t=1650507")
2)See if post#3 [here]("http://ubuntuforums.org/showthread.php?t=1505217") helps
3)If there is no luck see 
[http://ubuntuforums.org/showthread.php?t=1594577](http://ubuntuforums.org/showthread.php?t=1594577)
EDIT: Please try sudo lshw -C network and iwconfig after removing ethernet cable

---

### Post by swissman on 2010-12-27
I feel really stupid, since i spent 4days looking for a solution, I find it hard that all the forums I went on did not mention this. If you have installed STA driver, and all other recommended kernels, and wifi still doesnt work just type this in terminal:

rfkill unblock all


thank you for you help

---

