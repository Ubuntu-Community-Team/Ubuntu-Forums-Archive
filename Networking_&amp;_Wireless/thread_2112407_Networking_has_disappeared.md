---
title: "Networking has disappeared"
date: 2013-02-04
forum: Networking &amp; Wireless
---

### Post by Cyclops_ on 2013-02-04
I logged in today and networking has disappeared. It seems to connect to my router, as it shows in the panel. However, I cannot get to any pages, and that includes the router itself through 192.168.1.1. I do get an IP address, but I'm not sure if it is one that I have set aside in my router, because I cannot get to my router. I also cannot connect via a wired connection. It simply stopped working. I did just receive an update, but I did restart the computer and go into my last known good kernel. That did not work any help would be appreciated.

EDIT: I do know that it is not related to protocol, because I tried both port 80 and port 21.

---

### Post by Cyclops_ on 2013-02-04
also, it is not hardware related. Networking and the internet work completely in Windows.

---

### Post by Cyclops_ on 2013-02-04
Can anyone think of anything I can troubleshoot or do?  If I can't even get on with wired, I won't be able to receive any pushed updates that would correct this.

I need to be able to work tomorrow!  Please help!!

---

### Post by steeldriver on 2013-02-04
what are the outputs of 

```
ifconfig
``````
route -n
```

---

### Post by Cyclops_ on 2013-02-04
```

$ ifconfig

lo      Link encap:Local Loopback
        inet addr:127.0.0.1  Mask 255.0.0.0
        inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING  MTU:16436  Metric:1
        RX packets:119 errors:0 dropped:0 overruns:0 frame:0
        TX packets:119 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:9153 (9.1 KB)  TX bytes:9153 (9.1 KB)

tun0    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
        inet addr:10.8.0.26  P-t-P:10.8.0.25  Mask:255.255.255.255
        UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:100
        RX bytes:0 (0.0 B)  TX bytes:1845 (1.8 KB)

wlan0   Link encap:Ethernet  HWaddr 6b:3d:43:45:3e:a7
        inet addr:192.168.1.72  Bcast:192.168.1.255  Mask:255.255.255.255
        inet6 addr: fe80::7d5d:83ff:fe85:3ed7/64
        UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
        RX packets:137 errors:0 dropped:0 overruns:0 frame:0
        TX packets:163 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:17025 (17.0 KB)  TX bytes:25702 (25.7 KB)

```

```

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0      0   wlan0
10.8.0.0        10.8.0.25       255.255.255.0   UG    0      0      0   tun0
10.8.0.25       0.0.0.0         255.255.255.255 UH    0      0      0   tun0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0      0   wlan0
192.168.1.0     10.8.0.25       255.255.255.0   UG    0      0      0   tun0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0      0   wlan0

```

---

### Post by Cyclops_ on 2013-02-05
Here is just about everything you might want to know:

