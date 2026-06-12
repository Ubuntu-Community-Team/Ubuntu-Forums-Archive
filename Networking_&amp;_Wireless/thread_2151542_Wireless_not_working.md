---
title: "Wireless not working"
date: 2013-06-04
forum: Networking &amp; Wireless
---

### Post by Tgmarques on 2013-06-04
Hello Forum,


I have installed 12.10 today and my wireless connection is not working. Could anyone help, please?


Code for $ lspci
```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09) 
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) 
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04) 
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04) 
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) 
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04) 
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4) 
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4) 
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4) 
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) 
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04) 
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04) 
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04) 
00:1f.6 Signal processing controller: Intel Corporation 7 Series/C210 Series Chipset Family Thermal Management Controller (rev 04) 
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8723 
08:00.0 Ethernet controller: Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 10) 
09:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01) 
```


Code for $ iwconfig
```
lo        no wireless extensions.
```


Code for $ lsmod
```
Module                  Size  Used by 
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_realtek    77876  1 
parport_pc             32688  0 
ppdev                  17073  0 
rfcomm                 46619  12 
bnep                   18140  2 
joydev                 17457  0 
coretemp               13400  0 
kvm_intel             132759  0 
kvm                   414070  1 kvm_intel 
ghash_clmulni_intel    13180  0 
cryptd                 20403  1 ghash_clmulni_intel 
snd_hda_intel          33491  3 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel 
microcode              22803  0 
snd_hwdep              13602  1 snd_hda_codec 
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi 
btusb                  18334  0 
bluetooth             209199  22 rfcomm,bnep,btusb 
snd_seq_midi_event     14899  1 snd_seq_midi 
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event 
wmi                    19070  0 
snd_timer              29425  2 snd_pcm,snd_seq 
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq 
psmouse                95552  0 
i915                  520519  3 
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo 
videodev              120309  2 uvcvideo,videobuf2_core 
videobuf2_vmalloc      12860  1 uvcvideo 
videobuf2_memops       13368  1 videobuf2_vmalloc 
serio_raw              13215  0 
drm_kms_helper         46784  1 i915 
drm                   275528  4 i915,drm_kms_helper 
mac_hid                13205  0 
i2c_algo_bit           13413  1 i915 
video                  19335  1 i915 
snd                    78734  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
lpc_ich                17061  0 
soundcore              15047  1 snd 
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm 
mei                    40690  0 
rts_pstor             433804  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp 
```


Code for $ iwlist scan
```
lo        Interface doesn't support scanning. 
```


Please let me know if more info is needed. Would really appreciate any help.

---

### Post by Hadaka on 2013-06-05
Hi, we can get your wireless going one of two ways.
1. Load Ubuntu 13.04 - it has the driver for your card built in.
2. Download the driver and complile it for your card.
 Which would you prefer to do?

---

