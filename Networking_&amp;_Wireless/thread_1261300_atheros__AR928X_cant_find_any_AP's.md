---
title: "atheros  AR928X cant find any AP's"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by jyoungjr on 2009-09-08
hey guys,

i know, im the 1 billionth person to try and get this card to work. it seems everything is working except that i cant find any access points. 

i am running ubuntu jaunty. i am using WICD as my network manager.

jeff@jeff-laptop:~$ lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 9600M GS [10de:0648] (rev a1)
03:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
09:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
09:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
09:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
09:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)

jeff@jeff-laptop:~$ lshw -C Network

WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:15:af:dd:96:35
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:22:15:36:99:75
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.114 latency=0 module=r8169 multicast=yes
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 0e:f6:1c:bc:b5:69
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

jeff@jeff-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.


jeff@jeff-laptop:~$ sudo selfdestruct

i tried compat-wireless, ndiswrapper, and other things. and when i use that script in other posts that builds you a package it tells me i wont do it because the version is too old. and apparently the new one doesnt work out for people. 

will appreciate any help
-Jeff

---

### Post by jyoungjr on 2009-09-08
now i really broke it. tried to reinstall compat drivers after a failed attemp from another thread.

jeff@jeff-laptop:~/Desktop/compat-wireless-2.6.31-rc7$ sudo make load
Unloading ipw2100...
Unloading ipw2200...
Unloading usb8xxx...
Unloading at76_usb...
Unloading rndis_host...
Unloading eeprom_93cx6...
Loading ipw2100...
Loading ipw2200...
Loading libertas_cs...
FATAL: Error inserting libertas_cs (/lib/modules/2.6.28-15-generic/updates/libertas_cs.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading usb8xxx...
Loading p54pci...
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting p54common (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/p54/p54common.ko): Invalid module format
FATAL: Error inserting p54pci (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/p54/p54pci.ko): Invalid module format
Loading p54usb...
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting p54common (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/p54/p54common.ko): Invalid module format
FATAL: Error inserting p54usb (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/p54/p54usb.ko): Invalid module format
Loading adm8211...
WARNING: Error inserting eeprom_93cx6 (/lib/modules/2.6.28-15-generic/updates/eeprom_93cx6.ko): Invalid module format
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting adm8211 (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/adm8211.ko): Invalid module format
Loading zd1211rw...
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting zd1211rw (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/zd1211rw/zd1211rw.ko): Invalid module format
Loading rtl8180...
WARNING: Error inserting eeprom_93cx6 (/lib/modules/2.6.28-15-generic/updates/eeprom_93cx6.ko): Invalid module format
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting rtl8180 (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rtl818x/rtl8180.ko): Invalid module format
Loading rtl8187...
WARNING: Error inserting eeprom_93cx6 (/lib/modules/2.6.28-15-generic/updates/eeprom_93cx6.ko): Invalid module format
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting rtl8187 (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rtl818x/rtl8187.ko): Invalid module format
Loading p54pci...
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting p54common (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/p54/p54common.ko): Invalid module format
FATAL: Error inserting p54pci (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/p54/p54pci.ko): Invalid module format
Loading p54usb...
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting p54common (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/p54/p54common.ko): Invalid module format
FATAL: Error inserting p54usb (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/p54/p54usb.ko): Invalid module format
Loading iwl3945...
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting iwlcore (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/iwlwifi/iwlcore.ko): Invalid module format
FATAL: Error inserting iwl3945 (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/iwlwifi/iwl3945.ko): Invalid module format
Loading iwlagn...
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting iwlcore (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/iwlwifi/iwlcore.ko): Invalid module format
FATAL: Error inserting iwlagn (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/iwlwifi/iwlagn.ko): Invalid module format
Loading ath...
FATAL: Error inserting ath (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/ath/ath.ko): Invalid module format
Loading ar9170usb...
FATAL: Module ar9170usb not found.
Loading rtl8180...
WARNING: Error inserting eeprom_93cx6 (/lib/modules/2.6.28-15-generic/updates/eeprom_93cx6.ko): Invalid module format
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting rtl8180 (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rtl818x/rtl8180.ko): Invalid module format
Loading rtl8187...
WARNING: Error inserting eeprom_93cx6 (/lib/modules/2.6.28-15-generic/updates/eeprom_93cx6.ko): Invalid module format
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting rtl8187 (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rtl818x/rtl8187.ko): Invalid module format
Loading rt2400pci...
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rt2x00/rt2x00lib.ko): Invalid module format
WARNING: Error inserting rt2x00pci (/lib/modules/2.6.28-15-generic/updates/rt2x00pci.ko): Invalid module format
FATAL: Error inserting rt2400pci (/lib/modules/2.6.28-15-generic/updates/rt2400pci.ko): Invalid module format
Loading rt2500pci...
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rt2x00/rt2x00lib.ko): Invalid module format
WARNING: Error inserting rt2x00pci (/lib/modules/2.6.28-15-generic/updates/rt2x00pci.ko): Invalid module format
FATAL: Error inserting rt2500pci (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rt2x00/rt2500pci.ko): Invalid module format
Loading rt61pci...
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rt2x00/rt2x00lib.ko): Invalid module format
WARNING: Error inserting rt2x00pci (/lib/modules/2.6.28-15-generic/updates/rt2x00pci.ko): Invalid module format
WARNING: Error inserting crc_itu_t (/lib/modules/2.6.28-15-generic/kernel/lib/crc-itu-t.ko): Invalid module format
FATAL: Error inserting rt61pci (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rt2x00/rt61pci.ko): Invalid module format
Loading rt2500usb...
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting input_polldev (/lib/modules/2.6.28-15-generic/kernel/drivers/input/input-polldev.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rt2x00/rt2x00lib.ko): Invalid module format
WARNING: Error inserting rt2x00usb (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rt2x00/rt2x00usb.ko): Invalid module format
FATAL: Error inserting rt2500usb (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rt2x00/rt2500usb.ko): Invalid module format
Loading rt73usb...
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting input_polldev (/lib/modules/2.6.28-15-generic/kernel/drivers/input/input-polldev.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rt2x00/rt2x00lib.ko): Invalid module format
WARNING: Error inserting rt2x00usb (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rt2x00/rt2x00usb.ko): Invalid module format
WARNING: Error inserting crc_itu_t (/lib/modules/2.6.28-15-generic/kernel/lib/crc-itu-t.ko): Invalid module format
FATAL: Error inserting rt73usb (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rt2x00/rt73usb.ko): Invalid module format
Loading rndis_wlan...
FATAL: Error inserting rndis_wlan (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/rndis_wlan.ko): Invalid module format
Loading at76_usb...
Loading mwl8k...
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting mwl8k (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/mwl8k.ko): Invalid module format
Loading mac80211_hwsim...
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting mac80211_hwsim (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/mac80211_hwsim.ko): Invalid module format
Loading at76c50x_usb...
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting at76c50x_usb (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/at76c50x-usb.ko): Invalid module format
Module ath_pci not detected -- this is fine
WARNING: Error inserting ath (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/ath/ath.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting ath5k (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/ath/ath5k/ath5k.ko): Invalid module format
ath5k loaded successfully
WARNING: Error inserting ath (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/ath/ath.ko): Invalid module format
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting ath9k (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko): Invalid module format
ath9k loaded successfully
Module bcm43xx not detected -- this is fine
Module wl not detected -- this is fine
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting pcmcia (/lib/modules/2.6.28-15-generic/kernel/drivers/pcmcia/pcmcia.ko): Invalid module format
WARNING: Error inserting ssb (/lib/modules/2.6.28-15-generic/updates/drivers/ssb/ssb.ko): Invalid module format
FATAL: Error inserting b43 (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/b43/b43.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting pcmcia_core (/lib/modules/2.6.28-15-generic/kernel/drivers/pcmcia/pcmcia_core.ko): Invalid module format
WARNING: Error inserting pcmcia (/lib/modules/2.6.28-15-generic/kernel/drivers/pcmcia/pcmcia.ko): Invalid module format
WARNING: Error inserting ssb (/lib/modules/2.6.28-15-generic/updates/drivers/ssb/ssb.ko): Invalid module format
FATAL: Error inserting b43legacy (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/b43legacy/b43legacy.ko): Invalid module format
b43 loaded successfully
b43legacy loaded successfully

jeff@jeff-laptop:~/Desktop/compat-wireless-2.6.31-rc7$ sudo lshw -C Network
  *-network UNCLAIMED     
       description: Network controller
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:22:15:36:99:75
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.114 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 2e:7d:78:3b:3a:8e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


getting ready to give up,
-Jeff

---

