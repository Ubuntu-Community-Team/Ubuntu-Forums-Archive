---
title: "Can't connect wifi with bcm4301"
date: 2012-01-25
forum: Networking &amp; Wireless
---

### Post by Pierrot86 on 2012-01-25
Hi,

First of all I'm sorry for my bad English.

My problem is that on Lubuntu 11.10, I can't connect to wifi. First, Network Manager said that firmware was missing. So I installed firmware-b43legacy-installer. Now, I can see the different network, but when I try to connect, it asks for password, and finally it never connects.

If someone could help me :)

Thanks a lot !

---

### Post by praseodym on 2012-01-25
Hi,

please show the outputs of:

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
dmesg | grep b43
sudo iwlist scan
rfkill list
```

---

### Post by Pierrot86 on 2012-01-26
> **praseodym said:**
> Hi,

please show the outputs of:

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
dmesg | grep b43
sudo iwlist scan
rfkill list
```

lspci -nnk | grep -iA2 net
```
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139]
	Kernel driver in use: 8139too
--
02:02.0 Network controller [0280]: Broadcom Corporation BCM4301 802.11b Wireless LAN Controller [14e4:4301] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:12f3]
	Kernel driver in use: b43-pci-bridge

```

lsmod
```
Module                  Size  Used by
joydev                 17393  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
ppdev                  12849  0 
zram                   18007  1 
snd_intel8x0           33318  1 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
nouveau               663226  3 
snd_pcm                80435  2 snd_intel8x0,snd_ac97_codec
arc4                   12473  2 
snd_seq_midi           13132  0 
pcmcia                 39822  0 
snd_rawmidi            25241  1 snd_seq_midi
b43legacy             131930  0 
ttm                    65224  1 nouveau
drm_kms_helper         32889  1 nouveau
mac80211              393459  1 b43legacy
drm                   192194  5 nouveau,ttm,drm_kms_helper
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
cfg80211              172427  2 b43legacy,mac80211
psmouse                73673  0 
snd_timer              28932  2 snd_pcm,snd_seq
i2c_algo_bit           13199  1 nouveau
serio_raw              12990  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
mxm_wmi                12859  1 nouveau
snd                    55902  9 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
k8temp                 12905  0 
shpchp                 32356  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
wmi                    18744  1 mxm_wmi
i2c_nforce2            12906  0 
parport_pc             32114  1 
video                  18908  1 nouveau
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
8139too                23283  0 
8139cp                 22636  0 
ssb                    50682  1 b43legacy
pata_amd               13753  2 

```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

