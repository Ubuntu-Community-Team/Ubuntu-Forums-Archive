---
title: "Dell XPS15 Ubuntu 12.04 LTS Wireless connects but doesnt do anything"
date: 2012-12-18
forum: Networking &amp; Wireless
---

### Post by scratchesheadinvain on 2012-12-18
Hi everyone,

I see wireless is a common problem so I guess I'll just add to it. I have had a look and can't find a problem like mine so apologies if I am doubling up. 

My wireless connects and shows a good signal but when I open an Internet browser (firefox), it works for 2 minutes then hangs. Browser complains of no connection. ssh doesn't work either.  Works fine on windows though.

I've posted below any possible info I can see people may want. Thanks in advance.

cat /etc/lsb-release; uname -a
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
Linux Leslie 3.2.0-30-generic #48-Ubuntu SMP Fri Aug 24 16:52:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```


lspci
```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev a1)
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
04:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

```iwconfig
```

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Nerd|16^0.5|sideways8"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: E8:40:F2:F1:3B:CB   
          Bit Rate=65 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:63  Invalid misc:45   Missed beacon:0

eth0      no wireless extensions.


```lsmod
```

Module                  Size  Used by
rfcomm                 47604  0 
parport_pc             32866  0 
ppdev                  17113  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224173  1 
joydev                 17693  0 
arc4                   12529  2 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
nvidia              12319264  0 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
hid_logitech_dj        18594  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
dell_laptop            18119  0 
dcdbas                 14490  1 dell_laptop
psmouse                87692  0 
iwlwifi               332525  0 
serio_raw              13211  0 
snd                    78855  19 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              506816  1 iwlwifi
i915                  473035  2 
drm_kms_helper         46978  1 i915
cfg80211              205544  2 iwlwifi,mac80211
drm                   242038  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
mei                    41616  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
wmi                    19256  1 dell_wmi
video                  19596  1 i915
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0 
usbhid                 47199  1 hid_logitech_dj
hid                    99559  2 hid_logitech_dj,usbhid

```sudo lshw -C network
```

[sudo] password for dbyrne: 
  *-network               
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 74:e5:0b:3e:ec:2c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-30-generic firmware=39.31.5.1 build 35138 ip=192.168.1.11 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:52 memory:f1b00000-f1b01fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 06
       serial: 84:8f:69:ac:89:d8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 latency=0 multicast=yes
       resources: irq:50 ioport:2000(size=256) memory:f1804000-f1804fff memory:f1800000-f1803fff

```iwlist scan
```

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: E8:40:F2:F1:3B:CB
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"Nerd|16^0.5|sideways8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002e9c8901198
                    Extra: Last beacon: 102184ms ago
                    IE: Unknown: 00154E6572647C31365E302E357C736964657761797338
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

eth0      Interface doesn't support scanning.

```lspci -nnk | grep -iA2 net
```

03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0083]
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1325]
    Kernel driver in use: iwlwifi
--
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Dell Device [1028:04b6]
    Kernel driver in use: r8169

```rfkill list all
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
dbyrne@Leslie:~$ 


```lsusb
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0408:2fb1 Quanta Computer, Inc. 
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver

```

---

