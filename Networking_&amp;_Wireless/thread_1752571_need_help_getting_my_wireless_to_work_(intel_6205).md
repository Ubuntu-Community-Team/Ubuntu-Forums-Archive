---
title: "need help getting my wireless to work (intel 6205)"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by swirve47 on 2011-05-08
I just got my brand new computer and have installed Ubuntu 10.10 (because my research led me to believe that my wireless card was compatible with kernel 2.6.35 and later).  As indicated in the title of this thread, I am unfortunately still having trouble getting the wireless up and running.  This is my first experience with Linux, so i'm not sure if this thread would be better served in the "Absolute beginners" forum...  

I have found another thread where the OP possessed the same card as I do and was able to get it working by downloading "compat-wireless", then building/installing it.  I followed all of the steps in that thread (including d/l the compat-wireless) but to no avail.  I am not sure, however, that I was able to follow the instructions of the build/install when working with the compat-wireless correctly.  Specifically, I wasn't sure if i was supposed to go all the way to an "Unload" instruction b/c it didn't immediately follow "Build" and "install".  Anyway, you can find that thread here: [http://ubuntuforums.org/showthread.php?t=1739047](http://ubuntuforums.org/showthread.php?t=1739047) (compat-wireless suggestion on pg. 3)  

Anyway, thank you in advance for any assistance you might provide in this matter.  Below, I have compiled all of the information recommended.  Please don't hesitate to let me know if there is any other information that I can provide!  

----------------------------------------------------------------------------------

**1 ) Machine Brand and Model (PC/Laptop)**:

Lenovo Thinkpad T520

[B]2 ) Wireless Brand, Model and Wireless Chipset:
[/B]
Intel Centrino Advanced-N 6205 (There is a wireless switch present and it is enabled...Windows is able to utilize the wireless card just fine)

$ lspci:

00:00.0 Host bridge: Intel Corporation Sandy Bridge DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation Cougar Point KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b4)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 5 (rev b4)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Cougar Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 04)
03:00.0 Network controller: Intel Corporation 6000 Series Gen2 (rev 34)
0d:00.0 System peripheral: Ricoh Co Ltd Device e823 (rev 05)
0d:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832 (rev 04)

[B]3 ) check interface: 

[/B]$ ifconfig:

eth0      Link encap:Ethernet  HWaddr f0:de:f1:59:97:d9  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f2de:f1ff:fe59:97d9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3924 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5036694 (5.0 MB)  TX bytes:676792 (676.7 KB)
          Interrupt:20 Memory:d2600000-d2620000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

$iwconfig:

ian@ian-ThinkPad-T520:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

**4 ) Check for modules:**

$ lsmod:
...
iwlagn                317401  0 
mac80211              290733  1 iwlagn
cfg80211              174836  2 iwlagn,mac80211
...

[B]5 ) Kernel boot messages

[/B]$ dmesg:
...
[   13.724236] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   13.724238] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   13.724495] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.724533] iwlagn 0000:03:00.0: setting latency timer to 64
[   13.724638] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[   13.735332] iwlagn 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[   13.735334] iwlagn 0000:03:00.0: Device SKU: 0Xb
[   13.735336] iwlagn 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[   13.735352] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   13.735552]   alloc irq_desc for 47 on node -1
[   13.735553]   alloc kstat_irqs on node -1
[   13.735622] iwlagn 0000:03:00.0: irq 47 for MSI/MSI-X
[   13.784294] iwlagn 0000:03:00.0: request for firmware file 'iwlwifi-6000g2a-5.ucode' failed.
[   13.785295] iwlagn 0000:03:00.0: request for firmware file 'iwlwifi-6000g2a-4.ucode' failed.
[   13.785329] iwlagn 0000:03:00.0: no suitable firmware found!
[   13.785574] iwlagn 0000:03:00.0: PCI INT A disabled
...

[B]6 ) Network configuration

[/B]$ sudo lshw -C network

 *-network               
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: f0:de:f1:59:97:d9
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k4 duplex=full firmware=0.13-3 ip=192.168.1.65 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:44 memory:d2600000-d261ffff memory:d262b000-d262bfff ioport:5080(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: 6000 Series Gen2
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:d2500000-d2501fff

[B]7 ) Scan for networks:

