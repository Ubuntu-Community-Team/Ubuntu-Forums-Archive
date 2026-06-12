---
title: "Macbook9,2 12.04 clean install - no network devices available"
date: 2012-11-21
forum: Networking &amp; Wireless
---

### Post by benjaminabruzzo on 2012-11-21
I have a 200gb partition on my 13" macbook pro (9,2).  I installed 12.04 via cd, which worked without trouble.

I have no access to the internet.  Neither my Broadcom wireless nor Broadcom wired connections work.  Network manager claims "No network devices available."

I think I have the drivers installed out of the box, but I'm not sure how to make them claim my devices.

I have the output from several prompts attached:
sudo dmidecode -s system-product-name
ifconfig
sudo lshw -class network


------------------------------------------
sudo dmidecode -s system-product-name
MacBookPro9,2

----
lspci
00:00.0 Host bridge: Intel Corporation Device 0154 (rev 09)
00:01.0 PCI bridge: Intel Corporation Device 0151 (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 0166 (rev 09)
00:14.0 USB Controller: Intel Corporation Device 1e31 (rev 04)
00:16.0 Communication controller: Intel Corporation Device 1e3a (rev 04)
00:1a.0 USB Controller: Intel Corporation Device 1e2d (rev 04)
00:1b.0 Audio device: Intel Corporation Device 1e20 (rev 04)
00:1c.0 PCI bridge: Intel Corporation Device 1e10 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Device 1e12 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Device 1e14 (rev c4)
00:1d.0 USB Controller: Intel Corporation Device 1e26 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Device 1e57 (rev 04)
00:1f.2 SATA controller: Intel Corporation Device 1e03 (rev 04)
00:1f.3 SMBus: Intel Corporation Device 1e22 (rev 04)
01:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe (rev 10)
01:00.1 SD Host controller: Broadcom Corporation Device 16bc (rev 10)
02:00.0 Network controller: Broadcom Corporation Device 4331 (rev 02)
03:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 08)

----
ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10960 (10.9 KB)  TX bytes:10960 (10.9 KB)
----
sudo lshw -class network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: NetXtreme BCM57765 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:a0400000-a040ffff(prefetchable) memory:a0410000-a041ffff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:a0600000-a0603fff

----
etc/network/
gedit interfaces

auto lo
iface lo inet loopback
------------------------------

Clearly the OS sees the devices, I just can't get them active.

---

### Post by nothingspecial on 2012-11-22
*Thread moved to **Networking & Wireless**.*

---

### Post by benjaminabruzzo on 2012-11-23
I upgraded to 12.04.1, that corrected the driver for ethernet.  



Once I fixed that, the wireless did not work.  I tried this page: [http://askubuntu.com/questions/183192/broadcom-bcm4331-device-not-ready-firmware-missing-error](http://askubuntu.com/questions/183192/broadcom-bcm4331-device-not-ready-firmware-missing-error).  To no avail, wireless still did not work.

Last shot, [http://ubuntuforums.org/showthread.php?t=2011756](http://ubuntuforums.org/showthread.php?t=2011756).  This fixed it.  I am now working a Macbook Pro 9,2 (13" non-retina) with 12.04.1 on both ethernet and wifi.

---

