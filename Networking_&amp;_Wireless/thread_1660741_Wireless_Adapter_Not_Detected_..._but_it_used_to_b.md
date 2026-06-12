---
title: "Wireless Adapter Not Detected ... but it used to be!"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by miniCruzer on 2011-01-05
**I will bold the areas where there is the most important information! Some of this post may be irrelevant, so I won't bore you with the details, unless you wish to read all of it.**

This machine is a Compaq Mini 110c-1105DX (netbook), running Ubuntu Maverick 10.10. I installed Ubuntu on this machine for a friend whose trial license ended for Windows 7 Starter Edition (ew).

When I installed Ubuntu approximately 19 days ago from the date of this post, the Wireless Drivers were not detected, and I had to jump through quite a few hoops to get them working. Some **b43** packages were missing. I had to compile **b43-fwcutter-011** from source. This was the eventual solution.

Two days ago, my friend came to me telling me that Wireless no longer worked. Specifically, **Ubuntu no longer detects the on-board wireless adapter**. The networking icon in the System Tray does not list a "Wireless Network" subtitle, and only a "Wired Network", showing **eth0**.

There is evidence the machine could at one point connect to wireless networks. Under **System -> Preferences -> Network Connections** on the **Wireless** tab, is a list of wireless networks connected to and when they were last used. My network displays that it was last used 19 days ago. Its home network was last connected 5 days ago.

**Miscellaneous Details**

[LIST]
[*]I have already tried [this]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#HP%20Mini%20110%20/%20Compaq%20Mini%20100c/110c").
[*]Ubuntu does **not** complain about any drivers or errors whatsoever.
[*]Yes, the machine's hardware switch indicates that the internal card is indeed on, however, I cannot turn it off. The user manual indicates the switch will be blue, and it is.
[*]Some commands I ran that may be useful to the reader:
[/LIST]
 _lshw -C network_ (this command was run while connected through Ethernet)
```

thault@baby:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:feafc000-feafffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: 18:a9:05:8f:34:6b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A ip=192.168.1.9 latency=0 multicast=yes
       resources: irq:44 memory:febc0000-febfffff ioport:ec80(size=128)

```_nm-tools_ (connected to Ethernet)
```

NetworkManager Tool
State: connected
- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        18:A9:05:8F:34:6B

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.9
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1

```_lspci_
```

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
02:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)

```**Upon request, I will post more details of commands!** I am about willing to try everything, even OS reinstall.

---

### Post by bkratz on 2011-01-05
From your device this sticky looks like it is useful

[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

---

### Post by miniCruzer on 2011-01-05
> **bkratz said:**
> From your device this sticky looks like it is useful

[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

I appreciate the quick reply!

Synaptic spit this out at me when I marked for **reinstallation**, however the sticky said to mark for installation.

```

E: firmware-b43-lpphy-installer: subprocess installed post-installation script returned error exit status 255

```

I will experiment more between system reboots.

---