[/B]$ iwlist scan:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

[B]8 ) Ubuntu Version: 

[/B]Ubuntu 10.10

[B]9 ) Kernel/architecture (including 32 vs. 64 bit): 

[/B]2.6.35-22-generic x86_64

[B]10 ) Restarting the network:

[/B]$ sudo /etc/init.d/networking restart: * Reconfiguring network interfaces...                                          
Ignoring unknown interface eth0=eth0.


----------------------------------------------------------------------------------

---

### Post by chili555 on 2011-05-08
I think compat-wireless is the solution. Please walk us through the process; especially show us where you think it fails. I believe, in your case, Unload is needed.

---

### Post by swirve47 on 2011-05-08
Okay, so the first step is to download the compat-wireless and open it with archive manager.  From there, you extract the files.  I am assuming that this is all that needs to be done with the files outside of Terminal, so I then open a Terminal window to begin following the instructions on the webpage.  

1) The first instruction is to build the wireless subsystem:

ian@ian-ThinkPad-T520:~/compat-wireless-2011-03-31$ make

make -C /lib/modules/2.6.35-22-generic/build M=/home/ian/compat-wireless-2011-03-31 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  Building modules, stage 2.
  MODPOST 105 modules
WARNING: "wl12xx_get_platform_data" [/home/ian/compat-wireless-2011-03-31/drivers/net/wireless/wl1251/wl1251_sdio.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'

2) Then, I follow the install instruction:

ian@ian-ThinkPad-T520:~/compat-wireless-2011-03-31$ sudo make install

Your old wireless subsystem modules were left intact:

kernel/net/mac80211/mac80211.ko
kernel/net/wireless/cfg80211.ko
kernel/net/wireless/lib80211.ko
kernel/drivers/net/wireless/adm8211.ko
kernel/drivers/net/wireless/ath/ar9170/ar9170usb.ko
kernel/drivers/net/wireless/at76c50x-usb.ko
kernel/drivers/net/wireless/ath/ath.ko
kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
kernel/drivers/net/wireless/b43/b43.ko
kernel/drivers/net/wireless/b43legacy/b43legacy.ko
kernel/drivers/net/b44.ko
kernel/drivers/net/usb/cdc_ether.ko
kernel/drivers/misc/eeprom/eeprom_93cx6.ko
kernel/drivers/net/wireless/ipw2x00/ipw2100.ko
kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
kernel/drivers/net/wireless/iwlwifi/iwlcore.ko
kernel/drivers/net/wireless/iwmc3200wifi/iwmc3200wifi.ko
kernel/net/wireless/lib80211_crypt_ccmp.ko
kernel/net/wireless/lib80211_crypt_tkip.ko
kernel/net/wireless/lib80211_crypt_wep.ko
kernel/drivers/net/wireless/libertas/libertas.ko
kernel/drivers/net/wireless/libertas/libertas_cs.ko
kernel/drivers/net/wireless/libertas/libertas_sdio.ko
kernel/drivers/net/wireless/libertas/libertas_spi.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
kernel/drivers/net/wireless/ipw2x00/libipw.ko
kernel/drivers/net/wireless/mac80211_hwsim.ko
kernel/drivers/net/wireless/mwl8k.ko
kernel/drivers/net/wireless/orinoco/orinoco_cs.ko
kernel/drivers/net/wireless/orinoco/orinoco_nortel.ko
kernel/drivers/net/wireless/orinoco/orinoco_plx.ko
kernel/drivers/net/wireless/orinoco/orinoco_usb.ko
kernel/drivers/net/wireless/orinoco/orinoco.ko
kernel/drivers/net/wireless/p54/p54common.ko
kernel/drivers/net/wireless/p54/p54pci.ko
kernel/drivers/net/wireless/p54/p54spi.ko
kernel/drivers/net/wireless/p54/p54usb.ko
kernel/drivers/net/usb/rndis_host.ko
kernel/drivers/net/wireless/rndis_wlan.ko
kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
kernel/drivers/net/wireless/rt2x00/rt61pci.ko
kernel/drivers/net/wireless/rt2x00/rt73usb.ko
kernel/drivers/net/wireless/rtl818x/rtl8180.ko
kernel/drivers/net/wireless/rtl818x/rtl8187.ko
kernel/drivers/net/wireless/orinoco/spectrum_cs.ko
kernel/drivers/ssb/ssb.ko
kernel/drivers/net/wireless/libertas/usb8xxx.ko
kernel/drivers/net/usb/usbnet.ko
kernel/drivers/net/wireless/wl12xx/wl1251.ko
kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko

