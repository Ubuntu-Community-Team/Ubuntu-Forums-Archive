---
title: "Wireless slow after update"
date: 2013-01-22
forum: Networking &amp; Wireless
---

### Post by chantaspell on 2013-01-22
Hi

Running 
Release 12.04 (precise) 64-bit
Kernel Linux 3.2.0-36-generic
GNOME 3.4.2
Intel® Core™ i7-2670QM CPU @ 2.20GHz × 8 

Ran an update last week when prompted by Ubuntu and afterwards my wifi was amazingly slow. My phone connects to my home wifi and runs well as usual, and when i boot into win7 the wireless speed is fine. But in ubuntu it runs at sub dial speeds!

Am new to this, but posted the following as it might be useful info?

Many thanks to any helpers.

PS, have looked in this forum and tried doing
```
sudo apt-get install linux-headers-generic sudo apt-get install --reinstall bcmwl-kernel-source sudo modprobe wl 
```
but it didnt help.



```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 058f:b002 Alcor Micro Corp. 
```

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 058f:b002 Alcor Micro Corp. 
thomas@thomas-Aspire-5755G:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev ff)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe (rev 10)
02:00.1 SD Host controller: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader (rev 10)
02:00.2 System peripheral: Broadcom Corporation Device 16be (rev 10)
02:00.3 System peripheral: Broadcom Corporation Device 16bf (rev 10)
03:00.0 Network controller: Broadcom Corporation BCM43227 802.11b/g/n
05:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)

```

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr b8:70:f4:e5:23:85  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth2      Link encap:Ethernet  HWaddr 38:59:f9:b2:cc:84  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::3a59:f9ff:feb2:cc84/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:282 errors:0 dropped:0 overruns:0 frame:851
          TX packets:422 errors:8 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:123711 (123.7 KB)  TX bytes:69321 (69.3 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1429 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1429 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:151134 (151.1 KB)  TX bytes:151134 (151.1 KB)

:~$ iwconfig
lo        no wireless extensions.

eth2      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:230  Noise level:170
          Rx invalid nwid:0  invalid crypt:2  invalid misc:0

eth0      no wireless extensions.

```

```
Module                  Size  Used by
michael_mic            12612  4 
arc4                   12529  2 
bbswitch               13396  0 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180153  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224173  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
lib80211_crypt_tkip    17390  0 
i915                  477602  3 
psmouse                97485  0 
wl                   2568249  0 
drm_kms_helper         46978  1 i915
drm                   241971  4 i915,drm_kms_helper
uvcvideo               72627  0 
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
serio_raw              13211  0 
videodev               98259  1 uvcvideo
i2c_algo_bit           13423  1 i915
mei                    41616  0 
lib80211               14381  2 lib80211_crypt_tkip,wl
v4l2_compat_ioctl32    17128  1 videodev
acer_wmi               28418  0 
mxm_wmi                13021  0 
sparse_keymap          13890  1 acer_wmi
mac_hid                13253  0 
video                  19596  1 i915
wmi                    19256  2 acer_wmi,mxm_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              18826  0 
tg3                   152032  0 
sdhci                  33205  1 sdhci_pci

```

---

