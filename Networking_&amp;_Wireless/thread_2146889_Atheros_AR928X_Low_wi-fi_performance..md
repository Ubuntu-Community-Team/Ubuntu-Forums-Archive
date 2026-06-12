---
title: "Atheros AR928X: Low wi-fi performance."
date: 2013-05-20
forum: Networking &amp; Wireless
---

### Post by adrian89 on 2013-05-20
I've used ubuntu 12.04 LTS and since 13.04 I upgraded but on both I had the same problem with my wi-fi signal.
Example, in the same place my laptop has at max 50% of signal strength while a tablet has around 90%, and this is not the strangest thing yet, if the tablet disconnects(from different reasons:manual disc,batter preservation) the signal becomes more unstable, the most of the resulting in a disconnect from the wireless network of my laptop,and I need reconnect the tablet or get closer the router to reconnect the laptop.

I have windows 7 on my laptop aswell and had this problem until I installed the laptop's driver after which the network experience changed(no much,but changed).
Meaning: at startup I get around 90% of wireless strength,after which it drops at "2-3 lines" of wireless signal.

Any ideea on how/if I can get more signal strength?

---

### Post by praseodym on 2013-05-20
Please show the outputs of:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
sudo iwlist scan
ifconfig -a
```

---

### Post by adrian89 on 2013-05-21
lspci -nnk | grep -iA2 net
```

04:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)    Subsystem: Lite-On Communications Inc Device [11ad:6632]
    Kernel driver in use: ath9k
05:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8132 Fast Ethernet [1969:1062] (rev c0)
    Subsystem: Acer Incorporated [ALI] Device [1025:0212]
    Kernel driver in use: atl1c



```


lsusb
```
Bus 002 Device 003: ID 064e:a103 Suyin Corp. Acer/HP Integrated Webcam [CN0314]
Bus 004 Device 003: ID 093a:2521 Pixart Imaging, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

lsmod
```

Module                  Size  Used by
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  0 
bnep                   18036  2 
bluetooth             228619  10 bnep,rfcomm
binfmt_misc            17500  1 
arc4                   12615  2 
ath9k                 149924  0 
ath9k_common           14055  1 ath9k
uvcvideo               80847  0 
ath9k_hw              413680  2 ath9k_common,ath9k
snd_hda_codec_realtek    78399  1 
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
mac80211              606457  1 ath9k
snd_hda_intel          39619  3 
snd_hda_codec         136453  2 snd_hda_codec_realtek,snd_hda_intel
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
coretemp               13355  0 
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  2 snd_hda_codec,snd_hda_intel
joydev                 17377  0 
cfg80211              510937  3 ath,ath9k,mac80211
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
acer_wmi               32467  0 
sparse_keymap          13890  1 acer_wmi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
psmouse                95870  0 
snd                    68876  15 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
microcode              22881  0 
serio_raw              13215  0 
lpc_ich                17061  0 
soundcore              12680  1 snd
lp                     17759  0 
mac_hid                13205  0 
parport                46345  3 lp,ppdev,parport_pc
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
mxm_wmi                13021  0 
radeon                937749  3 
i2c_algo_bit           13413  1 radeon
ttm                    83187  1 radeon
wmi                    19070  2 acer_wmi,mxm_wmi
video                  19390  1 acer_wmi
ahci                   25731  3 
atl1c                  41071  0 
libahci                31364  1 ahci
drm_kms_helper         49394  1 radeon
drm                   286313  5 ttm,drm_kms_helper,radeon



```

iwconfig
```
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"wireless"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 82:4C:A9:A2:78:A4   
          Bit Rate=39 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=37/70  Signal level=-73 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:25   Missed beacon:0
```

sudo iwlist scan
```

eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: 82:4C:A9:A2:78:A4
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"papadopoulos2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000017fe08c2ed8
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 000D70617061646F706F756C6F7332
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A8E1103FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DDA20050F204104A0001101044000102103B00010310470010BC329E001DD811B28601824CA9A278A41021001D48756177656920546563686E6F6C6F6769657320436F2E2C204C74642E1023001C48756177656920576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F204000110110009487561776569415053100800020084103C000100
                    IE: Unknown: 0B05030008127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706434120010D10
                    IE: Unknown: DD1E00904C338E1103FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401050700000000000000000000000000000000000000
          Cell 02 - Address: 82:4C:A9:A2:78:A5
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"RomTelecom-WPA-78A4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000017fe08c3f8a
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 0013526F6D54656C65636F6D2D5750412D37384134
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A8E1103FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05030008127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706434120010D10
                    IE: Unknown: DD1E00904C338E1103FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401050700000000000000000000000000000000000000
          Cell 03 - Address: 00:21:91:6C:2E:08
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"papadopoulos"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003c43c4b9a57
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 000C70617061646F706F756C6F73
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 82:D1:5E:0D:28:75
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"RomTelecom-WPA-2874"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c646a1af44
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 0013526F6D54656C65636F6D2D5750412D32383734
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A8E1103FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B070000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000006127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706434120010D10
          Cell 05 - Address: 82:D1:5E:0D:28:74
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"papser"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c646a1a010
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 0006706170736572
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A8E1103FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B070000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DDA20050F204104A0001101044000102103B00010310470010BC329E001DD811B2860182D15E0D28741021001D48756177656920546563686E6F6C6F6769657320436F2E2C204C74642E1023001C48756177656920576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F204000110110009487561776569415053100800020084103C000100
                    IE: Unknown: 0B05000006127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706434120010D10

```

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 70:5a:b6:24:f0:d1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1333 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1333 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:113094 (113.0 KB)  TX bytes:113094 (113.0 KB)


wlan0     Link encap:Ethernet  HWaddr 70:1a:04:da:2b:b5  
          inet addr:192.168.0.171  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::721a:4ff:feda:2bb5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6384 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6297 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5289148 (5.2 MB)  TX bytes:1364691 (1.3 MB)



```
When I wrote this post I was connect to one ssid until ifconfig -a which was made on other network hope this didn't matter.

---

### Post by praseodym on 2013-05-21
Deactivate the hardware encryption of the driver:
```

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by adrian89 on 2013-05-22
thank you I'l let you know if it works or not

---