Your old ethernet subsystem modules are left intact:

kernel/drivers/net/atlx/atl1.ko
kernel/drivers/net/atlx/atl2.ko
kernel/drivers/net/atl1e/atl1e.ko
kernel/drivers/net/atl1c/atl1c.ko

Your old bluetooth subsystem modules were left intact:

updates/drivers/bluetooth/ath3k.ko
...
kernel/net/bluetooth/sco.ko

make -C /lib/modules/2.6.35-22-generic/build M=/home/ian/compat-wireless-2011-03-31 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  Building modules, stage 2.
  MODPOST 105 modules
WARNING: "wl12xx_get_platform_data" [/home/ian/compat-wireless-2011-03-31/drivers/net/wireless/wl1251/wl1251_sdio.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make -C /lib/modules/2.6.35-22-generic/build M=/home/ian/compat-wireless-2011-03-31 "INSTALL_MOD_DIR=updates"  \
        modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  INSTALL /home/ian/compat-wireless-2011-03-31/compat/compat.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/compat/kfifo.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/bluetooth/ath3k.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/bluetooth/bcm203x.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/bluetooth/bfusb.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/bluetooth/bluecard_cs.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/bluetooth/bpa10x.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/bluetooth/bt3c_cs.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/bluetooth/btmrvl.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/bluetooth/btmrvl_sdio.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/bluetooth/btsdio.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/bluetooth/btuart_cs.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/bluetooth/btusb.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/bluetooth/dtl1_cs.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/bluetooth/hci_uart.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/bluetooth/hci_vhci.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/misc/eeprom/eeprom_93cx6.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/atl1c/atl1c.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/atl1e/atl1e.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/atlx/atl1.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/atlx/atl2.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/b44.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/usb/cdc_ether.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/usb/rndis_host.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/usb/usbnet.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/adm8211.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/at76c50x-usb.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/ath/ar9170/ar9170usb.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/ath/ath.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/ath/ath5k/ath5k.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/ath/ath9k/ath9k.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/ath/ath9k/ath9k_common.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/ath/carl9170/carl9170.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/b43/b43.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/b43legacy/b43legacy.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/ipw2x00/ipw2100.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/ipw2x00/ipw2200.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/ipw2x00/libipw.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/iwlegacy/iwl-legacy.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/iwlegacy/iwl3945.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/iwlegacy/iwl4965.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/iwlwifi/iwlagn.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/iwmc3200wifi/iwmc3200wifi.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/libertas/libertas.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/libertas/libertas_cs.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/libertas/libertas_sdio.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/libertas/libertas_spi.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/libertas/usb8xxx.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/libertas_tf/libertas_tf.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/mac80211_hwsim.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/mwl8k.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/orinoco/orinoco.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/orinoco/orinoco_cs.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/orinoco/orinoco_nortel.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/orinoco/orinoco_pci.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/orinoco/orinoco_plx.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/orinoco/orinoco_tmd.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/orinoco/orinoco_usb.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/orinoco/spectrum_cs.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/p54/p54common.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/p54/p54pci.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/p54/p54spi.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/p54/p54usb.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/rndis_wlan.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/rt2x00/rt2400pci.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/rt2x00/rt2500pci.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/rt2x00/rt2500usb.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/rt2x00/rt2800lib.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/rt2x00/rt2800pci.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/rt2x00/rt2800usb.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/rt2x00/rt2x00lib.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/rt2x00/rt2x00pci.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/rt2x00/rt2x00usb.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/rt2x00/rt61pci.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/rt2x00/rt73usb.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/rtl818x/rtl8180/rtl8180.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/rtlwifi/rtlwifi.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/wl1251/wl1251.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/wl1251/wl1251_sdio.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/wl1251/wl1251_spi.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/wl12xx/wl12xx.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/wl12xx/wl12xx_spi.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/net/wireless/zd1211rw/zd1211rw.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/ssb/ssb.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/staging/ath6kl/ath6kl.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/staging/brcm80211/brcmfmac/brcmfmac.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/drivers/staging/brcm80211/brcmsmac/brcmsmac.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/net/bluetooth/bluetooth.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/net/bluetooth/bnep/bnep.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/net/bluetooth/cmtp/cmtp.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/net/bluetooth/hidp/hidp.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/net/bluetooth/rfcomm/rfcomm.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/net/mac80211/mac80211.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/net/wireless/cfg80211.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/net/wireless/lib80211.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/net/wireless/lib80211_crypt_ccmp.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/net/wireless/lib80211_crypt_tkip.ko
  INSTALL /home/ian/compat-wireless-2011-03-31/net/wireless/lib80211_crypt_wep.ko
  DEPMOD  2.6.35-22-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
Updating Ubuntu's initramfs for 2.6.35-22-generic under /boot/ ...
Will now run update-grub to ensure grub will find the new initramfs ...
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
depmod will prefer updates/ over kernel/ -- OK!

Currently detected wireless subsystem modules:

updates/net/mac80211/mac80211.ko
updates/net/wireless/cfg80211.ko
updates/net/wireless/lib80211.ko
updates/drivers/net/wireless/adm8211.ko
updates/drivers/net/wireless/ath/ar9170/ar9170usb.ko
updates/drivers/net/wireless/at76c50x-usb.ko
updates/drivers/net/wireless/ath/ath.ko
updates/drivers/net/wireless/ath/ath5k/ath5k.ko
updates/drivers/staging/ath6kl/ath6kl.ko
updates/drivers/net/wireless/ath/ath9k/ath9k.ko
updates/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
updates/drivers/net/wireless/b43/b43.ko
updates/drivers/net/wireless/b43legacy/b43legacy.ko
updates/drivers/net/b44.ko
updates/drivers/net/wireless/ath/carl9170/carl9170.ko
updates/drivers/net/usb/cdc_ether.ko
updates/drivers/misc/eeprom/eeprom_93cx6.ko
updates/drivers/net/wireless/ipw2x00/ipw2100.ko
updates/drivers/net/wireless/ipw2x00/ipw2200.ko
updates/drivers/net/wireless/iwlegacy/iwl3945.ko
updates/drivers/net/wireless/iwlwifi/iwlagn.ko
kernel/drivers/net/wireless/iwlwifi/iwlcore.ko
updates/drivers/net/wireless/iwmc3200wifi/iwmc3200wifi.ko
updates/net/wireless/lib80211_crypt_ccmp.ko
updates/net/wireless/lib80211_crypt_tkip.ko
updates/net/wireless/lib80211_crypt_wep.ko
updates/drivers/net/wireless/libertas/libertas.ko
updates/drivers/net/wireless/libertas/libertas_cs.ko
updates/drivers/net/wireless/libertas/libertas_sdio.ko
updates/drivers/net/wireless/libertas/libertas_spi.ko
updates/drivers/net/wireless/libertas_tf/libertas_tf.ko
updates/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
updates/drivers/net/wireless/ipw2x00/libipw.ko
updates/drivers/net/wireless/mac80211_hwsim.ko
updates/drivers/net/wireless/mwl8k.ko
updates/drivers/net/wireless/orinoco/orinoco_cs.ko
updates/drivers/net/wireless/orinoco/orinoco_nortel.ko
updates/drivers/net/wireless/orinoco/orinoco_pci.ko
updates/drivers/net/wireless/orinoco/orinoco_plx.ko
updates/drivers/net/wireless/orinoco/orinoco_usb.ko
updates/drivers/net/wireless/orinoco/orinoco.ko
updates/drivers/net/wireless/p54/p54common.ko
updates/drivers/net/wireless/p54/p54pci.ko
updates/drivers/net/wireless/p54/p54spi.ko
updates/drivers/net/wireless/p54/p54usb.ko
updates/drivers/net/usb/rndis_host.ko
updates/drivers/net/wireless/rndis_wlan.ko
updates/drivers/net/wireless/rt2x00/rt2400pci.ko
updates/drivers/net/wireless/rt2x00/rt2500pci.ko
updates/drivers/net/wireless/rt2x00/rt2500usb.ko
updates/drivers/net/wireless/rt2x00/rt2800pci.ko
updates/drivers/net/wireless/rt2x00/rt2800usb.ko
updates/drivers/net/wireless/rt2x00/rt2x00lib.ko
updates/drivers/net/wireless/rt2x00/rt2x00pci.ko
updates/drivers/net/wireless/rt2x00/rt2x00usb.ko
updates/drivers/net/wireless/rt2x00/rt61pci.ko
updates/drivers/net/wireless/rt2x00/rt73usb.ko
updates/drivers/net/wireless/rtl818x/rtl8180/rtl8180.ko
updates/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko
updates/drivers/net/wireless/rtlwifi/rtlwifi.ko
updates/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
updates/drivers/net/wireless/orinoco/spectrum_cs.ko
updates/drivers/ssb/ssb.ko
updates/drivers/net/wireless/libertas/usb8xxx.ko
updates/drivers/net/usb/usbnet.ko
updates/drivers/net/wireless/wl1251/wl1251.ko
updates/drivers/net/wireless/wl12xx/wl12xx.ko
updates/drivers/net/wireless/zd1211rw/zd1211rw.ko

Currently detected ethernet subsystem modules:

updates/drivers/net/atlx/atl1.ko
updates/drivers/net/atlx/atl2.ko
updates/drivers/net/atl1e/atl1e.ko
updates/drivers/net/atl1c/atl1c.ko

Currently detected bluetooth subsystem modules:

updates/drivers/bluetooth/ath3k.ko
...
kernel/net/bluetooth/sco.ko

Now run:

sudo make unload to unload all: wireless, bluetooth and ethernet modules
sudo make wlunload to unload wireless modules
sudo make btunload to unload bluetooth modules

Run sudo modprobe driver-name to load your desired driver.
If unsure reboot.

3) I then attempt to unload all existing mac80211 and related drivers:

