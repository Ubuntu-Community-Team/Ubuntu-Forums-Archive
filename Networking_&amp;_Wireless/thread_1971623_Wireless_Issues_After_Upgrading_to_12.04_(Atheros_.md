---
title: "Wireless Issues After Upgrading to 12.04 (Atheros AR9285)"
date: 2012-05-02
forum: Networking &amp; Wireless
---

### Post by anonymoususername on 2012-05-02
Tried searching the forums but didn't see a solution to this particular problem but threads about similar ones, and tried asking the IRC but was told to create a thread.

Anyway, I upgraded from 11.10 to 12.04 and now I can't connect to my wireless, which was working smoothly before with the same settings. It just asks me for my WEP key, attempts to connect and then eventually gives in and asks for the key again. I've triple checked the key and tried resetting the router, no luck. Also tried inputting the same key as WPA/WPA-2 in case what was written on the router was in error (it states "WEP(64bit)") but again, no joy. As stated in the title, chipset is Atheros AR9285.

Outputs are:

sudo lshw -class network
```
PCI (sysfs)  
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 90:4c:e5:7d:e5:dc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-24-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:57100000-5710ffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 70:5a:b6:0c:f3:89
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.73 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:55000000-5503ffff ioport:2000(size=128)
```

lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:a102 Suyin Corp. Acer/Lenovo Webcam [CN0316]
Bus 001 Device 003: ID 13fd:1840 Initio Corporation Shintaro SH23SDOCK Hard Drive Docker [INIC-1608L]
```

lspci  -nn | grep 0280
```
01:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
```

lsmod
```
Module                  Size  Used by
dm_crypt               22528  0 
joydev                 17393  0 
acer_wmi               23612  0 
sparse_keymap          13658  1 acer_wmi
snd_hda_codec_realtek   174055  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
arc4                   12473  2 
snd_seq_midi           13132  0 
ath9k                 117425  0 
snd_rawmidi            25424  1 snd_seq_midi
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
mac80211              436455  1 ath9k
psmouse                87213  0 
snd_seq_midi_event     14475  1 snd_seq_midi
serio_raw              13027  0 
ath9k_common           13781  1 ath9k
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ath9k_hw              391523  2 ath9k,ath9k_common
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
cfg80211              178679  3 ath9k,mac80211,ath
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rfcomm                 38139  0 
bnep                   17830  2 
soundcore              14635  1 snd
parport_pc             32114  0 
bluetooth             158438  10 rfcomm,bnep
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
ppdev                  12849  0 
binfmt_misc            17292  1 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
i915                  414568  3 
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
atl1c                  36718  0 
video                  19068  1 i915
wmi                    18744  1 acer_wmi
usb_storage            39646  1 
```

Any help greatly appreciated, apologies if the answer is obvious or I missed some important diagnostic information. If it's at all relevant, my system is an eMachines eM250 series netbook, model number KAV60. Many thanks.

---

