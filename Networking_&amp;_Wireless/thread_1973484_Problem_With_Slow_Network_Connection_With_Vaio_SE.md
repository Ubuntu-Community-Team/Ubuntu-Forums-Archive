---
title: "Problem With Slow Network Connection With Vaio SE"
date: 2012-05-04
forum: Networking &amp; Wireless
---

### Post by nova_intel on 2012-05-04
Hey there, I am currently having a problem with my Sony Vaio SE that I bought a few months ago. I installed Ubuntu 12.04 and other then a few issues with the power consumption the only problem I have had is with the wifi. I am able to successfully connect to the network, however, the connection is slow and sometimes to the point that the connection times out. The model number is VPCSE23FD.

> 
02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6230 [8086:0091] (rev 34)
> 
wlan0     IEEE 802.11abgn  ESSID:"fishy"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: C0:C1:C0:0B:F1:F0   
          Bit Rate=26 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:16   Missed beacon:0
> 
Module                  Size  Used by
rfcomm                 47604  12 
bnep                   18281  2 
parport_pc             32866  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223867  1 
joydev                 17693  0 
arc4                   12529  2 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
radeon                804372  0 
ttm                    76949  1 radeon
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
sony_laptop            45393  0 
iwlwifi               328352  0 
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              506816  1 iwlwifi
i915                  468651  3 
uvcvideo               72627  0 
psmouse                87692  0 
btusb                  18288  2 
videodev               98259  1 uvcvideo
drm_kms_helper         46978  2 radeon,i915
serio_raw              13211  0 
mac_hid                13253  0 
cfg80211              205544  2 iwlwifi,mac80211
rts_pstor             445196  0 
v4l2_compat_ioctl32    17128  1 videodev
bluetooth             180104  23 bnep,rfcomm,btusb
drm                   242038  6 radeon,ttm,i915,drm_kms_helper
mei                    41616  0 
i2c_algo_bit           13423  2 radeon,i915
video                  19596  1 i915
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0 
>  *-network               
       description: Wireless interface
       product: Centrino Advanced-N 6230
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 34
       serial: 88:53:2e:8a:41:0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-24-generic firmware=18.168.6.1 ip=192.168.1.100 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:49 memory:c7400000-c7401fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 06
       serial: f0:bf:97:e4:28:ee
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:47 ioport:3000(size=256) memory:c3404000-c3404fff memory:c3400000-c3403fff
I have tried the power management off solution and turning off Wireless N support, however, this did not seem to work. Thank you in advance for any help.

---

### Post by nova_intel on 2012-05-06
Bump

---

