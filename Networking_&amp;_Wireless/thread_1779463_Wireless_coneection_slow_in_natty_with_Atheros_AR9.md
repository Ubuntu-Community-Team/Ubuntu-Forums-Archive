---
title: "Wireless coneection slow in natty with Atheros AR9285"
date: 2011-06-10
forum: Networking &amp; Wireless
---

### Post by Zargoon on 2011-06-10
Hello,

Since I've upgraded to 11.04, my wireless has been sporadically slow.  I've been trying to figure out why but all I've seen is a wide range of posts that aren't very helpful.

It will usually be really slow, and then randomly it will speed up before it goes back to being slow.

lscpi yields the following information:

03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

Any help would be greatly appreciated.

---

### Post by Linfreak on 2011-06-10
Same problem here :( No clues yet.. Makes it so hard to download stuff or stream videos.

---

### Post by garvinrick4 on 2011-06-10
What does this say:
```
sudo lshw -C network
```
EDIT: Check and see if you are stable running G more than N ?
         Just a thought, is router set at N only and driver will run better
         at G? Look and see what was changed in kernel driver from whatever
         you ran before 11.04? Maybe below will help? 
         [stable - Linux Wireless]("http://linuxwireless.org/en/users/Download/stable/#compat-wireless_3.0_stable_releases")
         Whatever you finds works for unstable wireless and your card and driver post back here.

---

### Post by Linfreak on 2011-06-11
```
sudo lshw -C network
```

gives..

```
 *-network               
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:26:2d:8c:46:d6
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=half firmware=sb latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 memory:f0400000-f040ffff
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: c4:17:fe:c1:e3:b6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A ip=62.78.145.142 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0500000-f050ffff
```

Will check the router and driver stuff and post that info as well.

---

### Post by garvinrick4 on 2011-06-11
That driver does have known bugs and here is an upgrade in kernel that
fixes it from launchpad. Launchpad.net is in upper right of Ubuntu Forums page.
Is nice to have a launchpad account if you do not. Let me know and mark as solved if works
if it is a fix for your machine others will want to know, a popular card and driver.
What did the N and G thing do in your router configuration?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/761176/comments/8](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/761176/comments/8)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/754176](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/754176)

---

### Post by garvinrick4 on 2011-06-11
#Earlier I gave the compat-wireless link:
If you use or have used make sure you use the right kernel as your "uname -a" read the read me file after extract.
#Can just make a new intramfs below if any problem. 
#I like to use the compat-wireless
always works for me. 
##Though earlier launchpad says new kernel has fix in it.
```
sudo update-initramfs -u
```

---

