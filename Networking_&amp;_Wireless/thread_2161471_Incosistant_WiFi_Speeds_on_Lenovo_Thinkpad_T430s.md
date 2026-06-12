---
title: "Incosistant WiFi Speeds on Lenovo Thinkpad T430s"
date: 2013-07-10
forum: Networking &amp; Wireless
---

### Post by zaza224 on 2013-07-10
I have a Lenovo Thinkpad T430s running Ubuntu 13.04 (technically, I'm running Linux Mint 15 but it's based off Ubuntu 13.04) and have been having serious issues with my wireless internet. While in Firefox or Minecraft, the wifi speed often drops or fails completely randomly despite the signal strength staying the same and others in the house reporting no issues. :confused: I've already tried disabling N and reverting to G but that only seemed to work for a short while. Please help!

P.S. If I can get this working again, I would also like to revert back to N.

---

### Post by praseodym on 2013-07-11
Please show the outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
iwlist chan
ifconfig -a
sudo iwlist scan
```

---

### Post by zaza224 on 2013-07-11
[SIZE=3][FONT=times new roman]1. 
```
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:21f3]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
    Kernel driver in use: rtl8192ce
```

2.
```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 006: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 003 Device 005: ID 04d9:2323 Holtek Semiconductor, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 5986:02d5 Acer, Inc 
Bus 002 Device 009: ID 17ef:100a Lenovo ThinkPad Mini Dock Plus Series 3
Bus 002 Device 011: ID 046d:0802 Logitech, Inc. Webcam C200
Bus 002 Device 010: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
```

3.
```
Module                  Size  Used by
parport_pc             28152  0 
bnep                   18036  2 
rfcomm                 42641  0 
ppdev                  17073  0 
bluetooth             228619  10 bnep,rfcomm
binfmt_misc            17500  1 
arc4                   12615  2 
ext2                   72837  1 
rtl8192ce              53594  0 
rtlwifi                79673  1 rtl8192ce
rtl8192c_common        48779  1 rtl8192ce
mac80211              606457  3 rtlwifi,rtl8192c_common,rtl8192ce
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
joydev                 17377  0 
videodev              129260  2 uvcvideo,videobuf2_core
cfg80211              510937  2 mac80211,rtlwifi
snd_usb_audio         140685  1 
snd_usbmidi_lib        24938  1 snd_usb_audio
coretemp               13355  0 
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_realtek    78399  1 
kvm                   443165  0 
snd_hda_intel          39619  5 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
snd_pcm                97451  5 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
thinkpad_acpi          81222  0 
dm_multipath           22843  0 
ghash_clmulni_intel    13259  0 
nvram                  14362  1 thinkpad_acpi
scsi_dh                14843  1 dm_multipath
psmouse                95870  0 
aesni_intel            55399  2 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  2 snd_usbmidi_lib,snd_seq_midi
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
mei                    41158  0 
ablk_helper            13597  1 aesni_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
lpc_ich                17061  0 
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
serio_raw              13215  0 
microcode              22881  0 
snd                     68876  24  snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device
tpm_tis                18675  0 
soundcore              12680  1 snd
mac_hid                13205  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
btrfs                 785967  0 
zlib_deflate           26885  1 btrfs
libcrc32c              12615  1 btrfs
dm_raid45              76725  0 
xor                    17116  1 dm_raid45
dm_mirror              21946  0 
dm_region_hash         20820  1 dm_mirror
dm_log                 18529  3 dm_region_hash,dm_mirror,dm_raid45
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
nouveau               939088  0 
i915                  600351  3 
ahci                   25731  4 
libahci                31364  1 ahci
mxm_wmi                13021  1 nouveau
wmi                    19070  2 mxm_wmi,nouveau
video                  19390  2 i915,nouveau
i2c_algo_bit           13413  2 i915,nouveau
ttm                    83187  1 nouveau
drm_kms_helper         49394  2 i915,nouveau
drm                   286313  6 ttm,i915,drm_kms_helper,nouveau
e1000e                198787  0
```

4.
```
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"saunders"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1D:D0:DA:FE:40   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4   Missed beacon:0
```

5.
```
eth0      no frequency information.

lo        no frequency information.

wlan0     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.437 GHz (Channel 6)
```

6.
```
eth0      Link encap:Ethernet  HWaddr 3c:97:0e:98:e1:db  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f3500000-f3520000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3466 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3466 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:343049 (343.0 KB)  TX bytes:343049 (343.0 KB)

wlan0     Link encap:Ethernet  HWaddr a4:17:31:f9:fe:ee  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::a617:31ff:fef9:feee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1419058 errors:0 dropped:0 overruns:0 frame:0
          TX packets:783413 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1132568486 (1.1 GB)  TX bytes:75420733 (75.4 MB)

```

7.
```
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1D:D0:DA:FE:40
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"saunders"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007bbcd69ddf
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 00087361756E64657273
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6C0017FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1606000400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05080028127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706555320010B10
                     IE: Unknown:  DD7D0050F204104A0001101044000102103B000103104700102880288028801880A880001DD0DAFE4010210005415252495310230006544738363247102400065254323836301042000831323334353637381054000800060050F204000110110012415252495320544738363220526F75746572100800020084103C000101
          Cell 02 - Address: 9C:D3:6D:B0:10:9A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"33liverpool"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000bcf1a10183
                    Extra: Last beacon: 820ms ago
                    IE: Unknown: 000B33336C69766572706F6F6C
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180201F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001300000000000000000000000000000000000000
          Cell 03 - Address: 00:0D:67:2C:46:14
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007bb7fc2180
                    Extra: Last beacon: 764ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 01088B960C1218243048
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 070655534F010D1E
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: 2D1AAD0103FFE0E000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1601001500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101060003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 04 - Address: 00:1D:D6:40:76:B0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"Wilker"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c0eacac147
                    Extra: Last beacon: 488ms ago
                    IE: Unknown: 000657696C6B6572
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 070C55532001010F0209110B010F
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A880001DD64076B0103C000101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0106
                    IE: Unknown: 2D1A6C0017FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1606030500000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010036127A
                    IE: Unknown: DD07000C4307000000
          Cell 05 - Address: 94:CC:B9:BB:9B:F0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"ATT344"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000060927ab183
                    Extra: Last beacon: 360ms ago
                    IE: Unknown: 0006415454333434
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180201F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: 00:13:D4:D6:0C:06
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"Wireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000068afa45d66
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 0008576972656C657373
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020000
```
[/FONT][/SIZE]

---

### Post by wildmanne39 on 2013-07-11
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by tgalati4 on 2013-07-11
I don't see anything amiss with your log files.  I would try a wired connection for a while and see if you notice any slowdowns.  It could be some background processes that are eating up CPU time and tying up the data bus.  This would appear to be network slow-downs, but are really CPU/IO WAIT issues.  Once you have done that then look at your log files in /var/log and see if there are any errors that are recurring.

I would suspect wireless interference.  You have no RX/TX errors in over 1 GB of data transfer, so I assume that your wireless antenna and chipset are working OK.  Channel 6 is in the middle of the band.  Try setting your router to Channel 1 or 11 or auto and see if you have better throughput.  How many wireless networks show up when you press on the Antenna icon?

---

### Post by zaza224 on 2013-07-11
> How many wireless networks show up when you press on the Antenna icon? 				

About 5.

---

### Post by praseodym on 2013-07-12
This driver need additional options:
```

echo "options rtl8192ce swlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce
```

---

