---
title: "WIFI not working on my HP Pavillion DV6500 running Ubuntu 12.04"
date: 2013-06-23
forum: Networking &amp; Wireless
---

### Post by seasalt8 on 2013-06-23
Hello, I am a new Ubuntu user. My HP notebook running Ubuntu 12.04 with the WIFI not working is not connected to the internet but I can transfer files via USB key from another computer that is connected to the internet.  After looking over some forum posts I am still not sure where to go to download the proper driver. Here is the latest output from my computer using terminal commands that I have seen other users post:jay@badkitty:~$ sudo lshw -C network
[sudo] password for jay: 
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:f4000000-f4003fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:24:dd:90:68
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:c000(size=256) memory:f8200000-f8200fff memory:80000000-8001ffff
jay@badkitty:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 0c)
00:1a.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 03)
00:1d.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
02:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
07:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
07:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
07:09.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
07:09.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
jay@badkitty:~$  rfkill list all
0: hp-wifi: Wireless LAN
 Soft blocked: no
 Hard blocked: no
jay@badkitty:~$ 
any help would be much appreciated!!

---

### Post by Hadaka on 2013-06-23
Hi, please post the output of..
```
lsmod
```
thanks.

---

### Post by praseodym on 2013-06-23
Hi,

install the package **linux-firmware-nonfree** via cable connection.

---

### Post by seasalt8 on 2013-06-23
[EMAIL="jay@badkitty:~$"]jay@badkitty:~$[/EMAIL] lsmod
Module                  Size  Used by
nls_iso8859_1          12618  0 
cdc_acm                22416  0 
usb_storage            39720  0 
joydev                 17394  0 
coretemp               13362  0 
hp_wmi                 13653  0 
sparse_keymap          13659  1 hp_wmi
snd_hda_codec_si3054    12865  1 
snd_hda_codec_realtek    64876  1 
parport_pc             32115  0 
rfcomm                 38104  0 
ppdev                  12850  0 
bnep                   17791  2 
bluetooth             189585  10 rfcomm,bnep
microcode              18396  0 
r852                   17906  0 
sm_common              16773  1 r852
nand                   49703  2 r852,sm_common
nand_ids                8548  1 nand
mtd                    38671  2 sm_common,nand
nand_bch               13004  1 nand
bch                    21768  1 nand_bch
nand_ecc               13106  1 nand
r592                   17809  0 
memstick               15886  1 r592
psmouse                91022  0 
serio_raw              13032  0 
lpc_ich                16993  0 
snd_hda_intel          33029  3 
snd_hda_codec         116477  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13277  1 snd_hda_codec
snd_pcm                81124  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25426  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
b43                   351489  0 
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
wmi                    18745  1 hp_wmi
mac80211              475488  1 b43
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13078  0 
snd                    62675  16 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              181041  2 b43,mac80211
soundcore              14636  1 snd
ssb_hcd                12782  0 
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
bcma                   34573  1 b43
i915                  470823  3 
drm_kms_helper         47459  1 i915
drm                   240232  4 i915,drm_kms_helper
i2c_algo_bit           13317  1 i915
video                  19070  1 i915
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
firewire_ohci          36110  0 
sdhci_pci              18263  0 
firewire_core          61957  1 firewire_ohci
crc_itu_t              12628  1 firewire_core
sdhci                  32293  1 sdhci_pci
r8169                  56853  0 
ssb                    50757  2 b43,ssb_hcd

---

### Post by seasalt8 on 2013-06-23
Thanks praseodym. I am new to both Ubuntu and Linux. I don't have a cable connection. Is it possible to download the package you recommend and an install manager if needed and put them both on my USB storage flash drive and use it to move them to the computer running Ubuntu then install off the package off the flash drive?

---

### Post by praseodym on 2013-06-23
Here it is:

[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.11_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.11_all.deb)

Install via double click

---

### Post by seasalt8 on 2013-06-23
Thanks again praseodym. I was able to get that file on my Ubuntu computer's hardrive desktop. When I double clicked on it the Ubuntu Software Center opened and identified the file and had an Install button. However the Install button is not active - It is somewhat greyed out and nothing happens when I click on it.  If this would be much easier to do with a cable connection to the internet I can wait a few days and try this at a friend's house but any additional advise on how to proceed using a USB flash drive would be appreciated.  Thanks!

---

### Post by praseodym on 2013-06-24
Save the file to "Downloads" and install it via:
```

sudo dpkg -i ~/Downloads/*.deb
```

---

### Post by Bucky Ball on 2013-06-24
Just wondering if it might be worth checking what is actually happening:

```
sudo lshw -C network
```

Is there anything installed already? Have you checked 'Additional Hardware'? Yes, all of this would be done in a flash with a connection to the net (no pun intended) and probably be installed automagically with a couple of clicks required from you. ;)

---

### Post by seasalt8 on 2013-06-28
Hi! thanks for your help. i am writing this from my Ubuntu computer. I ended up installing 13.04 and it had the drivers included for my WIFI card to work from the innitial install.

---

### Post by Bucky Ball on 2013-06-28
Great. Please mark thread as solved to help others by following the link in my signature.

---

