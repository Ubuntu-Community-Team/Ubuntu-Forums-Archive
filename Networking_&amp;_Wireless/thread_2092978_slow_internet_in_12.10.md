---
title: "slow internet in 12.10"
date: 2012-12-09
forum: Networking &amp; Wireless
---

### Post by exe8 on 2012-12-09
I recently installed a dual boot of ubuntu 12.10 and windows 8 and the internet is much faster on the windows side. It still works under ubuntu but is a whole lot slower. I read up a little and wondered if this is still an IP6 bug in ubuntu? here is some info that could potentially be useful:

EDIT: I also tried disabling IPv6 which didn't help. Still much slower than in windows 8.

iwconfig

```

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"xxxxx"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate=12 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=35/70  Signal level=-75 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:235   Missed beacon:0
```lspci -nnk | grep -iA2 net

```

01:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 0a)
    Subsystem: Hewlett-Packard Company Device [103c:1894]
    Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0887] (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4062]
    Kernel driver in use: iwlwifi
```lsmod

```

Module                  Size  Used by
parport_pc             32688  0 
ppdev                  17073  0 
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_idt      70209  1 
bnep                   18140  2 
rfcomm                 46619  16 
nls_iso8859_1          12713  1 
coretemp               13400  0 
kvm                   414070  0 
ghash_clmulni_intel    13180  0 
aesni_intel            51037  0 
cryptd                 20403  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17208  1 aesni_intel
arc4                   12529  2 
hp_wmi                 18048  0 
sparse_keymap          13890  1 hp_wmi
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
iwlwifi               386826  0 
mac80211              539908  1 iwlwifi
snd_hda_intel          33491  5 
microcode              22803  0 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
cfg80211              206566  2 iwlwifi,mac80211
psmouse                95552  0 
serio_raw              13215  0 
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
mei                    40690  0 
lpc_ich                17061  0 
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78734  19 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
btusb                  22474  0 
bluetooth             209199  22 bnep,rfcomm,btusb
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
joydev                 17457  0 
i915                  520629  3 
wmi                    19070  1 hp_wmi
drm_kms_helper         46784  1 i915
drm                   275528  4 i915,drm_kms_helper
i2c_algo_bit           13413  1 i915
hp_accel               25976  0 
video                  19335  1 i915
lis3lv02d              19829  1 hp_accel
input_polldev          13896  1 lis3lv02d
mac_hid                13205  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
hid_generic            12493  0 
usbhid                 46947  0 
hid                   100366  2 hid_generic,usbhid
r8169                  61650  0 
```This occurs both in ubuntu and xubuntu. Thanks in advance

---

### Post by dandroid7 on 2012-12-09
ditto on the scenario...

windows 8/ubuntu 12.04

great internet speed on win8

slow speed on ubuntu 12.04

disabled ipv6

here's some info on my setup: 

root@dubuntu-Inspiron-660:~# ifconfig
eth0      Link encap:Ethernet  HWaddr d4:be:d9:d7:8b:26  
          inet addr:192.168.1.18  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:90325 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82382 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34988651 (34.9 MB)  TX bytes:6707485 (6.7 MB)
          Interrupt:43 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:585 errors:0 dropped:0 overruns:0 frame:0
          TX packets:585 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:92465 (92.4 KB)  TX bytes:92465 (92.4 KB)

wlan0     Link encap:Ethernet  HWaddr e0:06:e6:73:fd:97  
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:421181 (421.1 KB)  TX bytes:11525 (11.5 KB)

root@dubuntu-Inspiron-660:~# sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: e0:06:e6:73:fd:97
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-34-generic firmware=N/A ip=192.168.1.14 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f7c00000-f7c7ffff memory:f7c80000-f7c8ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 07
       serial: d4:be:d9:d7:8b:26
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.18 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff

---

