---
title: "Ubuntu 12.04 network goes on and off"
date: 2013-08-08
forum: Networking &amp; Wireless
---

### Post by devassyhere on 2013-08-08
I was using Ubuntu 12.04 for a long time. I update Ubuntu once in a month. Last I updated networking issues started cropping up.

**Internet disconnects and after some long amount of time it reconnects.**

I tried searching a lot and tried some solutions, but none works for me.

The things that i tried are
1) editing /etc/resolvconf/resolv.conf.d/head and adding nameservers ( from google and open DNS ) - I did this because I found DNS resolution itself fails , So i thought this might help
2) editing /etc/NetworkManager/NetworkManager.conf turning off dnsmasq
3) Ignoring ipv6 as suggested in [http://askubuntu.com/questions/127614/internet-goes-on-and-off-after-updating-to-12-04](http://askubuntu.com/questions/127614/internet-goes-on-and-off-after-updating-to-12-04) 

but nothing seems to correct it.

**I keep disable-enable networking to fix the issue.**

Please help me.

---

### Post by praseodym on 2013-08-08
Hi,

please show the outputs of
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
iwlist chan
sudo iwlist scan
```

---

### Post by wildmanne39 on 2013-08-08
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by devassyhere on 2013-08-08
I am adding the outputs under. ( MAC addressess are striked out )

> **praseodym said:**
> Hi,

please show the outputs of
```

# uname -a
Linux echu 3.2.0-51-generic-pae #77-Ubuntu SMP Wed Jul 24 20:40:32 UTC 2013 i686 i686 i386 GNU/Linux

# lspci -nnk | grep -iA2 net
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Dell Device [1028:0506]
    Kernel driver in use: r8169
--
09:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Dell Device [1028:0012]
    Kernel driver in use: brcmsmac



# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0a5c:21bc Broadcom Corp. BCM2070 Bluetooth 2.1 + EDR
Bus 001 Device 004: ID 0bda:58c1 Realtek Semiconductor Corp.


# lsmod
Module                  Size  Used by
rfcomm                 38139  14 
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17830  2 
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_idt      60251  1 
joydev                 17393  0 
bcma                   25651  0 
arc4                   12473  2 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_hda_intel          32719  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
brcmsmac              540923  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               67203  0 
mac80211              436493  1 brcmsmac
psmouse                86520  0 
serio_raw              13027  0 
brcmutil               14675  1 brcmsmac
cfg80211              178877  2 brcmsmac,mac80211
crc8                   12781  1 brcmsmac
cordic                 12518  1 brcmsmac
videodev               86588  1 uvcvideo
btusb                  17948  2 
bluetooth             158447  23 rfcomm,bnep,btusb
wmi                    18744  1 dell_wmi
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  428056  3 
drm_kms_helper         45466  1 i915
drm                   197641  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
snd                    62218  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  19115  1 i915
mac_hid                13077  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mei                    36570  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56396  0 


# iwconfig
lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"arton"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate=65 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:29   Missed beacon:0


eth0      no wireless extensions.


# rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no



# iwlist chan
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
          Current Frequency=2.437 GHz (Channel 6)


eth0      no frequency information.


# sudo iwlist scan
lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: xx:xx:xx:xx:xx:xx
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"xxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000342029540
                    Extra: Last beacon: 808ms ago
                    IE: Unknown: 00056172746F6E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406080800000000000000000000000000000000000000
                    IE: Unknown: 3D1606080800000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD770050F204104A0001101044000102103B000103104700100000000000001000000014D64D34E60010210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363535104200046E6F6E651054000800060050F2040001101100074449522D363535100800020084103C000103
          Cell 02 - Address: xx:xx:xx:xx:xx:xx
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"xxxxxxx"
                    Bit Rates:9 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000332de388d8
                    Extra: Last beacon: 1168ms ago
                    IE: Unknown: 000E53746164656E476F7465626F7267
                    IE: Unknown: 0108129618243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706534520010D14
                    IE: Unknown: 0B050000028D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFE000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: 851E00008F000F00FF0359004150313035573030312D4B616C6C740000000036
                    IE: Unknown: 9606004096001100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961405
          Cell 03 - Address: xx:xx:xx:xx:xx:xx
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"xxxxxxxxxxxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000005aec2d604c6
                    Extra: Last beacon: 1160ms ago
                    IE: Unknown: 0011544E5F707269766174655F58454B433354
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706534520010D14
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000C4304000000
          Cell 04 - Address: xx:xx:xx:xx:xx:xx
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"xxxxxxxxxxxxxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002c26a74c18c
                    Extra: Last beacon: 1148ms ago
                    IE: Unknown: 00175472C3A5646CC3B673204EC3A474204CC3A56E6773616D
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 0B050100140000
                    IE: Unknown: 2D1AAD1817FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100080000000040
                    IE: Unknown: DD310050F204104A000110104400010210470010CF64BCE3A9B57E7B137BF652638DC71C103C0001031049000600372A000120
                    IE: Unknown: DD090010180201001C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: xx:xx:xx:xx:xx:xx
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"xxxxxxxxxxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002c26a74cc78
                    Extra: Last beacon: 1148ms ago
                    IE: Unknown: 00200000000000000000000000000000000000000000000000000000000000000000
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 0B050000140000
                    IE: Unknown: 2D1AAD1817FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100080000000040
                    IE: Unknown: DD090010180200001C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: xx:xx:xx:xx:xx:xx
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"xxxxxxx"
                    Bit Rates:9 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000332de4b344
                    Extra: Last beacon: 1144ms ago
                    IE: Unknown: 000C73746164656E216775657374
                    IE: Unknown: 0108129618243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 0706534520010D14
                    IE: Unknown: 0B050000028D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFE000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: 851E00008F000F00FF0359004150313035573030312D4B616C6C740000000036
                    IE: Unknown: 9606004096001100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
          Cell 07 - Address: xx:xx:xx:xx:xx:xx
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"xxxxxxxxxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002c66011dd46
                    Extra: Last beacon: 1076ms ago
                    IE: Unknown: 000744726F7373656C
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010006
                    IE: Unknown: DD270050F204104A000110104400010210470010BC329E001DD811B28601C8600093F37E103C000101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050100000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000019127A
                    IE: Unknown: DD07000C4307000000
          Cell 08 - Address: xx:xx:xx:xx:xx:xx
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"xxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b6fdc25ed9
                    Extra: Last beacon: 808ms ago
                    IE: Unknown: 00056172746F6E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706534520010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAD0103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 331AAD0103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D16060C0600000000000000000000000000000000000000
                    IE: Unknown: 3416060C0600000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101850003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 09 - Address: xx:xx:xx:xx:xx:xx
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"xxxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000008664e216b
                    Extra: Last beacon: 852ms ago
                    IE: Unknown: 000677696B6E6574
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030108
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A88028107B8E5700103C000101
                    IE: Unknown: 0504000100E0
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1608000400000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0504000D127A
                    IE: Unknown: DD07000C4307000000
          Cell 10 - Address: xx:xx:xx:xx:xx:xx
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Getlost.exe"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000028e63c29a5
                    Extra: Last beacon: 356ms ago
                    IE: Unknown: 000B4765746C6F73742E657865
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFD191BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DDAC0050F204104A0001101044000102103B000103104700105ACF2714EC1946C3D13F222A0EF431B7102100154153555354654B20436F6D707574657220496E632E1023001C57692D46692050726F74656374656420536574757020526F757465721024000752542D4E3636551042001130383A36303A36453A42413A41453A31381054000800060050F20400011011000752542D4E363655100800022008103C0001031049000600372A000120
                    IE: Unknown: DD090010180207F03C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 11 - Address: xx:xx:xx:xx:xx:xx
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"Thomson6B7BD1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000030e5fe4187
                    Extra: Last beacon: 1124ms ago
                    IE: Unknown: 000D54686F6D736F6E364237424431
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180201F0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: 08:76:FF:96:9D:14
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"TN_private_969D14"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000014219a12195
                    Extra: Last beacon: 932ms ago
                    IE: Unknown: 0011544E5F707269766174655F393639443134
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    IE: Unknown: DD090010180201000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 13 - Address: xx:xx:xx:xx:xx:xx
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"xxxxxvind"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000008bcd0d440d7
                    Extra: Last beacon: 160ms ago
                    IE: Unknown: 0011416B657272656E73675F32322D76696E64
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010D
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700E04C02022000
                    IE: Unknown: DD0E0050F204104A0001101044000101



```

---