```

*************** info trace ****************

**** uname -a ****

Linux sethmangold-N56VM 3.5.0-23-generic #35-Ubuntu SMP Thu Jan 24 13:15:40 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"


**** lspci ****


03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0887] (rev c4)
	Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4062]
	Kernel driver in use: iwlwifi
--
04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8161 Gigabit Ethernet [1969:1091] (rev 10)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1477]


**** lsusb ****


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 2109:2812  
Bus 004 Device 002: ID 2109:0812  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:07da Intel Corp. 
Bus 001 Device 004: ID 064e:d213 Suyin Corp. 
Bus 003 Device 003: ID 2109:2812  
Bus 003 Device 010: ID 2109:2812  
Bus 004 Device 003: ID 2109:0812  
Bus 004 Device 004: ID 2109:0812  
Bus 003 Device 005: ID 15ca:1804 Textech International Ltd. 
Bus 003 Device 006: ID 18ea:0003 Matrox Graphics, Inc. 
Bus 003 Device 007: ID 088e:5036 iLok Portable secure storage for software licenses
Bus 003 Device 008: ID 0819:0101 eLicenser License Management and Copy Protection
Bus 003 Device 012: ID 154b:005d PNY 
Bus 003 Device 011: ID 046d:c52b Logitech, Inc. Unifying Receiver


**** iwconfig ****


wlan0     IEEE 802.11bgn  ESSID:"moroni"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: <MAC address removed>   
          Bit Rate=39 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-29 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:45  Invalid misc:51   Missed beacon:0



**** rfkill ****


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


**** lsmod ****


Module                  Size  Used by
uas                    17845  0 
usb_storage            48839  1 
snd_hrtimer            12745  1 
bbswitch               13397  0 
rfcomm                 46620  16 
parport_pc             32689  0 
ppdev                  17074  0 
bnep                   18141  2 
binfmt_misc            17501  1 
coretemp               13401  0 
arc4                   12530  2 
kvm_intel             132760  0 
i915                  520621  3 
snd_hda_codec_realtek    78048  1 
iwlwifi               386874  0 
kvm                   414071  1 kvm_intel
snd_usb_audio         130468  0 
snd_hda_intel          33492  3 
asus_nb_wmi            12711  0 
snd_hda_codec         134213  2 snd_hda_codec_realtek,snd_hda_intel
drm_kms_helper         49113  1 i915
ghash_clmulni_intel    13221  0 
aesni_intel            51038  3 
asus_wmi               24089  1 asus_nb_wmi
joydev                 17458  0 
drm                   288721  4 i915,drm_kms_helper
snd_pcm                96668  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_hwdep              17699  2 snd_usb_audio,snd_hda_codec
snd_usbmidi_lib        24954  1 snd_usb_audio
mac80211              539958  1 iwlwifi
snd_seq_midi           13325  0 
snd_rawmidi            30513  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  3 snd_seq_midi,snd_seq_midi_event
snd_timer              29426  3 snd_hrtimer,snd_pcm,snd_seq
uvcvideo               76750  0 
i2c_algo_bit           13414  1 i915
btusb                  22475  0 
mxm_wmi                13022  0 
bluetooth             209249  22 rfcomm,bnep,btusb
video                  19336  1 i915
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
sparse_keymap          13891  1 asus_wmi
mac_hid                13206  0 
wmi                    19071  2 asus_wmi,mxm_wmi
aes_x86_64             17256  1 aesni_intel
videobuf2_core         32852  1 uvcvideo
lp                     17760  0 
psmouse                95595  0 
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78921  18 snd_hda_codec_realtek,snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
soundcore              15048  1 snd
parport                46346  3 parport_pc,ppdev,lp
videodev              120310  2 uvcvideo,videobuf2_core
cfg80211              206797  2 iwlwifi,mac80211
serio_raw              13216  0 
microcode              22804  0 
videobuf2_vmalloc      12861  1 uvcvideo
lpc_ich                17062  0 
videobuf2_memops       13405  1 videobuf2_vmalloc
mei                    40691  0 
nls_iso8859_1          12714  2 
hid_logitech_dj        18605  0 
hid_generic            12541  0 
usbhid                 46987  1 hid_logitech_dj
hid                   100411  3 hid_logitech_dj,hid_generic,usbhid


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: wlan0  [lenetwork] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    mike:            Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2
    BYUCougars2:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 75 WPA2
    ll126:           Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 55 WPA2
    fluffyLAZORZ:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    fluffyLAZORZ-guest: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57
    Coffeys:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    BAH:             Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 37 WPA2
    AnaeNET:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA
    chuckncynthia:   Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 59 WPA2
    belkin.98d:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA2
    NETGEAR72:       Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 52 WPA2
    *lenetwork:      Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 90 WPA2
    Hembysa:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Hembysa-guest:   Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34
    CoburnsConnection: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA2

  IPv4 Settings:
    Address:         192.168.1.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=70/70  Signal level=-31 dBm  
                    Encryption key:on
                    ESSID:"lenetwork"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000004828982
                    Extra: Last beacon: 347116ms ago
                    IE: Unknown: 00066D6F726F6E69
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3405080800000000000000000000000000000000000000
                    IE: Unknown: 3D1605080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: DD820050F204104A000110104400010210570001001041000100103B00010310470010565AA94967C14C0EAA8FF349E6F593111021000D4E6574676561722C20496E632E10230007574E523230303010240007574E523230303010420004353637381054000800060050F204000110110007574E5232303030100800020084103C000103
          Cell 02 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"chuckncynthia"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007249850160
                    Extra: Last beacon: 1116ms ago
                    IE: Unknown: 000D636875636B6E63796E74686961
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAC4117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1602001100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301720320
                    IE: Unknown: DD070017F203020180
                    IE: Unknown: DD0E0017F20700010106109ADD8C5517
          Cell 03 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=70/70  Signal level=-29 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000338f580
                    Extra: Last beacon: 156ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3405080800000000000000000000000000000000000000
                    IE: Unknown: 3D1605080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 04 - Address: <MAC address removed>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"ll126"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000162fc9d80
                    Extra: Last beacon: 940ms ago
                    IE: Unknown: 00056C6C313236
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: Unknown: 050400030000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34030D0A00000000000000000000000000000000000000
                    IE: Unknown: 3D16030D0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD270050F204104A00011010440001021047001000000000000010000000E091F5CB992A103C000103
          Cell 05 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"mike"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000039cc66218b
                    Extra: Last beacon: 688ms ago
                    IE: Unknown: 00046D696B65
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16090F1600000000000000000000000000000000000000
                    IE: Unknown: DD7C0050F204104A00011010440001021041000100103B000103104700104733250947AD946E16B885C801C04D471021000D4E4554474541522C20496E632E10230009574E5232303030763210240009574E523230303076321042000230311054000800060050F204000110110009574E52323030307632100800020084
                    IE: Unknown: DD090010180202F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34090F1600000000000000000000000000000000000000
          Cell 06 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"BYUCougars2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 548ms ago
                    IE: Unknown: 000B425955436F756761727332
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD830050F204104A0001101044000102103B00010310470010035E125477410AD5BE448A129D85ADA21021000D4E4554474541522C20496E632E10230008574E44523430303010240008574E4452343030301042000230311054000800060050F204000110110008574E445234303030100800020004103C0001031049000600372A000120
                    IE: Unknown: DD090010180202F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


**** dmesg ****


[   28.033307] wmi: Mapper loaded
[   28.267595] asus_wmi: ASUS WMI generic driver loaded
[   28.329167] asus_wmi: Initialization: 0x1asus_wmi: BIOS WMI version: 7.9
[   28.329214] asus_wmi: SFUN value: 0x6a0877<6>[   28.329633] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input7
[   28.395266] iwlwifi: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   28.395268] iwlwifi: Copyright(c) 2003-2012 Intel Corporation
[   28.395327] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[   28.395328] iwlwifi 0000:03:00.0: pci_resource_base = ffffc900040d4000
[   28.395329] iwlwifi 0000:03:00.0: HW Revision ID = 0xC4
[   28.395401] iwlwifi 0000:03:00.0: irq 48 for MSI/MSI-X
[   28.396768] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1
[   28.396924] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   28.396926] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   28.396927] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   28.396928] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   28.396929] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_P2P disabled
[   28.396930] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[   28.396982] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   28.408131] asus_wmi: Backlight controlled by ACPI video driver
[   28.413509] iwlwifi 0000:03:00.0: device EEPROM VER=0x81c, CALIB=0x6
[   28.413512] iwlwifi 0000:03:00.0: Device SKU: 0x150
[   28.413514] iwlwifi 0000:03:00.0: Valid Tx ant: 0x3, Valid Rx ant: 0x3
[   28.413529] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   28.467648] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   28.751911] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   28.759208] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[   29.022627] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   29.029946] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[   29.118796] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.119420] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.169926] wlan0: authenticate with <MAC address removed>
[   30.177848] wlan0: send auth to <MAC address removed> (try 1/3)
[   30.180201] wlan0: authenticated
[   30.180344] wlan0: waiting for beacon from <MAC address removed>
[   30.221628] wlan0: associate with <MAC address removed> (try 1/3)
[   30.225895] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[   30.245222] wlan0: associated
[   30.245690] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  176.463173] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  219.568506] wlan0: authenticate with <MAC address removed>
[  219.577308] wlan0: send auth to <MAC address removed> (try 1/3)
[  219.579639] wlan0: authenticated
[  219.579771] wlan0: waiting for beacon from <MAC address removed>
[  219.669219] wlan0: associate with <MAC address removed> (try 1/3)
[  219.673760] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[  219.678434] wlan0: associated


**************** done ********************

```

