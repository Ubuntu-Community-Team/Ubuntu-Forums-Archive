---
title: "Lubuntu 12.10/Atheros ar9285 no authentication with DD-WRT router"
date: 2013-03-28
forum: Networking &amp; Wireless
---

### Post by BazBear on 2013-03-28
This one has me pulling my hair out. I have a Asus Eee PC 1005ha, which I have set up dual boot with Windows 7 and Lubuntu 12.10 (btw, I've tried all the flavors of Ubuntu, in both their 12.04 and 12.10 incarnations, all show the same problem) with an Atheros ar9285 wireless adapter. 

The Windows OS on this machine, and every other device in the household (2 other Win PCs, a MacBook, iPad, iPhone, and 2 Android phones) can connect to my Linksys e1200 router with dd-wrt, setup as a wireless repeater, but the Lubuntu OS will not log in, and keeps getting rejected with bad password errors (yes, it *is* the correct password). 

The Lubuntu OS will connect to my primary router (e2500 stock firmware) as well as 3 other routers I've tried it with. I've tried using WPA2, WPA, and WEP (yeah I know it's insecure, but it's better than nuttin'), and all show the same symptom. It will work unsecured, but for obvious reasons I won't go that route. 

I've tried about everything I could find here and elsewhere even remotely related to my problem, but nothing has worked, not even getting a set of XP drivers and Ndiswrapping them (that didn't work at *all,* it wouldn't connect to anything lol, I quickly went back to ath9k).

I've almost come to the conclusion I may have a unresolvable problem, but if anyone has any more crazy ideas, I'll try virtually anything.

TIA

---

### Post by BazBear on 2013-06-25
My wireless script results as requested by Varunendra.

This was the output while NM was trying to connect:
```


*************** info trace ****************






**** uname -a ****




Linux ubuntu 3.8.0-25-generic #37-Ubuntu SMP Thu Jun 6 20:47:30 UTC 2013 i686 i686 i686 GNU/Linux




**** lsb-release ****




DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"




**** lspci ****




01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8132 Fast Ethernet [1969:1062] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:838a]
	Kernel driver in use: atl1c
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
	Kernel driver in use: ath9k




**** lsusb ****




Bus 001 Device 002: ID 13d3:5108 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




**** iwconfig ****




wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          




**** rfkill ****




0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no




**** lsmod ****




Module                  Size  Used by
coretemp               13131  0 
joydev                 17097  0 
eeepc_wmi              12983  0 
asus_wmi               23517  1 eeepc_wmi
sparse_keymap          13658  1 asus_wmi
uvcvideo               71279  0 
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
videobuf2_core         39161  1 uvcvideo
videodev               95806  2 uvcvideo,videobuf2_core
microcode              18286  0 
parport_pc             27504  0 
lpc_ich                16925  0 
ppdev                  12817  0 
bluetooth             202069  6 
psmouse                81038  0 
serio_raw              13031  0 
arc4                   12543  2 
ath9k                 134875  0 
snd_hda_codec_realtek    63791  1 
ath9k_common           13783  1 ath9k
ath9k_hw              398520  2 ath9k_common,ath9k
i915                  535544  2 
snd_hda_intel          38307  3 
ath                    19187  3 ath9k_common,ath9k,ath9k_hw
snd_hda_codec         117580  2 snd_hda_codec_realtek,snd_hda_intel
drm_kms_helper         47545  1 i915
mac80211              526519  1 ath9k
video                  18894  2 i915,asus_wmi
cfg80211              436177  3 ath,ath9k,mac80211
snd_hwdep              13272  1 snd_hda_codec
drm                   228489  3 i915,drm_kms_helper
snd_pcm                80890  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
wmi                    18590  1 asus_wmi
snd_timer              24411  1 snd_pcm
snd                    56485  12 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_hda_codec,snd_hda_intel
binfmt_misc            17260  1 
soundcore              12600  1 snd
mac_hid                13037  0 
i2c_algo_bit           13197  1 i915
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
ahci                   25507  1 
libahci                26108  1 ahci
atl1c                  36175  0 




**** nm-tool ****






NetworkManager Tool


State: connecting


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on




- Device: wlan0  [dd-wrt_vap] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connecting (configuring)
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    Cisco80625:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2
    Oscar:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2
    dd-wrt_vap:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA2








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








**** resolv ****




# Generated by resolvconf
nameserver 192.168.3.1




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


# Blacklisting Bluetooth
blacklist bnep
blacklist rfcomm




**** dmesg ****




[    1.102772] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: e20f7ab6198de3fe93af1d459153b337d0197de2'
[   26.241973] wmi: Mapper loaded
[   27.073619] ath: phy0: Disabling ASPM since BTCOEX is enabled
[   27.073634] ath: EEPROM regdomain: 0x60
[   27.073640] ath: EEPROM indicates we should expect a direct regpair map
[   27.073649] ath: Country alpha2 being used: 00
[   27.073654] ath: Regpair used: 0x60
[   27.200142] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   28.716734] asus_wmi: ASUS WMI generic driver loaded
[   28.809310] asus_wmi: Initialization: 0x0asus_wmi: BIOS WMI version: 0.5
[   28.809662] asus_wmi: SFUN value: 0x0<6>[   28.845311] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   28.847198] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input9
[   29.873741] asus_wmi: Backlight controlled by ACPI video driver
[   32.305787] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  192.925938] wlan0: authenticate with <MAC address removed>
[  192.938006] wlan0: send auth to <MAC address removed> (try 1/3)
[  193.140062] wlan0: send auth to <MAC address removed> (try 2/3)
[  193.344085] wlan0: send auth to <MAC address removed> (try 3/3)
[  193.548054] wlan0: authentication with <MAC address removed> timed out
[  193.697908] wlan0: authenticate with <MAC address removed>
[  193.718018] wlan0: direct probe to <MAC address removed> (try 1/3)
[  193.920091] wlan0: direct probe to <MAC address removed> (try 2/3)
[  194.124106] wlan0: direct probe to <MAC address removed> (try 3/3)
[  194.328078] wlan0: authentication with <MAC address removed> timed out
[ 2639.778738] wlan0: authenticate with <MAC address removed>
[ 2639.790206] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2639.992155] wlan0: send auth to <MAC address removed> (try 2/3)
[ 2640.196113] wlan0: send auth to <MAC address removed> (try 3/3)
[ 2640.400103] wlan0: authentication with <MAC address removed> timed out
[ 2640.551110] wlan0: authenticate with <MAC address removed>
[ 2640.571271] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2640.772126] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2640.976098] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2641.180072] wlan0: authentication with <MAC address removed> timed out




**************** done ********************





```

And this is immediately after failure:
```


*************** info trace ****************






**** uname -a ****




Linux ubuntu 3.8.0-25-generic #37-Ubuntu SMP Thu Jun 6 20:47:30 UTC 2013 i686 i686 i686 GNU/Linux




**** lsb-release ****




DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"




**** lspci ****




01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8132 Fast Ethernet [1969:1062] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:838a]
	Kernel driver in use: atl1c
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
	Kernel driver in use: ath9k




**** lsusb ****




Bus 001 Device 002: ID 13d3:5108 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




**** iwconfig ****




wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          




**** rfkill ****




0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no




**** lsmod ****




Module                  Size  Used by
coretemp               13131  0 
joydev                 17097  0 
eeepc_wmi              12983  0 
asus_wmi               23517  1 eeepc_wmi
sparse_keymap          13658  1 asus_wmi
uvcvideo               71279  0 
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
videobuf2_core         39161  1 uvcvideo
videodev               95806  2 uvcvideo,videobuf2_core
microcode              18286  0 
parport_pc             27504  0 
lpc_ich                16925  0 
ppdev                  12817  0 
bluetooth             202069  6 
psmouse                81038  0 
serio_raw              13031  0 
arc4                   12543  2 
ath9k                 134875  0 
snd_hda_codec_realtek    63791  1 
ath9k_common           13783  1 ath9k
ath9k_hw              398520  2 ath9k_common,ath9k
i915                  535544  2 
snd_hda_intel          38307  3 
ath                    19187  3 ath9k_common,ath9k,ath9k_hw
snd_hda_codec         117580  2 snd_hda_codec_realtek,snd_hda_intel
drm_kms_helper         47545  1 i915
mac80211              526519  1 ath9k
video                  18894  2 i915,asus_wmi
cfg80211              436177  3 ath,ath9k,mac80211
snd_hwdep              13272  1 snd_hda_codec
drm                   228489  3 i915,drm_kms_helper
snd_pcm                80890  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
wmi                    18590  1 asus_wmi
snd_timer              24411  1 snd_pcm
snd                    56485  12 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_hda_codec,snd_hda_intel
binfmt_misc            17260  1 
soundcore              12600  1 snd
mac_hid                13037  0 
i2c_algo_bit           13197  1 i915
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
ahci                   25507  1 
libahci                26108  1 ahci
atl1c                  36175  0 




**** nm-tool ****






NetworkManager Tool


State: disconnected


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on




- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    Cisco80625:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WPA2
    Oscar:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2
    dd-wrt_vap:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA2








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
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Oscar"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000013b97513e1
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 00054F73636172
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: DD6F0050F204104A00011010440001021041000100103B00010310470010F1CFE440EF21811C171DB97C8A53C5EF102100074C696E6B737973102300075752543136304E102400063132333435361042000234321054000800060050F2040001101100075752543136304E100800020084
                    IE: Unknown: DD090010180205F4050000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B080400000000000000000000000000000000000000
          Cell 02 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"dd-wrt_vap"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000db4e00a7
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 000A64642D7772745F766170
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: DD09001018020511280000
          Cell 03 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"dd-wrt_vap"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000db5021d3
                    Extra: Last beacon: 316ms ago
                    IE: Unknown: 000A64642D7772745F766170
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: DD09001018020511280000
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Cisco80625"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000091aeacf93
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 000A436973636F3830363235
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFE181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16010D1600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B000103104700106BFE385A70D1DE6B39765DD7B7CF165910210005436973636F1023000D4C696E6B7379732045323530301024000776312E302E30351042000234321054000800060050F20400011011000D4C696E6B737973204532353030100800020084103C000103
                    IE: Unknown: DD090010180202F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00






**** resolv ****




# Generated by resolvconf
nameserver 192.168.3.1




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


# Blacklisting Bluetooth
blacklist bnep
blacklist rfcomm




**** dmesg ****




[    1.102772] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: e20f7ab6198de3fe93af1d459153b337d0197de2'
[   26.241973] wmi: Mapper loaded
[   27.073619] ath: phy0: Disabling ASPM since BTCOEX is enabled
[   27.073634] ath: EEPROM regdomain: 0x60
[   27.073640] ath: EEPROM indicates we should expect a direct regpair map
[   27.073649] ath: Country alpha2 being used: 00
[   27.073654] ath: Regpair used: 0x60
[   27.200142] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   28.716734] asus_wmi: ASUS WMI generic driver loaded
[   28.809310] asus_wmi: Initialization: 0x0asus_wmi: BIOS WMI version: 0.5
[   28.809662] asus_wmi: SFUN value: 0x0<6>[   28.845311] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   28.847198] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input9
[   29.873741] asus_wmi: Backlight controlled by ACPI video driver
[   32.305787] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  192.925938] wlan0: authenticate with <MAC address removed>
[  192.938006] wlan0: send auth to <MAC address removed> (try 1/3)
[  193.140062] wlan0: send auth to <MAC address removed> (try 2/3)
[  193.344085] wlan0: send auth to <MAC address removed> (try 3/3)
[  193.548054] wlan0: authentication with <MAC address removed> timed out
[  193.697908] wlan0: authenticate with <MAC address removed>
[  193.718018] wlan0: direct probe to <MAC address removed> (try 1/3)
[  193.920091] wlan0: direct probe to <MAC address removed> (try 2/3)
[  194.124106] wlan0: direct probe to <MAC address removed> (try 3/3)
[  194.328078] wlan0: authentication with <MAC address removed> timed out
[ 2639.778738] wlan0: authenticate with <MAC address removed>
[ 2639.790206] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2639.992155] wlan0: send auth to <MAC address removed> (try 2/3)
[ 2640.196113] wlan0: send auth to <MAC address removed> (try 3/3)
[ 2640.400103] wlan0: authentication with <MAC address removed> timed out
[ 2640.551110] wlan0: authenticate with <MAC address removed>
[ 2640.571271] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2640.772126] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2640.976098] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2641.180072] wlan0: authentication with <MAC address removed> timed out




**************** done ********************





```

I can connect to non-dd-wrt routers on the list, and I can hardwire to the dd-wrt router.

---

### Post by varunendra on 2013-06-25
You mentioned that you have already tried everything found on this forum. Have you also tried the "nohwcrypt=1" parameter for ath9k?

If not, please try that -
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

If this doesn't help, please also post -
```
cat /var/log/syslog | egrep -i 'ath|network|wlan'
```
..on a fresh boot after failing to connect. Fresh boot will ensure that the output is rather small, else it may be too long to post here.

As a side note, it seems you are running the older version of "wireless_script". Try the newer one, it is cleaner (not that it will catch anymore info..) ;)
Also, why have you blacklisted the bluetooth drivers? Any specific reasons?

---

### Post by BazBear on 2013-06-25
> **varunendra said:**
> You mentioned that you have already tried everything found on this forum. Have you also tried the "nohwcrypt=1" parameter for ath9k?

If not, please try that -
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```I had tried this before, but I did just try it again. It didn't help.

> If this doesn't help, please also post -
```
cat /var/log/syslog | egrep -i 'ath|network|wlan'
```
..on a fresh boot after failing to connect. Fresh boot will ensure that the output is rather small, else it may be too long to post here.Here's the output: ```
bazbear@ubuntu:~$ cat /var/log/syslog | egrep -i 'ath|network|wlan'Jun 25 00:49:21 ubuntu NetworkManager[867]: <info> (eth0): device state change: activated -> disconnected (reason 'user-requested') [100 30 39]
Jun 25 00:49:21 ubuntu NetworkManager[867]: <info> (eth0): deactivating device (reason 'user-requested') [39]
Jun 25 00:49:21 ubuntu NetworkManager[867]: <info> (eth0): canceled DHCP transaction, DHCP client pid 980
Jun 25 00:49:21 ubuntu NetworkManager[867]: <warn> DNS: plugin dnsmasq update failed
Jun 25 00:49:21 ubuntu NetworkManager[867]: <info> Removing DNS information from /sbin/resolvconf
Jun 25 00:49:57 ubuntu NetworkManager[867]: <info> Activation (wlan0) starting connection 'dd-wrt_vap'
Jun 25 00:49:57 ubuntu NetworkManager[867]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 25 00:49:57 ubuntu NetworkManager[867]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 25 00:49:57 ubuntu NetworkManager[867]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 25 00:49:57 ubuntu NetworkManager[867]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 25 00:49:57 ubuntu NetworkManager[867]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 25 00:49:57 ubuntu NetworkManager[867]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 25 00:49:57 ubuntu NetworkManager[867]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 25 00:49:57 ubuntu NetworkManager[867]: <info> Activation (wlan0/wireless): access point 'dd-wrt_vap' has security, but secrets are required.
Jun 25 00:49:57 ubuntu NetworkManager[867]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jun 25 00:49:57 ubuntu NetworkManager[867]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 25 00:49:57 ubuntu NetworkManager[867]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 25 00:49:57 ubuntu NetworkManager[867]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 25 00:49:57 ubuntu NetworkManager[867]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jun 25 00:49:57 ubuntu NetworkManager[867]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 25 00:49:57 ubuntu NetworkManager[867]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 25 00:49:57 ubuntu NetworkManager[867]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 25 00:49:57 ubuntu NetworkManager[867]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 25 00:49:57 ubuntu NetworkManager[867]: <info> Activation (wlan0/wireless): connection 'dd-wrt_vap' has security, and secrets exist.  No new secrets needed.
Jun 25 00:49:57 ubuntu NetworkManager[867]: <info> Config: added 'ssid' value 'dd-wrt_vap'
Jun 25 00:49:57 ubuntu NetworkManager[867]: <info> Config: added 'scan_ssid' value '1'
Jun 25 00:49:57 ubuntu NetworkManager[867]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jun 25 00:49:57 ubuntu NetworkManager[867]: <info> Config: added 'psk' value '<omitted>'
Jun 25 00:49:57 ubuntu NetworkManager[867]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 25 00:49:57 ubuntu NetworkManager[867]: <info> Config: set interface ap_scan to 1
Jun 25 00:49:57 ubuntu NetworkManager[867]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun 25 00:49:58 ubuntu wpa_supplicant[951]: wlan0: SME: Trying to authenticate with 00:00:00:00:00:00 (SSID='dd-wrt_vap' freq=2462 MHz)
Jun 25 00:49:58 ubuntu kernel: [ 2639.778738] wlan0: authenticate with 00:00:00:00:00:00
Jun 25 00:49:58 ubuntu kernel: [ 2639.790206] wlan0: send auth to 00:00:00:00:00:00 (try 1/3)
Jun 25 00:49:58 ubuntu NetworkManager[867]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jun 25 00:49:58 ubuntu kernel: [ 2639.992155] wlan0: send auth to 00:00:00:00:00:00 (try 2/3)
Jun 25 00:49:58 ubuntu kernel: [ 2640.196113] wlan0: send auth to 00:00:00:00:00:00 (try 3/3)
Jun 25 00:49:59 ubuntu kernel: [ 2640.400103] wlan0: authentication with 00:00:00:00:00:00 timed out
Jun 25 00:49:59 ubuntu NetworkManager[867]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jun 25 00:49:59 ubuntu NetworkManager[867]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun 25 00:49:59 ubuntu wpa_supplicant[951]: wlan0: SME: Trying to authenticate with 22:aa:4b:0f:3c:d9 (SSID='dd-wrt_vap' freq=2462 MHz)
Jun 25 00:49:59 ubuntu kernel: [ 2640.551110] wlan0: authenticate with 22:aa:4b:0f:3c:d9
Jun 25 00:49:59 ubuntu kernel: [ 2640.571271] wlan0: direct probe to 22:aa:4b:0f:3c:d9 (try 1/3)
Jun 25 00:49:59 ubuntu NetworkManager[867]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jun 25 00:49:59 ubuntu kernel: [ 2640.772126] wlan0: direct probe to 22:aa:4b:0f:3c:d9 (try 2/3)
Jun 25 00:49:59 ubuntu kernel: [ 2640.976098] wlan0: direct probe to 22:aa:4b:0f:3c:d9 (try 3/3)
Jun 25 00:49:59 ubuntu kernel: [ 2641.180072] wlan0: authentication with 22:aa:4b:0f:3c:d9 timed out
Jun 25 00:49:59 ubuntu NetworkManager[867]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jun 25 00:50:00 ubuntu NetworkManager[867]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun 25 00:50:22 ubuntu NetworkManager[867]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Jun 25 00:50:22 ubuntu NetworkManager[867]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
Jun 25 00:50:22 ubuntu NetworkManager[867]: <warn> Activation (wlan0) failed for connection 'dd-wrt_vap'
Jun 25 00:50:22 ubuntu NetworkManager[867]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jun 25 00:50:22 ubuntu NetworkManager[867]: <info> (wlan0): deactivating device (reason 'none') [0]
Jun 25 00:50:22 ubuntu NetworkManager[867]: <info> (wlan0): supplicant interface state: scanning -> disconnected
Jun 25 00:50:22 ubuntu NetworkManager[867]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jun 25 00:53:49 ubuntu NetworkManager[867]: <info> Activation (eth0) starting connection 'Wired connection 1'
Jun 25 00:53:49 ubuntu NetworkManager[867]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 25 00:53:49 ubuntu NetworkManager[867]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 25 00:53:49 ubuntu NetworkManager[867]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jun 25 00:53:49 ubuntu NetworkManager[867]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jun 25 00:53:49 ubuntu NetworkManager[867]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jun 25 00:53:49 ubuntu NetworkManager[867]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jun 25 00:53:49 ubuntu NetworkManager[867]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 25 00:53:49 ubuntu NetworkManager[867]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jun 25 00:53:49 ubuntu NetworkManager[867]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 25 00:53:49 ubuntu NetworkManager[867]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jun 25 00:53:49 ubuntu NetworkManager[867]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jun 25 00:53:49 ubuntu NetworkManager[867]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun 25 00:53:49 ubuntu NetworkManager[867]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun 25 00:53:49 ubuntu NetworkManager[867]: <info> dhclient started with pid 3659
Jun 25 00:53:49 ubuntu NetworkManager[867]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jun 25 00:53:49 ubuntu NetworkManager[867]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jun 25 00:53:49 ubuntu NetworkManager[867]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Jun 25 00:53:49 ubuntu NetworkManager[867]: <info>   address 192.168.3.102
Jun 25 00:53:49 ubuntu NetworkManager[867]: <info>   prefix 24 (255.255.255.0)
Jun 25 00:53:49 ubuntu NetworkManager[867]: <info>   gateway 192.168.3.1
Jun 25 00:53:49 ubuntu NetworkManager[867]: <info>   hostname 'ubuntu'
Jun 25 00:53:49 ubuntu NetworkManager[867]: <info>   nameserver '192.168.3.1'
Jun 25 00:53:49 ubuntu NetworkManager[867]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun 25 00:53:49 ubuntu NetworkManager[867]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Jun 25 00:53:50 ubuntu NetworkManager[867]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jun 25 00:53:50 ubuntu NetworkManager[867]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Jun 25 00:53:50 ubuntu NetworkManager[867]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jun 25 00:53:50 ubuntu NetworkManager[867]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jun 25 00:53:50 ubuntu NetworkManager[867]: <info> Writing DNS information to /sbin/resolvconf
Jun 25 00:53:50 ubuntu NetworkManager[867]: <info> Activation (eth0) successful, device activated.
Jun 25 02:52:18 ubuntu dhcpcd[1288]: wlan0: removing interface
Jun 25 02:52:18 ubuntu avahi-daemon[643]: Withdrawing workstation service for wlan0.
Jun 25 02:52:18 ubuntu NetworkManager[867]: <info> (wlan0): device state change: disconnected -> unmanaged (reason 'removed') [30 10 36]
Jun 25 02:52:18 ubuntu NetworkManager[867]: <info> (wlan0): cleaning up...
Jun 25 02:52:18 ubuntu NetworkManager[867]: <warn> (3) failed to find interface name for index
Jun 25 02:52:18 ubuntu NetworkManager[867]: (nm-system.c:766):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Jun 25 02:52:18 ubuntu NetworkManager[867]: <error> [1372143138.917720] [nm-system.c:768] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Jun 25 02:52:18 ubuntu NetworkManager[867]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun 25 02:52:18 ubuntu NetworkManager[867]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/wlan0/accept_ra': (2) No such file or directory
Jun 25 02:52:18 ubuntu NetworkManager[867]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/wlan0/use_tempaddr': (2) No such file or directory
Jun 25 02:52:18 ubuntu NetworkManager[867]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0)
Jun 25 02:52:18 ubuntu NetworkManager[867]: <info> radio killswitch /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/ieee80211/phy0/rfkill0 disappeared
Jun 25 02:52:18 ubuntu kernel: [ 9980.221206] ath9k: ath9k: Driver unloaded
Jun 25 02:52:19 ubuntu wpa_supplicant[951]: Could not read interface wlan0 flags: No such device
Jun 25 02:52:38 ubuntu kernel: [ 9999.611044] ath: EEPROM regdomain: 0x60
Jun 25 02:52:38 ubuntu kernel: [ 9999.611051] ath: EEPROM indicates we should expect a direct regpair map
Jun 25 02:52:38 ubuntu kernel: [ 9999.611059] ath: Country alpha2 being used: 00
Jun 25 02:52:38 ubuntu kernel: [ 9999.611063] ath: Regpair used: 0x60
Jun 25 02:52:38 ubuntu kernel: [ 9999.616854] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
Jun 25 02:52:38 ubuntu kernel: [ 9999.629104] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xf8740000, irq=17
Jun 25 02:52:38 ubuntu kernel: [ 9999.652292] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 25 02:52:38 ubuntu NetworkManager[867]: <info> rfkill2: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/ieee80211/phy0/rfkill2) (driver ath9k)
Jun 25 02:52:38 ubuntu NetworkManager[867]: <info> (wlan0): using nl80211 for WiFi device control
Jun 25 02:52:38 ubuntu NetworkManager[867]: <info> (wlan0): driver supports Access Point (AP) mode
Jun 25 02:52:38 ubuntu NetworkManager[867]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath9k' ifindex: 4)
Jun 25 02:52:38 ubuntu NetworkManager[867]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/2
Jun 25 02:52:38 ubuntu NetworkManager[867]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 25 02:52:38 ubuntu NetworkManager[867]: <info> (wlan0): preparing device.
Jun 25 02:52:38 ubuntu NetworkManager[867]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun 25 02:52:38 ubuntu NetworkManager[867]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0)
Jun 25 02:52:38 ubuntu NetworkManager[867]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun 25 02:52:38 ubuntu NetworkManager[867]: <info> (wlan0) supports 4 scan SSIDs
Jun 25 02:52:38 ubuntu NetworkManager[867]: <warn> Trying to remove a non-existant call id.
Jun 25 02:52:38 ubuntu NetworkManager[867]: <info> (wlan0): supplicant interface state: starting -> ready
Jun 25 02:52:38 ubuntu NetworkManager[867]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun 25 02:52:38 ubuntu NetworkManager[867]: <info> (wlan0): supplicant interface state: ready -> inactive
Jun 25 02:52:38 ubuntu NetworkManager[867]: <info> (wlan0) supports 4 scan SSIDs
Jun 25 02:52:38 ubuntu dhcpcd[1288]: wlan0: waiting for carrier
Jun 25 02:52:38 ubuntu dhcpcd[1288]: wlan0: carrier acquired
Jun 25 02:52:38 ubuntu dhcpcd[1288]: wlan0: carrier lost
Jun 25 02:52:38 ubuntu dhcpcd[1288]: wlan0: waiting for carrier
Jun 25 02:53:08 ubuntu NetworkManager[867]: <info> (eth0): device state change: activated -> disconnected (reason 'user-requested') [100 30 39]
Jun 25 02:53:08 ubuntu NetworkManager[867]: <info> (eth0): deactivating device (reason 'user-requested') [39]
Jun 25 02:53:09 ubuntu NetworkManager[867]: <info> (eth0): canceled DHCP transaction, DHCP client pid 3659
Jun 25 02:53:09 ubuntu NetworkManager[867]: <warn> DNS: plugin dnsmasq update failed
Jun 25 02:53:09 ubuntu NetworkManager[867]: <info> Removing DNS information from /sbin/resolvconf
Jun 25 02:53:14 ubuntu NetworkManager[867]: <info> Activation (wlan0) starting connection 'dd-wrt_vap'
Jun 25 02:53:14 ubuntu NetworkManager[867]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 25 02:53:14 ubuntu NetworkManager[867]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 25 02:53:14 ubuntu NetworkManager[867]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 25 02:53:14 ubuntu NetworkManager[867]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 25 02:53:14 ubuntu NetworkManager[867]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 25 02:53:14 ubuntu NetworkManager[867]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 25 02:53:14 ubuntu NetworkManager[867]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 25 02:53:14 ubuntu NetworkManager[867]: <info> Activation (wlan0/wireless): access point 'dd-wrt_vap' has security, but secrets are required.
Jun 25 02:53:14 ubuntu NetworkManager[867]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jun 25 02:53:14 ubuntu NetworkManager[867]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 25 02:53:14 ubuntu NetworkManager[867]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 25 02:53:14 ubuntu NetworkManager[867]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 25 02:53:14 ubuntu NetworkManager[867]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jun 25 02:53:14 ubuntu NetworkManager[867]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 25 02:53:14 ubuntu NetworkManager[867]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 25 02:53:14 ubuntu NetworkManager[867]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 25 02:53:14 ubuntu NetworkManager[867]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 25 02:53:14 ubuntu NetworkManager[867]: <info> Activation (wlan0/wireless): connection 'dd-wrt_vap' has security, and secrets exist.  No new secrets needed.
Jun 25 02:53:14 ubuntu NetworkManager[867]: <info> Config: added 'ssid' value 'dd-wrt_vap'
Jun 25 02:53:14 ubuntu NetworkManager[867]: <info> Config: added 'scan_ssid' value '1'
Jun 25 02:53:14 ubuntu NetworkManager[867]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jun 25 02:53:14 ubuntu NetworkManager[867]: <info> Config: added 'psk' value '<omitted>'
Jun 25 02:53:14 ubuntu NetworkManager[867]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 25 02:53:14 ubuntu NetworkManager[867]: <info> Config: set interface ap_scan to 1
Jun 25 02:53:14 ubuntu NetworkManager[867]: <info> (wlan0): supplicant interface state: inactive -> scanning
Jun 25 02:53:15 ubuntu wpa_supplicant[951]: wlan0: SME: Trying to authenticate with 22:aa:4b:0f:3c:d9 (SSID='dd-wrt_vap' freq=2462 MHz)
Jun 25 02:53:15 ubuntu kernel: [10036.422648] wlan0: authenticate with 22:aa:4b:0f:3c:d9
Jun 25 02:53:15 ubuntu kernel: [10036.434702] wlan0: direct probe to 22:aa:4b:0f:3c:d9 (try 1/3)
Jun 25 02:53:15 ubuntu NetworkManager[867]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jun 25 02:53:15 ubuntu kernel: [10036.636111] wlan0: direct probe to 22:aa:4b:0f:3c:d9 (try 2/3)
Jun 25 02:53:15 ubuntu kernel: [10036.840103] wlan0: direct probe to 22:aa:4b:0f:3c:d9 (try 3/3)
Jun 25 02:53:15 ubuntu kernel: [10037.044093] wlan0: authentication with 22:aa:4b:0f:3c:d9 timed out
Jun 25 02:53:15 ubuntu NetworkManager[867]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jun 25 02:53:15 ubuntu NetworkManager[867]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun 25 02:53:39 ubuntu NetworkManager[867]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Jun 25 02:53:39 ubuntu NetworkManager[867]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
Jun 25 02:53:39 ubuntu NetworkManager[867]: <warn> Activation (wlan0) failed for connection 'dd-wrt_vap'
Jun 25 02:53:39 ubuntu NetworkManager[867]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jun 25 02:53:39 ubuntu NetworkManager[867]: <info> (wlan0): deactivating device (reason 'none') [0]
Jun 25 02:53:39 ubuntu NetworkManager[867]: <info> (wlan0): supplicant interface state: scanning -> disconnected
Jun 25 02:53:39 ubuntu NetworkManager[867]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jun 25 02:54:42 ubuntu kernel: [    1.098958] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: e20f7ab6198de3fe93af1d459153b337d0197de2'
Jun 25 02:54:42 ubuntu kernel: [   25.829572] type=1400 audit(1372143282.201:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=656 comm="apparmor_parser"
Jun 25 02:54:42 ubuntu kernel: [   25.913685] ath: phy0: ASPM enabled: 0x42
Jun 25 02:54:42 ubuntu kernel: [   25.913699] ath: EEPROM regdomain: 0x60
Jun 25 02:54:42 ubuntu kernel: [   25.913705] ath: EEPROM indicates we should expect a direct regpair map
Jun 25 02:54:42 ubuntu kernel: [   25.913714] ath: Country alpha2 being used: 00
Jun 25 02:54:42 ubuntu kernel: [   25.913720] ath: Regpair used: 0x60
Jun 25 02:54:42 ubuntu kernel: [   26.034480] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
Jun 25 02:54:42 ubuntu kernel: [   26.035464] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xf8680000, irq=17
Jun 25 02:54:42 ubuntu bluetoothd[658]: Failed to init network plugin
Jun 25 02:54:42 ubuntu avahi-daemon[675]: Network interface enumeration completed.
Jun 25 02:54:45 ubuntu NetworkManager[835]: <info> NetworkManager (version 0.9.8.0) is starting...
Jun 25 02:54:45 ubuntu NetworkManager[835]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Jun 25 02:54:45 ubuntu NetworkManager[835]: <info> WEXT support is enabled
Jun 25 02:54:45 ubuntu NetworkManager[835]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jun 25 02:54:45 ubuntu NetworkManager[835]: <info> DNS: loaded plugin dnsmasq
Jun 25 02:54:45 ubuntu NetworkManager[835]:    SCPlugin-Ifupdown: init!
Jun 25 02:54:45 ubuntu NetworkManager[835]:    SCPlugin-Ifupdown: update_system_hostname
Jun 25 02:54:45 ubuntu NetworkManager[835]:    SCPluginIfupdown: management mode: unmanaged
Jun 25 02:54:45 ubuntu NetworkManager[835]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0)
Jun 25 02:54:45 ubuntu NetworkManager[835]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun 25 02:54:45 ubuntu NetworkManager[835]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:01:00.0/net/eth0, iface: eth0)
Jun 25 02:54:45 ubuntu NetworkManager[835]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:01:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jun 25 02:54:45 ubuntu NetworkManager[835]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun 25 02:54:45 ubuntu NetworkManager[835]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun 25 02:54:45 ubuntu NetworkManager[835]:    SCPlugin-Ifupdown: end _init.
Jun 25 02:54:45 ubuntu NetworkManager[835]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun 25 02:54:45 ubuntu NetworkManager[835]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun 25 02:54:45 ubuntu NetworkManager[835]:    Ifupdown: get unmanaged devices count: 0
Jun 25 02:54:45 ubuntu NetworkManager[835]:    SCPlugin-Ifupdown: (160617296) ... get_connections.
Jun 25 02:54:45 ubuntu NetworkManager[835]:    SCPlugin-Ifupdown: (160617296) ... get_connections (managed=false): return empty list.
Jun 25 02:54:45 ubuntu NetworkManager[835]:    keyfile: parsing Oscar ... 
Jun 25 02:54:45 ubuntu NetworkManager[835]:    keyfile:     read connection 'Oscar'
Jun 25 02:54:45 ubuntu NetworkManager[835]:    keyfile: parsing dd-wrt_vap ... 
Jun 25 02:54:45 ubuntu NetworkManager[835]: Connection failed to verify: (unknown)
Jun 25 02:54:45 ubuntu NetworkManager[835]:    keyfile:     error: invalid or missing connection property 'NMSettingWirelessSecurity/key-mgmt'
Jun 25 02:54:45 ubuntu NetworkManager[835]:    keyfile: parsing dd-wrt_vap-8526d858-0d3b-4758-96c8-3671f155642f ... 
Jun 25 02:54:46 ubuntu NetworkManager[835]:    keyfile:     read connection 'dd-wrt_vap'
Jun 25 02:54:46 ubuntu NetworkManager[835]:    keyfile: parsing Cisco80625 ... 
Jun 25 02:54:46 ubuntu NetworkManager[835]:    keyfile:     read connection 'Cisco80625'
Jun 25 02:54:46 ubuntu NetworkManager[835]:    keyfile: parsing Wired connection 1 ... 
Jun 25 02:54:46 ubuntu NetworkManager[835]:    keyfile:     read connection 'Wired connection 1'
Jun 25 02:54:46 ubuntu NetworkManager[835]:    Ifupdown: get unmanaged devices count: 0
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> modem-manager is now available
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/ieee80211/phy0/rfkill0) (driver ath9k)
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> rfkill1: found WiFi radio killswitch (at /sys/devices/platform/eeepc-wmi/rfkill/rfkill1) (platform driver eeepc-wmi)
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> WiFi hardware radio set enabled
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> WiFi enabled by radio killswitch; enabled by state file
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> WWAN enabled by radio killswitch; enabled by state file
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> Networking is enabled by state file
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> (wlan0): using nl80211 for WiFi device control
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> (wlan0): driver supports Access Point (AP) mode
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath9k' ifindex: 3)
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> (wlan0): bringing up device.
Jun 25 02:54:46 ubuntu kernel: [   30.000552] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> (wlan0): preparing device.
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun 25 02:54:46 ubuntu NetworkManager[835]: <warn> failed to allocate link cache: (-10) Operation not supported
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> (eth0): carrier is OFF
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> (eth0): new Ethernet device (driver: 'atl1c' ifindex: 2)
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> (eth0): bringing up device.
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> (eth0): carrier now ON (device state 20)
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> (eth0): preparing device.
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> (eth0): deactivating device (reason 'managed') [2]
Jun 25 02:54:46 ubuntu NetworkManager[835]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jun 25 02:54:46 ubuntu NetworkManager[835]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> wpa_supplicant started
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> (eth0): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> Auto-activating connection 'Wired connection 1'.
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> Activation (eth0) starting connection 'Wired connection 1'
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun 25 02:54:46 ubuntu kernel: [   30.133687] type=1400 audit(1372143286.505:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=949 comm="apparmor_parser"
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> dhclient started with pid 950
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> (wlan0) supports 4 scan SSIDs
Jun 25 02:54:46 ubuntu NetworkManager[835]: <warn> Trying to remove a non-existant call id.
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> (wlan0): supplicant interface state: starting -> ready
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> (wlan0): supplicant interface state: ready -> inactive
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> (wlan0) supports 4 scan SSIDs
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info>   address 192.168.3.102
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info>   prefix 24 (255.255.255.0)
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info>   gateway 192.168.3.1
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info>   hostname 'ubuntu'
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info>   nameserver '192.168.3.1'
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun 25 02:54:46 ubuntu NetworkManager[835]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Jun 25 02:54:47 ubuntu NetworkManager[835]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jun 25 02:54:47 ubuntu NetworkManager[835]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Jun 25 02:54:47 ubuntu dhcpcd[1015]: eth0: sendmsg: Network is unreachable
Jun 25 02:54:47 ubuntu dhcpcd[1015]: wlan0: waiting for carrier
Jun 25 02:54:47 ubuntu NetworkManager[835]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jun 25 02:54:47 ubuntu NetworkManager[835]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jun 25 02:54:47 ubuntu NetworkManager[835]: <info> DNS: starting dnsmasq...
Jun 25 02:54:47 ubuntu NetworkManager[835]: <warn> dnsmasq not available on the bus, can't update servers.
Jun 25 02:54:47 ubuntu NetworkManager[835]: <error> [1372143287.865655] [nm-dns-dnsmasq.c:402] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Jun 25 02:54:47 ubuntu NetworkManager[835]: <warn> DNS: plugin dnsmasq update failed
Jun 25 02:54:47 ubuntu NetworkManager[835]: <info> Writing DNS information to /sbin/resolvconf
Jun 25 02:54:47 ubuntu NetworkManager[835]: <info> Activation (eth0) successful, device activated.
Jun 25 02:54:48 ubuntu NetworkManager[835]: <warn> dnsmasq appeared on DBus: :1.15
Jun 25 02:54:48 ubuntu NetworkManager[835]: <info> Writing DNS information to /sbin/resolvconf
Jun 25 02:54:51 ubuntu dhcpcd[1271]: eth0: sendmsg: Network is unreachable
Jun 25 02:54:55 ubuntu dhcpcd[1271]: eth0: sendmsg: Network is unreachable
Jun 25 02:54:59 ubuntu dhcpcd[1271]: eth0: sendmsg: Network is unreachable
Jun 25 02:57:34 ubuntu NetworkManager[835]: <info> (eth0): device state change: activated -> disconnected (reason 'user-requested') [100 30 39]
Jun 25 02:57:34 ubuntu NetworkManager[835]: <info> (eth0): deactivating device (reason 'user-requested') [39]
Jun 25 02:57:34 ubuntu NetworkManager[835]: <info> (eth0): canceled DHCP transaction, DHCP client pid 950
Jun 25 02:57:34 ubuntu NetworkManager[835]: <warn> DNS: plugin dnsmasq update failed
Jun 25 02:57:34 ubuntu NetworkManager[835]: <info> Removing DNS information from /sbin/resolvconf
Jun 25 02:57:40 ubuntu NetworkManager[835]: <info> Activation (wlan0) starting connection 'dd-wrt_vap'
Jun 25 02:57:40 ubuntu NetworkManager[835]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 25 02:57:40 ubuntu NetworkManager[835]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 25 02:57:40 ubuntu NetworkManager[835]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 25 02:57:40 ubuntu NetworkManager[835]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 25 02:57:40 ubuntu NetworkManager[835]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 25 02:57:40 ubuntu NetworkManager[835]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 25 02:57:40 ubuntu NetworkManager[835]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 25 02:57:40 ubuntu NetworkManager[835]: <info> Activation (wlan0/wireless): connection 'dd-wrt_vap' has security, and secrets exist.  No new secrets needed.
Jun 25 02:57:40 ubuntu NetworkManager[835]: <info> Config: added 'ssid' value 'dd-wrt_vap'
Jun 25 02:57:40 ubuntu NetworkManager[835]: <info> Config: added 'scan_ssid' value '1'
Jun 25 02:57:40 ubuntu NetworkManager[835]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jun 25 02:57:40 ubuntu NetworkManager[835]: <info> Config: added 'psk' value '<omitted>'
Jun 25 02:57:40 ubuntu NetworkManager[835]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 25 02:57:40 ubuntu NetworkManager[835]: <info> Config: set interface ap_scan to 1
Jun 25 02:57:41 ubuntu NetworkManager[835]: <info> (wlan0): supplicant interface state: inactive -> scanning
Jun 25 02:57:42 ubuntu wpa_supplicant[938]: wlan0: SME: Trying to authenticate with 00:00:00:00:00:00 (SSID='dd-wrt_vap' freq=2462 MHz)
Jun 25 02:57:42 ubuntu kernel: [  205.698112] wlan0: authenticate with 00:00:00:00:00:00
Jun 25 02:57:42 ubuntu kernel: [  205.710581] wlan0: send auth to 00:00:00:00:00:00 (try 1/3)
Jun 25 02:57:42 ubuntu NetworkManager[835]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jun 25 02:57:42 ubuntu kernel: [  205.912102] wlan0: send auth to 00:00:00:00:00:00 (try 2/3)
Jun 25 02:57:42 ubuntu kernel: [  206.116104] wlan0: send auth to 00:00:00:00:00:00 (try 3/3)
Jun 25 02:57:42 ubuntu kernel: [  206.320064] wlan0: authentication with 00:00:00:00:00:00 timed out
Jun 25 02:57:42 ubuntu NetworkManager[835]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jun 25 02:57:42 ubuntu NetworkManager[835]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun 25 02:57:42 ubuntu kernel: [  206.470525] wlan0: authenticate with 22:aa:4b:0f:3c:d9
Jun 25 02:57:42 ubuntu wpa_supplicant[938]: wlan0: SME: Trying to authenticate with 22:aa:4b:0f:3c:d9 (SSID='dd-wrt_vap' freq=2462 MHz)
Jun 25 02:57:42 ubuntu kernel: [  206.491951] wlan0: direct probe to 22:aa:4b:0f:3c:d9 (try 1/3)
Jun 25 02:57:42 ubuntu NetworkManager[835]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jun 25 02:57:43 ubuntu kernel: [  206.692118] wlan0: direct probe to 22:aa:4b:0f:3c:d9 (try 2/3)
Jun 25 02:57:43 ubuntu kernel: [  206.896062] wlan0: direct probe to 22:aa:4b:0f:3c:d9 (try 3/3)
Jun 25 02:57:43 ubuntu kernel: [  207.100088] wlan0: authentication with 22:aa:4b:0f:3c:d9 timed out
Jun 25 02:57:43 ubuntu NetworkManager[835]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jun 25 02:57:43 ubuntu NetworkManager[835]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun 25 02:58:06 ubuntu NetworkManager[835]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Jun 25 02:58:06 ubuntu NetworkManager[835]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
Jun 25 02:58:06 ubuntu NetworkManager[835]: <warn> Activation (wlan0) failed for connection 'dd-wrt_vap'
Jun 25 02:58:06 ubuntu NetworkManager[835]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jun 25 02:58:06 ubuntu NetworkManager[835]: <info> (wlan0): deactivating device (reason 'none') [0]
Jun 25 02:58:06 ubuntu NetworkManager[835]: <info> (wlan0): supplicant interface state: scanning -> disconnected
Jun 25 02:58:06 ubuntu NetworkManager[835]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
bazbear@ubuntu:~$ 
```



> As a side note, it seems you are running the older version of "wireless_script". Try the newer one, it is cleaner (not that it will catch anymore info..) ;)  Didn't know there was a new one, thanks for the heads up, I just downloaded it :)
> Also, why have you blacklisted the bluetooth drivers? Any specific reasons?I knew it was very very unlikely to have anything to do with my problem, but I was just grasping at straws; there's no Bluetooth card on this computer anyway, so I knew it couldn't hurt to try (and it would be easy enough to reverse anyway).

Thanks for your help!:D

---

### Post by varunendra on 2013-06-25
> **BazBear said:**
>  ```

Jun 25 02:57:42 ubuntu wpa_supplicant[938]: wlan0: SME: Trying to authenticate with **[COLOR="#FF0000"]00:00:00:00:00:00[/COLOR] (SSID='[COLOR="#FF0000"]dd-wrt_vap[/COLOR]' freq=2462 MHz)**
....
....
Jun 25 02:57:42 ubuntu wpa_supplicant[938]: wlan0: SME: Trying to authenticate with 22:aa:4b:0f:3c:d9 (SSID='[COLOR="#FF0000"]dd-wrt_vap[/COLOR]' freq=2462 MHz)
....
....
Jun 25 02:58:06 ubuntu NetworkManager[835]: <info> (wlan0): device state change: config -> **failed (reason '[COLOR="#FF0000"]SSID not found[/COLOR]')** [50 120 53]
Jun 25 02:58:06 ubuntu NetworkManager[835]: <warn> Activation (wlan0) failed for connection 'dd-wrt_vap'
```

Do you have two routers/access-points with same SSID? Did you manually change the mac id of the one highlighted above? If not, this is something I have never seen before. I don't know why it would display a mac id as all zeros. Maybe look into the router's settings to see if it is spoofing that mac id. Disable mac spoofing if it is enabled (or set it to something that makes more sense).

Also, see in the connected systems what mac id they are connected to. (is it the 22:aa:..... or something else?). Post back if it is anything else (or the weird 00:00... one).

If you are sure about the mac id of your router, try saving it in the BSSID field for that connection in Network Manager settings. You should also try saving the authentication settings in NM if you already haven't.

---

### Post by BazBear on 2013-06-25
The weird second dd-wrt is, I believe, due to it being in a wireless repeater configuration. I have no idea why one comes up with an all zeros MAC addy. I originally noticed this using WICD, as it showed both dd-wrts in the available wireless router list (NM doesn't do this, it just shows one). There is no place for me to change the MAC address for the other interface. And yes, the 22:aa etc. is what the Windows, OS X, Android, and iOS "see" as the virtual AP. 

I just checked the primary routers GUI, and it does see the repeater with a slightly different MAC  (first pair and last pair are slightly different). Why can't Lubuntu see the other MAC addy? (rhetorical question).

---

### Post by BazBear on 2013-06-25
I just tried both the vap MAC (the 22:aa one) and the MAC the router uses to "talk" to the primary router into the BSSID field, no good :( The other settings were already saved.

---

### Post by varunendra on 2013-06-26
To be honest, I'm out of ideas now.

As a blind shot (actually based on an apparently unrelated dmesg messages in your outputs), you may try the "btcoex_enable" parameter for ath9k -
```
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k btcoex_enable=0
```

Then run -
```
[COLOR="#FF0000"]dmesg[/COLOR] | grep ath
```
and see if the "**ath: phy0: Disabling ASPM since BTCOEX is enabled**" message is gone, or changed. Moreover, if it helps. If not I'm out of ammo for now :(

---

### Post by BazBear on 2013-06-26
Ran those commands, the last one's output was:
```
dpkg: error: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;


Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
```

---

### Post by BazBear on 2013-06-27
You must have meant ```
dmesg | grep ath
``` and yes ```
ath: phy0: ASPM enabled: 0x42
```

But still no dice on connecting to that blasted little black wedge!:(

As I said to you in PM, I think I'm screwed on this one... though I'm sure in a week or so, I'll try beating this dead horse again; I'm stubborn like that :)

Thanks again for all your time and effort!

---

### Post by varunendra on 2013-06-27
> **BazBear said:**
> You must have meant ```
dmesg | grep ath
```

Yess! Perhaps I watched too many crappy movies in a row before making that post :/ going to correct that !

(and I'm surprised how I missed your last post for 11 hours!!)

And I love seeing dead horses running :P

---

### Post by BazBear on 2013-07-16
This dead horse is, I believe, truly dead. I'm going to pick up another cheap router, turn my dd-wrt router into a wireless client bridge, and then plug the new box into it as my second AP. Not being able to use Lubuntu in about a third of the house (including our patio deck) is just too annoying! It would be cheaper to do a cable run, but it would be a major pain in the butt (the danged shame is that if someone were paying me to do such a job, I'd gladly do it, but I'm too lazy to do it for myself :D )

---

### Post by varunendra on 2013-07-16
Ahh.. there used to be days when linux was too buggy on sandy-bridge processors. Now it's a charm.

I wish we could have the same experience with wireless cards, but alas!

---

### Post by BazBear on 2014-03-19
I don't know why I can now login to my wireless repeater, but I suddenly can. I've been trying it twice week or so right along, and bada bing, today it works. I imagine it must have been one of the OS updates that finally fixed it, as I haven't updated the router firmware. Whatever did it, all's well that ends well! :p

---

### Post by varunendra on 2014-03-19
> **BazBear said:**
> Whatever did it, all's well that ends well! :p

Indeed. :)

---

