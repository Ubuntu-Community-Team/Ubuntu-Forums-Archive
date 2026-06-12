---
title: "Networks suddenly disappears"
date: 2013-07-10
forum: Networking &amp; Wireless
---

### Post by fragusius on 2013-07-10
I've tried a few different versions of Ubuntu(Ubuntu, Xubuntu, Lubuntu) 12.04, 12.10 and 13.04 and I've had the same problem with all of them, for the moment anyway I'm on Xubuntu 13.04. Sometimes Network Manager can't find any networks(and sometimes a few that belongs to my neighbours). I'm using a mobile internet, through usb, but even when some of the wireless networks are available most of them are not, so I guess the problem is more about Network Manager or something in Ubuntu(since I never had these problem with Windows). When I used 12.04 and 12.10 the only solution to get the networks started again was to reboot(several times mostly), but since I upgraded to 13.04 waiting a few minutes usually helps.

If anyone could help it would be really nice! Please tell what information you need to help and I'll post it as soon as possible. Would be cool if I had connection whenever I wanted to =)

---

### Post by praseodym on 2013-07-10
Please show the outputs of these commands:
```

lsusb
lsmod
iwconfig
route -n
iwlist chan
sudo iwlist scan
```

---

### Post by fragusius on 2013-07-11
lsusb
```
Bus 001 Device 002: ID 5986:0130 Acer, Inc 
Bus 001 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 008: ID 12d1:1506 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```


lsmod
```
Module                  Size  Used by
ppp_deflate            12806  0 
zlib_deflate           26445  1 ppp_deflate
bsd_comp               12785  0 
ppp_async              17205  1 
crc_ccitt              12627  1 ppp_async
snd_hrtimer            12648  1 
parport_pc             27504  0 
ppdev                  12817  0 
rfcomm                 37420  0 
bnep                   17669  2 
bluetooth             202069  10 bnep,rfcomm
binfmt_misc            17260  1 
qmi_wwan               12771  0 
option                 29746  2 
cdc_wdm                17663  1 qmi_wwan
usb_wwan               14830  1 option
usbnet                 26567  1 qmi_wwan
usbserial              27423  7 option,usb_wwan
arc4                   12543  2 
rtl8187                60184  0 
mac80211              526519  1 rtl8187
cfg80211              436177  2 mac80211,rtl8187
eeprom_93cx6           13168  1 rtl8187
uvcvideo               71279  0 
videobuf2_vmalloc      12920  1 uvcvideo
snd_hda_codec_conexant    52256  1 
videobuf2_memops       13042  1 videobuf2_vmalloc
snd_hda_intel          38307  3 
videobuf2_core         39161  1 uvcvideo
snd_usb_audio         114886  1 
videodev               95806  2 uvcvideo,videobuf2_core
snd_hda_codec         117580  2 snd_hda_codec_conexant,snd_hda_intel
snd_usbmidi_lib        24210  1 snd_usb_audio
snd_hwdep              13272  2 snd_usb_audio,snd_hda_codec
snd_pcm                80890  3 snd_usb_audio,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  2 snd_usbmidi_lib,snd_seq_midi
snd_seq                51280  3 snd_seq_midi_event,snd_seq_midi
joydev                 17097  0 
coretemp               13131  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  3 snd_hrtimer,snd_pcm,snd_seq
sp5100_tco             13447  0 
snd                    56485  20 snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12600  1 snd
microcode              18286  0 
psmouse                81038  0 
shpchp                 32129  0 
i2c_piix4              13066  0 
serio_raw              13031  0 
mac_hid                13037  0 
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
ext2                   63166  1 
xts                    12749  1 
gf128mul               14503  1 xts
dm_crypt               22321  1 
pata_acpi              12886  0 
usb_storage            47684  0 
radeon                875070  2 
video                  18894  0 
i2c_algo_bit           13197  1 radeon
ttm                    71289  1 radeon
drm_kms_helper         47545  1 radeon
drm                   228489  4 ttm,drm_kms_helper,radeon
pata_atiixp            13058  0 
ati_agp                13177  0 
sky2                   52846  0 
ahci                   25507  2 
libahci                26108  1 ahci

```

iwconfig
```
ppp0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wwan0     no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.


```

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.64.64.64     0.0.0.0         UG    0      0        0 ppp0
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ppp0


```

iwlist chan
```
ppp0      no frequency information.

wlan0     14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
wwan0     no frequency information.

lo        no frequency information.

eth0      no frequency information.


```

sudo iwlist scan
```
ppp0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 24:EC:99:39:50:A9
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"TeliaGateway24-EC-99-39-50-A9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000d640e61119b
                    Extra: Last beacon: 1044ms ago
                    IE: Unknown: 001D54656C69614761746577617932342D45432D39392D33392D35302D4139
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001100000000000000000000000000000000000000
                    IE: Unknown: DD09001018020000050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001100000000000000000000000000000000000000
          Cell 02 - Address: F8:3D:FF:14:A5:12
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Tele2Internet-2B5DE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000071efab71a0
                    Extra: Last beacon: 676ms ago
                    IE: Unknown: 001354656C6532496E7465726E65742D3242354445
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1609000000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 20:4E:7F:1B:48:98
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Tele2Gateway4897"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000075da4b1c6b
                    Extra: Last beacon: 2040ms ago
                    IE: Unknown: 001054656C65324761746577617934383937
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180202F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401080400000000000000000000000000000000000000
          Cell 04 - Address: 00:1D:AA:A5:F6:78
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"BIFROST"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001364319814c
                    Extra: Last beacon: 1752ms ago
                    IE: Unknown: 0007424946524F5354
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030103
                    IE: Unknown: 32040C183060
                    IE: Unknown: DD270050F204104A000110104400010110470010BC329E001DD811B28601001DAAA5F678103C000100
                    IE: Unknown: 0505000100360F
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A6E1017FFFFFF0001000000000000000000000000000000000000
                    IE: Unknown: 3D1603050600000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500020D7A12
                    IE: Unknown: DD1E00904C336E1017FFFFFF0001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3403050600000000000000000000000000000000000000
                    IE: Unknown: DD07000C4300000000
          Cell 05 - Address: 00:1D:AA:A5:F6:79
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:"Open-Hotspot-500kbps"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000136431b1b75
                    Extra: Last beacon: 1648ms ago
                    IE: Unknown: 00144F70656E2D486F7473706F742D3530306B627073
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030103
                    IE: Unknown: 32040C183060
                    IE: Unknown: 05050001003C06
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A6E1017FFFFFF0001000000000000000000000000000000000000
                    IE: Unknown: 3D1603050600000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500020D7A12
                    IE: Unknown: DD1E00904C336E1017FFFFFF0001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3403050600000000000000000000000000000000000000
                    IE: Unknown: DD07000C4300000000

wwan0     Interface doesn't support scanning.

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


```

Thanks!

---

### Post by praseodym on 2013-07-11
Change the encryption to WPA2-AES (CCMP) only, see the router manual.

---

### Post by fragusius on 2013-07-11
Maybe I'm wrong, but isn't router only for wireless? I got my internet through an usb. Is it still this that I should change?

---

