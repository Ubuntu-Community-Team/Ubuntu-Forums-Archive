---
title: "No intermediate sound, either on or off"
date: 2010-01-02
forum: Multimedia Software
---

### Post by dictum9 on 2010-01-02
Ubuntu 9.10

My sound works again but it's either on or off, no intermediate volume control. How do I enable intermediate settings? 



# cat lspci.out
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
root@juno:/var/tmp# 




more lsmod.out
Module                  Size  Used by
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10272  0 
snd_hda_codec_idt      59844  1 
arc4                    1660  2 
ecb                     2524  2 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
b43                   122136  0 
mac80211              181076  1 b43
iptable_filter          3100  0 
snd_pcm                75296  3 snd_pcm_oss,snd_hda_intel,snd_hda_codec
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
dell_wmi                2564  0 
dell_laptop             8128  0 
dcdbas                  7292  1 dell_laptop
cfg80211               93052  2 b43,mac80211
snd_timer              22276  2 snd_seq,snd_pcm
psmouse                56500  0 
serio_raw               5280  0 
ricoh_mmc               3676  0 
sdhci_pci               7100  0 
sdhci                  17472  1 sdhci_pci
led_class               4096  2 b43,sdhci
lp                      8964  0 
parport                35340  2 ppdev,lp
snd                    59204  16 snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_pcm_oss,snd_mixer_os
s,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
usbhid                 38208  0 
b44                    28684  0 
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
ssb                    35300  2 b43,b44
mii                     5212  1 b44
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video

---

