---
title: "Atheros AR9285 not working in 12.10"
date: 2013-02-24
forum: Networking &amp; Wireless
---

### Post by patyh on 2013-02-24
Hi guys, I recently decided to install ubuntu on my newly purchased laptop.. However, I can't seem to get my wireless card to work.. It will appears on the network manager but will not be able to detect any wireless network.. Here's hoping someone here can help me out. 

[B]1) Machine Brand 
[/B]
```
Lenovo G485
```[B]2) Running lspci
[/B]
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 9809
00:10.0 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 14)
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices [AMD] Device 43a0
00:15.1 PCI bridge: Advanced Micro Devices [AMD] Device 43a1
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
06:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```**3)** [B]Running iwconfig 

[/B]```
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

```[B]4) Running lsmod

[/B]```
Module                  Size  Used by
nls_iso8859_1          12618  1 
snd_hda_codec_conexant    52170  1 
joydev                 17162  0 
kvm_amd                54395  0 
kvm                   357807  1 kvm_amd
snd_hda_intel          32516  3 
snd_hda_codec         111548  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
snd_pcm                80235  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25383  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
arc4                   12474  2 
microcode              18210  0 
psmouse                84878  0 
ath9k                 116588  0 
mac80211              461261  1 ath9k
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
ath9k_common           13784  1 ath9k
ath9k_hw              376228  2 ath9k,ath9k_common
rts5139               281401  0 
snd_timer              24412  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
ath                    19188  3 ath9k,ath9k_common,ath9k_hw
snd                    62146  15 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13032  0 
uvcvideo               71278  0 
videobuf2_core         32071  1 uvcvideo
videodev               95842  2 uvcvideo,videobuf2_core
k10temp                12959  0 
soundcore              14600  1 snd
videobuf2_vmalloc      12757  1 uvcvideo
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
cfg80211              175574  3 ath9k,mac80211,ath
videobuf2_memops       13213  1 videobuf2_vmalloc
i2c_piix4              12984  0 
rfcomm                 37277  0 
parport_pc             31969  0 
bnep                   17708  2 
radeon                820764  3 
bluetooth             183270  10 rfcomm,bnep
ppdev                  12818  0 
ttm                    75535  1 radeon
drm_kms_helper         47304  1 radeon
drm                   238811  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13198  1 radeon
ideapad_laptop         13671  0 
sparse_keymap          13659  1 ideapad_laptop
video                  18895  0 
mac_hid                13038  0 
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
usb_storage            39351  1 
hid_generic            12485  0 
usbhid                 41734  0 
hid                    82179  2 hid_generic,usbhid
r8169                  55977  0 
root@Lebuntu:/home/pipat# lsmod | grep "wlan_module_name"
root@Lebuntu:/home/pipat# lsmod
Module                  Size  Used by
nls_iso8859_1          12618  1 
snd_hda_codec_conexant    52170  1 
joydev                 17162  0 
kvm_amd                54395  0 
kvm                   357807  1 kvm_amd
snd_hda_intel          32516  3 
snd_hda_codec         111548  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
snd_pcm                80235  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25383  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
arc4                   12474  2 
microcode              18210  0 
psmouse                84878  0 
ath9k                 116588  0 
mac80211              461261  1 ath9k
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
ath9k_common           13784  1 ath9k
ath9k_hw              376228  2 ath9k,ath9k_common
rts5139               281401  0 
snd_timer              24412  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
ath                    19188  3 ath9k,ath9k_common,ath9k_hw
snd                    62146  15 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13032  0 
uvcvideo               71278  0 
videobuf2_core         32071  1 uvcvideo
videodev               95842  2 uvcvideo,videobuf2_core
k10temp                12959  0 
soundcore              14600  1 snd
videobuf2_vmalloc      12757  1 uvcvideo
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
cfg80211              175574  3 ath9k,mac80211,ath
videobuf2_memops       13213  1 videobuf2_vmalloc
i2c_piix4              12984  0 
rfcomm                 37277  0 
parport_pc             31969  0 
bnep                   17708  2 
radeon                820764  3 
bluetooth             183270  10 rfcomm,bnep
ppdev                  12818  0 
ttm                    75535  1 radeon
drm_kms_helper         47304  1 radeon
drm                   238811  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13198  1 radeon
ideapad_laptop         13671  0 
sparse_keymap          13659  1 ideapad_laptop
video                  18895  0 
mac_hid                13038  0 
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
usb_storage            39351  1 
hid_generic            12485  0 
usbhid                 41734  0 
hid                    82179  2 hid_generic,usbhid
r8169                  55977  0 

```[B]5) Running lshw -C network

[/B]```
*-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 20:68:9d:fb:bd:ee
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-25-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:90100000-9010ffff

```[B]6) Running iwlist wlan0 scan

[/B]```
wlan0     No scan results

```[B]7) Ubuntu Version

[/B]```
Description:    Ubuntu 12.10

```[B]8) Running uname -mr

[/B]```
3.5.0-25-generic i686

```I am unable to run the restart network command as doing so will cause Unity to crash and me being able to do anything other than reboot.. 

Hope someone here can help me out soon.. A laptop without wireless is a pain in the butt.

---

