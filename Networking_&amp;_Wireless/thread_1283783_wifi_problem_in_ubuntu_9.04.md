---
title: "wifi problem in ubuntu 9.04"
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by shibinjohn on 2009-10-05
hi all,
         i upgraded ubuntu UE 2.0 to ubuntu 9.04 and found my wifi not working. I am absolute beginner so please help.  My laptop is compaq presario 791TU and wifi card is from Atheros. I found my wifi working under windows. I cheked the hardware drivers in the administration menu and found alternate madwifi driver which i activated but still the priblem exists. pls help.. thaks in advance..

---

### Post by Crafty Kisses on 2009-10-05
What are the results of the following?
```
lspci
lshw -C network
```

---

### Post by shibinjohn on 2009-10-07
for lspci i got the following

[FONT=Arial Black]00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
[/FONT]

When i typed lshw -C network i got 
[FONT=Arial Black]WARNING: you should run this program as super-user.
  *-network UNCLAIMED                              
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1e:ec:8d:b7:82
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.2 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 66:98:5b:d7:96:77
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


[/FONT]

---

### Post by Runnerzdad on 2009-10-07
Did you reboot after activating the new driver?  I had the same problem last nite after installing Koala.  After activating the driver I was getting aggravated because it wasn't helping.  After I rebooted everything was fine

Runnerzdad

---

### Post by shibinjohn on 2009-10-08
yes i rebooted but still it doesn't work.. what may be the reason? kindly help..

---

