---
title: "cannot connect to rmy network ?"
date: 2012-12-28
forum: Networking &amp; Wireless
---

### Post by geordiejohn on 2012-12-28
hello i cannot connect to my network unless i am right on top of my router,i was about 3 foot away and it just kept trying so i took my Acer Aspire 5536 laptop so it was right above the router and it connected,any ideas what to do so it connects from any where please ?
thank you.

---

### Post by praseodym on 2012-12-28
Please show the following terminal outputs:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
iwlist chan
sudo iwlist scan
rfkill list
```

---

### Post by geordiejohn on 2012-12-28
03:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:0207]
	Kernel driver in use: tg3
--
06:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
	Subsystem: Foxconn International, Inc. T77H053.00 802.11bgn Wireless Mini PCIe Card [AR9281] [105b:e006]
	Kernel driver in use: ath9k

---

### Post by geordiejohn on 2012-12-28
Bus 002 Device 002: ID 04f2:b044 Chicony Electronics Co., Ltd Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by geordiejohn on 2012-12-28
Module                  Size  Used by
xt_recent              17994  0 
xt_hl                  12465  6 
ip6t_rt                12473  3 
nf_conntrack_ipv6      13705  7 
nf_defrag_ipv6         12969  1 nf_conntrack_ipv6
ipt_REJECT             12485  1 
xt_LOG                 17149  10 
xt_limit               12541  13 
xt_tcpudp              12531  18 
xt_addrtype            12563  4 
xt_state               12514  14 
ip6table_filter        12711  1 
ip6_tables             17969  2 ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12548  0 
nf_nat                 20316  1 nf_nat_ftp
nf_conntrack_ipv4      14080  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_conntrack_ftp       13106  1 nf_nat_ftp
nf_conntrack           66307  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12706  1 
ip_tables              17791  1 iptable_filter
x_tables               21898  13 xt_recent,xt_hl,ip6t_rt,ipt_REJECT,xt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
bnep                   17707  2 
rfcomm                 37276  0 
bluetooth             183228  10 bnep,rfcomm
parport_pc             31968  0 
ppdev                  12817  0 
snd_hda_codec_hdmi     31423  1 
arc4                   12473  2 
snd_hda_codec_realtek    63493  1 
snd_hda_intel          32515  4 
snd_hda_codec         111547  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
ath9k                 116557  0 
mac80211              461161  1 ath9k
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
binfmt_misc            17260  1 
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
radeon                820734  3 
uvcvideo               71277  0 
ath9k_common           13783  1 ath9k
snd_seq_midi_event     14475  1 snd_seq_midi
ath9k_hw              376155  2 ath9k,ath9k_common
videobuf2_core         32070  1 uvcvideo
videodev               95841  2 uvcvideo,videobuf2_core
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
ttm                    75534  1 radeon
videobuf2_vmalloc      12756  1 uvcvideo
videobuf2_memops       13184  1 videobuf2_vmalloc
drm_kms_helper         47303  1 radeon
snd_timer              24411  2 snd_pcm,snd_seq
ath                    19187  3 ath9k,ath9k_common,ath9k_hw
drm                   238768  5 radeon,ttm,drm_kms_helper
kvm_amd                54394  0 
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
kvm                   357806  1 kvm_amd
cfg80211              175375  3 ath9k,mac80211,ath
psmouse                84843  0 
snd                    61991  18 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13417  0 
joydev                 17161  0 
i2c_piix4              12983  0 
i2c_algo_bit           13197  1 radeon
serio_raw              13031  0 
acer_wmi               27586  0 
soundcore              14599  1 snd
sparse_keymap          13658  1 acer_wmi
shpchp                 32189  0 
microcode              18209  0 
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
video                  18847  1 acer_wmi
k10temp                12958  0 
wmi                    18590  1 acer_wmi
mac_hid                13037  0 
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
tg3                   130448  0

---

### Post by geordiejohn on 2012-12-28
wlan0     IEEE 802.11bgn  ESSID:"geordiejohn"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 4C:17:EB:8B:F8:44   
          Bit Rate=13 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:13  Invalid misc:42   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by geordiejohn on 2012-12-28
wlan0     13 channels in total; available frequencies :
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
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.437 GHz (Channel 6)

lo        no frequency information.

eth0      no frequency information.

---

### Post by geordiejohn on 2012-12-28
0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by geordiejohn on 2012-12-28
on this command it says i am using 10 images and i am only allowed 8 buti cannot see any images ?
sudo iwlist scan

---

### Post by geordiejohn on 2012-12-28
Cell 01 - Address: 4C:17:EB:8B:F8:44
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"geordiejohn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000010b99f021
                    Extra: Last beacon: 84ms ago
                    IE: Unknown: 000B67656F726469656A6F686E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001500000000000000000000000000000000000000
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B0001031047001066DE1CEF8DE42D831A1C744662160AEB1021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020084103C000101
                    IE: Unknown: DD090010180202F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:1C:DF:11:71:CD
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"euan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000cc7284247
                    Extra: Last beacon: 3428ms ago
                    IE: Unknown: 00046575616E
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000C4307000000
          Cell 03 - Address: 00:24:B2:74:C6:A0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"virgin broadband"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000564abeeaa
                    Extra: Last beacon: 3424ms ago
                    IE: Unknown: 001076697267696E2062726F616462616E64
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 070A474200010D14010D1400
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD890050F204104A00011010440001021041000100103B00010310470010EA07C9A21479B6DB3E35C7436E0F1FA0102100074E4554474541521023000844473833344776351024000844473833344776351042000A313233343536373839301054000800060050F20400011011001644473833344776352028576972656C65737320415029100800020086
          Cell 04 - Address: 00:24:B2:25:DB:EA

---

### Post by praseodym on 2012-12-28
Try to deactivate the hardware encryption of the driver:
```

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by geordiejohn on 2012-12-28
Cell 04 - Address: 00:24:B2:25:DB:EA
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"St Clare"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f1a3ed1bf
                    Extra: Last beacon: 84ms ago
                    IE: Unknown: 0008537420436C617265
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: 00:1D:0F:ED:E9:BA
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003bb1d6181
                    Extra: Last beacon: 292ms ago
                    IE: Unknown: 000700000000000000
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706594520010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F0301000000001D0FEDE9BA021D0FEDE9BA64002C010808
          Cell 06 - Address: 00:8E:F2:B0:95:B6
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"virginmedia9044034"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000007b9778e01
                    Extra: Last beacon: 84ms ago
                    IE: Unknown: 001276697267696E6D6564696139303434303334
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
                    IE: Unknown: 3D1606001300000000000000000000000000000000000000
                    IE: Unknown: DD7E0050F204104A0001101044000102103B0001031047001027486E79ED9CE137593216EF35754FB3102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F20400011011000743473331303144100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180201F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: 00:50:7F:A7:20:68
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"DrayTek"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000097c5cbe165
                    Extra: Last beacon: 244ms ago
                    IE: Unknown: 00074472617954656B
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706545720010D10
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A000110104400010110470010BC329E001DD811B2860100507FA72068103C000100
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1606070100000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050000267A12
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406070100000000000000000000000000000000000000
                    IE: Unknown: DD07000C4300000000
          Cell 08 - Address: 00:24:B2:A1:5F:9C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"Jaimatadi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001dda3965c04
                    Extra: Last beacon: 84ms ago
                    IE: Unknown: 00094A61696D6174616469
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: 4C:17:EB:A0:18:B1
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"SKY018B0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000017e3f10eb7b
                    Extra: Last beacon: 808ms ago
                    IE: Unknown: 0008534B593031384230
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001500000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180202F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by praseodym on 2012-12-28
Additionally, change the encryption mode in your router interface to pure WPA2-AES, if possible.

---

### Post by geordiejohn on 2012-12-28
i think you have every thing now ?

---

### Post by geordiejohn on 2012-12-28
mine is setup as wpa and wpa2 personnel

---

### Post by geordiejohn on 2012-12-28
all ok now thank you very much

---

