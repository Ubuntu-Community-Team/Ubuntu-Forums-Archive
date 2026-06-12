---
title: "Wireless card sees networks but can't connect (Dell Vostro V13, Lubuntu 10.10)"
date: 2012-03-13
forum: Networking &amp; Wireless
---

### Post by Stebbins on 2012-03-13
My wireless card (built-in on the Vostro V13) is showing available networks, but it can't connect to any of them. They have strong signals, and until about 24 hours ago I could connect to them with no problems. I've tried disabling and re-enabling my wireless card. I've tried waiting. The Ethernet connection works fine.

Any idea what could be the issue? Below I've tried to include all the information requested in the HOWTO thread. Thanks for taking the time to help... sorry if I did something stupid!

**1) Machine Model**
Dell Vostro V13

**2) Wireless Model (lspci output)**
```
09:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
```

**3) ifconfig output**
```
wlan0     Link encap:Ethernet  HWaddr 00:24:d6:af:48:42  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:746445 errors:0 dropped:0 overruns:0 frame:0
          TX packets:242730 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:462941444 (462.9 MB)  TX bytes:37633250 (37.6 MB)
```

**3b) iwconfig output**
```
wlan0     IEEE 802.11abg  ESSID:"AugerABGN01"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

**4) Modules**
*(I'm unsure what is relevant, so I've dumped all the lsmod output)*
```
Module                  Size  Used by
aes_i586                7280  0 
aes_generic            26875  1 aes_i586
rfcomm                 33843  4 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37040  16 rfcomm,bnep
btusb                  11065  2 
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
usbhid                 36882  0 
hid                    67934  1 usbhid
snd_hda_codec_realtek   218460  1 
joydev                  8767  0 
snd_hda_intel          22235  1 
arc4                    1165  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
i915                  296139  3 
iwlagn                179111  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  3 snd_seq_midi,snd_seq_midi_event
iwlcore               127415  1 iwlagn
drm_kms_helper         30200  1 i915
mac80211              231959  2 iwlagn,iwlcore
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168124  3 i915,drm_kms_helper
uvcvideo               55943  0 
videodev               43194  1 uvcvideo
cfg80211              144758  3 iwlagn,iwlcore,mac80211
dell_laptop             5730  0 
dcdbas                  5402  1 dell_laptop
psmouse                59027  0 
v4l1_compat            13359  2 uvcvideo,videodev
intel_agp              26566  2 i915
serio_raw               4022  0 
snd                    49102  12 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            5168  1 i915
agpgart                32011  2 drm,intel_agp
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
video                  18712  1 i915
```

**5) Kernel boot messages pertaining to wlan0**
```
[165062.706080] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[165812.112998] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[165837.984040] wlan0: no IPv6 routers present
[166162.917807] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[166246.933446] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[166417.457038] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[170697.045743] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[185909.921859] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[185934.961136] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[209057.305164] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[209140.088788] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[209398.201465] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[209417.649489] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[209438.781911] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[209504.369432] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[209514.041529] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[209525.921402] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[209536.845717] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[209546.965399] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[209556.889450] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[209587.701460] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[209592.729458] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[209595.677585] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[209598.472950] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[209602.121565] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[209605.738282] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[209609.781444] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[209614.324384] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[209619.421451] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[209627.219710] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[209645.201714] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[209739.433233] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[209774.441113] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[209855.294130] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[209910.377441] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[209976.792847] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[210074.117673] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[210099.882041] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[210118.445693] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[212497.296244] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

**6) Network configuration**
```
  *-network
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlan0
       version: 00
       serial: 00:24:d6:af:48:42
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-32-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:47 memory:c8000000-c8001fff
```

**7) Available Networks** *(I have successfully connected to both of these in the past)*
```
          Cell 01 - Address: 68:7F:74:35:86:08
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:off
                    ESSID:"AugerABGN01"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    ESSID:""
                    ESSID:""
                    Mode:Master
                    Extra:tsf=00000108c4eec183
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 000B41756765724142474E3031
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 05050001030001
                    IE: Unknown: 2A0107
                    IE: Unknown: 2F0107
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180225F4050000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001700000000000000000000000000000000000000
                    IE: Unknown: 0000
                    IE: Unknown: 0000
          Cell 02 - Address: 68:7F:74:35:86:80
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:off
                    ESSID:"AugerABGN03"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000108c512b184
                    Extra: Last beacon: 204ms ago
                    IE: Unknown: 000B41756765724142474E3033
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010100
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD09001018020AF4050000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001700000000000000000000000000000000000000
```

**8. Ubuntu version**
Lubuntu 10.10

**9) Kernel architecture**
2.6.35-32-generic i686

**10) Restarting network**
*changes nothing. Output:*
```
 * Reconfiguring network interfaces...
```

---

### Post by Stebbins on 2012-03-22
I solved my problem. I did an apt-get dist-upgrade, rebooted the machine, and now everything appears to be functioning properly.

---

