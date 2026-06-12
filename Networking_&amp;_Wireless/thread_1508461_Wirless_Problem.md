---
title: "Wirless Problem"
date: 2010-06-13
forum: Networking &amp; Wireless
---

### Post by fidogenial on 2010-06-13
Hi all,
 
  My Ubuntu wirless internet connection keeps breaking (disconnected) and sometimes when it breaks it doesn't allow me to re-connect (it say connecting... forever....). How do i make it stable without breaking.... 
 
My computer network cards is  [FONT=monospace]Intel wireless card. Do i need to install any separate  drive for this ?

Thanks
fido



[/FONT]

---

### Post by pytheas22 on 2010-06-13
Please post the output of the following commands so we know exactly which type of wireless card you have, and I'll try to help:
```

lspci -nn
lshw -C Network
uname -rm
dmesg | grep -e iwl -e wlan
```

---

### Post by fidogenial on 2010-06-13
**-laptop:~$ lspci -nn**

00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
04:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
06:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
08:06.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
08:06.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
08:06.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
08:06.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
08:06.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)

**-laptop:~$ lshw -C Network**
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 02
       serial: 00:1b:77:xx:xx:xx
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:28 memory:f0000000-f0000fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: xx:xx:xx:xx:xx:xx
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.102 firmware=sb v3.04 ip=1xx.1xx.x.1xx latency=0 multicast=yes
       resources: irq:30 memory:b8000000-b800ffff

[B]-laptop:~$ uname -rm
[/B]
2.6.32-21-generic i686

**-laptop:~$ dmesg | grep -e iwl -e wlan**

[   20.255163] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   20.255168] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   20.255292] iwl3945 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.255308] iwl3945 0000:04:00.0: setting latency timer to 64
[   20.326746] iwl3945 0000:04:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   20.326751] iwl3945 0000:04:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   20.326912] iwl3945 0000:04:00.0: irq 28 for MSI/MSI-X
[   21.577884] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   22.322811] iwl3945 0000:04:00.0: firmware: requesting iwlwifi-3945-2.ucode
[   22.375213] iwl3945 0000:04:00.0: loaded firmware version 15.32.2.9
[   22.484091] Registered led device: iwl-phy0::radio
[   22.484116] Registered led device: iwl-phy0::assoc
[   22.484135] Registered led device: iwl-phy0::RX
[   22.484154] Registered led device: iwl-phy0::TX
[   22.490753] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   40.699789] wlan0: deauthenticating from 00:23:69:e0:d7:e9 by local choice (reason=3)
[   40.704950] wlan0: direct probe to AP 00:23:69:e0:d7:e9 (try 1)
[   40.709613] wlan0: direct probe responded
[   40.709618] wlan0: authenticate with AP 00:23:69:e0:d7:e9 (try 1)
[   40.711394] wlan0: authenticated
[   40.711419] wlan0: associate with AP 00:23:69:e0:d7:e9 (try 1)
[   40.714234] wlan0: RX AssocResp from 00:23:69:e0:d7:e9 (capab=0x411 status=0 aid=2)
[   40.714239] wlan0: associated
[   40.718091] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   51.016043] wlan0: no IPv6 routers present
[   51.333152] wlan0: deauthenticating from 00:23:69:e0:d7:e9 by local choice (reason=3)


******************************************************************************************************************************





> **pytheas22 said:**
> Please post the output of the following commands so we know exactly which type of wireless card you have, and I'll try to help:
```

lspci -nn
lshw -C Network
uname -rm
dmesg | grep -e iwl -e wlan
```

---

### Post by pytheas22 on 2010-06-13
Unfortunately there's no concrete explanation of what's wrong.  But updating the driver using more recent source code may help.  To do that, frst go to [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) and download the file named "compat-wireless-2.6.tar.bz2." Save it to your desktop.  Then run these commands:

```
sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
scripts/driver-select intel
make
sudo make unload
sudo make load
sudo make install
```

As long as you don't receive any error messages, reboot, and please see if the connection is more stable.

---

### Post by fidogenial on 2010-06-18
Hi 

Thanks for you suggestion. But now i am not able to connect to my wireless internet router.. it keep connecting for ever. How can reset so that it will start connecting to the internet...
thanks
fido 

> **pytheas22 said:**
> Unfortunately there's no concrete explanation of what's wrong.  But updating the driver using more recent source code may help.  To do that, frst go to [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) and download the file named "compat-wireless-2.6.tar.bz2." Save it to your desktop.  Then run these commands:

```
sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
scripts/driver-select intel
make
sudo make unload
sudo make load
sudo make install
```As long as you don't receive any error messages, reboot, and please see if the connection is more stable.

---

### Post by pytheas22 on 2010-06-18
I'm really sorry to hear that only made things worse.  You should be able to undo the changes made by the commands I told you to run by typing:
```

cd ~/Desktop/*compat-wireless*
sudo make uninstall
```

That will remove the updated drivers and replace them with the older ones, which apparently at least allowed you to connect for a little while.

Unfortunately I'm not really sure of anything else you might try to stabilize your connection, other than possibly changing the settings on your router.  Changing the wireless channel, mode or security type can sometimes help.

If you need help with that, or if you're still not able to connect to your router after removing the updated drivers, let me know.  If it's the case that you can't connect, please post the output of these commands so I'll know what's wrong:
```

lshw -C Network
sudo iwlist scan
locate iwl3945.ko
modinfo iwl3945
```

---

