---
title: "Wifi timeout problem"
date: 2010-11-27
forum: Networking &amp; Wireless
---

### Post by shabin5785 on 2010-11-27
Hi all,
 I installed ubuntu 10.10. But if i keep my laptop for downloading and keep it idle, my wireless gets signed out so that i have to enter password and have to sign into to the network again. I had no problem with 10.04. 
Also do let me know the command to find info about my network card.

thanks in advance

---

### Post by Tobeus on 2010-11-27
I'm not sure what is causing your wifi to time out, but I would start by deleting the wifi profile you have set up for your access point and then set up a new one.  Perhaps something is wrong with the wifi profile.

As far as the command(s) to view information about your network card, I'm not sure what you are looking for, but here are a couple of helpful commands to view things related to your network card:

```
ifconfig
```

```
sudo lshw -C network
```

Hope these help!

---

### Post by shabin5785 on 2010-11-27
*-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 00:26:2d:55:cf:ba
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 firmware=sb v2.19 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:f0200000-f020ffff
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlan0
       version: 01
       serial: 00:17:c4:bd:34:41
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-22-generic firmware=N/A ip=192.168.1.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f0300000-f030ffff


Output for sudo lshw -c network. Do help. it takes abt 5 mins for the network to be signed out.

---

### Post by Phkillah on 2010-12-09
Same problem here.

---

### Post by Phkillah on 2010-12-09
This is all over the Internet, how come there isn't a solution yet?

Please Notice that this happens only with specific Networks (WPA times out for me. Wep doesn't).

Come'on Ubuntu, 2 month of 10.10 and still these bugs?! This didn't happen in 10.04!

For example, if I keep a ping running, my wifi connection will not drop. Otherwise, i can go away for a minute or so, and my connection drops asking me the password again.

---

### Post by EMABrad on 2010-12-15
I have a problem similar to this.  Perhaps this bug report can be of insight: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/644452]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/644452")

---