ian@ian-ThinkPad-T520:~/compat-wireless-2011-03-31$ sudo make unload

Stoping bluetooth service..
 * bluetooth is not running
Unloading iwlagn...

4) Finally, I reboot the system and check the wireless.  Unfortunately, it still does not work.  I'm sure that I am doing something wrong with these instructions, or missing something in Terminal but I just don't know what it is.  

Thanks so much for your help with this issue!

---

### Post by chili555 on 2011-05-08
I don't see anything wrong so far. Let's do a bit of diagnostics:```
sudo modprobe iwlagn
dmesg | grep iwl
modinfo iwlagn
```Thanks.

---

### Post by swirve47 on 2011-05-08
Okay, 

**$ sudo modprobe iwlagn:**

it asks me for my password, but then nothing. no response.

**$ dmesg | grep iwl:**

[   19.623355] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   19.623361] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   19.623604] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.623660] iwlagn 0000:03:00.0: setting latency timer to 64
[   19.623828] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[   19.634995] iwlagn 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[   19.634997] iwlagn 0000:03:00.0: Device SKU: 0Xb
[   19.634999] iwlagn 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[   19.635020] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   19.635323] iwlagn 0000:03:00.0: irq 47 for MSI/MSI-X
[   19.694301] iwlagn 0000:03:00.0: request for firmware file 'iwlwifi-6000g2a-5.ucode' failed.
[   19.695376] iwlagn 0000:03:00.0: request for firmware file 'iwlwifi-6000g2a-4.ucode' failed.
[   19.695409] iwlagn 0000:03:00.0: no suitable firmware found!
[   19.695725] iwlagn 0000:03:00.0: PCI INT A disabled

