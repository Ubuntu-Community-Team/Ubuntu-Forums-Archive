---
title: "Ubuntu 12.04 doesn't connect"
date: 2012-05-17
forum: Networking &amp; Wireless
---

### Post by joshjo on 2012-05-17
I try to connect to through Wireless to a WPA network, and it doesn't connect, even it did on Windows. I'm using a laptop. I think this is the model of the NIC

```

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```Hope, help me!.

Greetings!

---

### Post by praseodym on 2012-05-17
Hi,
please show

```
lsmod
iwconfig
rfkill list
ifconfig -a
```

---

### Post by joshjo on 2012-05-18
> **praseodym said:**
> Hi,
please show

```
lsmod
iwconfig
rfkill list
ifconfig -a
```

ok,

'lsmod' shows:
```

Module                  Size  Used by
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223867  1 
arc4                   12529  2 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
psmouse                87692  0 
serio_raw              13211  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
intel_ips              18089  0 
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rtl8192se              99989  0 
rtlwifi               111202  1 rtl8192se
mac80211              506816  2 rtl8192se,rtlwifi
wmi                    19256  1 hp_wmi
cfg80211              205544  2 rtlwifi,mac80211
mac_hid                13253  0 
i915                  468651  8 
drm_kms_helper         46978  1 i915
soundcore              15091  1 snd
drm                   242038  4 i915,drm_kms_helper
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
mei                    41616  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ums_realtek            18248  0 
usb_storage            49198  1 ums_realtek
uas                    18027  0 
r8169                  62099  0 

```with 'iwconfig', well in this part the laptop is connected to other wireless.

```

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"UCSP-hall2p"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:D1:C5:16:F4   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:68   Missed beacon:0

eth0      no wireless extensions.

```
'rfkill list'

```

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```and the last command 'ifconfig -a'

```

eth0      Link encap:Ethernet  HWaddr c8:0a:a9:ef:aa:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:174 errors:0 dropped:0 overruns:0 frame:0
          TX packets:174 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19940 (19.9 KB)  TX bytes:19940 (19.9 KB)

wlan0     Link encap:Ethernet  HWaddr 70:f1:a1:ee:7d:42  
          inet addr:192.168.160.107  Bcast:192.168.160.255  Mask:255.255.255.0
          inet6 addr: fe80::72f1:a1ff:feee:7d42/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2078 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1045 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1033775 (1.0 MB)  TX bytes:202201 (202.2 KB)

```

---

### Post by joshjo on 2012-05-18
:d

---

### Post by praseodym on 2012-05-18
Which channel do you want to connect to? Try a fixed one on the channels 1-11, change the encryption mode to pure WPA2-AES (CCMP), if possible.

---

### Post by bawig1 on 2012-05-18
I've tried this on my gateway (changing from TKIP to AES) and it works. The details of my system are below; I have no idea why TKIP doesn't work.

```
HP Mini 5102
```lsmod;
```

mac80211   436455 1 iwlwifi
cfg80211     178679 2 iwlwifi,mac80211

```lspci
```

01:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000

```

---

### Post by joshjo on 2012-05-21
> **praseodym said:**
> Which channel do you want to connect to? Try a fixed one on the channels 1-11, change the encryption mode to pure WPA2-AES (CCMP), if possible.

Sorry for answering late, can you explain how to do that?.

---

### Post by praseodym on 2012-05-21
Connect via cable and type the router IP address into your browser's URL line. There you should be able to setup the NW properly.

---

