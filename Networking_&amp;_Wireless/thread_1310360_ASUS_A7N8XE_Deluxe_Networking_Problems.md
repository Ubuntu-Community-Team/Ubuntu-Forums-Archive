---
title: "ASUS A7N8XE Deluxe Networking Problems"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by devnull on 2009-11-01
Hello,

I'm having some problems with the on-board NICs on my motherboard while using Ubuntu 9.10.  Both are gigabit capable, but I am unable to get them to auto-negotiate properly with my Netgear WNDR3700 router.  After some toying around with ethtool and mii-tool, I have been unsuccessful in getting either NIC to manually run at 1000baseT/Full.  Also disturbing, the second NIC claims to not even support it when using ethtool.

Here is the output of a few different commands to hopefully help you kind souls out:

```
gabriel@itachi:~$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pg
	Wake-on: g
	Current message level: 0x00000037 (55)
	Link detected: yes
```


```
gabriel@itachi:~$ sudo mii-tool -vv eth0
Using SIOCGMIIPHY=0x8947
eth0: negotiated 100baseTx-FD flow-control, link ok
  registers for MII PHY 0: 
    1000 796d 0141 0c25 0de1 4de1 0007 2001
    4393 0300 4000 0000 0000 0000 0000 3000
    0068 6d6c c480 0000 0170 0000 0000 0000
    4105 0008 000a 848f 0000 0000 0000 0000
  product info: Yukon 88E1011 rev 5
  basic mode:   autonegotiation enabled
  basic status: autonegotiation complete, link ok
  capabilities: 1000baseT-HD 1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control
  link partner: 1000baseT-HD 1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control
```

```
gabriel@itachi:~$ sudo ethtool eth1
Settings for eth1:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: d
	Link detected: yes
```

```
gabriel@itachi:~$ sudo mii-tool -vv eth1
Using SIOCGMIIPHY=0x8947
SIOCGMIIPHY on 'eth1' failed: Operation not supported
```

```
gabriel@itachi:~$ sudo lspci -vv
...
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 80a7
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (250ns min, 5000ns max)
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at e9086000 (32-bit, non-prefetchable) [size=4K]
	Region 1: I/O ports at e000 [size=8]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable+ DSel=0 DScale=0 PME-
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth
...
01:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
	Subsystem: ASUSTeK Computer Inc. Device 811a
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (5750ns min, 7750ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at e8020000 (32-bit, non-prefetchable) [size=16K]
	Region 1: I/O ports at 8000 [size=256]
	[virtual] Expansion ROM at 40080000 [disabled] [size=128K]
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-
	Capabilities: [50] Vital Product Data <?>
	Kernel driver in use: skge
	Kernel modules: skge
...
```

```
gabriel@itachi:~$ sudo lsmod
Module                  Size  Used by
cbc                     3516  317 
aes_i586                8124  318 
aes_generic            27484  1 aes_i586
binfmt_misc             8356  1 
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
snd_wavefront          37332  0 
snd_cs4236             29620  0 
snd_wss_lib            26012  2 snd_wavefront,snd_cs4236
snd_opl3_lib           10396  2 snd_wavefront,snd_cs4236
snd_intel8x0           30168  2 
snd_hwdep               7200  2 snd_wavefront,snd_opl3_lib
snd_mpu401              7016  0 
snd_mpu401_uart         6940  3 snd_wavefront,snd_cs4236,snd_mpu401
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_seq_dummy           2656  0 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  5 snd_cs4236,snd_wss_lib,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_oss            28576  0 
arc4                    1660  2 
ecb                     2524  3 
snd_seq_midi            6432  0 
iptable_filter          3100  0 
ppdev                   6688  0 
lp                      8964  0 
snd_rawmidi            22208  3 snd_wavefront,snd_mpu401_uart,snd_seq_midi
b43legacy             117752  0 
ip_tables              11692  1 iptable_filter
parport_pc             31940  1 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
mac80211              181236  1 b43legacy
x_tables               16544  1 ip_tables
parport                35340  3 ppdev,lp,parport_pc
dm_crypt               12928  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ns558                   5404  0 
cfg80211               93052  2 b43legacy,mac80211
snd_timer              22276  4 snd_wss_lib,snd_opl3_lib,snd_pcm,snd_seq
led_class               4096  1 b43legacy
snd_seq_device          6920  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_nforce2             6784  0 
gameport               11368  2 ns558
serio_raw               5280  0 
snd                    59204  21 snd_wavefront,snd_cs4236,snd_wss_lib,snd_opl3_lib,snd_intel8x0,snd_hwdep,snd_mpu401,snd_mpu401_uart,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 32272  0 
soundcore               7264  1 snd
snd_page_alloc          9156  3 snd_wss_lib,snd_intel8x0,snd_pcm
b44                    28684  0 
mii                     5212  1 b44
usbhid                 38208  0 
ssb                    35300  2 b43legacy,b44
skge                   39180  0 
nvidia_agp              6200  1 
floppy                 54916  0 
forcedeth              54152  0 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
agpgart                34988  3 ttm,drm,nvidia_agp
```

The router is brand new, so this is the first time I've had an opportunity to run at gigabit speeds from my desktop, so unfortunately I can't tell you this has worked in the past.

---

### Post by devnull on 2009-11-01
Here is some more output:

```
gabriel@itachi:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth1
       version: a1
       serial: 00:11:2f:56:1f:34
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:21 memory:e9086000-e9086fff ioport:e000(size=8)
  *-network:0
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 4
       bus info: pci@0000:01:04.0
       logical name: eth0
       version: 13
       serial: 00:11:2f:56:25:74
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=full firmware=N/A ip=192.168.1.5 latency=32 link=yes maxlatency=31 mingnt=23 multicast=yes port=twisted pair speed=100MB/s
       resources: irq:17 memory:e8020000-e8023fff ioport:8000(size=256) memory:40080000-4009ffff(prefetchable)
  *-network:1
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:18 memory:e8024000-e8025fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:06:25:0a:5a:a0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b
```

---

### Post by devnull on 2009-11-02
Well, after further reading it appears to be a driver problem with my Marvell 88E8001.  Looks like I have to patch my kernel according to some other posts I've stumbled across, but not a single one has actually done it successfully it seems.

---

