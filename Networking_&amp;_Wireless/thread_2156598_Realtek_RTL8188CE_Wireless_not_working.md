---
title: "Realtek RTL8188CE: Wireless not working"
date: 2013-06-22
forum: Networking &amp; Wireless
---

### Post by Safeeq on 2013-06-22
I just installed Ubuntu 12.04 with CD booting and the wireless connected at the first use after installation. Wireless stopped working and not detecting my network. Tried creating one using hidden networks & create new connections but no luck. Can anyone help me with resolving this issue.

My laptop is TOSHIBA-TAIS. When I switch to windows7, wireless works fine.

---

### Post by praseodym on 2013-06-22
Please show the outputs of:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by Safeeq on 2013-06-22
> **praseodym said:**
> Please show the outputs of:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
```


Please see the outputs of the aforementioned commands,

lspci -nnk | grep -iA2 net:

[COLOR=#800000]safeeq@safeeq-Satellite-L735:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8181]
    Kernel driver in use: rtl8192ce
--
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: Toshiba America Info Systems Device [1179:fcc0]
    Kernel driver in use: atl1c
safeeq@safeeq-Satellite-L735:~$ [/COLOR]

lsusb:

[COLOR=#800000]safeeq@safeeq-Satellite-L735:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 058f:b003 Alcor Micro Corp. 
Bus 002 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
safeeq@safeeq-Satellite-L735:~$ 
[/COLOR]
lsmod:[COLOR=#800000]

safeeq@safeeq-Satellite-L735:~$ lsmod
Module                  Size  Used by
ipt_MASQUERADE         12664  1 
xt_state               12515  1 
ipt_REJECT             12513  2 
xt_tcpudp              12532  4 
iptable_filter         12707  1 
nf_nat_h323            12810  0 
nf_conntrack_h323      52413  1 nf_nat_h323
nf_nat_pptp            12537  0 
nf_conntrack_pptp      13554  1 nf_nat_pptp
nf_conntrack_proto_gre    13581  1 nf_conntrack_pptp
nf_nat_proto_gre       12672  1 nf_nat_pptp
nf_nat_tftp            12421  0 
nf_conntrack_tftp      12818  1 nf_nat_tftp
nf_nat_sip             16946  0 
nf_conntrack_sip       24793  1 nf_nat_sip
nf_nat_irc             12543  0 
nf_conntrack_irc       13139  1 nf_nat_irc
nf_nat_ftp             12596  0 
nf_conntrack_ftp       13184  1 nf_nat_ftp
iptable_nat            13017  1 
nf_nat                 20645  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      14123  4 iptable_nat,nf_nat
nf_conntrack           66862  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12650  1 nf_conntrack_ipv4
ip_tables              18107  2 iptable_filter,iptable_nat
x_tables               22012  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
dm_crypt               22572  1 
joydev                 17394  0 
snd_hda_codec_hdmi     31778  1 
snd_hda_codec_conexant    52560  1 
bnep                   17791  2 
rfcomm                 38104  0 
bluetooth             189585  10 bnep,rfcomm
parport_pc             32115  0 
ppdev                  12850  0 
coretemp               13362  0 
kvm_intel             127736  0 
kvm                   365588  1 kvm_intel
arc4                   12474  2 
snd_hda_intel          32983  3 
snd_hda_codec         116477  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13277  1 snd_hda_codec
snd_pcm                81124  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
microcode              18396  0 
snd_seq_midi           13133  0 
snd_rawmidi            25426  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
rts5139               279419  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72249  0 
videobuf2_core         32212  1 uvcvideo
videodev              100265  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12757  1 uvcvideo
videobuf2_memops       13213  1 videobuf2_vmalloc
rtl8192ce              53780  0 
rtl8192c_common        47696  1 rtl8192ce
rtlwifi                65304  1 rtl8192ce
mac80211              475546  3 rtl8192ce,rtl8192c_common,rtlwifi
psmouse                91381  0 
snd                    62675  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              181041  2 rtlwifi,mac80211
serio_raw              13032  0 
toshiba_acpi           18287  0 
sparse_keymap          13659  1 toshiba_acpi
mei                    36404  0 
soundcore              14636  1 snd
lpc_ich                16993  0 
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
mac_hid                13078  0 
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
aesni_intel            17979  352 
cryptd                 19822  9 aesni_intel
aes_i586               16996  1 aesni_intel
wmi                    18745  1 toshiba_acpi
ahci                   25621  2 
libahci                26166  1 ahci
i915                  479235  3 
atl1c                  36969  0 
drm_kms_helper         47459  1 i915
drm                   239971  4 i915,drm_kms_helper
i2c_algo_bit           13317  1 i915
video                  19117  1 i915
safeeq@safeeq-Satellite-L735:~$ [/COLOR]


iwconfig:

[COLOR=#800000]safeeq@safeeq-Satellite-L735:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"HOME-BAD2"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 02:87:47:DA:72:4A   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.

[/COLOR]
rfkill list:

[COLOR=#800000]safeeq@safeeq-Satellite-L735:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

[/COLOR]sudo iwlist scan:


   [COLOR=#800000]safeeq@safeeq-Satellite-L735:~$ sudo iwlist scan 
[/COLOR]
[COLOR=#800000]wlan0     Scan completed : [/COLOR]
[COLOR=#800000]          Cell 01 - Address: 02:87:47:DA:72:4A [/COLOR]
[COLOR=#800000]                    Channel:1 [/COLOR]
[COLOR=#800000]                    Frequency:2.412 GHz (Channel 1) [/COLOR]
[COLOR=#800000]                    Quality=70/70  Signal level=0 dBm   [/COLOR]
[COLOR=#800000]                    Encryption key:on [/COLOR]
[COLOR=#800000]                    ESSID:"HOME-BAD2" [/COLOR]
[COLOR=#800000]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s [/COLOR]
[COLOR=#800000]                              9 Mb/s; 12 Mb/s; 18 Mb/s [/COLOR]
[COLOR=#800000]                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s [/COLOR]
[COLOR=#800000]                    Mode:Ad-Hoc [/COLOR]
[COLOR=#800000]                    Extra:tsf=0000000000000000 [/COLOR]
[COLOR=#800000]                    Extra: Last beacon: 1049336ms ago [/COLOR]
[COLOR=#800000]                    IE: Unknown: 0009484F4D452D42414432 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 010882040B160C121824 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 030101 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 06020000 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 32043048606C [/COLOR]
[COLOR=#800000]                    IE: Unknown: DD070050F202000100 [/COLOR]
[COLOR=#800000]          Cell 02 - Address: E4:83:99:60:05:6B [/COLOR]
[COLOR=#800000]                    Channel:1 [/COLOR]
[COLOR=#800000]                    Frequency:2.412 GHz (Channel 1) [/COLOR]
[COLOR=#800000]                    Quality=52/70  Signal level=-58 dBm   [/COLOR]
[COLOR=#800000]                    Encryption key:on [/COLOR]
[COLOR=#800000]                    ESSID:"MOTOROLA-F9F6F" [/COLOR]
[COLOR=#800000]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s [/COLOR]
[COLOR=#800000]                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s [/COLOR]
[COLOR=#800000]                              36 Mb/s; 48 Mb/s; 54 Mb/s [/COLOR]
[COLOR=#800000]                    Mode:Master [/COLOR]
[COLOR=#800000]                    Extra:tsf=0000007287fd31d4 [/COLOR]
[COLOR=#800000]                    Extra: Last beacon: 12ms ago [/COLOR]
[COLOR=#800000]                    IE: Unknown: 000E4D4F544F524F4C412D4639463646 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 010482848B96 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 030101 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 2A0100 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 2F0100 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 32080C1218243048606C [/COLOR]
[COLOR=#800000]                    IE: Unknown: DD090010180204F02C0000 [/COLOR]
[COLOR=#800000]                    IE: WPA Version 1 [/COLOR]
[COLOR=#800000]                        Group Cipher : TKIP [/COLOR]
[COLOR=#800000]                        Pairwise Ciphers (1) : TKIP [/COLOR]
[COLOR=#800000]                        Authentication Suites (1) : PSK [/COLOR]
[COLOR=#800000]                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00 [/COLOR]
[COLOR=#800000]          Cell 03 - Address: 00:26:62:C9:D8:4F [/COLOR]
[COLOR=#800000]                    Channel:1 [/COLOR]
[COLOR=#800000]                    Frequency:2.412 GHz (Channel 1) [/COLOR]
[COLOR=#800000]                    Quality=53/70  Signal level=-57 dBm   [/COLOR]
[COLOR=#800000]                    Encryption key:on 
[/COLOR]
[COLOR=#800000]                    ESSID:"EVIV7" [/COLOR]
[COLOR=#800000]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s [/COLOR]
[COLOR=#800000]                              9 Mb/s; 12 Mb/s; 18 Mb/s [/COLOR]
[COLOR=#800000]                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s [/COLOR]
[COLOR=#800000]                    Mode:Master [/COLOR]
[COLOR=#800000]                    Extra:tsf=0000007286caf186 [/COLOR]
[COLOR=#800000]                    Extra: Last beacon: 12ms ago [/COLOR]
[COLOR=#800000]                    IE: Unknown: 00054556495637 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 010882848B960C121824 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 030101 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 200100 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 2A0100 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 32043048606C [/COLOR]
[COLOR=#800000]                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 2D1A8C131BFF00000000000000000000000000000000000000000000 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000 [/COLOR]
[COLOR=#800000]                    IE: Unknown: DD0900037F01010000FF7F [/COLOR]
[COLOR=#800000]                    IE: Unknown: DD0A00037F04010020000000 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 0706555320010B1B [/COLOR]
[COLOR=#800000]          Cell 04 - Address: CC:5D:4E:49:AF:6F [/COLOR]
[COLOR=#800000]                    Channel:1 [/COLOR]
[COLOR=#800000]                    Frequency:2.412 GHz (Channel 1) [/COLOR]
[COLOR=#800000]                    Quality=52/70  Signal level=-58 dBm   [/COLOR]
[COLOR=#800000]                    Encryption key:on [/COLOR]
[COLOR=#800000]                    ESSID:"Shree" [/COLOR]
[COLOR=#800000]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s [/COLOR]
[COLOR=#800000]                              9 Mb/s; 12 Mb/s; 18 Mb/s [/COLOR]
[COLOR=#800000]                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s [/COLOR]
[COLOR=#800000]                    Mode:Master [/COLOR]
[COLOR=#800000]                    Extra:tsf=0000007286cfa176 [/COLOR]
[COLOR=#800000]                    Extra: Last beacon: 17728ms ago [/COLOR]
[COLOR=#800000]                    IE: Unknown: 00055368726565 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 010882848B960C121824 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 030101 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 050400010000 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 2A0104 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 32043048606C [/COLOR]
[COLOR=#800000]                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00 [/COLOR]
[COLOR=#800000]                    IE: Unknown: DD0600E04C020160 [/COLOR]
[COLOR=#800000]                    IE: Unknown: DD300050F204104A0001101044000102101100185A7958454C204E42472D3431384E20415020526F75746572100800020086 [/COLOR]
[COLOR=#800000]          Cell 05 - Address: 00:1D:D4:62:BA:D0 [/COLOR]
[COLOR=#800000]                    Channel:6 [/COLOR]
[COLOR=#800000]                    Frequency:2.437 GHz (Channel 6) [/COLOR]
[COLOR=#800000]                    Quality=55/70  Signal level=-55 dBm   [/COLOR]
[COLOR=#800000]                    Encryption key:on [/COLOR]
[COLOR=#800000]                    ESSID:"" [/COLOR]
[COLOR=#800000]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s [/COLOR]
[COLOR=#800000]                              18 Mb/s; 36 Mb/s; 54 Mb/s [/COLOR]
[COLOR=#800000]                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s [/COLOR]
[COLOR=#800000]                    Mode:Master [/COLOR]
[COLOR=#800000]                    Extra:tsf=00000072844f0167 [/COLOR]
[COLOR=#800000]                    Extra: Last beacon: 400ms ago [/COLOR]
[COLOR=#800000]                    IE: Unknown: 0000 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 010882848B961224486C [/COLOR]
[COLOR=#800000]                    IE: Unknown: 030106 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 32040C183060 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 070C55532001010F0209110B010F [/COLOR]
[COLOR=#800000]                    IE: Unknown: 33082001020304050607 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 33082105060708090A0B [/COLOR]
[COLOR=#800000]                    IE: Unknown: 050400010000 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 2A0104 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 3D1606030500000000000000000000000000000000000000 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 7F0101 [/COLOR]
[COLOR=#800000]                    IE: WPA Version 1 [/COLOR]
[COLOR=#800000]                        Group Cipher : TKIP [/COLOR]
[COLOR=#800000]                        Pairwise Ciphers (2) : TKIP CCMP [/COLOR]
[COLOR=#800000]                        Authentication Suites (1) : PSK [/COLOR]
[COLOR=#800000]                    IE: IEEE 802.11i/WPA2 Version 1 [/COLOR]
[COLOR=#800000]                        Group Cipher : TKIP [/COLOR]
[COLOR=#800000]                        Pairwise Ciphers (2) : TKIP CCMP [/COLOR]
[COLOR=#800000]                        Authentication Suites (1) : PSK [/COLOR]
[COLOR=#800000]                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 0B05020071127A [/COLOR]
[COLOR=#800000]                    IE: Unknown: DD07000C4303000000 [/COLOR]
[COLOR=#800000]          Cell 06 - Address: 02:1D:D4:62:BA:D0 [/COLOR]
[COLOR=#800000]                    Channel:6 [/COLOR]
[COLOR=#800000]                    Frequency:2.437 GHz (Channel 6) [/COLOR]
[COLOR=#800000]                    Quality=55/70  Signal level=-55 dBm   [/COLOR]
[COLOR=#800000]                    Encryption key:on [/COLOR]
[COLOR=#800000]                    ESSID:"" [/COLOR]
[COLOR=#800000]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s [/COLOR]
[COLOR=#800000]                              18 Mb/s; 36 Mb/s; 54 Mb/s [/COLOR]
[COLOR=#800000]                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s [/COLOR]
[COLOR=#800000]                    Mode:Master [/COLOR]
[COLOR=#800000]                    Extra:tsf=00000072844f0a31 [/COLOR]
[COLOR=#800000]                    Extra: Last beacon: 396ms ago [/COLOR]
[COLOR=#800000]                    IE: Unknown: 0000 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 010882848B961224486C [/COLOR]
[COLOR=#800000]                    IE: Unknown: 030106 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 32040C183060 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 070C55532001010F0209110B010F [/COLOR]
[COLOR=#800000]                    IE: Unknown: 33082001020304050607 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 33082105060708090A0B [/COLOR]
[COLOR=#800000]                    IE: Unknown: 050400010000 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 2A0104 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 3D1606030500000000000000000000000000000000000000 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 7F0101 [/COLOR]
[COLOR=#800000]                    IE: IEEE 802.11i/WPA2 Version 1 [/COLOR]
[COLOR=#800000]                        Group Cipher : CCMP [/COLOR]
[COLOR=#800000]                        Pairwise Ciphers (1) : CCMP [/COLOR]
[COLOR=#800000]                        Authentication Suites (1) : PSK [/COLOR]
[COLOR=#800000]                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 0B05020071127A 
[/COLOR]
[COLOR=#800000]                    IE: Unknown: DD07000C4303000000 [/COLOR]
[COLOR=#800000]          Cell 07 - Address: 00:1D:D4:62:BA:D0 [/COLOR]
[COLOR=#800000]                    Channel:6 [/COLOR]
[COLOR=#800000]                    Frequency:2.437 GHz (Channel 6) [/COLOR]
[COLOR=#800000]                    Quality=53/70  Signal level=-57 dBm   [/COLOR]
[COLOR=#800000]                    Encryption key:on [/COLOR]
[COLOR=#800000]                    ESSID:"HOME-BAD2" [/COLOR]
[COLOR=#800000]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s [/COLOR]
[COLOR=#800000]                              18 Mb/s; 36 Mb/s; 54 Mb/s [/COLOR]
[COLOR=#800000]                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s [/COLOR]
[COLOR=#800000]                    Mode:Master [/COLOR]
[COLOR=#800000]                    Extra:tsf=00000072833f4e14 [/COLOR]
[COLOR=#800000]                    Extra: Last beacon: 18204ms ago [/COLOR]
[COLOR=#800000]                    IE: Unknown: 0009484F4D452D42414432 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 010882848B961224486C [/COLOR]
[COLOR=#800000]                    IE: Unknown: 030106 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 2A0104 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 32040C183060 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 3D1606030500000000000000000000000000000000000000 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 3E0100 [/COLOR]
[COLOR=#800000]                    IE: WPA Version 1 [/COLOR]
[COLOR=#800000]                        Group Cipher : TKIP [/COLOR]
[COLOR=#800000]                        Pairwise Ciphers (2) : TKIP CCMP [/COLOR]
[COLOR=#800000]                        Authentication Suites (1) : PSK [/COLOR]
[COLOR=#800000]                    IE: IEEE 802.11i/WPA2 Version 1 [/COLOR]
[COLOR=#800000]                        Group Cipher : TKIP [/COLOR]
[COLOR=#800000]                        Pairwise Ciphers (2) : TKIP CCMP [/COLOR]
[COLOR=#800000]                        Authentication Suites (1) : PSK [/COLOR]
[COLOR=#800000]                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 0B0502005B127A [/COLOR]
[COLOR=#800000]                    IE: Unknown: 7F0101 [/COLOR]
[COLOR=#800000]                    IE: Unknown: DD07000C4303000000 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 0706555320010B10 [/COLOR]
[COLOR=#800000]          Cell 08 - Address: 00:18:01:F2:57:92 [/COLOR]
[COLOR=#800000]                    Channel:6 [/COLOR]
[COLOR=#800000]                    Frequency:2.437 GHz (Channel 6) [/COLOR]
[COLOR=#800000]                    Quality=55/70  Signal level=-55 dBm   [/COLOR]
[COLOR=#800000]                    Encryption key:on [/COLOR]
[COLOR=#800000]                    ESSID:"PARAM" [/COLOR]
[COLOR=#800000]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s [/COLOR]
[COLOR=#800000]                              11 Mb/s; 12 Mb/s; 18 Mb/s [/COLOR]
[COLOR=#800000]                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s [/COLOR]
[COLOR=#800000]                    Mode:Master [/COLOR]
[COLOR=#800000]                    Extra:tsf=00000072872ef181 [/COLOR]
[COLOR=#800000]                    Extra: Last beacon: 392ms ago [/COLOR]
[COLOR=#800000]                    IE: Unknown: 0005504152414D [/COLOR]
[COLOR=#800000]                    IE: Unknown: 010882848B0C12961824 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 030106 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 0706555320010B1B [/COLOR]
[COLOR=#800000]                    IE: Unknown: 200100 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 2A0100 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 32043048606C [/COLOR]
[COLOR=#800000]                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00 [/COLOR]
[COLOR=#800000]          Cell 09 - Address: 00:1E:58:E1:0E:24 [/COLOR]
[COLOR=#800000]                    Channel:11 [/COLOR]
[COLOR=#800000]                    Frequency:2.462 GHz (Channel 11) [/COLOR]
[COLOR=#800000]                    Quality=56/70  Signal level=-54 dBm   [/COLOR]
[COLOR=#800000]                    Encryption key:on [/COLOR]
[COLOR=#800000]                    ESSID:"RamavathuFamily" [/COLOR]
[COLOR=#800000]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s [/COLOR]
[COLOR=#800000]                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s [/COLOR]
[COLOR=#800000]                              36 Mb/s; 48 Mb/s; 54 Mb/s [/COLOR]
[COLOR=#800000]                    Mode:Master [/COLOR]
[COLOR=#800000]                    Extra:tsf=0000001cb701d1e1 [/COLOR]
[COLOR=#800000]                    Extra: Last beacon: 32ms ago [/COLOR]
[COLOR=#800000]                    IE: Unknown: 000F52616D61766174687546616D696C79 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 010582848B962C [/COLOR]
[COLOR=#800000]                    IE: Unknown: 03010B [/COLOR]
[COLOR=#800000]                    IE: Unknown: 2A0104 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 32080C1218243048606C [/COLOR]
[COLOR=#800000]          Cell 10 - Address: 00:1E:2A:54:B1:84 [/COLOR]
[COLOR=#800000]                    Channel:11 [/COLOR]
[COLOR=#800000]                    Frequency:2.462 GHz (Channel 11) [/COLOR]
[COLOR=#800000]                    Quality=55/70  Signal level=-55 dBm   [/COLOR]
[COLOR=#800000]                    Encryption key:on [/COLOR]
[COLOR=#800000]                    ESSID:"Monarchs" [/COLOR]
[COLOR=#800000]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s [/COLOR]
[COLOR=#800000]                              24 Mb/s; 36 Mb/s; 54 Mb/s [/COLOR]
[COLOR=#800000]                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s [/COLOR]
[COLOR=#800000]                    Mode:Master [/COLOR]
[COLOR=#800000]                    Extra:tsf=0000007287c9a236 [/COLOR]
[COLOR=#800000]                    Extra: Last beacon: 172ms ago [/COLOR]
[COLOR=#800000]                    IE: Unknown: 00084D6F6E6172636873 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 010882848B962430486C [/COLOR]
[COLOR=#800000]                    IE: Unknown: 03010B [/COLOR]
[COLOR=#800000]                    IE: Unknown: 2A0100 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 2F0100 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 32040C121860 [/COLOR]
[COLOR=#800000]                    IE: Unknown: DD090010180202F0000000 [/COLOR]
[COLOR=#800000]                    IE: WPA Version 1 [/COLOR]
[COLOR=#800000]                        Group Cipher : TKIP [/COLOR]
[COLOR=#800000]                        Pairwise Ciphers (1) : TKIP [/COLOR]
[COLOR=#800000]                        Authentication Suites (1) : PSK [/COLOR]
[COLOR=#800000]                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00 [/COLOR]
[COLOR=#800000]          Cell 11 - Address: 00:24:B2:84:03:0E [/COLOR]
[COLOR=#800000]                    Channel:11 [/COLOR]
[COLOR=#800000]                    Frequency:2.462 GHz (Channel 11) [/COLOR]
[COLOR=#800000]                    Quality=56/70  Signal level=-54 dBm   [/COLOR]
[COLOR=#800000]                    Encryption key:on [/COLOR]
[COLOR=#800000]                    ESSID:"nihasantosh" [/COLOR]
[COLOR=#800000]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s [/COLOR]
[COLOR=#800000]                              12 Mb/s; 24 Mb/s; 36 Mb/s [/COLOR]
[COLOR=#800000]                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s [/COLOR]
[COLOR=#800000]                    Mode:Master [/COLOR]
[COLOR=#800000]                    Extra:tsf=0000001cb80b7181 [/COLOR]
[COLOR=#800000]                    Extra: Last beacon: 68ms ago [/COLOR]
[COLOR=#800000]                    IE: Unknown: 000B6E69686173616E746F7368 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 010882848B960C183048 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 03010B [/COLOR]
[COLOR=#800000]                    IE: Unknown: 2A0100 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 32041224606C [/COLOR]
[COLOR=#800000]                    IE: WPA Version 1 [/COLOR]
[COLOR=#800000]                        Group Cipher : TKIP [/COLOR]
[COLOR=#800000]                        Pairwise Ciphers (1) : TKIP [/COLOR]
[COLOR=#800000]                        Authentication Suites (1) : PSK [/COLOR]
[COLOR=#800000]          Cell 12 - Address: 00:19:5B:58:41:7B [/COLOR]
[COLOR=#800000]                    Channel:11 [/COLOR]
[COLOR=#800000]                    Frequency:2.462 GHz (Channel 11) [/COLOR]
[COLOR=#800000]                    Quality=56/70  Signal level=-54 dBm   [/COLOR]
[COLOR=#800000]                    Encryption key:on [/COLOR]
[COLOR=#800000]                    ESSID:"Dodo" [/COLOR]
[COLOR=#800000]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s [/COLOR]
[COLOR=#800000]                              12 Mb/s; 24 Mb/s; 36 Mb/s [/COLOR]
[COLOR=#800000]                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s [/COLOR]
[COLOR=#800000]                    Mode:Master [/COLOR]
[COLOR=#800000]                    Extra:tsf=0000001cb69dd181 [/COLOR]
[COLOR=#800000]                    Extra: Last beacon: 92ms ago [/COLOR]
[COLOR=#800000]                    IE: Unknown: 0004446F646F [/COLOR]
[COLOR=#800000]                    IE: Unknown: 010882848B960C183048 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 03010B [/COLOR]
[COLOR=#800000]                    IE: Unknown: 2A0100 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 32041224606C [/COLOR]
[COLOR=#800000]                    IE: WPA Version 1 [/COLOR]
[COLOR=#800000]                        Group Cipher : TKIP [/COLOR]
[COLOR=#800000]                        Pairwise Ciphers (1) : TKIP [/COLOR]
[COLOR=#800000]                        Authentication Suites (1) : PSK [/COLOR]
[COLOR=#800000]          Cell 13 - Address: 00:21:91:FD:D8:E7 [/COLOR]
[COLOR=#800000]                    Channel:11 [/COLOR]
[COLOR=#800000]                    Frequency:2.462 GHz (Channel 11) [/COLOR]
[COLOR=#800000]                    Quality=56/70  Signal level=-54 dBm   [/COLOR]
[COLOR=#800000]                    Encryption key:on [/COLOR]
[COLOR=#800000]                    ESSID:"amit-guddi" [/COLOR]
[COLOR=#800000]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s [/COLOR]
[COLOR=#800000]                              12 Mb/s; 24 Mb/s; 36 Mb/s [/COLOR]
[COLOR=#800000]                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s [/COLOR]
[COLOR=#800000]                    Mode:Master [/COLOR]
[COLOR=#800000]                    Extra:tsf=00000072883bb181 [/COLOR]
[COLOR=#800000]                    Extra: Last beacon: 84ms ago [/COLOR]
[COLOR=#800000]                    IE: Unknown: 000A616D69742D6775646469 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 010882848B960C183048 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 03010B [/COLOR]
[COLOR=#800000]                    IE: Unknown: 2A0100 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 32041224606C [/COLOR]
[COLOR=#800000]                    IE: WPA Version 1 [/COLOR]
[COLOR=#800000]                        Group Cipher : TKIP [/COLOR]
[COLOR=#800000]                        Pairwise Ciphers (1) : TKIP [/COLOR]
[COLOR=#800000]                        Authentication Suites (1) : PSK [/COLOR]
[COLOR=#800000]          Cell 14 - Address: 00:0D:3A:6F:43:01 [/COLOR]
[COLOR=#800000]                    Channel:6 [/COLOR]
[COLOR=#800000]                    Frequency:2.437 GHz (Channel 6) [/COLOR]
[COLOR=#800000]                    Quality=55/70  Signal level=-55 dBm   [/COLOR]
[COLOR=#800000]                    Encryption key:off [/COLOR]
[COLOR=#800000]                    ESSID:"MSHOME" [/COLOR]
[COLOR=#800000]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s [/COLOR]
[COLOR=#800000]                              24 Mb/s; 36 Mb/s; 54 Mb/s [/COLOR]
[COLOR=#800000]                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s [/COLOR]
[COLOR=#800000]                    Mode:Master [/COLOR]
[COLOR=#800000]                    Extra:tsf=0000007287849104 [/COLOR]
[COLOR=#800000]                    Extra: Last beacon: 364ms ago [/COLOR]
[COLOR=#800000]                    IE: Unknown: 00064D53484F4D45 [/COLOR]

[COLOR=#800000]                    IE: Unknown: 010882848B962430486C [/COLOR]
[COLOR=#800000]                    IE: Unknown: 030106 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 2A0104 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 2F0104 [/COLOR]
[COLOR=#800000]                    IE: Unknown: 32040C121860 [/COLOR]
[COLOR=#800000]                    IE: Unknown: DD050010180101 [/COLOR]

[COLOR=#800000]lo        Interface doesn't support scanning. [/COLOR]

[COLOR=#800000]eth0      Interface doesn't support scanning. 
[/COLOR]

Thanks
Safeeq

---

### Post by praseodym on 2013-06-22
Do you use internet connection sharing? It shows an "Ad-Hoc"-network...

You may want to update the driver according to this:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential
wget media.cdn.ubuntu-de.org/forum/attachments/39/19/5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz
tar xvf 5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz
cd rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/
make
sudo make install
sudo depmod -a
sudo update-initramfs -u
sudo cp -r firmware/* /lib/firmware  
```
Reboot.

---

### Post by Safeeq on 2013-06-22
> **praseodym said:**
> Do you use internet connection sharing? It shows an "Ad-Hoc"-network...

You may want to update the driver according to this:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential
wget media.cdn.ubuntu-de.org/forum/attachments/39/19/5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz
tar xvf 5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz
cd rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/
make
sudo make install
sudo depmod -a
sudo update-initramfs -u
sudo cp -r firmware/* /lib/firmware  
```
Reboot.

It connected for once after running the above commands and when I rebooted the laptop. When I restart it for the second time, I am back to square one. Wireless stopped working again.

---

### Post by praseodym on 2013-06-22
Open the network-manager applet, remove the current wireless profile and create a new one in "infrastructure" mode.

---