**$ modinfo iwlagn:**

ERROR: modinfo: could not find module iwlgan

---

### Post by jawilljr on 2011-05-08
Here is your problem:

```
[ 19.694301] iwlagn 0000:03:00.0: request for firmware file 'iwlwifi-6000g2a-5.ucode' failed.
[ 19.695376] iwlagn 0000:03:00.0: request for firmware file 'iwlwifi-6000g2a-4.ucode' failed.
[ 19.695409] iwlagn 0000:03:00.0: no suitable firmware found!
```

Please post output of:

```
ll /lib/firmware/iwl*
```

Jerry

---

### Post by swirve47 on 2011-05-08
Hey, Jerry.

yeah, i saw those lines.  Here is the response to $ ll /lib/firmware/iwl*:

-rw-r--r-- 1 root root 335056 2010-08-16 15:02 /lib/firmware/iwlwifi-1000-3.ucode
-rw-r--r-- 1 root root 150100 2010-08-16 15:02 /lib/firmware/iwlwifi-3945-2.ucode
-rw-r--r-- 1 root root 187972 2010-08-16 15:02 /lib/firmware/iwlwifi-4965-2.ucode
-rw-r--r-- 1 root root 345008 2010-08-16 15:02 /lib/firmware/iwlwifi-5000-1.ucode
-rw-r--r-- 1 root root 353240 2010-08-16 15:02 /lib/firmware/iwlwifi-5000-2.ucode
-rw-r--r-- 1 root root 337400 2010-08-16 15:02 /lib/firmware/iwlwifi-5150-2.ucode
-rw-r--r-- 1 root root 454608 2010-08-16 15:02 /lib/firmware/iwlwifi-6000-4.ucode
-rwxr-xr-x 1 root root 463692 2010-08-16 15:02 /lib/firmware/iwlwifi-6050-4.ucode*

