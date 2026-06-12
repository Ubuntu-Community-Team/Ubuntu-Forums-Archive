---
title: "Can't use wireless conection (Intel 3945ABG) in 11.04"
date: 2011-09-20
forum: Networking &amp; Wireless
---

### Post by lucasrato on 2011-09-20
Guys, i'm having a lot a trouble to get this working... my wireless card is activated but it says it's hardware blocked and i can't connect. when i use 
rfkill list all i get
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

and then dmesg | grep iwl
```
[   18.122734] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   18.122739] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[   18.122828] iwl3945 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   18.122844] iwl3945 0000:05:00.0: setting latency timer to 64
[   18.169877] iwl3945 0000:05:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   18.169883] iwl3945 0000:05:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   18.170039] iwl3945 0000:05:00.0: irq 44 for MSI/MSI-X
[   18.211920] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'

```

note: i'm pretty noob in this matter... i used this commends reading another thread here but it did nos solved my problem..

could anybody help?

---

### Post by lucasrato on 2011-09-20
commends = commands

---

### Post by praseodym on 2011-09-20
Please show:

```
iwconfig
sudo iwlist scan
iwlist chan
lsmod
dmesg | egrep 'radio|switch|iwl|wmi'
```
You may check your BIOS settings, if wifi can be activated there; or reset the BIOS to manufacturer settings. What kind of computer/note-/netbook is that?

---

### Post by lucasrato on 2011-09-20
my bad, it's a notebook HP Pavilion dv2250

i didn't find any option referring to wireless conection on the BIOS but i can try reseting it ( how do i do that?)

showing what the terminal returned
for iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

for sudo iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

```

for iwlist chan
```
lo        no frequency information.

eth0      no frequency information.

wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz

```

for lsmod
```
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_conexant    43782  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
i915                  451033  3 
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
joydev                 17322  0 
snd_seq_midi           13132  0 
uvcvideo               66851  0 
binfmt_misc            13213  1 
drm_kms_helper         40745  1 i915
snd_rawmidi            25269  1 snd_seq_midi
videodev               75143  1 uvcvideo
hp_wmi                 13418  0 
snd_seq_midi_event     14475  1 snd_seq_midi
r852                   17878  0 
sparse_keymap          13666  1 hp_wmi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
sm_common              16737  1 r852
drm                   184164  4 i915,drm_kms_helper
nand                   49822  2 r852,sm_common
snd_timer              28659  2 snd_pcm,snd_seq
psmouse                73312  0 
nand_ids                8547  1 nand
nand_ecc               13070  1 nand
i2c_algo_bit           13184  1 i915
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              12990  0 
mtd                    26720  2 sm_common,nand
arc4                   12473  2 
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
iwl3945               126017  0 
video                  18951  1 i915
iwlcore               148964  1 iwl3945
mac80211              257001  2 iwl3945,iwlcore
cfg80211              156212  3 iwl3945,iwlcore,mac80211
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
sdhci_pci              13623  0 
firewire_core          56138  1 firewire_ohci
e100                   40108  0 
sdhci                  22720  1 sdhci_pci
ahci                   21591  2 
crc_itu_t              12627  1 firewire_core
libahci                25548  1 ahci

```

and for the last command
```
[    0.313030] wmi: Mapper loaded
[   18.187719] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   18.187724] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[   18.187808] iwl3945 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   18.187824] iwl3945 0000:05:00.0: setting latency timer to 64
[   18.228353] iwl3945 0000:05:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   18.228358] iwl3945 0000:05:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   18.228516] iwl3945 0000:05:00.0: irq 44 for MSI/MSI-X
[   18.279497] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   19.679171] Console: switching to colour frame buffer device 160x50

```

---

### Post by josephmills on 2011-09-20
I think I see what is going on here but could we please see a ```
lspci -nn
``` thanks

---

### Post by lucasrato on 2011-09-20
sure, for lspci -nn i got
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
05:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
08:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 02)
08:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
08:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
08:09.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
08:09.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05
```

---

### Post by lucasrato on 2011-09-21
Anybody?? Plese help me!!!

---

### Post by lucasrato on 2011-09-21
guys, using more /var/lib/NetworkManager/NetworkManager.state i get
```
[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true

```

any ideas?

---

### Post by praseodym on 2011-09-21
```
gksudo gedit /var/lib/NetworkManager/NetworkManager.state
```
change "false" in "true", save, close and restart the network:

```
sudo service network-manager restart
```

---

### Post by chili555 on 2011-09-21
I hope this may be helpful: [http://ubuntuforums.org/showthread.php?t=1837729](http://ubuntuforums.org/showthread.php?t=1837729)> sudo servcie network-manager restartHe means servi**[COLOR="Red"]c[/COLOR]**e.

---

