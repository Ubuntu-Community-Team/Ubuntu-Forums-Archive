---
title: "Wireless cycling between connected and disconnected"
date: 2012-12-04
forum: Networking &amp; Wireless
---

### Post by amber95 on 2012-12-04
My friend has a  [SIZE=1][SIZE=2]Acer Aspire 5733Z-4851 it keeps disconnecting and conn[SIZE=2]ecting to his wifi but his hard wire will run just fine. An[SIZE=2]y [SIZE=2]sug[SIZE=2]gestio[SIZE=2]ns?[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]
All the codes:
lspci:
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
```lsmod:
```
Module                  Size  Used by
snd_seq_dummy          12798  0 
rfcomm                 46619  0 
bnep                   18140  2 
bluetooth             209199  10 rfcomm,bnep
parport_pc             32688  0 
ppdev                  17073  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
binfmt_misc            17500  1 
ums_realtek            17949  0 
snd_hda_codec_realtek    77876  1 
uas                    17844  0 
coretemp               13400  0 
snd_hda_intel          33491  4 
snd_hda_codec         134212  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
arc4                   12529  2 
snd_seq_device         14497  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                95552  0 
ath9k                 131308  0 
tg3                   148780  0 
snd                    78734  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
microcode              22803  0 
mac80211              539908  1 ath9k
ath9k_common           14055  1 ath9k
ath9k_hw              395218  2 ath9k,ath9k_common
ath                    23827  3 ath9k,ath9k_common,ath9k_hw
i915                  520629  3 
soundcore              15047  1 snd
serio_raw              13215  0 
cfg80211              206566  3 ath9k,mac80211,ath
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
intel_ips              18049  0 
lpc_ich                17061  0 
drm_kms_helper         46784  1 i915
drm                   275528  4 i915,drm_kms_helper
mei                    40690  0 
i2c_algo_bit           13413  1 i915
joydev                 17457  0 
acer_wmi               32453  0 
sparse_keymap          13890  1 acer_wmi
mxm_wmi                12979  0 
mac_hid                13205  0 
wmi                    19070  2 acer_wmi,mxm_wmi
video                  19335  2 i915,acer_wmi
usb_storage            48838  1 ums_realtek
```sudo lshw -C network:
```
*-network               
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: b8:70:f4:9a:35:b6
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 duplex=half firmware=sb latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 memory:d3400000-d340ffff[/QUOTE][QUOTE]*-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 68:a3:c4:eb:60:7d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-19-generic firmware=N/A ip=192.168.0.168 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d2400000-d240ffff)
```

---

### Post by howefield on 2012-12-08
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by amber95 on 2012-12-10
Bump, Now wireless at times will not work at all.

---

### Post by PapaNerd on 2012-12-10
Please post the output of these two commands:
ifconfig -a
route

---

### Post by amber95 on 2012-12-11
ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr b8:70:f4:9a:35:b6  
          inet addr:[192.168.0.150]("http://192.168.0.150")  Bcast:[192.168.0.255]("http://192.168.0.255")  Mask:[255.255.255.0]("http://255.255.255.0")
          inet6 addr: fe80::ba70:f4ff:fe9a:35b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4597 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3956 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4031799 (4.0 MB)  TX bytes:851293 (851.2 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:[127.0.0.1]("http://127.0.0.1")  Mask:[255.0.0.0]("http://255.0.0.0")
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5397 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5397 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:787770 (787.7 KB)  TX bytes:787770 (787.7 KB)

wlan0     Link encap:Ethernet  HWaddr 68:a3:c4:eb:60:7d  
          inet addr:[192.168.0.168]("http://192.168.0.168")  Bcast:[192.168.0.255]("http://192.168.0.255")  Mask:[255.255.255.0]("http://255.255.255.0")
          inet6 addr: fe80::6aa3:c4ff:feeb:607d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10959 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3940107 (3.9 MB)  TX bytes:1217096 (1.2 MB)
```

route
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         www             [0.0.0.0]("http://0.0.0.0")         UG    0      0        0 eth0
[169.254.0.0]("http://169.254.0.0")     *               [255.255.0.0]("http://255.255.0.0")     U     1000   0        0 wlan0
[192.168.0.0]("http://192.168.0.0")     *               [255.255.255.0]("http://255.255.255.0")   U     1      0        0 eth0
[192.168.0.0]("http://192.168.0.0")     *               [255.255.255.0]("http://255.255.255.0")   U     9      0        0 wlan0
```

---

### Post by PapaNerd on 2012-12-11
I really hate it when the inexpensive modems place both wireless and wired connections on the same subnet as it makes it difficult for a laptop to communicate unless good metrics are set.  End rant, sorry.

Suggest changing your default route for the wlan0 interface to an IP address instead of the "www" currently being used.  A geek would do this via the route command (run "man route" in a terminal window for the syntax).  It can also be set via "Network Connections" using the graphical interface.  You'll need to know the IP of the modem (192.168.0.1 is common for most vendors using this subnet).

---

### Post by amber95 on 2012-12-12
> **PapaNerd said:**
> I really hate it when the inexpensive modems place both wireless and wired connections on the same subnet as it makes it difficult for a laptop to communicate unless good metrics are set.  End rant, sorry.

Suggest changing your default route for the wlan0 interface to an IP address instead of the "www" currently being used.  A geek would do this via the route command (run "man route" in a terminal window for the syntax).  It can also be set via "Network Connections" using the graphical interface.  You'll need to know the IP of the modem (192.168.0.1 is common for most vendors using this subnet).

Ok so can you please tell me more "detail" on  how to do this please, I see the route button under the "Network Connections" and what do you mean the ip of the modem? the submask net for it?

---

### Post by amber95 on 2012-12-18
bump

---

### Post by amber95 on 2012-12-21
Bump

---