---

### Post by jawilljr on 2011-05-08
It doesn't look like you have the firmware install... no problem, down load [this file from Intel](http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6000g2a-ucode-17.168.5.2.tgz)

The you have to untar it:

```
cd /path/to/download
```

then:

```
tar xzvf iwlwifi-6000g2a-ucode-17.168.5.2.tgz
```

Then:

```
cd iwlwifi-6000g2a-ucode-17.168.5.2
```

And finally:

```
sudo cp iwlwifi-6000g2a-5.ucode /lib/firmware
```

After that do these:

```
sudo rmmod iwlagn
```
```
sudo modprobe iwlagn
```

or just reboot

hope this helps...

Jerry

---

### Post by swirve47 on 2011-05-08
Hey, 

cd /path/to/download:

no such directory exists.....

I opened the download with archive manager and extracted the files using that application.  it is now in the /home/ian directory.  was that wrong?

---

### Post by jawilljr on 2011-05-08
This command:

```
cd /path/to/download:
```

Is generic... of course I do not know where you downloaded the file to.

But this sound like it is your home directory:

```
/home/ian
```

Just open terminal in your home directory then begin with this command:

```
tar xzvf iwlwifi-6000g2a-ucode-17.168.5.2.tgz
```

And do the rest.

Jerry

---

### Post by swirve47 on 2011-05-08
Okay, so i figured out that to untar IS to extract...

So, 

sudo cp iwlwifi-6000g2a-5.ucode /lib/firmware
gives no response.

---

### Post by jawilljr on 2011-05-08
> **swirve47 said:**
> Okay, so i figured out that to untar IS to extract...

So, 

sudo cp iwlwifi-6000g2a-5.ucode /lib/firmware
**gives no response.**

Good that means it probably copied correctly.

Now do this again.

```
ll /lib/firmware
```

If that file is there then just reboot.... and hopefully it works.

Jerry

---

### Post by swirve47 on 2011-05-08
IT'S ALIIIIIIIIIIIIIIIIIIIIIIIIIIVE!!! 

Jerry, we have confirmation of wireless liftoff!  Thank you so much for helping me out with this.  I really appreciate it!.

---

### Post by jawilljr on 2011-05-08
No problem... please test it for a while, and when you are satisfied, please mark as solved.

Jerry

---

### Post by swirve47 on 2011-05-08
Now, I don't see anywhere that enables me to mark this thread as [solved]....

---

### Post by jawilljr on 2011-05-09
[heres how](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6)

Jerry

---

