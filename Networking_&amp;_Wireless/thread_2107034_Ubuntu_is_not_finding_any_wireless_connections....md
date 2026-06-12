---
title: "Ubuntu is not finding any wireless connections..."
date: 2013-01-20
forum: Networking &amp; Wireless
---

### Post by collinbrown13 on 2013-01-20
Hi there!
I'm a new user to the linux world. I am currently working through my Mac right now.
I need Help getting Ubuntu to find any WiFi!

This is going to be asked so here's what I think you need...

Code: sudo lshw -C network
```
[sudo] password for collinbrown: 
PCI (sysfs)  

  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:c0200000-c0203fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:ac:8c:5f
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:21 memory:c0300000-c0301fff 
```

Code: lspci  -nnk | grep -iA2 net
```
 05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
	Kernel driver in use: b43-pci-bridge
--
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Dell Device [1028:01f5]
	Kernel driver in use: b44
collinbrown@ubuntu:~$ lspci -nnk | grep -iA2 net
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
	Kernel driver in use: b43-pci-bridge
--
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Dell Device [1028:01f5]
	Kernel driver in use: b44
 
```

Code: iwconfig
```
 lo        no wireless extensions.

eth0      no wireless extensions. 
```

Code: rfkill list all
```
 0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no 
```

Code: lsmod
```
 Module                  Size  Used by
rfcomm                 47604  0 
bnep                   18281  2 
parport_pc             32866  0 
ppdev                  17113  0 
bluetooth             180104  10 rfcomm,bnep
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
b44                    36276  0 
ssb                    52752  1 b44
radeon                804372  3 
joydev                 17693  0 
wl                   2568210  0 
ttm                    76949  1 radeon
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
drm_kms_helper         46978  1 radeon
drm                   242038  5 radeon,ttm,drm_kms_helper
dell_laptop            18119  0 
dcdbas                 14490  1 dell_laptop
snd_hda_codec_idt      70795  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
i2c_algo_bit           13423  1 radeon
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
psmouse                87692  0 
edac_core              53746  0 
snd_timer              29990  2 snd_pcm,snd_seq
serio_raw              13211  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
edac_mce_amd           23709  0 
k8temp                 13057  0 
snd                    78855  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    19256  1 dell_wmi
lib80211               14381  1 wl
sp5100_tco             13791  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_piix4              13301  0 
shpchp                 37277  0 
video                  19596  0 
mac_hid                13253  0 
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
pata_atiixp            13204  0 
```

Code: sudo cat /var/log/syslog | grep -e b43 -e wl -e firmware -e wlan0 | tail -n35
```
 Jan 20 16:51:56 ubuntu kernel: [    5.854652] b43-pci-bridge 0000:05:00.0: setting latency timer to 64
Jan 20 16:51:56 ubuntu kernel: [   51.155449] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
Jan 20 16:51:56 ubuntu kernel: [   51.594596] Registered led device: b43-phy0::tx
Jan 20 16:51:56 ubuntu kernel: [   51.594634] Registered led device: b43-phy0::rx
Jan 20 16:51:56 ubuntu kernel: [   51.594663] Registered led device: b43-phy0::radio
Jan 20 16:52:03 ubuntu NetworkManager[1779]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:06.0/0000:05:00.0/ssb0:0/net/wlan0, iface: wlan0)
Jan 20 16:52:03 ubuntu NetworkManager[1779]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:06.0/0000:05:00.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan 20 16:52:03 ubuntu NetworkManager[1779]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan 20 16:52:03 ubuntu NetworkManager[1779]: <info> (wlan0): using nl80211 for WiFi device control
Jan 20 16:52:03 ubuntu NetworkManager[1779]: <warn> (wlan0): driver supports Access Point (AP) mode
Jan 20 16:52:03 ubuntu NetworkManager[1779]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Jan 20 16:52:03 ubuntu NetworkManager[1779]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan 20 16:52:03 ubuntu NetworkManager[1779]: <info> (wlan0): now managed
Jan 20 16:52:03 ubuntu NetworkManager[1779]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan 20 16:52:03 ubuntu NetworkManager[1779]: <info> (wlan0): bringing up device.
Jan 20 16:52:03 ubuntu NetworkManager[1779]: <warn> (wlan0): firmware may be missing.
Jan 20 16:52:03 ubuntu NetworkManager[1779]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jan 20 16:52:03 ubuntu kernel: [   58.208595] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
Jan 20 16:52:03 ubuntu kernel: [   58.208601] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
Jan 20 16:52:03 ubuntu kernel: [   58.208606] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
Jan 20 16:52:03 ubuntu kernel: [   58.208924] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 20 16:59:47 ubuntu avahi-daemon[1662]: Withdrawing workstation service for wlan0.
Jan 20 16:59:47 ubuntu NetworkManager[1779]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:06.0/0000:05:00.0/ssb0:0/net/wlan0, iface: wlan0)
Jan 20 16:59:47 ubuntu NetworkManager[1779]: <info> (wlan0): now unmanaged
Jan 20 16:59:47 ubuntu NetworkManager[1779]: <info> (wlan0): device state change: unavailable -> unmanaged (reason 'removed') [20 10 36]
Jan 20 17:11:48 ubuntu kernel: [ 1242.348219] b43-pci-bridge 0000:05:00.0: PCI INT A disabled
Jan 20 17:11:48 ubuntu kernel: [ 1242.431499] wl: module license 'MIXED/Proprietary' taints kernel.
Jan 20 17:11:48 ubuntu kernel: [ 1242.476133] wl 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jan 20 17:11:48 ubuntu kernel: [ 1242.476154] wl 0000:05:00.0: setting latency timer to 64
Jan 20 17:11:48 ubuntu kernel: [ 1242.492759] b43-pci-bridge 0000:05:00.0: setting latency timer to 64
Jan 20 17:14:14 ubuntu kernel: [   26.718226] wl: module license 'MIXED/Proprietary' taints kernel.
Jan 20 17:14:14 ubuntu kernel: [   26.734715] wl 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jan 20 17:14:14 ubuntu kernel: [   26.734726] wl 0000:05:00.0: setting latency timer to 64
Jan 20 17:14:14 ubuntu kernel: [   27.024057] b43-pci-bridge 0000:05:00.0: setting latency timer to 64
Jan 20 17:14:15 ubuntu NetworkManager[819]: <info> monitoring kernel firmware directory '/lib/firmware'. 
```

Thank you guys for any help you can provide, hope we can get this solved! :D

---

### Post by chili555 on 2013-01-20
We can get it solved pretty easily. Please get a temporary wired ethernet connection and do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r wl
sudo modprobe -r b43 && sudo modprobe b43
```Is it working now?

---

### Post by joco1500 on 2013-01-20
you could just reinstall

---

### Post by collinbrown13 on 2013-01-20
HEY chili555 that worked! Thank you!
joco1500 Sorry I guess I didn't think about that.

---

### Post by chili555 on 2013-01-20
> **collinbrown13 said:**
> HEY chili555 that worked! Thank you!
Glad it's working.Please use thread tools at the top to mark Solved.

---

