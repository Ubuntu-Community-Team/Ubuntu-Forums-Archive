---
title: "Wireless Connection Problems"
date: 2011-06-20
forum: Networking &amp; Wireless
---

### Post by rayred on 2011-06-20
I have been having trouble with Ubuntu 11.04 when connecting to the Internet via Wireless Networking. It will connect, and has good speed once it connects, however it takes upward of 10 minutes and over 20 times of me clicking 'Connect'. 

Is there a way to connect to a wireless network quicker? My network is unsecured and without a keyring. It is not only slow connecting to my network, but the network of other's.

lspci information:
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

Thanks for the help

---

### Post by nm_geo on 2011-06-20
redray 

do a 

```
lsmod
```

and post

---

### Post by rayred on 2011-06-20
The lsmod is:
Module                  Size  Used by
cryptd                   19801  0 
aes_i586                16956  1 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                    12849  0 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
radeon                896428  4 
arc4                   12473  2 
snd_seq_midi           13132  0 
binfmt_misc            13213  1 
snd_rawmidi            25269  1 snd_seq_midi
ath5k                 144412  0 
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17322  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ath                    19141  1 ath5k
mac80211              257001  1 ath5k
ttm                    65184  1 radeon
snd_timer              28659  2 snd_pcm,snd_seq
drm_kms_helper         40745  1 radeon
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   180037  6 radeon,ttm,drm_kms_helper
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
cfg80211              156212  3 ath5k,ath,mac80211
i2c_algo_bit           13184  1 radeon
soundcore              12600  1 snd
serio_raw              12990  0 
sp5100_tco             13456  0 
k8temp                 12872  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  0 
i2c_piix4              13095  0 
ati_agp                13202  0 
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
pata_atiixp            12968  0 
r8169                  42534  0 
libahci                25548  1 ahci

---

