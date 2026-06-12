---
title: "Can't connect to internet when there's a password. Ubuntu 13.04 and Realtek 8723."
date: 2013-06-16
forum: Networking &amp; Wireless
---

### Post by phoreeyes on 2013-06-16
I just installed Ubuntu 13.04 yesterday from a USB key, When I attempt to connect to my home network after I enter the password and wait a few seconds a message pops up notifying me I have been disconnected from internet... Although I was never connected. The password is entered correctly and the internet works just fine on my Ipod. When I connect to the free wifi (no password) at mcDonalds the internet works fine. I have seen [http://askubuntu.com/questions/286687/cant-connect-to-wifi-on-13-04](http://askubuntu.com/questions/286687/cant-connect-to-wifi-on-13-04) but the answer there did not help solve my problem and I have a realtek 8723 not 8188. I also upgraded my kernel to 3.9 as someone suggested that may help. It did not. Any help would be greatly appreciated, thanks very much!!

---

### Post by Techyte on 2013-06-17
It's an authentication  problem. A common Ubuntu bug. Try changing the password to a hex or completely remove the password. I am not 100% sure if the hex will work but removing the password will. Or just connect to a wired connection.

---

### Post by mastablasta on 2013-06-17
which password? for the keyring? note keyring password is (usually) not the same as user password.

---

### Post by phoreeyes on 2013-06-17
The password is the internet password. Unfortunatley the internet is for the entire apartment building and I'm unable to remove/change the password (although I'm sure that would work as I can connect whenever there isn't one). Is there any other way around this?

---

### Post by user_of_gnomes on 2013-06-17
You mean the network key for wireless?

---

### Post by phoreeyes on 2013-06-17
Yes, I have the correct password and all my other devices can connect fine.

---

### Post by varunendra on 2013-06-17
Please show us the card and driver in use -
```
lspci -nnk | grep -iA2 net
```

If it is a usb device, then -
```
lsusb
lsmod
```

If you know the driver in use, please also post -
```
modinfo *<driver name>*
```

---

### Post by phoreeyes on 2013-06-17
I'm at work right now, will update with that info when I get home. Thanks for the help!

---

### Post by phoreeyes on 2013-06-17
Terminal output for  lspci -nnk | grep -iA2 net:

```
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0726]
    Kernel driver in use: rtl8723ae
--
04:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 0a)
    Subsystem: CLEVO/KAPOK Computer Device [1558:1550]
    Kernel driver in use: r8168
```


Terminal output for lsusb:

```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 004: ID 0bda:8723 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 147e:1002 Upek 
Bus 002 Device 004: ID 5986:0308 Acer, Inc 
```



Terminal output for lsmod:


```
Module                  Size  Used by
parport_pc             28284  0 
ppdev                  17106  0 
rfcomm                 47863  12 
snd_hda_codec_hdmi     37407  1 
bnep                   18258  2 
joydev                 17613  0 
snd_hda_codec_via      31915  1 
coretemp               13596  0 
kvm_intel             138733  0 
uvcvideo               82296  0 
kvm                   452835  1 kvm_intel
videobuf2_vmalloc      13056  1 uvcvideo
nouveau              1001310  0 
arc4                   12573  2 
snd_hda_intel          44397  3 
videobuf2_memops       13202  1 videobuf2_vmalloc
snd_hda_codec         190010  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
rtl8723ae              88982  0 
ghash_clmulni_intel    13259  0 
rtlwifi                81185  1 rtl8723ae
i915                  631614  3 
aesni_intel            55449  0 
videobuf2_core         40785  1 uvcvideo
snd_hwdep              13613  1 snd_hda_codec
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
mac80211              656164  1 rtlwifi
videodev              131329  2 uvcvideo,videobuf2_core
ttm                    88251  1 nouveau
drm_kms_helper         49082  2 i915,nouveau
snd_page_alloc         18798  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30417  1 snd_seq_midi
aes_x86_64             17131  1 aesni_intel
psmouse                97838  0 
drm                   295908  6 ttm,i915,drm_kms_helper,nouveau
snd_seq                61930  2 snd_seq_midi_event,snd_seq_midi
cfg80211              547224  2 mac80211,rtlwifi
xts                    12922  1 aesni_intel
btusb                  18291  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29989  2 snd_pcm,snd_seq
lrw                    13294  1 aesni_intel
gf128mul               14951  2 lrw,xts
bluetooth             251354  22 bnep,btusb,rfcomm
i2c_algo_bit           13564  2 i915,nouveau
ablk_helper            13597  1 aesni_intel
lpc_ich                17060  0 
mei                    46588  0 
snd                    69533  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
serio_raw              13215  0 
soundcore              12680  1 snd
cryptd                 20501  3 ghash_clmulni_intel,aesni_intel,ablk_helper
rtsx_pci_ms            13180  0 
memstick               16605  1 rtsx_pci_ms
mxm_wmi                13021  1 nouveau
microcode              22923  0 
video                  19467  2 i915,nouveau
wmi                    19256  2 mxm_wmi,nouveau
lp                     17799  0 
parport                46562  3 lp,ppdev,parport_pc
mac_hid                13253  0 
hid_generic            12548  0 
usbhid                 47346  0 
hid                   101248  2 hid_generic,usbhid
rtsx_pci_sdmmc         17800  0 
ahci                   30063  2 
libahci                32088  1 ahci
rtsx_pci               33539  2 rtsx_pci_ms,rtsx_pci_sdmmc
r8168                 260963  0
```

---

### Post by squakie on 2013-06-17
post the output of:

ifconfig

iwconifg


Also, I have noticed in the past that sometimes it's best to go into network manager/edit connections and delete any definition that shows there for your network.  Then wait a few minutes and try to connect again.  It will ask for a password at that point.  Please take a desktop snapshot and post it back here.  Then enter in your password and when it fails take another screen shot and post it back here as well.

---

### Post by phoreeyes on 2013-06-17
...Well don't I feel silly, deleting the network from the manager and adding it again a couple minutes later has allowed me to connect!! However, I'm getting disconnected very frequently (mulitple times a minute) so I figured I'd post those outputs anyways. In chrome I get an error 21, say I can't see the page due to a change in network? Thanks for all the help!!!

ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:90:f5:d1:61:4f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:47 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1152 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:94232 (94.2 KB)  TX bytes:94232 (94.2 KB)

wlan0     Link encap:Ethernet  HWaddr 44:6d:57:52:cb:f4  
          inet6 addr: fe80::466d:57ff:fe52:cbf4/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:868 (868.0 B)  TX bytes:6967 (6.9 KB)
```

iwconfig:

```
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
```

---

### Post by varunendra on 2013-06-18
> **phoreeyes said:**
> ```
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0726]
    Kernel driver in use: **[COLOR="#800000"]rtl8723ae[/COLOR]**
