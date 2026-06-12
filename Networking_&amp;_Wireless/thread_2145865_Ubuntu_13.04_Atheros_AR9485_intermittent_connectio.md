---
title: "Ubuntu 13.04 Atheros AR9485 intermittent connection"
date: 2013-05-16
forum: Networking &amp; Wireless
---

### Post by chrisjlee84 on 2013-05-16
Just bought a new laptop and i'm havin issues with the Atheros Communications Inc. AR9485 wireless. Seems like it's very slow or it goes in and out often. I ran the wireless script. 

<code>


*************** info trace ****************






**** uname -a ****




Linux chris-S500CA 3.8.0-21-generic #32-Ubuntu SMP Tue May 14 22:16:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux




**** lsb-release ****




DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"




**** lspci ****




02:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: AzureWave Device [1a3b:2126]
    Kernel driver in use: ath9k
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: alx




**** lsusb ****




Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:5705 Realtek Semiconductor Corp. 
Bus 001 Device 007: ID 03eb:880a Atmel Corp. 




**** iwconfig ****




wlan0     IEEE 802.11bgn  ESSID:"D2LD9"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=40/70  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:132  Invalid misc:29   Missed beacon:0






**** rfkill ****




0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no




**** lsmod ****




Module                  Size  Used by
parport_pc             28152  0 
ppdev                  17073  0 
bnep                   18036  2 
rfcomm                 42641  0 
nls_iso8859_1          12713  1 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
btusb                  22474  0 
hid_multitouch         17366  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55399  3 
aes_x86_64             17255  1 aesni_intel
arc4                   12615  2 
bluetooth             228619  11 bnep,btusb,rfcomm
snd_hda_codec_hdmi     36913  1 
ath9k                 149924  0 
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
i915                  600351  4 
snd_hda_codec_via      51018  1 
ath9k_common           14055  1 ath9k
snd_hda_intel          39619  3 
gf128mul               14951  2 lrw,xts
joydev                 17377  0 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
ath9k_hw              413680  2 ath9k_common,ath9k
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
drm_kms_helper         49394  1 i915
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
drm                   286313  5 i915,drm_kms_helper
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
mac80211              606457  1 ath9k
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
i2c_algo_bit           13413  1 i915
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
cfg80211              510937  3 ath,ath9k,mac80211
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
alx                    67960  0 
mei                    41158  0 
snd_timer              29425  2 snd_pcm,snd_seq
asus_nb_wmi            12854  0 
mdio                   13807  1 alx
asus_wmi               24213  1 asus_nb_wmi
psmouse                95870  0 
mac_hid                13205  0 
snd                    68876  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
sparse_keymap          13890  1 asus_wmi
microcode              22881  0 
soundcore              12680  1 snd
serio_raw              13215  0 
wmi                    19070  1 asus_wmi
lpc_ich                17061  0 
video                  19390  2 i915,asus_wmi
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
hid_generic            12540  0 
usbhid                 47074  1 hid_multitouch
hid                   101002  3 hid_multitouch,hid_generic,usbhid
ahci                   25731  3 
libahci                31364  1 ahci




**** nm-tool ****






NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




- Device: wlan0  [D2LD9] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
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
    *D2LD9:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA2


  IPv4 Settings:
    Address:         192.168.1.15
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




# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback




**** iwlist ****




wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"D2LD9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c63189803b
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 000544324C4439
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A8C131BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706555320010B1B






**** resolv ****




# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search home




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