---

### Post by Cyclops_ on 2013-02-05
Please, anyone?  I need to get back to work!!!!!  I'm losing daylight and moneys...

---

### Post by Cyclops_ on 2013-02-05
I'm willing to try anything... I just need to know what I can try!!!!

---

### Post by mörgæs on 2013-02-05
Please stop bumping your thread.

---

### Post by Cyclops_ on 2013-02-05
I do sincerely apologize for that.

It's really hard sitting on my hands, not having a clue what I can do on the networking side when I'm supposed to be working.  (And losing a lot of money by not working.)

Ubuntu isn't exactly a hobby for me.  It's my working environment.  And to give you an idea, I'll probably end up losing $1000 today alone if I can't get this up fast.

I've also been watching all other similar threads to see if anyone else is being given advice that I haven't.

Anyway - I apologize, the intent wasn't to bump, but mostly to plea.

---

### Post by Cyclops_ on 2013-02-05
(In fact, if there was any kind of phone support or paid support that would allow me to get this back up *now*, I will take it.)

---

### Post by Cyclops_ on 2013-02-05
Oh no.  Now I don't know what I did....

Somehow I lost both eth0 and wlan0 when I do ifconfig.  Also, there is no networking icon in the panel anymore.

---

### Post by Cyclops_ on 2013-02-05
Here is what everything looks like now (it looks like stuff has changed, like the network interfaces have disappeared, etc).