dmesg | grep b43
```
[    1.903082] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNK3] -> GSI 17 (level, low) -> IRQ 17
[   18.473014] b43legacy-phy0: Broadcom 4301 WLAN found
[   18.496202] b43legacy-phy0 debug: Found PHY: Analog 0, Type 1, Revision 4
[   18.496225] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   18.520086] b43legacy-phy0 debug: Radio initialized
[   21.672319] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   21.844323] b43legacy-phy0 debug: Chip initialized
[   21.844580] b43legacy-phy0 debug: 30-bit DMA initialized
[   21.847946] Registered led device: b43legacy-phy0::tx
[   21.849771] Registered led device: b43legacy-phy0::rx
[   21.849839] Registered led device: b43legacy-phy0::radio
[   21.849886] b43legacy-phy0 debug: Wireless interface started
[   21.865088] b43legacy-phy0: Radio hardware status changed to DISABLED
[   21.865097] b43legacy-phy0 debug: Radio initialized
[   21.868823] b43legacy-phy0 debug: Adding Interface type 2
[   22.012045] b43legacy-phy0: Radio turned on by software
[   22.012051] b43legacy-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[   22.013077] b43legacy-phy0 debug: Removing Interface type 2
[   22.013119] b43legacy-phy0 debug: Wireless interface stopped
[   22.013300] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[   22.013348] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[   22.013397] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[   22.020093] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[   22.028056] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[   22.036039] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[   22.044037] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[   22.052040] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[   22.061164] b43legacy-phy0 debug: Radio initialized
[   22.061174] b43legacy-phy0 debug: Radio initialized
[   26.832457] b43legacy-phy0: Radio hardware status changed to ENABLED
[   26.988056] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   27.052309] b43legacy-phy0 debug: Chip initialized
[   27.052550] b43legacy-phy0 debug: 30-bit DMA initialized
[   27.055797] Registered led device: b43legacy-phy0::tx
[   27.057591] Registered led device: b43legacy-phy0::rx
[   27.057660] Registered led device: b43legacy-phy0::radio
[   27.057697] b43legacy-phy0 debug: Wireless interface started
[   27.072076] b43legacy-phy0 debug: Adding Interface type 2
[   27.412039] b43legacy-phy0 ERROR: MAC suspend failed
[   31.824050] b43legacy-phy0: Radio hardware status changed to DISABLED
[   31.824059] b43legacy-phy0 debug: Radio initialized
[   31.826447] b43legacy-phy0 debug: Removing Interface type 2
[   31.826491] b43legacy-phy0 debug: Wireless interface stopped
[   31.826672] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[   31.826717] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[   31.826766] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[   31.832065] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[   31.840059] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[   31.848046] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[   31.856038] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[   31.864039] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[   31.872034] b43legacy-phy0 debug: Radio initialized
[   31.872044] b43legacy-phy0 debug: Radio initialized
[   36.832067] b43legacy-phy0: Radio hardware status changed to ENABLED
[   36.988038] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   37.056311] b43legacy-phy0 debug: Chip initialized
[   37.056549] b43legacy-phy0 debug: 30-bit DMA initialized
[   37.059795] Registered led device: b43legacy-phy0::tx
[   37.061634] Registered led device: b43legacy-phy0::rx
[   37.061702] Registered led device: b43legacy-phy0::radio
[   37.061740] b43legacy-phy0 debug: Wireless interface started
[   37.068079] b43legacy-phy0 debug: Adding Interface type 2
[   41.824051] b43legacy-phy0: Radio hardware status changed to DISABLED
[   41.824060] b43legacy-phy0 debug: Radio initialized
[   41.828953] b43legacy-phy0 debug: Removing Interface type 2
[   41.828997] b43legacy-phy0 debug: Wireless interface stopped
[   41.829179] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[   41.829225] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[   41.829274] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[   41.836269] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[   41.844049] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[   41.852037] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[   41.860035] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[   41.868035] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[   41.876036] b43legacy-phy0 debug: Radio initialized
[   41.876045] b43legacy-phy0 debug: Radio initialized
[   46.832062] b43legacy-phy0: Radio hardware status changed to ENABLED
[   46.988051] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   47.056306] b43legacy-phy0 debug: Chip initialized
[   47.056546] b43legacy-phy0 debug: 30-bit DMA initialized
[   47.059791] Registered led device: b43legacy-phy0::tx
[   47.061627] Registered led device: b43legacy-phy0::rx
[   47.061699] Registered led device: b43legacy-phy0::radio
[   47.061737] b43legacy-phy0 debug: Wireless interface started
[   47.068079] b43legacy-phy0 debug: Adding Interface type 2
[   47.408041] b43legacy-phy0 ERROR: MAC suspend failed
[   51.824042] b43legacy-phy0: Radio hardware status changed to DISABLED
[   51.824050] b43legacy-phy0 debug: Radio initialized
[   51.834668] b43legacy-phy0 debug: Removing Interface type 2
[   51.834711] b43legacy-phy0 debug: Wireless interface stopped
[   51.836146] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[   51.836195] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[   51.836244] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[   51.844062] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[   51.852039] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[   51.860037] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[   51.868041] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[   51.876037] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[   51.884036] b43legacy-phy0 debug: Radio initialized
[   51.884045] b43legacy-phy0 debug: Radio initialized
[   56.832063] b43legacy-phy0: Radio hardware status changed to ENABLED
[   56.988050] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   57.056307] b43legacy-phy0 debug: Chip initialized
[   57.056546] b43legacy-phy0 debug: 30-bit DMA initialized
[   57.059797] Registered led device: b43legacy-phy0::tx
[   57.061686] Registered led device: b43legacy-phy0::rx
[   57.061755] Registered led device: b43legacy-phy0::radio
[   57.061792] b43legacy-phy0 debug: Wireless interface started
[   57.076077] b43legacy-phy0 debug: Adding Interface type 2
[   57.416040] b43legacy-phy0 ERROR: MAC suspend failed
[   61.824043] b43legacy-phy0: Radio hardware status changed to DISABLED
[   61.824052] b43legacy-phy0 debug: Radio initialized
[   61.829970] b43legacy-phy0 debug: Removing Interface type 2
[   61.830013] b43legacy-phy0 debug: Wireless interface stopped
[   61.831383] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[   61.831432] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[   61.831479] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[   61.836117] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[   61.844052] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[   61.852044] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[   61.860037] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[   61.868036] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[   61.876035] b43legacy-phy0 debug: Radio initialized
[   61.876044] b43legacy-phy0 debug: Radio initialized
[   66.832067] b43legacy-phy0: Radio hardware status changed to ENABLED
[   66.988052] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   67.056310] b43legacy-phy0 debug: Chip initialized
[   67.056549] b43legacy-phy0 debug: 30-bit DMA initialized
[   67.059817] Registered led device: b43legacy-phy0::tx
[   67.061682] Registered led device: b43legacy-phy0::rx
[   67.061755] Registered led device: b43legacy-phy0::radio
[   67.061792] b43legacy-phy0 debug: Wireless interface started
[   67.068080] b43legacy-phy0 debug: Adding Interface type 2
[   67.408048] b43legacy-phy0 ERROR: MAC suspend failed
[   71.824079] b43legacy-phy0: Radio hardware status changed to DISABLED
[   71.824090] b43legacy-phy0 debug: Radio initialized
[   71.829125] b43legacy-phy0 debug: Removing Interface type 2
[   71.836073] b43legacy-phy0 debug: Wireless interface stopped
[   71.841730] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[   71.841777] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[   71.841823] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[   71.848056] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[   71.856043] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[   71.864036] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[   71.872035] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[   71.880035] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[   71.888038] b43legacy-phy0 debug: Radio initialized
[   71.888048] b43legacy-phy0 debug: Radio initialized
[   76.832080] b43legacy-phy0: Radio hardware status changed to ENABLED
[   76.988066] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   77.056309] b43legacy-phy0 debug: Chip initialized
[   77.056556] b43legacy-phy0 debug: 30-bit DMA initialized
[   77.060920] Registered led device: b43legacy-phy0::tx
[   77.062523] Registered led device: b43legacy-phy0::rx
[   77.062593] Registered led device: b43legacy-phy0::radio
[   77.062631] b43legacy-phy0 debug: Wireless interface started
[   77.068092] b43legacy-phy0 debug: Adding Interface type 2
[   81.824075] b43legacy-phy0: Radio hardware status changed to DISABLED
[   81.824091] b43legacy-phy0 debug: Radio initialized
[   81.825628] b43legacy-phy0 debug: Removing Interface type 2
[   81.825683] b43legacy-phy0 debug: Wireless interface stopped
[   81.825958] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[   81.826024] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[   81.826093] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[   81.832426] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[   81.840088] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[   81.848051] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[   81.856058] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[   81.864081] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[   81.872044] b43legacy-phy0 debug: Radio initialized
[   81.872058] b43legacy-phy0 debug: Radio initialized
[   86.832105] b43legacy-phy0: Radio hardware status changed to ENABLED
[   86.988081] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   87.056355] b43legacy-phy0 debug: Chip initialized
[   87.056723] b43legacy-phy0 debug: 30-bit DMA initialized
[   87.062604] Registered led device: b43legacy-phy0::tx
[   87.062707] Registered led device: b43legacy-phy0::rx
[   87.062773] Registered led device: b43legacy-phy0::radio
[   87.062822] b43legacy-phy0 debug: Wireless interface started
[   87.068322] b43legacy-phy0 debug: Adding Interface type 2
[   91.824056] b43legacy-phy0: Radio hardware status changed to DISABLED
[   91.824066] b43legacy-phy0 debug: Radio initialized
[   91.826590] b43legacy-phy0 debug: Removing Interface type 2
[   91.826634] b43legacy-phy0 debug: Wireless interface stopped
[   91.826826] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[   91.826875] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[   91.826922] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[   91.832071] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[   91.840053] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[   91.848048] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[   91.856037] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[   91.864178] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[   91.872056] b43legacy-phy0 debug: Radio initialized
[   91.872071] b43legacy-phy0 debug: Radio initialized
[   96.832095] b43legacy-phy0: Radio hardware status changed to ENABLED
[   96.988104] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   97.056325] b43legacy-phy0 debug: Chip initialized
[   97.056660] b43legacy-phy0 debug: 30-bit DMA initialized
[   97.062718] Registered led device: b43legacy-phy0::tx
[   97.062816] Registered led device: b43legacy-phy0::rx
[   97.062870] Registered led device: b43legacy-phy0::radio
[   97.062917] b43legacy-phy0 debug: Wireless interface started
[   97.076104] b43legacy-phy0 debug: Adding Interface type 2
[  101.824093] b43legacy-phy0: Radio hardware status changed to DISABLED
[  101.824109] b43legacy-phy0 debug: Radio initialized
[  101.826456] b43legacy-phy0 debug: Removing Interface type 2
[  101.832083] b43legacy-phy0 debug: Wireless interface stopped
[  101.832384] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[  101.832453] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[  101.832519] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[  101.840096] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[  101.848073] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[  101.856049] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[  101.864076] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[  101.872056] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[  101.880046] b43legacy-phy0 debug: Radio initialized
[  101.880061] b43legacy-phy0 debug: Radio initialized
[  106.832117] b43legacy-phy0: Radio hardware status changed to ENABLED
[  106.988107] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[  107.056327] b43legacy-phy0 debug: Chip initialized
[  107.056692] b43legacy-phy0 debug: 30-bit DMA initialized
[  107.061974] Registered led device: b43legacy-phy0::tx
[  107.062082] Registered led device: b43legacy-phy0::rx
[  107.062141] Registered led device: b43legacy-phy0::radio
[  107.062191] b43legacy-phy0 debug: Wireless interface started
[  107.068756] b43legacy-phy0 debug: Adding Interface type 2
[  111.824086] b43legacy-phy0: Radio hardware status changed to DISABLED
[  111.824102] b43legacy-phy0 debug: Radio initialized
[  111.825536] b43legacy-phy0 debug: Removing Interface type 2
[  111.825592] b43legacy-phy0 debug: Wireless interface stopped
[  111.825888] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[  111.825958] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[  111.826026] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[  111.832082] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[  111.840092] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[  111.848066] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[  111.856061] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[  111.864077] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[  111.872093] b43legacy-phy0 debug: Radio initialized
[  111.872113] b43legacy-phy0 debug: Radio initialized
[  116.832120] b43legacy-phy0: Radio hardware status changed to ENABLED
[  116.988097] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[  117.059200] b43legacy-phy0 debug: Chip initialized
[  117.059541] b43legacy-phy0 debug: 30-bit DMA initialized
[  117.067678] Registered led device: b43legacy-phy0::tx
[  117.070566] Registered led device: b43legacy-phy0::rx
[  117.070672] Registered led device: b43legacy-phy0::radio
[  117.070722] b43legacy-phy0 debug: Wireless interface started
[  117.084089] b43legacy-phy0 debug: Adding Interface type 2
[  121.824099] b43legacy-phy0: Radio hardware status changed to DISABLED
[  121.824116] b43legacy-phy0 debug: Radio initialized
[  121.825535] b43legacy-phy0 debug: Removing Interface type 2
[  121.832095] b43legacy-phy0 debug: Wireless interface stopped
[  121.832395] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[  121.832466] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[  121.832532] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[  121.840106] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[  121.848072] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[  121.856062] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[  121.864106] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[  121.872109] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[  121.880090] b43legacy-phy0 debug: Radio initialized
[  121.880109] b43legacy-phy0 debug: Radio initialized
[  126.832112] b43legacy-phy0: Radio hardware status changed to ENABLED
[  126.989679] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[  127.072610] b43legacy-phy0 debug: Chip initialized
[  127.072864] b43legacy-phy0 debug: 30-bit DMA initialized
[  127.073089] Registered led device: b43legacy-phy0::tx
[  127.073122] Registered led device: b43legacy-phy0::rx
[  127.073151] Registered led device: b43legacy-phy0::radio
[  127.073186] b43legacy-phy0 debug: Wireless interface started
[  127.073193] b43legacy-phy0 debug: Adding Interface type 2
[  131.824083] b43legacy-phy0: Radio hardware status changed to DISABLED
[  131.824097] b43legacy-phy0 debug: Radio initialized
[  131.832401] b43legacy-phy0 debug: Removing Interface type 2
[  131.840087] b43legacy-phy0 debug: Wireless interface stopped
[  131.848948] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[  131.849023] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[  131.849089] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[  131.856066] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[  131.864051] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[  131.872049] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[  131.880049] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[  131.888055] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[  131.896047] b43legacy-phy0 debug: Radio initialized
[  131.896061] b43legacy-phy0 debug: Radio initialized
[  136.832107] b43legacy-phy0: Radio hardware status changed to ENABLED
[  136.988090] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[  137.056327] b43legacy-phy0 debug: Chip initialized
[  137.056671] b43legacy-phy0 debug: 30-bit DMA initialized
[  137.062832] Registered led device: b43legacy-phy0::tx
[  137.062933] Registered led device: b43legacy-phy0::rx
[  137.062996] Registered led device: b43legacy-phy0::radio
[  137.063043] b43legacy-phy0 debug: Wireless interface started
[  137.068153] b43legacy-phy0 debug: Adding Interface type 2
[  141.824070] b43legacy-phy0: Radio hardware status changed to DISABLED
[  141.824084] b43legacy-phy0 debug: Radio initialized
[  141.832493] b43legacy-phy0 debug: Removing Interface type 2
[  141.840086] b43legacy-phy0 debug: Wireless interface stopped
[  141.849019] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[  141.849094] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[  141.849163] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[  141.856066] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[  141.864064] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[  141.872074] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[  141.880070] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[  141.888065] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[  141.896060] b43legacy-phy0 debug: Radio initialized
[  141.896076] b43legacy-phy0 debug: Radio initialized
[  146.832101] b43legacy-phy0: Radio hardware status changed to ENABLED
[  146.988082] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[  147.056324] b43legacy-phy0 debug: Chip initialized
[  147.056664] b43legacy-phy0 debug: 30-bit DMA initialized
[  147.062803] Registered led device: b43legacy-phy0::tx
[  147.062905] Registered led device: b43legacy-phy0::rx
[  147.062965] Registered led device: b43legacy-phy0::radio
[  147.063012] b43legacy-phy0 debug: Wireless interface started
[  147.068116] b43legacy-phy0 debug: Adding Interface type 2
[  151.824088] b43legacy-phy0: Radio hardware status changed to DISABLED
[  151.824104] b43legacy-phy0 debug: Radio initialized
[  151.825514] b43legacy-phy0 debug: Removing Interface type 2
[  151.832076] b43legacy-phy0 debug: Wireless interface stopped
[  151.832384] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[  151.832474] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[  151.832542] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[  151.840094] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[  151.848099] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[  151.856065] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[  151.864064] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[  151.872079] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[  151.880090] b43legacy-phy0 debug: Radio initialized
[  151.880109] b43legacy-phy0 debug: Radio initialized
[  156.832130] b43legacy-phy0: Radio hardware status changed to ENABLED
[  157.019454] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[  157.084321] b43legacy-phy0 debug: Chip initialized
[  157.084662] b43legacy-phy0 debug: 30-bit DMA initialized
[  157.093701] Registered led device: b43legacy-phy0::tx
[  157.093803] Registered led device: b43legacy-phy0::rx
[  157.093867] Registered led device: b43legacy-phy0::radio
[  157.093916] b43legacy-phy0 debug: Wireless interface started
[  157.100492] b43legacy-phy0 debug: Adding Interface type 2
[  161.824068] b43legacy-phy0: Radio hardware status changed to DISABLED
[  161.824082] b43legacy-phy0 debug: Radio initialized
[  161.832350] b43legacy-phy0 debug: Removing Interface type 2
[  161.832403] b43legacy-phy0 debug: Wireless interface stopped
[  161.841038] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[  161.841109] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[  161.841177] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[  161.848089] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[  161.856062] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[  161.864051] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[  161.872051] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[  161.880049] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[  161.888051] b43legacy-phy0 debug: Radio initialized
[  161.888065] b43legacy-phy0 debug: Radio initialized
[  166.832101] b43legacy-phy0: Radio hardware status changed to ENABLED
[  166.988094] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[  167.060340] b43legacy-phy0 debug: Chip initialized
[  167.060702] b43legacy-phy0 debug: 30-bit DMA initialized
[  167.066790] Registered led device: b43legacy-phy0::tx
[  167.066891] Registered led device: b43legacy-phy0::rx
[  167.066954] Registered led device: b43legacy-phy0::radio
[  167.067004] b43legacy-phy0 debug: Wireless interface started
[  167.072111] b43legacy-phy0 debug: Adding Interface type 2
[  171.824073] b43legacy-phy0: Radio hardware status changed to DISABLED
[  171.824100] b43legacy-phy0 debug: Radio initialized
[  171.826962] b43legacy-phy0 debug: Removing Interface type 2
[  171.832096] b43legacy-phy0 debug: Wireless interface stopped
[  171.832403] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[  171.832476] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[  171.832539] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[  171.840107] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[  171.848076] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[  171.857555] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[  171.864556] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[  171.872075] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[  171.880069] b43legacy-phy0 debug: Radio initialized
[  171.880088] b43legacy-phy0 debug: Radio initialized
[  176.832098] b43legacy-phy0: Radio hardware status changed to ENABLED
[  176.988082] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[  177.056330] b43legacy-phy0 debug: Chip initialized
[  177.056668] b43legacy-phy0 debug: 30-bit DMA initialized
[  177.062510] Registered led device: b43legacy-phy0::tx
[  177.062827] Registered led device: b43legacy-phy0::rx
[  177.062890] Registered led device: b43legacy-phy0::radio
[  177.062938] b43legacy-phy0 debug: Wireless interface started
[  177.068153] b43legacy-phy0 debug: Adding Interface type 2
[  181.824069] b43legacy-phy0: Radio hardware status changed to DISABLED
[  181.824083] b43legacy-phy0 debug: Radio initialized
[  181.832304] b43legacy-phy0 debug: Removing Interface type 2
[  181.832357] b43legacy-phy0 debug: Wireless interface stopped
[  181.839699] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[  181.839773] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[  181.839837] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[  181.844099] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[  181.852082] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[  181.860057] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[  181.868071] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[  181.876074] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[  181.884060] b43legacy-phy0 debug: Radio initialized
[  181.884076] b43legacy-phy0 debug: Radio initialized
[  186.832115] b43legacy-phy0: Radio hardware status changed to ENABLED
[  186.988090] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[  187.062188] b43legacy-phy0 debug: Chip initialized
[  187.062525] b43legacy-phy0 debug: 30-bit DMA initialized
[  187.068686] Registered led device: b43legacy-phy0::tx
[  187.068787] Registered led device: b43legacy-phy0::rx
[  187.068852] Registered led device: b43legacy-phy0::radio
[  187.068902] b43legacy-phy0 debug: Wireless interface started
[  187.076841] b43legacy-phy0 debug: Adding Interface type 2
[  191.824075] b43legacy-phy0: Radio hardware status changed to DISABLED
[  191.824089] b43legacy-phy0 debug: Radio initialized
[  191.833064] b43legacy-phy0 debug: Removing Interface type 2
[  191.833120] b43legacy-phy0 debug: Wireless interface stopped
[  191.845830] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[  191.845906] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[  191.845963] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[  191.852066] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[  191.860054] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[  191.868058] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[  191.876051] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[  191.884072] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[  191.892050] b43legacy-phy0 debug: Radio initialized
[  191.892064] b43legacy-phy0 debug: Radio initialized
[  196.832111] b43legacy-phy0: Radio hardware status changed to ENABLED
[  196.988087] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[  197.060341] b43legacy-phy0 debug: Chip initialized
[  197.060679] b43legacy-phy0 debug: 30-bit DMA initialized
[  197.066915] Registered led device: b43legacy-phy0::tx
[  197.067019] Registered led device: b43legacy-phy0::rx
[  197.067079] Registered led device: b43legacy-phy0::radio
[  197.067128] b43legacy-phy0 debug: Wireless interface started
[  197.072180] b43legacy-phy0 debug: Adding Interface type 2
[  201.824102] b43legacy-phy0: Radio hardware status changed to DISABLED
[  201.824118] b43legacy-phy0 debug: Radio initialized
[  201.832648] b43legacy-phy0 debug: Removing Interface type 2
[  201.832702] b43legacy-phy0 debug: Wireless interface stopped
[  201.842553] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[  201.842626] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[  201.842691] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[  201.848091] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[  201.856064] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[  201.864096] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[  201.872059] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[  201.880067] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[  201.888090] b43legacy-phy0 debug: Radio initialized
[  201.888108] b43legacy-phy0 debug: Radio initialized
[  206.832093] b43legacy-phy0: Radio hardware status changed to ENABLED
[  206.988089] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[  207.056326] b43legacy-phy0 debug: Chip initialized
[  207.056671] b43legacy-phy0 debug: 30-bit DMA initialized
[  207.063212] Registered led device: b43legacy-phy0::tx
[  207.063315] Registered led device: b43legacy-phy0::rx
[  207.063379] Registered led device: b43legacy-phy0::radio
[  207.063427] b43legacy-phy0 debug: Wireless interface started
[  207.068156] b43legacy-phy0 debug: Adding Interface type 2
[  211.824071] b43legacy-phy0: Radio hardware status changed to DISABLED
[  211.824085] b43legacy-phy0 debug: Radio initialized
[  211.832855] b43legacy-phy0 debug: Removing Interface type 2
[  211.832911] b43legacy-phy0 debug: Wireless interface stopped
[  211.845522] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[  211.845597] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[  211.845658] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[  211.852076] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[  211.860052] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[  211.868050] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[  211.876049] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[  211.884050] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[  211.896430] b43legacy-phy0 debug: Radio initialized
[  211.896449] b43legacy-phy0 debug: Radio initialized
[  216.832110] b43legacy-phy0: Radio hardware status changed to ENABLED
[  216.988079] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[  217.056338] b43legacy-phy0 debug: Chip initialized
[  217.056705] b43legacy-phy0 debug: 30-bit DMA initialized
[  217.062850] Registered led device: b43legacy-phy0::tx
[  217.062951] Registered led device: b43legacy-phy0::rx
[  217.063011] Registered led device: b43legacy-phy0::radio
[  217.063059] b43legacy-phy0 debug: Wireless interface started
[  217.068128] b43legacy-phy0 debug: Adding Interface type 2
[  226.832093] b43legacy-phy0: Radio hardware status changed to DISABLED
[  226.832110] b43legacy-phy0 debug: Radio initialized
[  226.836202] b43legacy-phy0 debug: Removing Interface type 2
[  226.836257] b43legacy-phy0 debug: Wireless interface stopped
[  226.836546] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[  226.836619] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 2/64
[  226.836686] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[  226.844096] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[  226.852083] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[  226.860071] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[  226.868055] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[  226.876049] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[  226.884047] b43legacy-phy0 debug: Radio initialized
[  226.884061] b43legacy-phy0 debug: Radio initialized
[  231.824118] b43legacy-phy0: Radio hardware status changed to ENABLED
[  231.980084] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[  232.048326] b43legacy-phy0 debug: Chip initialized
[  232.048672] b43legacy-phy0 debug: 30-bit DMA initialized
[  232.054553] Registered led device: b43legacy-phy0::tx
[  232.054657] Registered led device: b43legacy-phy0::rx
[  232.054720] Registered led device: b43legacy-phy0::radio
[  232.054768] b43legacy-phy0 debug: Wireless interface started
[  232.060128] b43legacy-phy0 debug: Adding Interface type 2

```