[    0.825673] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: da639d7d39047796a6cdf66158dce65752f170ea'
[   10.418203] wmi: Mapper loaded
[   10.657788] asus_wmi: ASUS WMI generic driver loaded
[   10.780824] asus_wmi: Initialization: 0x1asus_wmi: BIOS WMI version: 7.9
[   10.780918] asus_wmi: SFUN value: 0x4a0877<6>[   10.782008] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input4
[   10.845602] asus_wmi: Backlight controlled by ACPI video driver
[   12.233427] ath: EEPROM regdomain: 0x60
[   12.233431] ath: EEPROM indicates we should expect a direct regpair map
[   12.233434] ath: Country alpha2 being used: 00
[   12.233436] ath: Regpair used: 0x60
[   12.325575] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   25.998030] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.001021] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.614865] wlan0: authenticate with <MAC address removed>
[   28.623994] wlan0: send auth to <MAC address removed> (try 1/3)
[   28.625922] wlan0: authenticated
[   28.626306] wlan0: associate with <MAC address removed> (try 1/3)
[   28.629962] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[   28.630036] wlan0: associated
[   28.630048] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   28.633964] ath: regdomain 0x8348 updated by CountryIE
[   28.633967] ath: EEPROM regdomain: 0x8348
[   28.633967] ath: EEPROM indicates we should expect a country code
[   28.633969] ath: doing EEPROM country->regdmn map search
[   28.633970] ath: country maps to regdmn code: 0x3a
[   28.633971] ath: Country alpha2 being used: US
[   28.633972] ath: Regpair used: 0x3a
[ 2911.175798] wlan0: authenticate with <MAC address removed>
[ 2911.185075] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2911.187044] wlan0: authenticated
[ 2911.187248] wlan0: associate with <MAC address removed> (try 1/3)
[ 2911.190909] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 2911.190988] wlan0: associated
[ 2911.197334] ath: regdomain 0x8348 updated by CountryIE
[ 2911.197339] ath: EEPROM regdomain: 0x8348
[ 2911.197342] ath: EEPROM indicates we should expect a country code
[ 2911.197346] ath: doing EEPROM country->regdmn map search
[ 2911.197349] ath: country maps to regdmn code: 0x3a
[ 2911.197352] ath: Country alpha2 being used: US
[ 2911.197354] ath: Regpair used: 0x3a
[ 2924.157295] wlan0: authenticate with <MAC address removed>
[ 2924.165664] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2924.178285] wlan0: authenticated
[ 2924.179739] wlan0: associate with <MAC address removed> (try 1/3)
[ 2924.183449] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 2924.183516] wlan0: associated
[ 2924.189032] ath: regdomain 0x8348 updated by CountryIE
[ 2924.189036] ath: EEPROM regdomain: 0x8348
[ 2924.189038] ath: EEPROM indicates we should expect a country code
[ 2924.189040] ath: doing EEPROM country->regdmn map search
[ 2924.189042] ath: country maps to regdmn code: 0x3a
[ 2924.189044] ath: Country alpha2 being used: US
[ 2924.189045] ath: Regpair used: 0x3a
[ 2926.146911] wlan0: authenticate with <MAC address removed>
[ 2926.155580] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2926.157599] wlan0: authenticated
[ 2926.161351] wlan0: associate with <MAC address removed> (try 1/3)
[ 2926.165029] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 2926.165141] wlan0: associated
[ 2926.174994] ath: regdomain 0x8348 updated by CountryIE
[ 2926.175003] ath: EEPROM regdomain: 0x8348
[ 2926.175006] ath: EEPROM indicates we should expect a country code
[ 2926.175010] ath: doing EEPROM country->regdmn map search
[ 2926.175014] ath: country maps to regdmn code: 0x3a
[ 2926.175017] ath: Country alpha2 being used: US
[ 2926.175020] ath: Regpair used: 0x3a
[ 2935.943179] wlan0: authenticate with <MAC address removed>
[ 2935.951746] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2936.153356] wlan0: send auth to <MAC address removed> (try 2/3)
[ 2936.357191] wlan0: send auth to <MAC address removed> (try 3/3)
[ 2936.367442] wlan0: authenticated
[ 2936.369204] wlan0: associate with <MAC address removed> (try 1/3)
[ 2936.572895] wlan0: associate with <MAC address removed> (try 2/3)
[ 2936.776616] wlan0: associate with <MAC address removed> (try 3/3)
[ 2936.980410] wlan0: association with <MAC address removed> timed out
[ 2944.089459] wlan0: authenticate with <MAC address removed>
[ 2944.098046] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2944.299654] wlan0: send auth to <MAC address removed> (try 2/3)
[ 2944.301692] wlan0: authenticated
[ 2944.303715] wlan0: associate with <MAC address removed> (try 1/3)
[ 2944.316391] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 2944.316514] wlan0: associated
[ 2944.326135] ath: regdomain 0x8348 updated by CountryIE
[ 2944.326143] ath: EEPROM regdomain: 0x8348
[ 2944.326146] ath: EEPROM indicates we should expect a country code
[ 2944.326150] ath: doing EEPROM country->regdmn map search
[ 2944.326154] ath: country maps to regdmn code: 0x3a
[ 2944.326157] ath: Country alpha2 being used: US
[ 2944.326159] ath: Regpair used: 0x3a
[ 2951.927268] wlan0: authenticate with <MAC address removed>
[ 2951.936585] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2952.138272] wlan0: send auth to <MAC address removed> (try 2/3)
[ 2952.342023] wlan0: send auth to <MAC address removed> (try 3/3)
[ 2952.545786] wlan0: authentication with <MAC address removed> timed out
[ 2965.656169] wlan0: authenticate with <MAC address removed>
[ 2965.664503] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2965.670086] wlan0: authenticated
[ 2965.674124] wlan0: associate with <MAC address removed> (try 1/3)
[ 2965.877784] wlan0: associate with <MAC address removed> (try 2/3)
[ 2966.081546] wlan0: associate with <MAC address removed> (try 3/3)
[ 2966.285330] wlan0: association with <MAC address removed> timed out
[ 2966.447347] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3082.769632] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3084.833033] wlan0: authenticate with <MAC address removed>
[ 3084.841594] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3085.043201] wlan0: send auth to <MAC address removed> (try 2/3)
[ 3085.051697] wlan0: authenticated
[ 3085.055274] wlan0: associate with <MAC address removed> (try 1/3)
[ 3085.061830] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 3085.061994] wlan0: associated
[ 3085.062080] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3085.074686] ath: regdomain 0x8348 updated by CountryIE
[ 3085.074695] ath: EEPROM regdomain: 0x8348
[ 3085.074698] ath: EEPROM indicates we should expect a country code
[ 3085.074702] ath: doing EEPROM country->regdmn map search
[ 3085.074705] ath: country maps to regdmn code: 0x3a
[ 3085.074709] ath: Country alpha2 being used: US
[ 3085.074712] ath: Regpair used: 0x3a
[ 3588.816970] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3603.310940] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3675.517521] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3776.307822] wlan0: authenticate with <MAC address removed>
[ 3776.317300] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3776.322296] wlan0: authenticated
[ 3776.326707] wlan0: associate with <MAC address removed> (try 1/3)
[ 3776.330433] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 3776.330557] wlan0: associated
[ 3776.330578] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3776.341360] ath: regdomain 0x8348 updated by CountryIE
[ 3776.341370] ath: EEPROM regdomain: 0x8348
[ 3776.341375] ath: EEPROM indicates we should expect a country code
[ 3776.341381] ath: doing EEPROM country->regdmn map search
[ 3776.341388] ath: country maps to regdmn code: 0x3a
[ 3776.341393] ath: Country alpha2 being used: US
[ 3776.341398] ath: Regpair used: 0x3a
[ 3881.086886] wlan0: authenticate with <MAC address removed>
[ 3881.096375] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3881.101868] wlan0: authenticated
[ 3881.105940] wlan0: associate with <MAC address removed> (try 1/3)
[ 3881.113285] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 3881.113407] wlan0: associated
[ 3881.123123] ath: regdomain 0x8348 updated by CountryIE
[ 3881.123130] ath: EEPROM regdomain: 0x8348
[ 3881.123133] ath: EEPROM indicates we should expect a country code
[ 3881.123138] ath: doing EEPROM country->regdmn map search
[ 3881.123141] ath: country maps to regdmn code: 0x3a
[ 3881.123145] ath: Country alpha2 being used: US
[ 3881.123147] ath: Regpair used: 0x3a
[ 3901.775861] wlan0: authenticate with <MAC address removed>
[ 3901.784877] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3901.798913] wlan0: authenticated
[ 3901.802854] wlan0: associate with <MAC address removed> (try 1/3)
[ 3901.844391] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 3901.844512] wlan0: associated
[ 3901.853328] ath: regdomain 0x8348 updated by CountryIE
[ 3901.853337] ath: EEPROM regdomain: 0x8348
[ 3901.853339] ath: EEPROM indicates we should expect a country code
[ 3901.853344] ath: doing EEPROM country->regdmn map search
[ 3901.853347] ath: country maps to regdmn code: 0x3a
[ 3901.853351] ath: Country alpha2 being used: US
[ 3901.853354] ath: Regpair used: 0x3a
[ 3955.926961] wlan0: authenticate with <MAC address removed>
[ 3955.936322] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3956.138312] wlan0: send auth to <MAC address removed> (try 2/3)
[ 3956.342091] wlan0: send auth to <MAC address removed> (try 3/3)
[ 3956.545885] wlan0: authentication with <MAC address removed> timed out
[ 3963.655042] wlan0: authenticate with <MAC address removed>
[ 3963.663900] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3963.668145] wlan0: authenticated
[ 3963.669352] wlan0: associate with <MAC address removed> (try 1/3)
[ 3963.685380] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 3963.685573] wlan0: associated
[ 3963.696110] ath: regdomain 0x8348 updated by CountryIE
[ 3963.696118] ath: EEPROM regdomain: 0x8348
[ 3963.696121] ath: EEPROM indicates we should expect a country code
[ 3963.696125] ath: doing EEPROM country->regdmn map search
[ 3963.696129] ath: country maps to regdmn code: 0x3a
[ 3963.696132] ath: Country alpha2 being used: US
[ 3963.696135] ath: Regpair used: 0x3a
[ 3993.646524] wlan0: authenticate with <MAC address removed>
[ 3993.655505] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3993.857196] wlan0: send auth to <MAC address removed> (try 2/3)
[ 3993.863889] wlan0: authenticated
[ 3993.865243] wlan0: associate with <MAC address removed> (try 1/3)
[ 3994.068948] wlan0: associate with <MAC address removed> (try 2/3)
[ 3994.086372] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 3994.086495] wlan0: associated
[ 3994.095866] ath: regdomain 0x8348 updated by CountryIE
[ 3994.095874] ath: EEPROM regdomain: 0x8348
[ 3994.095877] ath: EEPROM indicates we should expect a country code
[ 3994.095881] ath: doing EEPROM country->regdmn map search
[ 3994.095885] ath: country maps to regdmn code: 0x3a
[ 3994.095888] ath: Country alpha2 being used: US
[ 3994.095891] ath: Regpair used: 0x3a
[ 4078.769321] wlan0: authenticate with <MAC address removed>
[ 4078.777577] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4078.780287] wlan0: authenticated
[ 4078.783554] wlan0: associate with <MAC address removed> (try 1/3)
[ 4078.815744] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 4078.815868] wlan0: associated
[ 4078.826713] ath: regdomain 0x8348 updated by CountryIE
[ 4078.826721] ath: EEPROM regdomain: 0x8348
[ 4078.826724] ath: EEPROM indicates we should expect a country code
[ 4078.826728] ath: doing EEPROM country->regdmn map search
[ 4078.826732] ath: country maps to regdmn code: 0x3a
[ 4078.826735] ath: Country alpha2 being used: US
[ 4078.826738] ath: Regpair used: 0x3a
[ 4084.729532] wlan0: authenticate with <MAC address removed>
[ 4084.738644] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4084.940201] wlan0: send auth to <MAC address removed> (try 2/3)
[ 4085.143949] wlan0: send auth to <MAC address removed> (try 3/3)
[ 4085.347713] wlan0: authentication with <MAC address removed> timed out
[ 4086.455916] wlan0: authenticate with <MAC address removed>
[ 4086.464482] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4086.666105] wlan0: send auth to <MAC address removed> (try 2/3)
[ 4086.691069] wlan0: authenticated
[ 4086.694093] wlan0: associate with <MAC address removed> (try 1/3)
[ 4086.897860] wlan0: associate with <MAC address removed> (try 2/3)
[ 4086.916173] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 4086.916296] wlan0: associated
[ 4086.925931] ath: regdomain 0x8348 updated by CountryIE
[ 4086.925939] ath: EEPROM regdomain: 0x8348
[ 4086.925942] ath: EEPROM indicates we should expect a country code
[ 4086.925947] ath: doing EEPROM country->regdmn map search
[ 4086.925950] ath: country maps to regdmn code: 0x3a
[ 4086.925954] ath: Country alpha2 being used: US
[ 4086.925957] ath: Regpair used: 0x3a
[ 4126.731217] wlan0: authenticate with <MAC address removed>
[ 4126.740380] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4126.941909] wlan0: send auth to <MAC address removed> (try 2/3)
[ 4126.949926] wlan0: authenticated
[ 4126.953908] wlan0: associate with <MAC address removed> (try 1/3)
[ 4127.157649] wlan0: associate with <MAC address removed> (try 2/3)
[ 4127.361410] wlan0: associate with <MAC address removed> (try 3/3)
[ 4127.565180] wlan0: association with <MAC address removed> timed out
[ 4128.673523] wlan0: authenticate with <MAC address removed>
[ 4128.682004] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4128.883687] wlan0: send auth to <MAC address removed> (try 2/3)
[ 4129.087349] wlan0: send auth to <MAC address removed> (try 3/3)
[ 4129.091381] wlan0: authenticated
[ 4129.095373] wlan0: associate with <MAC address removed> (try 1/3)
[ 4129.299123] wlan0: associate with <MAC address removed> (try 2/3)
[ 4129.502879] wlan0: associate with <MAC address removed> (try 3/3)
[ 4129.521696] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 4129.521820] wlan0: associated
[ 4129.531497] ath: regdomain 0x8348 updated by CountryIE
[ 4129.531500] ath: EEPROM regdomain: 0x8348
[ 4129.531501] ath: EEPROM indicates we should expect a country code
[ 4129.531503] ath: doing EEPROM country->regdmn map search
[ 4129.531504] ath: country maps to regdmn code: 0x3a
[ 4129.531505] ath: Country alpha2 being used: US
[ 4129.531506] ath: Regpair used: 0x3a
[ 4138.448484] wlan0: authenticate with <MAC address removed>
[ 4138.457839] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4138.659850] wlan0: send auth to <MAC address removed> (try 2/3)
[ 4138.863634] wlan0: send auth to <MAC address removed> (try 3/3)
[ 4139.067474] wlan0: authentication with <MAC address removed> timed out
[ 4146.172442] wlan0: authenticate with <MAC address removed>
[ 4146.181062] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4146.182977] wlan0: authenticated
[ 4146.186887] wlan0: associate with <MAC address removed> (try 1/3)
[ 4146.191799] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 4146.191918] wlan0: associated
[ 4146.200549] ath: regdomain 0x8348 updated by CountryIE
[ 4146.200558] ath: EEPROM regdomain: 0x8348
[ 4146.200561] ath: EEPROM indicates we should expect a country code
[ 4146.200565] ath: doing EEPROM country->regdmn map search
[ 4146.200569] ath: country maps to regdmn code: 0x3a
[ 4146.200572] ath: Country alpha2 being used: US
[ 4146.200575] ath: Regpair used: 0x3a
[ 4167.634340] wlan0: authenticate with <MAC address removed>
[ 4167.643419] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4167.844962] wlan0: send auth to <MAC address removed> (try 2/3)
[ 4167.847859] wlan0: authenticated
[ 4167.849031] wlan0: associate with <MAC address removed> (try 1/3)
[ 4167.929194] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 4167.929316] wlan0: associated
[ 4167.938746] ath: regdomain 0x8348 updated by CountryIE
[ 4167.938753] ath: EEPROM regdomain: 0x8348
[ 4167.938756] ath: EEPROM indicates we should expect a country code
[ 4167.938760] ath: doing EEPROM country->regdmn map search
[ 4167.938764] ath: country maps to regdmn code: 0x3a
[ 4167.938767] ath: Country alpha2 being used: US
[ 4167.938770] ath: Regpair used: 0x3a
[ 4190.634833] wlan0: authenticate with <MAC address removed>
[ 4190.643863] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4190.845456] wlan0: send auth to <MAC address removed> (try 2/3)
[ 4191.049219] wlan0: send auth to <MAC address removed> (try 3/3)
[ 4191.252976] wlan0: authentication with <MAC address removed> timed out
[ 4192.360204] wlan0: authenticate with <MAC address removed>
[ 4192.369763] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4192.374424] wlan0: authenticated
[ 4192.375602] wlan0: associate with <MAC address removed> (try 1/3)
[ 4192.579383] wlan0: associate with <MAC address removed> (try 2/3)
[ 4192.783166] wlan0: associate with <MAC address removed> (try 3/3)
[ 4192.798508] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 4192.798632] wlan0: associated
[ 4192.807515] ath: regdomain 0x8348 updated by CountryIE
[ 4192.807523] ath: EEPROM regdomain: 0x8348
[ 4192.807526] ath: EEPROM indicates we should expect a country code
[ 4192.807530] ath: doing EEPROM country->regdmn map search
[ 4192.807534] ath: country maps to regdmn code: 0x3a
[ 4192.807538] ath: Country alpha2 being used: US
[ 4192.807540] ath: Regpair used: 0x3a
[ 4196.603762] wlan0: authenticate with <MAC address removed>
[ 4196.612760] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4196.814294] wlan0: send auth to <MAC address removed> (try 2/3)
[ 4196.825588] wlan0: authenticated
[ 4196.826350] wlan0: associate with <MAC address removed> (try 1/3)
[ 4197.030077] wlan0: associate with <MAC address removed> (try 2/3)
[ 4197.233820] wlan0: associate with <MAC address removed> (try 3/3)
[ 4197.242382] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 4197.242507] wlan0: associated
[ 4197.252037] ath: regdomain 0x8348 updated by CountryIE
[ 4197.252045] ath: EEPROM regdomain: 0x8348
[ 4197.252048] ath: EEPROM indicates we should expect a country code
[ 4197.252052] ath: doing EEPROM country->regdmn map search
[ 4197.252056] ath: country maps to regdmn code: 0x3a
[ 4197.252060] ath: Country alpha2 being used: US
[ 4197.252062] ath: Regpair used: 0x3a
[ 4207.598410] wlan0: authenticate with <MAC address removed>
[ 4207.607469] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4207.809187] wlan0: send auth to <MAC address removed> (try 2/3)
[ 4207.817377] wlan0: authenticated
[ 4207.821198] wlan0: associate with <MAC address removed> (try 1/3)
[ 4208.024912] wlan0: associate with <MAC address removed> (try 2/3)
[ 4208.228666] wlan0: associate with <MAC address removed> (try 3/3)
[ 4208.238543] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 4208.238667] wlan0: associated
[ 4208.248497] ath: regdomain 0x8348 updated by CountryIE
[ 4208.248506] ath: EEPROM regdomain: 0x8348
[ 4208.248509] ath: EEPROM indicates we should expect a country code
[ 4208.248513] ath: doing EEPROM country->regdmn map search
[ 4208.248517] ath: country maps to regdmn code: 0x3a
[ 4208.248520] ath: Country alpha2 being used: US
[ 4208.248523] ath: Regpair used: 0x3a
[ 4209.242224] wlan0: deauthenticated from <MAC address removed> (Reason: 2)
[ 4215.652978] wlan0: authenticate with <MAC address removed>
[ 4215.662396] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4215.674306] wlan0: authenticated
[ 4215.675760] wlan0: associate with <MAC address removed> (try 1/3)
[ 4215.879477] wlan0: associate with <MAC address removed> (try 2/3)
[ 4215.890957] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 4215.891117] wlan0: associated
[ 4215.902147] ath: regdomain 0x8348 updated by CountryIE
[ 4215.902151] ath: EEPROM regdomain: 0x8348
[ 4215.902152] ath: EEPROM indicates we should expect a country code
[ 4215.902153] ath: doing EEPROM country->regdmn map search
[ 4215.902155] ath: country maps to regdmn code: 0x3a
[ 4215.902156] ath: Country alpha2 being used: US
[ 4215.902157] ath: Regpair used: 0x3a
[ 4236.145267] wlan0: authenticate with <MAC address removed>
[ 4236.153841] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4236.164407] wlan0: authenticated
[ 4236.167624] wlan0: associate with <MAC address removed> (try 1/3)
[ 4236.221455] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 4236.221576] wlan0: associated
[ 4236.231544] ath: regdomain 0x8348 updated by CountryIE
[ 4236.231554] ath: EEPROM regdomain: 0x8348
[ 4236.231559] ath: EEPROM indicates we should expect a country code
[ 4236.231566] ath: doing EEPROM country->regdmn map search
[ 4236.231572] ath: country maps to regdmn code: 0x3a
[ 4236.231576] ath: Country alpha2 being used: US
[ 4236.231581] ath: Regpair used: 0x3a
[ 4239.526281] wlan0: authenticate with <MAC address removed>
[ 4239.535590] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4239.540796] wlan0: authenticated
[ 4239.541901] wlan0: associate with <MAC address removed> (try 1/3)
[ 4239.745551] wlan0: associate with <MAC address removed> (try 2/3)
[ 4239.949206] wlan0: associate with <MAC address removed> (try 3/3)
[ 4240.152856] wlan0: association with <MAC address removed> timed out
[ 4241.384037] WARNING: at /build/buildd/linux-3.8.0/drivers/net/wireless/ath/ath9k/hw.c:794 ar9003_get_pll_sqsum_dvc+0xb6/0xc0 [ath9k_hw]()
[ 4241.384044] Modules linked in: parport_pc(F) ppdev(F) bnep rfcomm nls_iso8859_1(F) uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev coretemp kvm_intel kvm btusb hid_multitouch ghash_clmulni_intel(F) aesni_intel(F) aes_x86_64(F) arc4(F) bluetooth snd_hda_codec_hdmi ath9k xts(F) lrw(F) i915 snd_hda_codec_via ath9k_common snd_hda_intel gf128mul(F) joydev(F) snd_hda_codec ath9k_hw snd_hwdep(F) snd_pcm(F) drm_kms_helper ablk_helper(F) cryptd(F) ath drm snd_page_alloc(F) mac80211 snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) i2c_algo_bit snd_seq(F) cfg80211 snd_seq_device(F) alx mei snd_timer(F) asus_nb_wmi mdio asus_wmi psmouse(F) mac_hid snd(F) sparse_keymap microcode(F) soundcore(F) serio_raw(F) wmi lpc_ich video(F) lp(F) parport(F) hid_generic usbhid hid ahci(F) libahci(F)
[ 4241.384161]  [<ffffffff810587ef>] warn_slowpath_common+0x7f/0xc0
[ 4241.384168]  [<ffffffff8105884a>] warn_slowpath_null+0x1a/0x20
[ 4241.384184]  [<ffffffffa02ed9a6>] ar9003_get_pll_sqsum_dvc+0xb6/0xc0 [ath9k_hw]
[ 4241.384198]  [<ffffffffa04632e3>] ath_hw_pll_work+0x53/0xd0 [ath9k]
[ 4241.384261] ath: phy0: PLL4 meaurement not done
[ 4241.495814] ath: phy0: PLL4 meaurement not done
[ 4241.607624] ath: phy0: PLL4 meaurement not done
[ 4241.719460] ath: phy0: PLL4 meaurement not done
[ 4241.831204] ath: phy0: PLL4 meaurement not done
[ 4241.943060] ath: phy0: PLL4 meaurement not done
[ 4242.054764] ath: phy0: PLL4 meaurement not done
[ 4242.166682] ath: phy0: PLL4 meaurement not done
[ 4242.278486] ath: phy0: PLL4 meaurement not done
[ 4242.390299] ath: phy0: PLL4 meaurement not done
[ 4242.502054] ath: phy0: PLL4 meaurement not done
[ 4242.613923] ath: phy0: PLL4 meaurement not done
[ 4242.725668] ath: phy0: PLL4 meaurement not done
[ 4242.837537] ath: phy0: PLL4 meaurement not done
[ 4242.949345] ath: phy0: PLL4 meaurement not done
[ 4243.061160] ath: phy0: PLL4 meaurement not done
[ 4243.172967] ath: phy0: PLL4 meaurement not done
[ 4243.284780] ath: phy0: PLL4 meaurement not done
[ 4243.396514] ath: phy0: PLL4 meaurement not done
[ 4243.508397] ath: phy0: PLL4 meaurement not done
[ 4243.620215] ath: phy0: PLL4 meaurement not done
[ 4243.732021] ath: phy0: PLL4 meaurement not done
[ 4243.843829] ath: phy0: PLL4 meaurement not done
[ 4243.955568] ath: phy0: PLL4 meaurement not done
[ 4244.067462] ath: phy0: PLL4 meaurement not done
[ 4244.179262] ath: phy0: PLL4 meaurement not done
[ 4244.291073] ath: phy0: PLL4 meaurement not done
[ 4244.402836] ath: phy0: PLL4 meaurement not done
[ 4244.514693] ath: phy0: PLL4 meaurement not done
[ 4244.626502] ath: phy0: PLL4 meaurement not done
[ 4244.738311] ath: phy0: PLL4 meaurement not done
[ 4244.850117] ath: phy0: PLL4 meaurement not done
[ 4244.961937] ath: phy0: PLL4 meaurement not done
[ 4245.073606] ath: phy0: PLL4 meaurement not done
[ 4245.185591] ath: phy0: PLL4 meaurement not done
[ 4245.297370] ath: phy0: PLL4 meaurement not done
[ 4245.409103] ath: phy0: PLL4 meaurement not done
[ 4245.520925] ath: phy0: PLL4 meaurement not done
[ 4245.632794] ath: phy0: PLL4 meaurement not done
[ 4245.744603] ath: phy0: PLL4 meaurement not done
[ 4245.856412] ath: phy0: PLL4 meaurement not done
[ 4245.968135] ath: phy0: PLL4 meaurement not done
[ 4246.080037] ath: phy0: PLL4 meaurement not done
[ 4246.191851] ath: phy0: PLL4 meaurement not done
[ 4247.254312] wlan0: authenticate with <MAC address removed>
[ 4247.262968] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4247.464432] wlan0: send auth to <MAC address removed> (try 2/3)
[ 4247.668107] wlan0: send auth to <MAC address removed> (try 3/3)
[ 4247.871755] wlan0: authentication with <MAC address removed> timed out
[ 4250.906347] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4277.392367] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4279.447284] wlan0: authenticate with <MAC address removed>
[ 4279.456627] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4279.657810] wlan0: send auth to <MAC address removed> (try 2/3)
[ 4279.659823] wlan0: authenticated
[ 4279.661802] wlan0: associate with <MAC address removed> (try 1/3)
[ 4279.666993] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 4279.667152] wlan0: associated
[ 4279.667225] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4279.679219] ath: regdomain 0x8348 updated by CountryIE
[ 4279.679227] ath: EEPROM regdomain: 0x8348
[ 4279.679230] ath: EEPROM indicates we should expect a country code
[ 4279.679234] ath: doing EEPROM country->regdmn map search
[ 4279.679238] ath: country maps to regdmn code: 0x3a
[ 4279.679241] ath: Country alpha2 being used: US
[ 4279.679244] ath: Regpair used: 0x3a
[ 4300.466657] wlan0: authenticate with <MAC address removed>
[ 4300.475268] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4301.525746] wlan0: send auth to <MAC address removed> (try 2/3)
[ 4301.530954] wlan0: authenticated
[ 4301.532334] wlan0: associate with <MAC address removed> (try 1/3)
[ 4301.551461] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 4301.551537] wlan0: associated
[ 4301.560493] ath: regdomain 0x8348 updated by CountryIE
[ 4301.560502] ath: EEPROM regdomain: 0x8348
[ 4301.560505] ath: EEPROM indicates we should expect a country code
[ 4301.560509] ath: doing EEPROM country->regdmn map search
[ 4301.560513] ath: country maps to regdmn code: 0x3a
[ 4301.560517] ath: Country alpha2 being used: US
[ 4301.560519] ath: Regpair used: 0x3a
[ 4304.523787] wlan0: authenticate with <MAC address removed>
[ 4304.532429] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4304.534835] wlan0: authenticated
[ 4304.538328] wlan0: associate with <MAC address removed> (try 1/3)
[ 4304.543940] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 4304.544063] wlan0: associated
[ 4304.554077] ath: regdomain 0x8348 updated by CountryIE
[ 4304.554085] ath: EEPROM regdomain: 0x8348
[ 4304.554088] ath: EEPROM indicates we should expect a country code
[ 4304.554093] ath: doing EEPROM country->regdmn map search
[ 4304.554096] ath: country maps to regdmn code: 0x3a
[ 4304.554100] ath: Country alpha2 being used: US
[ 4304.554103] ath: Regpair used: 0x3a




**************** done ********************

</code>

---