```



*************** info trace ****************



**** uname -a ****


Linux <name removed>-N56VM 3.5.0-23-generic #35-Ubuntu SMP Thu Jan 24 13:15:40 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"


**** lspci ****


03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0887] (rev c4)
	Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4062]
	Kernel driver in use: iwlwifi
--
04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8161 Gigabit Ethernet [1969:1091] (rev 10)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1477]


**** lsusb ****


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 2109:2812  
Bus 004 Device 002: ID 2109:0812  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:07da Intel Corp. 
Bus 001 Device 004: ID 064e:d213 Suyin Corp. 
Bus 003 Device 003: ID 2109:2812  
Bus 003 Device 012: ID 2109:2812  
Bus 004 Device 003: ID 2109:0812  
Bus 004 Device 004: ID 2109:0812  
Bus 003 Device 005: ID 15ca:1804 Textech International Ltd. 
Bus 003 Device 006: ID 18ea:0003 Matrox Graphics, Inc. 
Bus 003 Device 007: ID 088e:5036 iLok Portable secure storage for software licenses
Bus 003 Device 008: ID 0819:0101 eLicenser License Management and Copy Protection
Bus 003 Device 013: ID 046d:c52b Logitech, Inc. Unifying Receiver


**** iwconfig ****


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


**** rfkill ****


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


**** lsmod ****


Module                  Size  Used by
snd_hrtimer            12745  1 
bbswitch               13397  0 
snd_hda_codec_realtek    78048  1 
parport_pc             32689  0 
ppdev                  17074  0 
bnep                   18141  2 
rfcomm                 46620  16 
binfmt_misc            17501  1 
uvcvideo               76750  0 
arc4                   12530  2 
snd_hda_intel          33492  3 
videobuf2_core         32852  1 uvcvideo
iwlwifi               386874  0 
videodev              120310  2 uvcvideo,videobuf2_core
snd_hda_codec         134213  2 snd_hda_codec_realtek,snd_hda_intel
snd_usb_audio         130468  0 
i915                  520621  3 
snd_usbmidi_lib        24954  1 snd_usb_audio
videobuf2_vmalloc      12861  1 uvcvideo
snd_hwdep              17699  2 snd_hda_codec,snd_usb_audio
snd_pcm                96668  3 snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_seq_midi           13325  0 
snd_rawmidi            30513  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  3 snd_seq_midi,snd_seq_midi_event
mac80211              539958  1 iwlwifi
videobuf2_memops       13405  1 videobuf2_vmalloc
drm_kms_helper         49113  1 i915
snd_timer              29426  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
coretemp               13401  0 
asus_nb_wmi            12711  0 
drm                   288721  4 i915,drm_kms_helper
kvm_intel             132760  0 
kvm                   414071  1 kvm_intel
snd                    78921  18 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_usbmidi_lib,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
btusb                  22475  0 
joydev                 17458  0 
soundcore              15048  1 snd
i2c_algo_bit           13414  1 i915
mei                    40691  0 
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
psmouse                95595  0 
asus_wmi               24089  1 asus_nb_wmi
lpc_ich                17062  0 
video                  19336  1 i915
sparse_keymap          13891  1 asus_wmi
ghash_clmulni_intel    13221  0 
aesni_intel            51038  0 
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
mac_hid                13206  0 
mxm_wmi                13022  0 
bluetooth             209249  22 bnep,rfcomm,btusb
cfg80211              206797  2 iwlwifi,mac80211
serio_raw              13216  0 
wmi                    19071  2 asus_wmi,mxm_wmi
aes_x86_64             17256  1 aesni_intel
lp                     17760  0 
microcode              22804  0 
parport                46346  3 parport_pc,ppdev,lp
nls_iso8859_1          12714  1 
hid_logitech_dj        18605  0 
hid_generic            12541  0 
usbhid                 46987  1 hid_logitech_dj
hid                   100411  3 hid_logitech_dj,hid_generic,usbhid


**** nm-tool ****



NetworkManager Tool

State: unknown



**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


auto lo
iface lo inet loopback


**** iwlist ****




**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


**** dmesg ****


[   21.833784] wmi: Mapper loaded
[   21.944500] asus_wmi: ASUS WMI generic driver loaded
[   22.228432] asus_wmi: Initialization: 0x1asus_wmi: BIOS WMI version: 7.9
[   22.228492] asus_wmi: SFUN value: 0x6a0877<6>[   22.228903] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input6
[   22.298421] asus_wmi: Backlight controlled by ACPI video driver
[   22.500619] iwlwifi: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   22.500621] iwlwifi: Copyright(c) 2003-2012 Intel Corporation
[   22.500678] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[   22.500680] iwlwifi 0000:03:00.0: pci_resource_base = ffffc900040e0000
[   22.500681] iwlwifi 0000:03:00.0: HW Revision ID = 0xC4
[   22.500753] iwlwifi 0000:03:00.0: irq 48 for MSI/MSI-X
[   22.502217] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1
[   22.502374] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   22.502375] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   22.502376] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   22.502377] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   22.502378] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_P2P disabled
[   22.502379] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[   22.502428] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   22.518786] iwlwifi 0000:03:00.0: device EEPROM VER=0x81c, CALIB=0x6
[   22.518788] iwlwifi 0000:03:00.0: Device SKU: 0x150
[   22.518790] iwlwifi 0000:03:00.0: Valid Tx ant: 0x3, Valid Rx ant: 0x3
[   22.518803] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   22.530727] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[  327.405641] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[  331.499527] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.


**************** done ********************

```