sudo iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: C6:8E:37:E4:AB:48
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"freeazeclem"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000012e30e6a172
                    Extra: Last beacon: 912ms ago
                    IE: Unknown: 000B66726565617A65636C656D
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1602050100000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000018127A
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402050100000000000000000000000000000000000000
                    IE: Unknown: DD07000C4300000000
          Cell 02 - Address: C6:8E:37:E4:AB:49
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000012e30e51b30
                    Extra: Last beacon: 1012ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1602050100000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000018127A
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402050100000000000000000000000000000000000000
                    IE: Unknown: DD07000C4300000000
          Cell 03 - Address: C6:8E:37:E4:AB:4A
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000012e30e6b46d
                    Extra: Last beacon: 908ms ago
                    IE: Unknown: 00084672656557696669
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1602050100000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000018127A
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402050100000000000000000000000000000000000000
                    IE: Unknown: DD07000C4300000000
          Cell 04 - Address: C6:8E:37:E4:AB:4B
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"freephonie"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000012e30e52d33
                    Extra: Last beacon: 1008ms ago
                    IE: Unknown: 000A6672656570686F6E6965
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1602050100000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000018127A
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402050100000000000000000000000000000000000000
                    IE: Unknown: DD07000C4300000000
          Cell 05 - Address: C2:17:33:AE:73:0D
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:off
                    ESSID:"SFR WiFi Public"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d24b0f70a
                    Extra: Last beacon: 332ms ago
                    IE: Unknown: 000F5346522057694669205075626C6963
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180203F0040000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 06 - Address: 00:17:33:AE:73:0C
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"NEUF_7308"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d24b0f18f
                    Extra: Last beacon: 332ms ago
                    IE: Unknown: 00094E4555465F37333038
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180203F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 07 - Address: 42:78:94:E2:DC:88
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"freebox_ZJRJBA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009cf1adf172
                    Extra: Last beacon: 516ms ago
                    IE: Unknown: 000E66726565626F785F5A4A524A4241
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B070100000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000020127A
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B070100000000000000000000000000000000000000
                    IE: Unknown: DD07000C4300000000

