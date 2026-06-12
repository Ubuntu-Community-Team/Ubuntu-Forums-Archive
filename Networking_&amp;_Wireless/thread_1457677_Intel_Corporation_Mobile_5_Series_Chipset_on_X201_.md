---
title: "Intel Corporation Mobile 5 Series Chipset on X201 wifi doesn't work"
date: 2010-04-18
forum: Networking &amp; Wireless
---

### Post by gregnorc on 2010-04-18
So I recently got a thinkpad X201, installed Ubuntu 9.10 via the alternate install CD (regular one wasn't working). I just got the GUI working, and ethernet works, but there's no wireless connectivity, and I googled a bit but couldn't find a solution.

I think my chipset is Intel Corporation Mobile 5 Series Chipset but I'm not positive, I'm very unfamiliar with how to set this up, every time I've used linux before the wireless card was recognized.

If anyone has any ideas PLEASE let me know, I will post any additional info if needed...

lspci:
```
holly@deepthought:~$ lspci
00:00.0 Host bridge: Intel Corporation Arrandale DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Arrandale Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:16.3 Serial controller: Intel Corporation 5 Series/3400 Series Chipset KT Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
ff:00.0 Host bridge: Intel Corporation QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Device 2d12 (rev 02)
ff:02.3 Host bridge: Intel Corporation Device 2d13 (rev 02)
```

lsmod:
```

holly@deepthought:~$ lsmod
Module                  Size  Used by
ecb                     3296  1 
sha256_generic         10816  0 
aesni_intel            13408  212 
cryptd                  8008  2 aesni_intel
aes_x86_64              8992  1 aesni_intel
aes_generic            28480  2 aesni_intel,aes_x86_64
cbc                     4224  208 
dm_crypt               14888  1 
binfmt_misc            10220  1 
ppdev                   8232  0 
snd_hda_codec_intelhdmi    14880  1 
snd_hda_intel          31880  2 
snd_hda_codec          87584  2 snd_hda_codec_intelhdmi,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
uvcvideo               65260  0 
iptable_filter          3872  0 
snd_rawmidi            27296  1 snd_seq_midi
videodev               43360  1 uvcvideo
ip_tables              21200  1 iptable_filter
v4l1_compat            16644  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev
x_tables               25832  1 ip_tables
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                57124  0 
serio_raw               6596  0 
snd                    77096  16 snd_hda_codec_intelhdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
thinkpad_acpi          79196  0 
led_class               5256  1 thinkpad_acpi
nvram                   9356  1 thinkpad_acpi
lp                     11908  0 
parport                40528  2 ppdev,lp
fbcon                  41344  72 
tileblit                3136  1 fbcon
font                    8832  1 fbcon
bitblit                 6688  1 fbcon
softcursor              2336  1 bitblit
e1000e                138544  0 
i915                  252424  3 
drm                   194400  3 i915
i2c_algo_bit            7076  1 i915
intel_agp              33040  2 i915
video                  23612  1 i915
output                  3680  1 video

```

ifconfig:```

holly@deepthought:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:2d:f8:e9:22  
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:2dff:fef8:e922/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2765 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2310 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:10 
          RX bytes:3245969 (3.2 MB)  TX bytes:394456 (394.4 KB)
          Memory:f2500000-f2520000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```

---

### Post by gregnorc on 2010-04-19
I found this wikipage but it lists 4 different possible wifi cards, I have no clue which is correct:

[http://www.thinkwiki.org/wiki/Category:X200](http://www.thinkwiki.org/wiki/Category:X200)

If I could narrow it down between these 4 chips I could follow the instructions on said wiki:

    *  Intel Wifi Link 5100 (AGN)
    * Intel Wifi Link 5300 (AGN)
    * Intel WiMAX/WiFi Link 5150
    * Intel WiMAX/WiFi Link 5350

---