---

### Post by jdthood on 2013-02-05
In your last listing there was an important anomaly (which did not exist in the first listing). You have configured NetworkManager to use dnsmasq as a forwarding nameserver, as indicated by the line
```

    dns=dnsmasq

```
in /etc/NetworkManager/NetworkManager.conf. However, /etc/resolv.conf does not contain the line
```

    nameserver 127.0.1.1

```
which causes the resolver to talk to the dnsmasq process controlled by NetworkManager.

1. Are you using a third-party VPN client? Which one? Sometimes third-party VPN clients trash /etc/resolv.conf. Run 
```

    sudo dpkg-reconfigure resolvconf

```
and see if /etc/resolv.conf contains the "nameserver 127.0.1.1" line again; and see if this improves anything.

2. Disable the NetworkManager-controlled nameserver. It's not always reliable. Edit /etc/NetworkManager/NetworkManager.conf and comment out the line "dns=dnsmasq" so that it looks like the following.
```

    #dns=dnsmasq

```

P.S. If this helps I want a cut of the $1000. ;)

---

### Post by Cyclops_ on 2013-02-05
Well done jthood.  I think we're back to where we were originally.  Still no network... but I have the icon back and ifconfig lists stuff now.  Here's the output:

```



*************** info trace ****************



**** uname -a ****


Linux <name removed>-N56VM 3.5.0-23-generic #35-Ubuntu SMP Thu Jan 24 13:15:40 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"


**** lspci ****


03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0887] (rev c4)
	Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4062]
	Kernel driver in use: iwlwifi
--
04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8161 Gigabit Ethernet [1969:1091] (rev 10)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1477]


**** lsusb ****


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 2109:2812  
Bus 004 Device 002: ID 2109:0812  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:07da Intel Corp. 
Bus 001 Device 004: ID 064e:d213 Suyin Corp. 
Bus 003 Device 003: ID 2109:2812  
Bus 003 Device 004: ID 2109:2812  
Bus 004 Device 003: ID 2109:0812  
Bus 004 Device 004: ID 2109:0812  
Bus 003 Device 005: ID 15ca:1804 Textech International Ltd. 
Bus 003 Device 006: ID 18ea:0003 Matrox Graphics, Inc. 
Bus 003 Device 007: ID 088e:5036 iLok Portable secure storage for software licenses
Bus 003 Device 008: ID 0819:0101 eLicenser License Management and Copy Protection
Bus 003 Device 010: ID 154b:005d PNY 
Bus 003 Device 009: ID 046d:c52b Logitech, Inc. Unifying Receiver


**** iwconfig ****


wlan0     IEEE 802.11bgn  ESSID:"lenetwork"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: <MAC address removed>   
          Bit Rate=65 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-23 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:30  Invalid misc:48   Missed beacon:0



**** rfkill ****


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no


**** lsmod ****


Module                  Size  Used by
uas                    17845  0 
usb_storage            48839  1 
snd_hrtimer            12745  1 
bbswitch               13397  0 
snd_hda_codec_realtek    78048  1 
parport_pc             32689  0 
rfcomm                 46620  16 
ppdev                  17074  0 
bnep                   18141  2 
binfmt_misc            17501  1 
coretemp               13401  0 
snd_hda_intel          33492  3 
kvm_intel             132760  0 
snd_hda_codec         134213  2 snd_hda_codec_realtek,snd_hda_intel
asus_nb_wmi            12711  0 
mxm_wmi                13022  0 
asus_wmi               24089  1 asus_nb_wmi
sparse_keymap          13891  1 asus_wmi
kvm                   414071  1 kvm_intel
wmi                    19071  2 mxm_wmi,asus_wmi
i915                  520621  3 
arc4                   12530  2 
iwlwifi               386874  0 
ghash_clmulni_intel    13221  0 
aesni_intel            51038  3 
snd_usb_audio         130468  0 
uvcvideo               76750  0 
snd_pcm                96668  3 snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_hwdep              17699  2 snd_hda_codec,snd_usb_audio
snd_usbmidi_lib        24954  1 snd_usb_audio
btusb                  22475  0 
drm_kms_helper         49113  1 i915
videobuf2_core         32852  1 uvcvideo
drm                   288721  4 i915,drm_kms_helper
videodev              120310  2 uvcvideo,videobuf2_core
bluetooth             209249  22 rfcomm,bnep,btusb
videobuf2_vmalloc      12861  1 uvcvideo
snd_seq_midi           13325  0 
snd_seq_midi_event     14900  1 snd_seq_midi
videobuf2_memops       13405  1 videobuf2_vmalloc
joydev                 17458  0 
mac_hid                13206  0 
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
lp                     17760  0 
mac80211              539958  1 iwlwifi
snd_seq                61555  3 snd_seq_midi,snd_seq_midi_event
snd_timer              29426  3 snd_hrtimer,snd_pcm,snd_seq
snd_rawmidi            30513  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_device         14498  3 snd_seq_midi,snd_seq,snd_rawmidi
cfg80211              206797  2 iwlwifi,mac80211
snd                    78921  18 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_seq,snd_timer,snd_rawmidi,snd_seq_device
i2c_algo_bit           13414  1 i915
soundcore              15048  1 snd
aes_x86_64             17256  1 aesni_intel
mei                    40691  0 
parport                46346  3 parport_pc,ppdev,lp
psmouse                95595  0 
microcode              22804  0 
serio_raw              13216  0 
video                  19336  1 i915
hid_logitech_dj        18605  0 
lpc_ich                17062  0 
nls_iso8859_1          12714  2 
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
hid_generic            12541  0 
usbhid                 46987  1 hid_logitech_dj
hid                   100411  3 hid_logitech_dj,hid_generic,usbhid


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: wlan0  [lenetwork] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    BYUCougars2:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 87 WPA2
    mike:            Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    ll126:           Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 49 WPA2
    chuckncynthia:   Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 47 WPA2
    fluffyLAZORZ:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    Coffeys:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    NETGEAR72:       Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 39 WPA2
    BAH:             Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 37 WPA2
    CoburnsConnection: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA2
    DB Airport Express: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA2
    NETGEAR25:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA2
    fluffyLAZORZ-guest: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44
    *lenetwork:      Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 95 WPA2
    belkin.98d:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA2
    los taco amigos: Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 34 WPA2
    Hembysa:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    NETGEAR92:       Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 34 WPA2
    SilverMonkey:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    myqwest4359:     Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    AnaeNET:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA
    beachhouse:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


auto lo
iface lo inet loopback


**** iwlist ****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=70/70  Signal level=-23 dBm  
                    Encryption key:on
                    ESSID:"lenetwork"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000002b1558
                    Extra: Last beacon: 131708ms ago
                    IE: Unknown: 00066D6F726F6E69
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3405080800000000000000000000000000000000000000
                    IE: Unknown: 3D1605080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: DD820050F204104A000110104400010210570001001041000100103B00010310470010565AA94967C14C0EAA8FF349E6F593111021000D4E6574676561722C20496E632E10230007574E523230303010240007574E523230303010420004353637381054000800060050F204000110110007574E5232303030100800020084103C000103
          Cell 02 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"chuckncynthia"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000075744547b5
                    Extra: Last beacon: 22320ms ago
                    IE: Unknown: 000D636875636B6E63796E74686961
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAC4117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1602001100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301720320
                    IE: Unknown: DD070017F203020180
                    IE: Unknown: DD0E0017F20700010106109ADD8C5517
          Cell 03 - Address: <MAC address removed>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"ll126"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002c0811d91
                    Extra: Last beacon: 940ms ago
                    IE: Unknown: 00056C6C313236
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34030D0A00000000000000000000000000000000000000
                    IE: Unknown: 3D16030D0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD870050F204104A0001101044000102103B0001031047001000000000000010000000E091F5CB992A1021000D4E6574676561722C20496E632E1023000757504E3832344E1024000456324831104200046E6F6E651054000800060050F20400011011001957504E3832344E28576972656C6573732041502D322E344729100800020086103C000103
          Cell 04 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR72"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000014fc14aa27e
                    Extra: Last beacon: 1108ms ago
                    IE: Unknown: 00094E4554474541523732
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3404080800000000000000000000000000000000000000
                    IE: Unknown: 3D1604080800000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD7A0050F204104A0001101044000102103B0001031047001000000000000010000000008EF25B4FC6102100044E54475210230009776E72323030307633102400016E104200046E6F6E651054000800060050F204000110110016574E5232303030763328576972656C65737320415029100800020086103C000103
          Cell 05 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=70/70  Signal level=-25 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000008051580
                    Extra: Last beacon: 140ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3405080800000000000000000000000000000000000000
                    IE: Unknown: 3D1605080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 06 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR25"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000033681680d1
                    Extra: Last beacon: 928ms ago
                    IE: Unknown: 00094E4554474541523235
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC191BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: DD870050F204104A00011010440001021041000100103B0001031047001052B95F2796B6E6AD820FBE381D1030CB1021000D4E4554474541522C20496E632E1023000A574E52333530304C76321024000A574E52333530304C763210420005333530304C1054000800060050F20400011011000A574E52333530304C7632100800020084103C000101
                    IE: Unknown: DD090010180203F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"AnaeNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001c74d6c1c9
                    Extra: Last beacon: 22104ms ago
                    IE: Unknown: 0007416E61654E4554
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 050400010006
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F0101001DFF7F
                    IE: Unknown: DD0C00037F020101000002A34000
                    IE: Unknown: DD1A00037F030100000000146C9618A602146C9618A664002C011D08
          Cell 08 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"mike"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003cf86a994f
                    Extra: Last beacon: 684ms ago
                    IE: Unknown: 00046D696B65
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16090F1600000000000000000000000000000000000000
                    IE: Unknown: DD7C0050F204104A00011010440001021041000100103B000103104700104733250947AD946E16B885C801C04D471021000D4E4554474541522C20496E632E10230009574E5232303030763210240009574E523230303076321042000230311054000800060050F204000110110009574E52323030307632100800020084
                    IE: Unknown: DD090010180202F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34090F1600000000000000000000000000000000000000
          Cell 09 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"BYUCougars2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 724ms ago
                    IE: Unknown: 000B425955436F756761727332
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD830050F204104A0001101044000102103B00010310470010035E125477410AD5BE448A129D85ADA21021000D4E4554474541522C20496E632E10230008574E44523430303010240008574E4452343030301042000230311054000800060050F204000110110008574E445234303030100800020004103C0001031049000600372A000120
                    IE: Unknown: DD090010180202F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 10 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"fluffyLAZORZ-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000037fcdfafed
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 0012666C756666794C415A4F525A2D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081100000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 11 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"fluffyLAZORZ"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000037fcdfa4e2
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 000C666C756666794C415A4F525A
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180201F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 12 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Coffeys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000018bcde74198
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 0007436F6666657973
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180201F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B081500000000000000000000000000000000000000
          Cell 13 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"belkin.98d"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000009376e70ee
                    Extra: Last beacon: 1272ms ago
                    IE: Unknown: 000A62656C6B696E2E393864
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180202100C0000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD9D0050F204104A00011010440001021041000100103B0001031047001000000000000000010003EC1A5909198D1021001242656C6B696E20436F72706F726174696F6E1023000946394B31303031763410240007342E30302E30361042000E31323132323447423432303430331054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020080
          Cell 14 - Address: <MAC address removed>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"ppsm"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a11328176
                    Extra: Last beacon: 1132ms ago



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


**** dmesg ****


[   20.041429] iwlwifi: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   20.041431] iwlwifi: Copyright(c) 2003-2012 Intel Corporation
[   20.041491] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[   20.041493] iwlwifi 0000:03:00.0: pci_resource_base = ffffc900040b8000
[   20.041495] iwlwifi 0000:03:00.0: HW Revision ID = 0xC4
[   20.041569] iwlwifi 0000:03:00.0: irq 47 for MSI/MSI-X
[   20.042920] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1
[   20.043093] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   20.043095] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   20.043097] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   20.043098] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   20.043100] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_P2P disabled
[   20.043102] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[   20.043154] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   20.059424] iwlwifi 0000:03:00.0: device EEPROM VER=0x81c, CALIB=0x6
[   20.059427] iwlwifi 0000:03:00.0: Device SKU: 0x150
[   20.059428] iwlwifi 0000:03:00.0: Valid Tx ant: 0x3, Valid Rx ant: 0x3
[   20.059444] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   20.087940] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   20.132107] wmi: Mapper loaded
[   20.152271] asus_wmi: ASUS WMI generic driver loaded
[   20.164280] asus_wmi: Initialization: 0x1asus_wmi: BIOS WMI version: 7.9
[   20.164349] asus_wmi: SFUN value: 0x6a0877<6>[   20.165012] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input7
[   20.259973] asus_wmi: Backlight controlled by ACPI video driver
[   20.626881] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   20.634226] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[   20.899696] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   20.907034] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[   20.995220] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.995439] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.152726] wlan0: authenticate with <MAC address removed>
[   22.161065] wlan0: send auth to <MAC address removed> (try 1/3)
[   22.163387] wlan0: authenticated
[   22.163532] wlan0: waiting for beacon from <MAC address removed>
[   22.197980] wlan0: associate with <MAC address removed> (try 1/3)
[   22.201728] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[   22.221583] wlan0: associated
[   22.222064] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


**************** done ********************

```

