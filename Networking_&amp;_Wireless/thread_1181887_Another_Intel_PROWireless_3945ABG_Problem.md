---
title: "Another Intel PRO/Wireless 3945ABG Problem"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by Daewoos on 2009-06-08
Hy all,

here's my problem: I have an Dell with Ubuntu 8.04 - the Hardy Heron installed, after those updates that ubuntu have weekely my wired connection dissapired. I searched for a solution and i found that i have to install the packet  compat-wireless-old-2009-05-21.tar.bz2 at [http://wireless.kernel.org/download/compat-wireless-2.6]("http://wireless.kernel.org/download/compat-wireless-2.6/") . I did it and my wired connection appeared but with another problem, when i use the command  sudo lshw -C network the return is : 

```

 *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info:  pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:59:5b:1c
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg

```I really dont know what to do now... and i'm afraid of making a mess that i cant return.

Here's all other information that may be usefull:

```
cat /etc/modprobe.d/iwl3945
cat: /etc/modprobe.d/iwl3945: No such file or directory

``````
dmesg | grep iwl
[   18.253551] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   18.253556] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   18.253766] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   18.317551] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   18.334057] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   19.424608] iwl3945: Radio disabled by HW RF Kill switch
[   19.700013] iwl3945: Radio disabled by HW RF Kill switch
[   19.700655] iwl3945: Radio  disabled by HW RF Kill switch
[   24.892875] iwl3945: Radio disabled by HW RF Kill switch
[   30.918772] iwl3945: Radio disabled by HW RF Kill switch

``````
uname -a 
Linux neco 2.6.24-24-generic #1 SMP Wed Apr 15 15:54:25 UTC 2009 i686 GNU/Linux

``` ```
lspci  
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation  82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA  AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```Thanks all for hellping, i know that we have others posts about intel pro/wireless 3945abg problem but i didnt find one that the problem is close to this one.
:)

---

### Post by superprash2003 on 2009-06-08
hope this helps [http://ubuntuforums.org/showthread.php?t=820297](http://ubuntuforums.org/showthread.php?t=820297)

---

### Post by Daewoos on 2009-06-08
> **superprash2003 said:**
> hope this helps [http://ubuntuforums.org/showthread.php?t=820297](http://ubuntuforums.org/showthread.php?t=820297)

Thx a lot superprash2003 for fast aswer.

---

### Post by Daewoos on 2009-06-08
Hi,
superprash2003 the link that you send shows a problem but is not the same i have...at this post the user yosva describes the same problem i have and no one gave a solution.
Someone have any idea to help?

Thanks all.

---

### Post by chili555 on 2009-06-08
> [   30.918772] iwl3945: Radio disabled by HW RF Kill switchThere is a hardware switch somewhere on your laptop that is nudged to 'off;' find it and nudge it over to 'on' and you should be all set.

---

