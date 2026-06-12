---
title: "Slow/no wireless upload on Aspire 5102"
date: 2011-01-10
forum: Networking &amp; Wireless
---

### Post by whitlecj on 2011-01-10
I am having issues with wireless really in general on an Acer Aspire 5102.  this is my first linux experience and it has been great with this exception.  i cannot upload a 1 mb file to my dropbox at all.  I have also been having problems browsing some websites. Logging into mint is an example.  It works fine on a wired connection.  I am very new to linux is there anyway to fix this?  Would some other version or distribution of linux be better for this laptop.  It has a 1.6ghz AMD Turion processor and 1gb of ram.

Thanks for any help you can give.

---

### Post by PatchesTheCaveman on 2011-01-11
Please provide diagnostic information as requested in this post:
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by whitlecj on 2011-01-11
Thank you.  Here is the info

1 ) Machine Brand and Model (PC/Laptop):
```
Acer Aspire 5102 WLMi
```

2 ) Wireless Brand, Model and Wireless Chipset:
```
06:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
```
3 ) check interface:
```
wlan0     IEEE 802.11bg  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: C0:3F:0E:56:E4:C8   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-29 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
4 ) Check for modules:
```
Module                  Size  Used by
aes_i586                7280  2 
aes_generic            26875  1 aes_i586
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
joydev                  8767  0 
snd_hda_codec_realtek   218227  1 
arc4                    1165  2 
snd_hda_intel          22107  4 
radeon                828445  4 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  3 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
ath5k                 130083  0 
pcmcia                 35973  0 
ttm                    56633  1 radeon
snd_rawmidi            17783  1 snd_seq_midi
mac80211              231541  1 ath5k
drm_kms_helper         30200  1 radeon
snd_seq_midi_event      6047  1 snd_seq_midi
ath                     8153  1 ath5k
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
video                  18712  0 
output                  1883  1 video
snd_timer              19067  2 snd_pcm,snd_seq
gspca_m5602            52354  0 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168092  6 radeon,ttm,drm_kms_helper
yenta_socket           21518  0 
gspca_main             23644  1 gspca_m5602
cfg80211              144470  3 ath5k,mac80211,ath
snd                    49038  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            10566  1 yenta_socket
videodev               43098  1 gspca_main
v4l1_compat            13359  1 videodev
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
ati_agp                 5202  0 
psmouse                59033  0 
soundcore                880  1 snd
serio_raw               4022  0 
i2c_algo_bit            5168  1 radeon
k8temp                  3228  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
i2c_piix4               8635  0 
shpchp                 29886  0 
agpgart                32011  3 ttm,drm,ati_agp
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
8139too                19581  0 
sdhci_pci               6339  0 
8139cp                 16934  0 
sdhci                  15890  1 sdhci_pci
led_class               2633  2 ath5k,sdhci
mii                     4425  2 8139too,8139cp
pata_atiixp             3288  2 
```
5 ) Kernel boot messages
```
[   23.542301] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.578497] Console: switching to colour frame buffer device 160x50
[   23.588856] fb0: radeondrmfb frame buffer device
[   23.588859] drm: registered panic notifier
[   23.588904] Slow work thread pool: Starting up
[   23.588969] Slow work thread pool: Ready
[   23.588979] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:05.0 on minor 0
[   23.708381] ppdev: user-space parallel port driver
[   27.781441] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   47.778883] wlan0: authenticate with c0:3f:0e:56:e4:c8 (try 1)
[   47.780634] wlan0: authenticated
[   47.780666] wlan0: associate with c0:3f:0e:56:e4:c8 (try 1)
[   47.782832] wlan0: RX AssocResp from c0:3f:0e:56:e4:c8 (capab=0x411 status=0 aid=5)
[   47.782838] wlan0: associated
[   47.783696] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   47.917539] padlock: VIA PadLock not detected.
[   89.157053] Clocksource tsc unstable (delta = -249850234 ns)
[ 1494.970377] lo: Disabled Privacy Extensions

```)

6 ) Network configuration
```
*-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:14:56:6a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:21 ioport:a000(size=256) memory:c0210000-c02100ff
  *-network:1
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: wlan0
       version: 01
       serial: 00:16:ce:55:ec:cc
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-24-generic firmware=N/A ip=10.0.0.11 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:22 memory:c0200000-c020ffff

```
7 ) Scan for networks:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: C0:3F:0E:56:E4:C8
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-31 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000006dfc29529
                    Extra: Last beacon: 908984ms ago
                    IE: Unknown: 00074E455447454152
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1606051700000000000000000000000000000000000000
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B0001031047001017990A514B62E0CCD13C2D0CC24E7B0D1021000D4E4554474541522C20496E632E10230008574E52333530304C10240008574E52333530304C10420004333530301054000800060050F204000110110008574E52333530304C100800020084
                    IE: Unknown: DD090010180206F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406051700000000000000000000000000000000000000

```
8 ) Ubuntu Version: 
```
Description:	Ubuntu 10.10

```
9 ) Kernel/architecture (including 32 vs. 64 bit): 
```
2.6.35-24-generic i686

```
10 ) Restarting the network:
```
 * Reconfiguring network interfaces...                                                                                                               Ignoring unknown interface wlan0=wlan0.

```


Thanks for any help anyone can provide.

---

### Post by whitlecj on 2011-01-11
Still can't resolve the problem.  I even tried installing another distro(opensuse) and it had the same issue.  Anyone have any idea how to fix this?

---