Dude, if you help me get this up, I'll throw a little cash your way :)  Probably won't be much, cuz I'm going to need it to get some long overdue bills paid, but I'll get you something when I get my next check.

---

### Post by Cyclops_ on 2013-02-05
Oh, I just saw your second line.  Applying now and restarting.

And, in answer to your question:  I'm not sure what vpn client I have installed (yes, I do have one, but I'm pretty sure I just got it out of synaptic).

---

### Post by Cyclops_ on 2013-02-05
Nope.  Still no luck.

Does it help to know that I can't even get to the router (192.168.1.1), even though it says I'm connected to it?

---

### Post by Cyclops_ on 2013-02-05
Another piece of the puzzle:

I just tried Wi-fi hotspot from my phone.  My computer connected just fine *and it worked*!  I can get internet from my phone.

This means it is something between my Ubuntu and the router.  But the same computer booted into Windows with the same router works just fine.

Any thoughts?

---

### Post by Cyclops_ on 2013-02-05
.... and here's another strange piece.  The computer (with ifconfig) is saying that I have an IP address (192.168.1.10).  If I go into "attached devices" on the router, it doesn't show any devices with that IP.  In fact, my device isn't on there at all.

Another thing I just thought of:  I have two other Ubuntu devices attached (wirelessly) to the router that can access things just fine.  (We just haven't given them the updates yet.)

---

### Post by steeldriver on 2013-02-05
I'm reluctant to jump in here because it seems like you have a VPN tunnel configuration - and I don't know anything about those

However as a basic test would it be possible to disable the VPN and see if you can get a regular routed connection?

---

### Post by Cyclops_ on 2013-02-05
I'd love to.  How does one disable a vpn connection?

---

### Post by Cyclops_ on 2013-02-05
THAT DID IT!!  openvpn was somehow mucking stuff up!

THANK YOU SO MUCH!!!!!!

---

### Post by jdthood on 2013-02-06
> **Cyclops_ said:**
> THAT DID IT!!  openvpn was somehow mucking stuff up!

Were you setting up a VPN without using NetworkManager to do it? That can cause problems.

---