```

rfkill list
```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

Tkank you for your help !

---

### Post by Pierrot86 on 2012-01-26
When I posted the output of "dmesg | grep b43", the wifi led didn't stop to light on and light off. So I booted into Windows, reactivated the wifi, and now I have booted into Lubuntu, and the led stays on. So I repost the output "of dmesg | grep b43" :

```
[    1.912614] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNK3] -> GSI 17 (level, low) -> IRQ 17
[   18.384819] b43legacy-phy0: Broadcom 4301 WLAN found
[   18.413048] b43legacy-phy0 debug: Found PHY: Analog 0, Type 1, Revision 4
[   18.413072] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   18.516247] b43legacy-phy0 debug: Radio initialized
[   21.576720] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   21.776305] b43legacy-phy0 debug: Chip initialized
[   21.776556] b43legacy-phy0 debug: 30-bit DMA initialized
[   21.786636] Registered led device: b43legacy-phy0::tx
[   21.788392] Registered led device: b43legacy-phy0::rx
[   21.788461] Registered led device: b43legacy-phy0::radio
[   21.788508] b43legacy-phy0 debug: Wireless interface started
[   21.796333] b43legacy-phy0 debug: Adding Interface type 2

```

---

### Post by praseodym on 2012-01-26
IMHO this (old) device only works with WEP encryption

---

### Post by Pierrot86 on 2012-01-26
I changed my network with a wep key, but it didn't work. Moreover, in Windows XP, the wifi works with a wpa key.

---

