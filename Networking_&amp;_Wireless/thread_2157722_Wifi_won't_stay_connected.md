---
title: "Wifi won't stay connected"
date: 2013-06-26
forum: Networking &amp; Wireless
---

### Post by c0lon on 2013-06-26
I just installed 13.04 and I can connect to wireless networks and at first, everything is fine. Then after a few minutes, I can't access the internet even though I'm still connected to Wifi. Then Ubuntu prompts me for the network password, and even after that it doesn't work. From then on I can only access the internet every once in a while, but only for a few minutes.

I'm pretty new to Linux so sorry that I haven't included any information but someone just let me know what to do.

Thanks in advance

---

### Post by praseodym on 2013-06-26
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
sudo iwlist scan
```

---

### Post by c0lon on 2013-06-27
$ lspci -nnk | grep -iA2 net

31-00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
32-    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
33:01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
34-    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
35-    Kernel driver in use: alx
36:02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]
37-    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0724]
38-    Kernel driver in use: rtl8723ae

$ lsusb

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0930:021d Toshiba Corp. 
Bus 001 Device 004: ID 10f1:1a43 Importek 
Bus 003 Device 003: ID 0bc2:a013 Seagate RSS LLC 
Bus 003 Device 004: ID 03f0:a407 Hewlett-Packard 
Bus 003 Device 005: ID 03f0:5307 Hewlett-Packard 

$ lsmod

Module Size Used by
parport_pc 28152 0 
ppdev 17073 0 
rfcomm 42641 12 
bnep 18036 2 
nls_iso8859_1 12713 2 
snd_hda_codec_hdmi 36913 1 
snd_hda_codec_realtek 78399 1 
btusb 22474 0 
bluetooth 228619 22 bnep,btusb,rfcomm
uvcvideo 80847 0 
videobuf2_vmalloc 13056 1 uvcvideo
rts5139 352481 0 
videobuf2_memops 13202 1 videobuf2_vmalloc
videobuf2_core 40513 1 uvcvideo
joydev 17377 0 
videodev 129260 2 uvcvideo,videobuf2_core
arc4 12615 2 
coretemp 13355 0 
kvm_intel 132891 0 
kvm 443165 1 kvm_intel
ghash_clmulni_intel 13259 0 
aesni_intel 55399 1 
aes_x86_64 17255 1 aesni_intel
xts 12885 1 aesni_intel
lrw 13257 1 aesni_intel
gf128mul 14951 2 lrw,xts
ablk_helper 13597 1 aesni_intel
cryptd 20373 3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_intel 39619 3 
snd_hda_codec 136453 3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep 13602 1 snd_hda_codec
snd_pcm 97451 3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc 18710 2 snd_pcm,snd_hda_intel
rtl8723ae 86459 0 
toshiba_bluetooth 12852 0 
rtlwifi 79673 1 rtl8723ae
snd_seq_midi 13324 0 
snd_seq_midi_event 14899 1 snd_seq_midi
mac80211 606457 1 rtlwifi
snd_rawmidi 30180 1 snd_seq_midi
i915 600396 3 
snd_seq 61554 2 snd_seq_midi_event,snd_seq_midi
cfg80211 510937 2 mac80211,rtlwifi
snd_seq_device 14497 3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer 29425 2 snd_pcm,snd_seq
video 19390 1 i915
mac_hid 13205 0 
drm_kms_helper 49394 1 i915
mei 41158 0 
snd 68876 16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
drm 286028 4 i915,drm_kms_helper
alx 67960 0 
soundcore 12680 1 snd
mdio 13807 1 alx
i2c_algo_bit 13413 1 i915
lp 17759 0 
lpc_ich 17061 0 
parport 46345 3 lp,ppdev,parport_pc
psmouse 95870 0 
serio_raw 13215 0 
microcode 22881 0 
hid_generic 12540 0 
usbhid 47074 0 
hid 101002 2 hid_generic,usbhid
usb_storage 57204 3 
ahci 25731 3 
libahci 31364 1 ahci

$ iwconfig

wlan0 IEEE 802.11bgn ESSID:"The Spot" 
Mode:Managed Frequency:2.437 GHz Access Point: C0:C1:C0:EA:7F:83 
Bit Rate=72.2 Mb/s Tx-Power=20 dBm 
Retry long limit:7 RTS thr=2347 B Fragment thrff
Power Managementff
Link Quality=70/70 Signal level=26 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:27 Missed beacon:0

$ sudo iwlist scan

wlan0 Scan completed :
Cell 01 - Address: C0:C1:C0:EA:7F:83
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=70/70 Signal level=26 dBm 
Encryption keyn
ESSID:"The Spot"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=00000198d6ce2183
Extra: Last beacon: 592ms ago
IE: Unknown: 00085468652053706F74
IE: Unknown: 010882848B962430486C
IE: Unknown: 030106
IE: Unknown: 2A0104
IE: Unknown: 2F0104
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: 32040C121860
IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
IE: Unknown: 3D1606081500000000000000000000000000000000000000
IE: Unknown: DD7F0050F204104A00011010440001011041000100103B0001031047001026A27B0A4A207D7D81AB25776F6286BF10210005436973636F1023000D4C696E6B7379732045313535301024000776312E302E30301042000234321054000800060050F20400011011000D4C696E6B737973204531353530100800020084103C000101
IE: Unknown: DD090010180205F0040000
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
Cell 02 - Address: B8:9B:C9:B6:9A:E9
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=46/70 Signal level=-64 dBm 
Encryption keyn
ESSID:""
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
18 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=0000022de93cfc75
Extra: Last beacon: 5388ms ago
IE: Unknown: 0000
IE: Unknown: 010882848B961224486C
IE: Unknown: 030101
IE: Unknown: 32040C183060
IE: Unknown: 0706555320010B14
IE: Unknown: 33082001020304050607
IE: Unknown: 33082105060708090A0B
IE: Unknown: 050400010000
IE: Unknown: 2A0106
IE: Unknown: 2D1AEE1117FFFFFF0001000000000000000000000000030000000000
IE: Unknown: 3D1601000700000000000000000000000000000000000000
IE: Unknown: 4A0E14000A002C01C800140005001900
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
IE: Unknown: 0B05020025127A
IE: Unknown: DD07000C4300000000
Cell 03 - Address: B8:9B:C9:B6:9A:EA
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=50/70 Signal level=-60 dBm 
Encryption keyn
ESSID:""
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
18 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=0000022de9803463
Extra: Last beacon: 980ms ago
IE: Unknown: 0000
IE: Unknown: 010882848B961224486C
IE: Unknown: 030101
IE: Unknown: 32040C183060
IE: Unknown: 0706555320010B14
IE: Unknown: 33082001020304050607
IE: Unknown: 33082105060708090A0B
IE: Unknown: 050400010000
IE: Unknown: 2A0106
IE: Unknown: 2D1AEE1117FFFFFF0001000000000000000000000000030000000000
IE: Unknown: 3D1601000700000000000000000000000000000000000000
IE: Unknown: 4A0E14000A002C01C800140005001900
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
IE: Unknown: 0B05020029127A
IE: Unknown: DD07000C4300000000
Cell 04 - Address: B8:9B:C9:B6:9A:EB
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=70/70 Signal level=26 dBm 
Encryption keyn
ESSID:""
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
18 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=0000022de9803d65
Extra: Last beacon: 980ms ago
IE: Unknown: 0000
IE: Unknown: 010882848B961224486C
IE: Unknown: 030101
IE: Unknown: 32040C183060
IE: Unknown: 0706555320010B14
IE: Unknown: 33082001020304050607
IE: Unknown: 33082105060708090A0B
IE: Unknown: 050400010000
IE: Unknown: 2A0106
IE: Unknown: 2D1AEE1117FFFFFF0001000000000000000000000000030000000000
IE: Unknown: 3D1601000700000000000000000000000000000000000000
IE: Unknown: 4A0E14000A002C01C800140005001900
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
IE: Unknown: 0B05020029127A
IE: Unknown: DD07000C4300000000
Cell 05 - Address: FC:94:E3:B0:2B:9D
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=46/70 Signal level=-64 dBm 
Encryption keyn
ESSID:"HOME-2B9D"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=00000293f3b161be
Extra: Last beacon: 5344ms ago
IE: Unknown: 0009484F4D452D32423944
IE: Unknown: 010882848B9624B0486C
IE: Unknown: 030101
IE: Unknown: 050400010000
IE: Unknown: 2A0100
IE: Unknown: 2F0100
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: 32048C129860
IE: Unknown: 2D1AFD181BFFFFFF0000000000000000000000000000000000000000
IE: Unknown: 3D1601081500000000000000000000000000000000000000
IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
IE: Unknown: DD090010180207F03C0000
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
Cell 06 - Address: 00:25:9C:23:8D:F8
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=50/70 Signal level=-60 dBm 
Encryption keyn
ESSID:"beth"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=0000043b6e924636
Extra: Last beacon: 60ms ago
IE: Unknown: 000462657468
IE: Unknown: 010882848B962430486C
IE: Unknown: 030106
IE: Unknown: 2A0104
IE: Unknown: 2F0104
IE: Unknown: 32040C121860
IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010138140001DD211B29FFFC67E816B4BFB102100074C696E6B73797310230006526F7574657210240007575254353447321042000C43535630314A3745333732331054000800060050F204000110110011576972656C6573732D4720526F75746572100800020084
IE: Unknown: DD090010180200F4000000
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
Cell 07 - Address: 00:1D:CE:7D:BB:AF
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=46/70 Signal level=-64 dBm 
Encryption keyn
ESSID:"HOME-BBB1"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
18 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=0000021fe65c57d3
Extra: Last beacon: 4848ms ago
IE: Unknown: 0009484F4D452D42424231
IE: Unknown: 010882848B961224486C
IE: Unknown: 030106
IE: Unknown: 32040C183060
IE: Unknown: 070C5553200101110209140B0111
IE: Unknown: 33082001020304050607
IE: Unknown: 33082105060708090A0B
IE: Unknown: 0505000100A001
IE: Unknown: DD310050F204104A0001101044000102104700102880288028801880A880001DCE7DBBAF103C0001011049000600372A000120
IE: Unknown: 2A0104
IE: Unknown: 2D1A0E1017FFFFFF00010000000000000000000000000C0000000000
IE: Unknown: 3D1606000700000000000000000000000000000000000000
IE: Unknown: 4A0E14000A002C01C800140005001900
IE: Unknown: 7F0101
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
IE: Unknown: 0B05050033127A
IE: Unknown: DD07000C4307000000
Cell 08 - Address: 02:1D:CE:7D:BB:AF
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=50/70 Signal level=-60 dBm 
Encryption keyn
ESSID:""
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
18 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=0000021fe65df94f
Extra: Last beacon: 4744ms ago
IE: Unknown: 0000
IE: Unknown: 010882848B961224486C
IE: Unknown: 030106
IE: Unknown: 32040C183060
IE: Unknown: 070C5553200101110209140B0111
IE: Unknown: 33082001020304050607
IE: Unknown: 33082105060708090A0B
IE: Unknown: 050400010000
IE: Unknown: 2A0104
IE: Unknown: 2D1A0E1017FFFFFF00010000000000000000000000000C0000000000
IE: Unknown: 3D1606000700000000000000000000000000000000000000
IE: Unknown: 4A0E14000A002C01C800140005001900
IE: Unknown: 7F0101
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
IE: Unknown: 0B05050033127A
IE: Unknown: DD07000C4307000000
Cell 09 - Address: 00:1D2:BA:F5:E0
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=46/70 Signal level=-64 dBm 
Encryption keyn
ESSID:"The Spot"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
18 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=00000198cb17cb8e
Extra: Last beacon: 4168ms ago
IE: Unknown: 00085468652053706F74
IE: Unknown: 010882848B961224486C
IE: Unknown: 03010B
IE: Unknown: 2A0104
IE: Unknown: 32040C183060
IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000
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
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
IE: Unknown: 0B05030026127A
IE: Unknown: 7F0101
IE: Unknown: DD07000C4303000000
IE: Unknown: 0706555320010B10
Cell 10 - Address: DC:9FB:00F:0B
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=22/70 Signal level=-88 dBm 
Encryption keyn
ESSID:""
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000005a89ee0666
Extra: Last beacon: 220ms ago
IE: Unknown: 0000
IE: Unknown: 010882848B960C121824
IE: Unknown: 03010B
IE: Unknown: 050400010000
IE: Unknown: 2A0100
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: DD26000C42000000011E040000001F660902FF0F4D6F756E742057617368696E6700000000000000
IE: Unknown: 32043048606C
IE: Unknown: DD180050F202010182000364000027A4000041435E0061322F00
IE: Unknown: DD1E00904C33CE111BFFFF000000000000000000000000000000000000000000
IE: Unknown: 2D1ACE111BFFFF000000000000000000000000000000000000000000
IE: Unknown: DD1A00904C340B071D00000000000000000000000000000000000000
IE: Unknown: 3D160B071D00000000000000000000000000000000000000
IE: Unknown: DD0900037F01010000FF7F
IE: Unknown: DD0A00037F04010002004000
IE: Unknown: DD0E00156D0000000102B2E102021200
IE: Unknown: DD2600156DFFFFFF489ACDF1242DF6F2EFC6E93B70E6747147A0964635A40F71DE627CFDF9781672

---

### Post by praseodym on 2013-06-27
Try pure WPA2-AES encryption instead of mixed WPA/WPA2.

---

### Post by Gfurst on 2013-06-27
I have a very similar problem, added that the connection keeps dropping even on wired connection.
I can't the config WPA thing, it's seems to be mixed WPA/WPA2 but no way to change.
it's worth mentioning that it happens on two different laptops, and they also work on a different router.

---

### Post by c0lon on 2013-06-28
how would i do that? when i click edit connection there's only an option for the mix, not just one or the other

---

### Post by Gfurst on 2013-06-30
I may have a way, even choosing WPA+WPA2 there's a option for encryption type: i can choose either AES or TKIP,
I've tried AES and nothing could connect anymore, TKIP solved it for me, both ubuntu machines and android devices were able to connect successfully.
Worth mention, is that i've also changed a "DNS relay" option, disabling it.

---

