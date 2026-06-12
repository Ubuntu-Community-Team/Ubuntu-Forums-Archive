---
title: "Wireless in Dell D630, Broadcom BCM4321"
date: 2013-02-27
forum: Networking &amp; Wireless
---

### Post by Bm1234 on 2013-02-27
Hi,

I am absolute new to Ubuntu platform.

I have a old Dell D630 and thought of trying Ubuntu and got rid of windows.

However, after installing Ubuntu, everything is well except the wireless network. The wireless icon is not active and it is not getting connected.

Wireless controller that i have is Broadcom BCM4321 and kernel module as SSB.
I am not sure how to resolve this wireless issue and appreciate any suggestions to resolve.
Thanks,
Ben

---

### Post by nns2006 on 2013-02-27
I think you need to install firmware b43 installer. see it [in this thread here]("http://ubuntuforums.org/showthread.php?p=12514555#post12514555")

---

### Post by Hadaka on 2013-02-27
hi please post the output of..

```
lspci -n | awk '{print$3}' 
```

thanks



reason for edit?????

---

### Post by grahammechanical on 2013-02-27
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

Regards

---

### Post by fr33z0n3r on 2013-02-27
I have the same laptop.  Interesting, I had no issue with it in part because mine has the Intel 3945ABG card.  Didn't know they had options on this model.

---

### Post by Bm1234 on 2013-03-01
> **Hadaka said:**
> hi please post the output of..

```
lspci -n | awk '{print$3}' 
```

thanks


Hi This is the update i get 

8086:2a00
8086:2a01
8086:2834
8086:2835
8086:283a
8086:284b
8086:283f
8086:2841
8086:2849
8086:2830
8086:2831
8086:2832
8086:2836
8086:2448
8086:2815
8086:2850
8086:2828
8086:283e
10de:042b
1217:7135
1217:00f7
14e4:1673
14e4:4328

I also tried to process the transaction

```
sudo lshw -c network
  *-network               
       description: Network controller
       product: BCM4321 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f1ffc000-f1ffffff memory:f0000000-f00fffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:08:3a:95
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 duplex=full firmware=5755m-v3.29 ip=192.168.0.5 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:f1ef0000-f1efffff

```
I hope this helps, i am really not sure why the wireless is not detected.
Thanks and appreciate your help.

---

### Post by Hadaka on 2013-03-01
Hi, try this
```
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
 
```

---

### Post by Bm1234 on 2013-03-04
I was able to resolve this issue, after going through few forums questions and help documentation, they issue was due to driver conflict.

---

