---
title: "Wireless not working in-case of force shutdown"
date: 2010-09-27
forum: Networking &amp; Wireless
---

### Post by kumpsath1 on 2010-09-27
Hi,
i'm using Ubuntu in my office. I have to report two issues with network connectivity.
1. Wireless doesn't work if come back after suspend/hibernate the computer. The work around I follow is,
a. Turnoff the wifi and restart the computer. (It won't shutdown. have to do force using the power button)
b. Reinstall the network-manager_0.8-0ubuntu3_amd64.deb and network-manager-gnome_0.8-0ubuntu3_amd64.deb
c. Restart the computer (Again it won't shutdown. Need force.)
d. Now wifi will detect the networks and shutdown works fine hereafter.
2. Sometimes the wired gets disconnect frequently (thrice in 2minutes). Physical connectivity is good and working well in Windows.

Details
Os: Ubuntu 10.04-64 bit
Model: Dell E6500
Kernal: 2.6.32-24-generic

please let me know how to resolve these two issues and if you need any other log. It really affects our productivity and if no solution we'll be forced to move back to windows.

thanks in advance.

---

### Post by grahammechanical on 2010-09-27
I do not know much. May I ask the following?

1) Is it a laptop? If so are you using the hardware switch to switch off the wireless card before suspend/hibernate? Perhaps you should.

2) Is this a wireless problem or a suspend/hibernate problem?

3) Have you examined the ethernet cable? Is it fitting correctly? Are there bends or kinks that could have damaged the wires inside the covering. Could you use another cable?

regards

---

### Post by kumpsath1 on 2010-09-28
Hi,
Thanks for your reply. 
DELL E6500 is the laptop model. Its happening mostly during the force shutdown (like battery goes low).
I don't know whether it is wireless/hibernate problem. 
There is no problem with the physical connectivity.

My understanding is if we don't do proper shut down then the wireless driver gets corrupted.



~sathish

---

### Post by hackedhacker on 2011-04-19
Hi, I was having a problem a bit similar, but different with this one.

I'm on a computer (not laptop).
I suppose it is very much possible a suspend/hibernate problem.

I could use my internet connection very well, I could even say online for weeks without disconnected. But my computer's jack on the front casing for the headphone, or even USB ain't working.

But after a suspend or two, it worked.
But after the 1st suspend, the wired connection is disconnected, and wouldn't connect at all.
But after trying to suspend and re-login into my computer again, it worked fine again.

*I'm not sure for mine its one problem or two, but it seems that the problem is somehow connected*

Hope this help and would help me also...
^_^

---

### Post by josephmills on 2011-04-19
could I please see a ```
lspci
```and ```
 sudo lshw -C network
```

---

### Post by hackedhacker on 2011-04-22
```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)
02:00.0 Ethernet controller: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)

```
```
  *-network               
       description: Ethernet interface
       product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:26:18:65:db:e2
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=172.30.4.168 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:44 memory:febc0000-febfffff ioport:ec00(size=128)

```

Thx for helping...
I'm really hoping to be able to use my computer completely again.

---

### Post by hackedhacker on 2011-05-05
no reply?

---

