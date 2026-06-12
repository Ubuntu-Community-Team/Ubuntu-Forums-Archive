---
title: "Intel Pro/wireless 3945ABG card"
date: 2011-05-27
forum: Networking &amp; Wireless
---

### Post by saulusoc on 2011-05-27
have been trying to get the wireless working on my lenovo 3000 n200 but all the stuff i have done have been fruitless, can someone please help before i toss the thing at the wall

---

### Post by josephmills on 2011-05-27
hi there and lets try to toss tomatoes at bad comedians and not computers at walls :) but could you please open your terminal (ctrl+alt+t) and type in ```
lspci -nn
``` and then ```
rfkill list all 
``` and then paste them here thanks

---

### Post by saulusoc on 2011-05-27
here is the read out for
 sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 02
       serial: 00:1c:bf:75:38:10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.38-8-generic firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:46 memory:f8000000-f8000fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:0c:a3:57
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=sb v3.03 ip=87.198.17.205 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:c8000000-c800ffff

---

### Post by saulusoc on 2011-05-27
hi mate, here you go
paul@paul-3000-N200:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 0c)
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
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
04:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)
06:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
08:06.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
08:06.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
08:06.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
08:06.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)
paul@paul-3000-N200:~$

---

### Post by saulusoc on 2011-05-27
and 

paul@paul-3000-N200:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
paul@paul-3000-N200:~$

---

### Post by josephmills on 2011-05-27
looks good so far! is this on a dual boot? do you have access to the net? this computer or a different one? and could we see a ```
lsmod 
``` and a ```
ifconfig -a 
``` you can **edit** your internet and mac address if you wish and the last one is ```
dmesg | grep iwl
``` thanks

---

### Post by saulusoc on 2011-05-27
Thanks for your quick reply joseph, not a dual boot just ubuntu 11.04, is connected via wired network
 

 lspci -nn 
 00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c) 
 00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 0c) 
 00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 0c) 
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
 00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03) 
 00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03) 
 00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03) 
 04:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02) 
 06:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02) 
 08:06.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] 
 08:06.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19) 
 08:06.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a) 
 08:06.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05) 
 paul@paul-3000-N200:~$ rfkill list all 
 0: phy0: Wireless LAN 
 	Soft blocked: no 
 	Hard blocked: no 
 paul@paul-3000-N200:~$ lsmod 
 Module                  Size  Used by 
 rfcomm                 38125  8  
 sco                    17779  2  
 bnep                   17785  2  
 l2cap                  48656  16 rfcomm,bnep 
 btusb                  18160  2  
 bluetooth              65565  9 rfcomm,sco,bnep,l2cap,btusb 
 parport_pc             32111  0  
 ppdev                  12849  0  
 joydev                 17322  0  
 snd_hda_codec_realtek   255820  1  
 snd_hda_intel          24140  2  
 snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel 
 snd_hwdep              13274  1 snd_hda_codec 
 snd_pcm                80244  2 snd_hda_intel,snd_hda_codec 
 arc4                   12473  2  
 snd_seq_midi           13132  0  
 snd_rawmidi            25269  1 snd_seq_midi 
 i915                  450944  3  
 snd_seq_midi_event     14475  1 snd_seq_midi 
 iwl3945               130113  0  
 snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event 
 binfmt_misc            13213  1  
 snd_timer              28659  2 snd_pcm,snd_seq 
 iwlcore               148965  1 iwl3945 
 r852                   17878  0  
 snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq 
 sm_common              16737  1 r852 
 nand                   49822  2 r852,sm_common 
 nand_ids                8547  1 nand 
 mac80211              257001  2 iwl3945,iwlcore 
 nand_ecc               13070  1 nand 
 psmouse                73312  0  
 mtd                    26720  2 sm_common,nand 
 drm_kms_helper         40745  1 i915 
 snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 serio_raw              12990  0  
 drm                   180037  4 i915,drm_kms_helper 
 cfg80211              156212  3 iwl3945,iwlcore,mac80211 
 soundcore              12600  1 snd 
 i2c_algo_bit           13184  1 i915 
 video                  18951  1 i915 
 snd_page_alloc         14073  2 snd_hda_intel,snd_pcm 
 lp                     13349  0  
 parport                36746  3 parport_pc,ppdev,lp 
 sdhci_pci              13623  0  
 ahci                   21591  2  
 tg3                   131476  0  
 firewire_ohci          31504  0  
 sdhci                  22720  1 sdhci_pci 
 firewire_core          56138  1 firewire_ohci 
 crc_itu_t              12627  1 firewire_core 
 libahci                25548  1 ahci 
 

 

 AND
 ifconfig -a 
 eth0      Link encap:Ethernet  HWaddr 00:1b:38:0c:a3:57   
           inet addr:87.198.17.205  Bcast:87.198.19.255  Mask:255.255.252.0 
           inet6 addr: fe80::21b:38ff:fe0c:a357/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:9955 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:8491 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:10328938 (10.3 MB)  TX bytes:1507654 (1.5 MB) 
           Interrupt:19  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:8 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:8 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B) 
  
 wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:75:38:10   
           BROADCAST MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
  
 AND
 

 dmesg | grep iwl 
 [   15.393348] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s 
 [   15.393353] iwl3945: Copyright(c) 2003-2010 Intel Corporation 
 [   15.393410] iwl3945 0000:04:00.0: sw scan support is deprecated 
 [   15.393439] iwl3945 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
 [   15.393455] iwl3945 0000:04:00.0: setting latency timer to 64 
 [   15.448926] iwl3945 0000:04:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels 
 [   15.448932] iwl3945 0000:04:00.0: Detected Intel Wireless WiFi Link 3945ABG 
 [   15.449092] iwl3945 0000:04:00.0: irq 46 for MSI/MSI-X 
 [   15.533884] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs' 
 [   15.632514] iwl3945 0000:04:00.0: loaded firmware version 15.32.2.9 
 [   15.632670] iwl3945 0000:04:00.0: Radio disabled by HW RF Kill switch 
 [   15.635130] iwl3945 0000:04:00.0: Radio disabled by HW RF Kill switch 
 [   40.073739] iwl3945 0000:04:00.0: Radio disabled by HW RF Kill switch

---

### Post by josephmills on 2011-05-27
```
iwlist scan 
``` thanks

---

### Post by saulusoc on 2011-05-27
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

thanks

---

### Post by josephmills on 2011-05-27
```
sudo ifup wlan0
``` then ```
sudo iwlist scan 
``` thanks

---

### Post by Joe of loath on 2011-05-27
You have to run the two above commands using sudo so that they will work.

---

### Post by josephmills on 2011-05-27
> **Joe of loath said:**
> You have to run the two above commands using sudo so that they will work.

thanks joe will edit now

---

### Post by josephmills on 2011-05-27
OHH NO I think that he threw it at the wall :roll:

---

