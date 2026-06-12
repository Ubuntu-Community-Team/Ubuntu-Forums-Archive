---
title: "Cannot find Wireless Network"
date: 2010-07-03
forum: Networking &amp; Wireless
---

### Post by kagardner on 2010-07-03
I downloaded Ubuntu this morning and added it to my laptop. upon finishing up I decided to go ahead and configure the wireless network, to no avail. I could not find the Network, even when typing in the SSID. what should I do to fix this problem?

I have a Netopia router.

---

### Post by roosh on 2010-07-03
Do you have any info on your wireless card?
Please open a terminal and paste the output of the following commands:
```
lsusb
``` ```
lspci
``` ```
lsmod
```

---

### Post by kagardner on 2010-07-03
kyle@kyle-laptop:~$ lsusb 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
kyle@kyle-laptop:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c) 
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) 
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) 
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02) 
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) 
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) 
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02) 
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2) 
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02) 
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02) 
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02) 
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) 
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) 
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12) 
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12) 
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) 
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01) 
kyle@kyle-laptop:~$ lsmod 
Module                  Size  Used by 
binfmt_misc             6587  1 
snd_hda_codec_idt      51914  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon 
font                    7557  1 fbcon 
bitblit                 4707  1 fbcon 
softcursor              1189  1 bitblit 
vga16fb                11385  0 
vgastate                8961  1 vga16fb 
ppdev                   5259  0 
joydev                  8708  0 
arc4                    1153  2 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel 
snd_hwdep               5412  1 snd_hda_codec 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss 
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss 
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              19098  2 snd_pcm,snd_seq 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
b43                   157218  0 
dell_wmi                1793  0 
i915                  282354  3 
mac80211              204922  1 b43 
drm_kms_helper         29297  1 i915 
dell_laptop             6856  0 
dcdbas                  5422  1 dell_laptop 
snd                    54148  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
psmouse                63245  0 
ricoh_mmc               2923  0 
cfg80211              126485  2 b43,mac80211 
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci 
led_class               2864  2 b43,sdhci 
drm                   162471  4 i915,drm_kms_helper 
i2c_algo_bit            5028  1 i915 
intel_agp              24177  2 i915 
serio_raw               3978  0 
soundcore               6620  1 snd 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm 
agpgart                31724  2 drm,intel_agp 
video                  17375  1 i915 
output                  1871  1 video 
lp                      7028  0 
parport                32635  2 ppdev,lp 
b44                    25542  0 
ohci1394               26950  0 
ieee1394               81181  1 ohci1394 
mii                     4381  1 b44 
ssb                    37336  2 b43,b44

---

### Post by kagardner on 2010-07-04
If I'm allowed,  to bump this. Then consider this a bump. If not, consider it a question.

---

