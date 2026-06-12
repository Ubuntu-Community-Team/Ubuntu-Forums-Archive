---
title: "Wireless on Lenovo  SL 510  Not Working #urgent#"
date: 2012-07-12
forum: Networking &amp; Wireless
---

### Post by Abo El Nile on 2012-07-12
I have Laptop Lenovo  SL 510 i was using ubuntu version 10.10 after upgrading to version to version 11.4 the wireless stop working 

after running this code
"sudo lshw -C network; lsb_release -a; sudo rfkill list"

that was the result 

 *-network DISABLED      
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 00
       serial: 00:26:c7:13:36:ea
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-22-generic firmware=39.31.5.1 build 35138 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:48 memory:f2200000-f2201fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:26:9e:d9:a9:be
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:46 ioport:3000(size=256) memory:f2004000-f2004fff memory:f2000000-f2003fff memory:f2020000-f203ffff
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.10
Release:    11.10
Codename:    oneiric
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Thanks ;

---

### Post by chili555 on 2012-07-12
Please post:```
dmesg | grep iwl
```Thanks.

---

### Post by irv on 2012-07-12
I just ran across this link for someone else. It was on [Ask Ubuntu]("http://askubuntu.com/questions/tagged/lenovo"). Looks like others were having some issues also.

---

### Post by Abo El Nile on 2012-07-12
thanks for your fast response and i will try it and give you the feedback as soon as possible

thanks;

---

### Post by Abo El Nile on 2012-07-15
after run this code

dmesg | grep iwldmesg | grep iwl
[   15.292319] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   15.292323] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   15.292420] iwlagn 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   15.292429] iwlagn 0000:05:00.0: setting latency timer to 64
[   15.292465] iwlagn 0000:05:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   15.312226] iwlagn 0000:05:00.0: device EEPROM VER=0x15d, CALIB=0x6
[   15.312230] iwlagn 0000:05:00.0: Device SKU: 0X9
[   15.312232] iwlagn 0000:05:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   15.314676] iwlagn 0000:05:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   15.314766] iwlagn 0000:05:00.0: irq 48 for MSI/MSI-X
[   15.318548] iwlagn 0000:05:00.0: loaded firmware version 128.50.3.1 build 13488
[   15.328707] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'

Thanks;

---

### Post by chili555 on 2012-07-15
> **Abo El Nile said:**
> after run this code

dmesg | grep iwldmesg | grep iwl
[   15.292319] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   15.292323] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   15.292420] iwlagn 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   15.292429] iwlagn 0000:05:00.0: setting latency timer to 64
[   15.292465] iwlagn 0000:05:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   15.312226] iwlagn 0000:05:00.0: device EEPROM VER=0x15d, CALIB=0x6
[   15.312230] iwlagn 0000:05:00.0: Device SKU: 0X9
[   15.312232] iwlagn 0000:05:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   15.314676] iwlagn 0000:05:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   15.314766] iwlagn 0000:05:00.0: irq 48 for MSI/MSI-X
[   15.318548] iwlagn 0000:05:00.0: loaded firmware version 128.50.3.1 build 13488
[   15.328707] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'

Thanks;Man, that looks awesome! Nothing to fix here. Let's look at:```
rfkill list all
iwconfig
sudo iwlist wlan0 scan
```Thanks.

---

