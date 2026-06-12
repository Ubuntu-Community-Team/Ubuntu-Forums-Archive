---
title: "After updating, wireless no longer shows"
date: 2013-05-31
forum: Networking &amp; Wireless
---

### Post by Jobbo256 on 2013-05-31
I recently updated to Elementary OS 0.2 and after the update my wireless just cut out and doesn't show anymore. I have an HP Pavilion g7.

```
sudo lspci
```

says:

00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 Network controller: Ralink corp. Device 3290
01:00.1 Bluetooth: Ralink corp. Device 3298
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5229 (rev 01)

```
sudo lsusb
```

says:

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 1bcf:2c1e Sunplus Innovation Technology Inc. 

```
ifconfig
```

says:

eth0      Link encap:Ethernet  HWaddr 84:34:97:6e:9d:9f  
          inet addr:192.168.1.217  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::8634:97ff:fe6e:9d9f/64 Scope:Link
          inet6 addr: 2602:306:32e2:820:2116:1a0b:de8c:9910/64 Scope:Global
          inet6 addr: 2602:306:32e2:820:8634:97ff:fe6e:9d9f/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3792 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2872 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3029131 (3.0 MB)  TX bytes:415785 (415.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:908 errors:0 dropped:0 overruns:0 frame:0
          TX packets:908 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:80427 (80.4 KB)  TX bytes:80427 (80.4 KB)

```
sudo lshw -C network
```

says:

*-network UNCLAIMED     
       description: Network controller
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c2510000-c251ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 05
       serial: 84:34:97:6e:9d:9f
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.217 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:3000(size=256) memory:c2404000-c2404fff memory:c2400000-c2403fff

```
iwconfig
```

says:

eth0      no wireless extensions.

lo        no wireless extensions.




I figured it was my wireless driver, so I followed the tutorial here:[HTML]http://forum.novatech.co.uk/showthread.php?25562-How-to-get-the-RAlink-3290-wireless-working[/HTML] but after I restarted still nothing happened. In my network center it doesn't show any network connections. Please, any help is much appreciated.

---

### Post by praseodym on 2013-05-31
Try this installation with dkms:

[http://forum.ubuntuusers.de/topic/nach-update-kein-wlan-mehr-433/2/#post-5641297](http://forum.ubuntuusers.de/topic/nach-update-kein-wlan-mehr-433/2/#post-5641297)

---

### Post by Jobbo256 on 2013-05-31
Thank you the wireless works now. However, every time I open an application while connected to wireless, I get a kernel panic. Could this possibly be due to compiling an old kernel with the other tutorial I used?

---

### Post by praseodym on 2013-05-31
Which kernel is it? Please show "uname -a"

---

### Post by Jobbo256 on 2013-05-31
```
Linux laptop 3.6.3-030603-generic #201210211349 SMP Sun Oct 21 17:50:41 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by praseodym on 2013-05-31
Why did you install the mainline kernel? Any possibility for kernel 3.5 regularly?

---

### Post by Jobbo256 on 2013-05-31
Ok, I reverted back to 3.2 and now everything is all working. Thank you for your help!

---