```

Please post the outputs of :
```
modinfo rtl8723ae
sudo iwlist scan
dmesg | grep rtl87
```

Let's see if there are any parameters for the driver that may help.
The second command is to just double-check that everything is okay with the access-point signals, I know you can't change it.

---

### Post by phoreeyes on 2013-06-18
modinfo rtl8723ae:


```
filename:       /lib/modules/3.9.0-030900-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
firmware:       rtlwifi/rtl8723aefw_B.bin
firmware:       rtlwifi/rtl8723aefw.bin
description:    Realtek 8723E 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     623F242E0943DFB93EDE7EA
alias:          pci:v000010ECd00008723sv*sd*bc*sc*i*
depends:        rtlwifi
intree:         Y
vermagic:       3.9.0-030900-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

```



sudo iwlist scan:


```
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: 98:FC:11:54:01:87
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"7421stlaurent2_4Ghz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001655a0f847
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 00133734323173746C617572656E74325F3447687A
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7A0050F204104A00011010440001021041000100103B00010310470010A5B2C8364F5151C0F591C133E507439610210005436973636F1023000D4C696E6B7379732045333030301024000776312E302E30311042000234321054000800060050F20400011011000D4C696E6B737973204533303030100800020084
                    IE: Unknown: DD09001018020FF0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33FC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001700000000000000000000000000000000000000
          Cell 02 - Address: 00:1C:F0:F6:D7:09
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"3 jules-verne"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000025dabc2181
                    Extra: Last beacon: 4356ms ago
                    IE: Unknown: 000D33206A756C65732D7665726E65
                    IE: Unknown: 010802040B160C183048
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F01010006FF7F
                    IE: Unknown: DD0C00037F020101010002A44000
          Cell 03 - Address: CC:B2:55:DD:9A:F6
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Loschupitos"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003455688a158
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000B4C6F736368757069746F73
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1013FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601050100000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500004C127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706434120010B10
          Cell 04 - Address: 84:C9:B2:D0:A5:BA
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"VIDEOTRON7995"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000167ec808db
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000D564944454F54524F4E37393935
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B0F0800000000000000000000000000000000000000
                    IE: Unknown: 3D160B0F0800000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD940050F204104A00011010440001021057000101103B00010310470010BD10B7981DD111B2A902A53AD2E456FF10210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D383235104200046E6F6E651054000800060050F2040001101100074449522D383235100800020084103C000103104900140024E26002000101600000020001600100020001
          Cell 05 - Address: 64:70:02:A2:F2:A8
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"VIF"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000023d6b48c4fa
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 0003564946
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B000700000000000000000000000000000000000000
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
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706555300010B10
                    IE: Unknown: DD9D0050F204104A0001101044000102103B00010310470010BC329E001DD811B28601647002A2F2A81021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B415053100800020084103C000100
          Cell 06 - Address: 00:1E:52:7C:55:2C
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006491e15907
                    Extra: Last beacon: 128ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400030000
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A0C501BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101060003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301690320
                    IE: Unknown: DD0E0017F20700010106001E527C552C
                    IE: Unknown: DD0B0017F2010001010000000B
          Cell 07 - Address: BC:AE:C5:C3:61:51
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"camionlime"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000017857e8b76
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000A63616D696F6E6C696D65
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AEC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD890050F204104A00011010440001021041000100103B00010310470010F914CFC9218F9F58E4B39C79B8910C21102100074153555354656B1023000F576972656C65737320526F75746572102400063132333435361042000234351054000800060050F2040001101100144153555320576972656C65737320526F75746572100800020084103C000101
                    IE: Unknown: DD090010180205F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 08 - Address: 4C:17:EB:E2:48:9D
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"BELL123"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002e77325162
                    Extra: Last beacon: 244ms ago
                    IE: Unknown: 000742454C4C313233
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706434120010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A8804C17EBE2489D103C000101
                    IE: Unknown: 050400010030
                    IE: Unknown: 2A0106
                    IE: Unknown: 2D1A6E1016FFFFFF0001000000000000000000000000030000000000
                    IE: Unknown: 3D160B000600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020035127A
                    IE: Unknown: DD07000C4300000000
          Cell 09 - Address: 00:26:82:FE:DD:74
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"BELL722"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000119410e5164
                    Extra: Last beacon: 156ms ago
                    IE: Unknown: 000742454C4C373232
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A0C0017FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D160B000100000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500003B127A
                    IE: Unknown: DD1E00904C330C0017FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340B000100000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 10 - Address: 84:C9:B2:4E:75:EB
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004d67a1ad80
                    Extra: Last beacon: 2908ms ago
                    IE: Unknown: 0005646C696E6B
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030105
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD260050F204104A0001101044000102104900140024E26002000101600000020001600100020001
          Cell 11 - Address: 3C:EA:4F:7B:66:39
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"BELL178"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000965a055181
                    Extra: Last beacon: 2904ms ago
                    IE: Unknown: 000742454C4C313738
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
          Cell 12 - Address: 5C:D9:98:6C:26:A0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Jolie Annie"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000582b19d80
                    Extra: Last beacon: 2556ms ago
                    IE: Unknown: 000B4A6F6C696520416E6E6965
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001900000000000000000000000000000000000000
                    IE: Unknown: 3D1606001900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD260050F204104A0001101044000102104900140024E26002000101600000020001600100020001

