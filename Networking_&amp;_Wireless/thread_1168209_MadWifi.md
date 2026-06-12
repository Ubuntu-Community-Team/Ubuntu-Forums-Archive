---
title: "MadWifi"
date: 2009-05-23
forum: Networking &amp; Wireless
---

### Post by Lacrimo on 2009-05-23
The driver works just fine until I reboot, when it refuses to connect. If I reinstall it, it works fine until the next reboot. Anyone know how to fix this?

---

### Post by t0mppa on 2009-05-23
Well, have you made sure the module gets loaded when you boot? Did you add a line containing 'ath_pci' to /etc/modules?

If that's taken care of though, please post output of following commands from the terminal on your next reboot before you reinstall anything ```
lshw -C network
dmesg | grep ath
```

---

### Post by Lacrimo on 2009-05-24
I added ath_pci to the modules to no avail.

>  *-network               
       description: Ethernet interface
       product: MCP78S [GeForce 8200] Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:7b:97:3f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.120 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 22:ea:78:0a:f1:9b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


> [   16.477261] ath_hal: module license 'Proprietary' taints kernel.
[   16.480403] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   16.530386] ath_pci: 0.9.4
[   16.530441] ath_pci 0000:07:00.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23
[   16.530459] ath_pci 0000:07:00.0: setting latency timer to 64
[   21.651040] ath_pci 0000:07:00.0: PCI INT A disabled


---

### Post by t0mppa on 2009-05-24
> [ 21.651040] ath_pci 0000:07:00.0: PCI INT A disabled 

That means something is disabling it. Try 'sudo modprobe ath_pci' to see if that helps. You can check with lsmod to see if the module got loaded and with lshw to see if the interface got associated with it.

---

