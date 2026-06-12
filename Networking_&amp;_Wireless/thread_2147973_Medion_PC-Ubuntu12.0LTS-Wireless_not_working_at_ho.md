---
title: "Medion PC-Ubuntu12.0LTS-Wireless not working at home but it works using phone hot-spo"
date: 2013-05-23
forum: Networking &amp; Wireless
---

### Post by angelsinnuendo on 2013-05-23
Dear all, I hope you can help me with my problem:

Old MEDION pc, Ubuntu 12.04LTS Installed. During installation wireless was working.
After wireless is not working, I can connect, but it does not manage to charge any internet page in reasonable time.

I can ping without any problem.
When I do:
wget --output-document=/dev/null [http://speedtest.wdc01.softlayer.com/downloads/test500.zip](http://speedtest.wdc01.softlayer.com/downloads/test500.zip)
the given time for downloading is --.- 14 days or more.

If I use my phone hot-spot the wireless works perfectly, the same using the wireless connection of other people.

Any clue? Listed below some, maybe useful informations.

THANKS A LOT IN ADVANCE


PS: you will notice some weird charcters in the mac address part. These are shown as asiatic characters, that is 
another problem that should be solved but the most important one is the wireless! Thanks!

lspci
__________________
00:00.0 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: NVIDIA Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: NVIDIA Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: NVIDIA Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: NVIDIA Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: NVIDIA Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: NVIDIA Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: NVIDIA Corporation C51 [GeForce Go 6150] (rev a2)
00:09.0 RAM memory: NVIDIA Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: NVIDIA Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: NVIDIA Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: NVIDIA Corporation MCP51 PMU (rev a3)
00:0b.0 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: NVIDIA Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: NVIDIA Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: NVIDIA Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: NVIDIA Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: NVIDIA Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
________

 lsusb
_____

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0ace:1215 ZyDAS ZD1211B 802.11g
Bus 001 Device 004: ID 8644:800b

____

 ifconfig
______________________

eth0      Link encap:Ethernet  Hardware Adresse 00:16:d3:82:31:30  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          æŽ¥æ”¶æ•°æ®åŒ…:0 é”™è¯¯:0 ä¸¢å¼ƒ:0 è¿‡è½½:0 å¸§æ•°:0
          å‘é€æ•°æ®åŒ…:0 é”™è¯¯:0 ä¸¢å¼ƒ:0 è¿‡è½½:0 è½½æ³¢:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000 
          RX-Bytes:0 (0.0 B)  TX-Bytes:0 (0.0 B)
          Interrupt:20 Basisadresse:0x4000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 GÃ¼ltigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          æŽ¥æ”¶æ•°æ®åŒ…:291 é”™è¯¯:0 ä¸¢å¼ƒ:0 è¿‡è½½:0 å¸§æ•°:0
          å‘é€æ•°æ®åŒ…:291 é”™è¯¯:0 ä¸¢å¼ƒ:0 è¿‡è½½:0 è½½æ³¢:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:0 
          RX-Bytes:23541 (23.5 KB)  TX-Bytes:23541 (23.5 KB)

wlan0     Link encap:Ethernet  Hardware Adresse 00:60:b3:36:ee:3b  
          inet Adresse:192.168.178.34  Bcast:192.168.178.255  Maske:255.255.255.0
          inet6-Adresse: fe80::260:b3ff:fe36:ee3b/64 GÃ¼ltigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          æŽ¥æ”¶æ•°æ®åŒ…:1304 é”™è¯¯:0 ä¸¢å¼ƒ:0 è¿‡è½½:0 å¸§æ•°:0
          å‘é€æ•°æ®åŒ…:1116 é”™è¯¯:0 ä¸¢å¼ƒ:0 è¿‡è½½:0 è½½æ³¢:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000 
          RX-Bytes:1023693 (1.0 MB)  TX-Bytes:151125 (151.1 KB)

____

iwconfig

_____


lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"DieBesteWG"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 24:65:11:D4:EB:C7   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/100  Signal level=57/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:20  Invalid misc:9   Missed beacon:0

eth0      no wireless extensions.


____

 lsmod

____



Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   174313  1 
joydev                 17393  0 
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  0 
ppdev                  12849  0 
bluetooth             158479  10 rfcomm,bnep
arc4                   12473  2 
binfmt_misc            17292  1 
snd_hda_intel          32765  3 
nouveau               712674  3 
snd_hda_codec         109562  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
ttm                    65344  1 nouveau
drm_kms_helper         45466  1 nouveau
snd_seq_midi_event     14475  1 snd_seq_midi
drm                   197641  5 nouveau,ttm,drm_kms_helper
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12893  1 nouveau
snd                    62218  16 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                86520  0 
r852                   17901  0 
serio_raw              13027  0 
sm_common              16772  1 r852
r592                   17808  0 
nand                   49667  2 r852,sm_common
nand_ids                8547  1 nand
zd1211rw               57509  0 
mtd                    35584  2 sm_common,nand
memstick               15857  1 r592
mac80211              436493  1 zd1211rw
nand_bch               13003  1 nand
bch                    21784  1 nand_bch
nand_ecc               13105  1 nand
soundcore              14635  1 snd
k8temp                 12905  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
cfg80211              178877  2 zd1211rw,mac80211
nv_tco                 13399  0 
i2c_nforce2            12906  0 
wmi                    18744  1 mxm_wmi
video                  19068  1 nouveau
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
firewire_core          56940  1 firewire_ohci
sdhci_pci              18324  0 
usb_storage            39646  1 
uas                    17828  0 
crc_itu_t              12627  1 firewire_core
sdhci                  28241  1 sdhci_pci
forcedeth              58096  0 
sata_nv                23360  2 
pata_amd               13750  0 


_________________________________________

---

### Post by josephmills on 2013-05-23
could we see the output of 
```
rfkill list all
```

thanks

---

### Post by angelsinnuendo on 2013-05-24
Thank you for helping me, here it is

rfkill list all --->

1: phy1: Wireless LAN
            Soft blocked: no
            Hard blocked: no

---

### Post by jdthood on 2013-05-26
What's the output of

cat /etc/resolv.conf
cat /etc/NetworkManager/NetworkManager.conf
nm-tool|grep -i dns

---

### Post by angelsinnuendo on 2013-05-28
The output is:

cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1

cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

nm-tool|grep -i dns
    DNS:             139.7.30.126
    DNS:             139.7.30.125

---

### Post by jdthood on 2013-05-28
Can you ping 139.7.30.126 and 139.7.30.125?  Can you resolve hostnames with these nameservers, e.g., `dig @139.7.30.126 www.google.com`?

---

