---
title: "Problems with wireless, Broadcom 4313, Ubuntu 11.10"
date: 2011-10-27
forum: Networking &amp; Wireless
---

### Post by FokkerCharlie on 2011-10-27
Hello!

I have a laptop running Oneiric 64, works mostly OK, and has a Boradcom 4313 wireless chip.  This has been working fine until recently... with Natty and the proprietary Broadcom driver, I had it working as an ad-hoc access point as well.

On (clean) installing Oneiric, I found that the ad-hoc wasn't working- even after installing the proprietary driver.  So, I uninstalled, re-installed, had a look around in synaptic, couldn't figure out why.  Unfortunately, all of that has resulted in the wireless not working at all.  I don't see any wireless option (no available networks, no 'enable wireless' menu item in nm-applet), although the driver looks like it's installed in jockey.

Here's some more stuff from my detective work:

```
nm-tool 

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        70:5A:B6:C3:52:04

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off
```

```
sudo lshw -C network
[sudo] password for charlie: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 70:5a:b6:c3:52:04
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-1.fw ip=10.0.61.110 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:45 ioport:6000(size=256) memory:d3104000-d3104fff memory:d3100000-d3103fff memory:d3120000-d313ffff
  *-network
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:d7300000-d7303fff

```

```
lsmod | grep bcma
bcma                   20219  0 

sudo iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

```

```
dmesg | grep bcm
[   10.988850] bcma-pci-bridge 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.988863] bcma-pci-bridge 0000:07:00.0: setting latency timer to 64
[   10.988916] bcma: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   10.988938] bcma: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   10.988988] bcma: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   11.020177] bcma: Bus registered

```

Contents of /etc/network/interfaces:

```
auto lo
iface lo inet loopback
```
Which doesn't look right to me...

but despite all this, no wireless!!!!  I've been searching the forums and elsewhere for similar issues, but no-one else seems to have quite the same snag.  Any suggestions?

Thanks in advance!

Charlie

---

### Post by mörgæs on 2011-10-27
Does this help?
[http://ubuntuforums.org/showthread.php?t=1870390](http://ubuntuforums.org/showthread.php?t=1870390)

---

### Post by FokkerCharlie on 2011-10-28
Yes!  Thanks very much.... back to the built-in drivers now.

Charlie

---