```





dmesg | grep rtl87:


```
[   15.265015] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin

```

---

### Post by wildmanne39 on 2013-06-18
*Thread moved to **Networking & Wireless**.*

---

### Post by varunendra on 2013-06-18
Which of the above scanned access-points was yours?
None of them seem optimal to me though. Some have poor signal quality (30/70 or less) with too much noise, others don't have the optimal encryption type (which is pure WPA2-PSK (AES)) or non-overlapping channels (channels 1 and 11 are supposed to be the best for most people).

The driver does have some parameters to play with -
> **phoreeyes said:**
> 
```

parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

```

You may try -
```
sudo modprobe -rfv rtl8723ae
sudo modprobe -v rtl8723ae swenc=Y
```
The first command will remove the driver (thus disabling the wireless),
the second will load it again with "swenc=Y" parameter (which is meant to take the burden of packet encryption away from card's hardware, and let it be done by the OS).

You may also try **ips=N** or **fwlps=N** insetad of swenc=Y, or a combination of these in the second command above. For example -
```
sudo modprobe -rfv rtl8723ae
sudo modprobe -v rtl8723ae swenc=Y ips=N
```
These will be temporary changes for the running session only. Everything will be reset to default on reboot. If any of the above seems to help, we can make them permanent.

---

### Post by phoreeyes on 2013-06-18
"7421stlaurent2_4Ghz" Is what I'm connecting to.  Setting swenc=Y hasn't seemed to help at all but I will continue to try more combinations.

---

### Post by varunendra on 2013-06-18
> **phoreeyes said:**
> "7421stlaurent2_4Ghz" Is what I'm connecting to.

Uh oh.. ! It has the worst kind of encryption with worst performance reputation - WPA/WPA2 mixed mode with TKIP :(
That is besides the poor signal quality (30/70) and too much noise (-80 dBm, upto -64 is usually okay, near -50 is good).

I don't think any of the parameters is going to help, but try them anyway.

If you can, you may request whoever controls the access point to change the encryption type to pure WPA2-PSK with AES.

---

### Post by phoreeyes on 2013-06-19
Well I haven't changed anything since yesterday but when I booted up today after a rough half hour or so everything seems to be working fine now... Thanks so much for all your help!!!

---

### Post by varunendra on 2013-06-20
> **phoreeyes said:**
> Well I haven't changed anything since yesterday but when I booted up today after a rough half hour or so everything seems to be working fine now... Thanks so much for all your help!!!

Glad it fixed itself. :)

One way to keep track of what changed between the good and bad situations is to check the outputs of these commands (and notice changes) -
```
iwconfig
sudo iwlist scan
```

The output of the second command maybe long. Only the part related to the access-point you are connected to is relevant in it, ignore the rest.

Not everything in these outputs can be controlled, but most things can be. And you can always safely try the parameters I suggested in my previous post. However, the instructions were for temporary change only. So if the connection got better after a reboot, they have no role in it - as you seem to already understand.

---

