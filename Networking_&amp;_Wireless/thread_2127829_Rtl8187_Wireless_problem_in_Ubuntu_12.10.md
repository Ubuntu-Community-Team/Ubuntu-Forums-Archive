---
title: "Rtl8187: Wireless problem in Ubuntu 12.10"
date: 2013-03-21
forum: Networking &amp; Wireless
---

### Post by HelpMeJo on 2013-03-21
Hello, guys. 2 years I use the same ubuntu configuration and hardware. I have never had any problems with the Wi-Fi 
connection. Yesterday after the manual installation of qt5 I lost connection. After that I did fresh installation of my Ubuntu 12.10 
deleting all my configurations and settings. I even try the same with ubuntu 11.10 and 12.04. My wireless indicator shows 
that I am connected and I do not have problems with the router because I reseted it several times to the Default Settings and 
all my other devices have Internet conneciton and work fine. I also have access to my router settings via 192.168.1.1. I tried 
many suggestions on the internet but nothing works. Here is the output of different commands like "ifconfig". Please can 
someone help me? [http://paste.ubuntu.com/5633671/](http://paste.ubuntu.com/5633671/)

I will also post the output here:



*************** info trace ****************



**** uname -a ****


Linux mashine 3.5.0-26-generic #42-Ubuntu SMP Fri Mar 8 23:20:06 UTC 2013 i686 i686 i686 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"


**** lspci ****


0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Toshiba America Info Systems Device [1179:ff00]
    Kernel driver in use: r8169


**** lsusb ****


Bus 001 Device 002: ID 0bda:8198 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 001 Device 003: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


**** iwconfig ****


wlan0     IEEE 802.11bg  ESSID:"TP-LINK_z"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: <MAC address removed>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:81  Invalid misc:324   Missed beacon:0



**** rfkill ****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
joydev                 17162  0 
arc4                   12474  2 
snd_hda_codec_hdmi     31457  1 
snd_hda_codec_realtek    63579  1 
coretemp               13169  0 
snd_hda_intel          32516  3 
snd_hda_codec         111548  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
parport_pc             31969  0 
snd_pcm                80235  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ppdev                  12818  0 
snd_seq_midi           13133  0 
snd_rawmidi            25383  1 snd_seq_midi
rfcomm                 37277  0 
snd_seq_midi_event     14476  1 snd_seq_midi
microcode              18210  0 
bnep                   17708  2 
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
bluetooth             183270  10 rfcomm,bnep
rtl8187                56225  0 
mac80211              461261  1 rtl8187
cfg80211              175574  2 rtl8187,mac80211
eeprom_93cx6           13169  1 rtl8187
snd_timer              24412  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                84878  0 
snd                    62146  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               71278  0 
serio_raw              13032  0 
videobuf2_core         32071  1 uvcvideo
lpc_ich                16926  0 
videodev               95842  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12757  1 uvcvideo
videobuf2_memops       13213  1 videobuf2_vmalloc
toshiba_acpi           18239  0 
sparse_keymap          13659  1 toshiba_acpi
soundcore              14600  1 snd
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
i915                  457241  3 
wmi                    18591  1 toshiba_acpi
drm_kms_helper         47304  1 i915
drm                   238811  4 i915,drm_kms_helper
i2c_algo_bit           13198  1 i915
mac_hid                13038  0 
video                  18895  1 i915
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
ahci                   25497  4 
libahci                25938  1 ahci
r8169                  55977  0 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: wlan0  [TP-LINK_z] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8187
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    vodafone38E2:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA
    RED FRAN:        Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 89 WPA
    jordi wifi :     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA
    *TP-LINK_z:      Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.212
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.20

    DNS:             192.168.1.20


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off




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
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_z"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001053fcd80
                    Extra: Last beacon: 228ms ago
                    IE: Unknown: 000954502D4C494E4B5F7A
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3404051B00000000000000000000000000000000000000
                    IE: Unknown: 3D1604051B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD850050F204104A0001101044000102103B0001031047001000000000000010000000B0487AF012B81021000754502D4C494E4B10230009544C2D57523734304E10240007312E302F322E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523734304E100800020086103C000101
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"jordi wifi "
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001bb6fff52fd
                    Extra: Last beacon: 2268ms ago
                    IE: Unknown: 000B6A6F726469207769666920
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180203F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"RED FRAN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000c02dd6c8
                    Extra: Last beacon: 1532ms ago
                    IE: Unknown: 0008524544204652414E
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC address removed>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"RED GABI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000040fc25825a
                    Extra: Last beacon: 792ms ago
                    IE: Unknown: 00085245442047414249
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010C
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD050010910400
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"vodafone38E2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001bb6db8b4c7
                    Extra: Last beacon: 912ms ago
                    IE: Unknown: 000C766F6461666F6E6533384532
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 200100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B0F0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: DD790050F204104A0001101044000102103B00010310470010000000000000100000005C4CA97238E31021000648756177656910230006484735353661102400085631303052303031104200064847353536611054000800060050F20400011011000D4855415745492D484735353661100800020084103C000103



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


[ 4094.497786] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4099.948743] wlan0: authenticate with <MAC address removed>
[ 4100.087141] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4100.089812] wlan0: authenticated
[ 4100.172046] wlan0: associate with <MAC address removed> (try 1/3)
[ 4100.174457] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=1)
[ 4100.178445] wlan0: associated
[ 4100.178754] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4161.670777] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4168.001682] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4172.160769] wlan0: authenticate with <MAC address removed>
[ 4172.304760] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4172.308334] wlan0: authenticated
[ 4172.380054] wlan0: associate with <MAC address removed> (try 1/3)
[ 4172.382479] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=1)
[ 4172.386955] wlan0: associated
[ 4172.387283] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4203.162332] wlan0: deauthenticated from <MAC address removed> (Reason: 3)
[ 4205.348782] wlan0: authenticate with <MAC address removed>
[ 4205.487171] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4205.688032] wlan0: send auth to <MAC address removed> (try 2/3)
[ 4205.892043] wlan0: send auth to <MAC address removed> (try 3/3)
[ 4206.096047] wlan0: authentication with <MAC address removed> timed out
[ 4218.241486] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4301.964655] wlan0: authenticate with <MAC address removed>
[ 4302.111293] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4302.113340] wlan0: authenticated
[ 4302.184039] wlan0: associate with <MAC address removed> (try 1/3)
[ 4302.186963] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=1)
[ 4302.190472] wlan0: associated
[ 4302.190667] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4366.786040] wlan0: deauthenticated from <MAC address removed> (Reason: 3)
[ 4368.968839] wlan0: authenticate with <MAC address removed>
[ 4369.107197] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4369.308043] wlan0: send auth to <MAC address removed> (try 2/3)
[ 4369.512037] wlan0: send auth to <MAC address removed> (try 3/3)
[ 4369.716039] wlan0: authentication with <MAC address removed> timed out
[ 4382.248863] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4421.912832] wlan0: authenticate with <MAC address removed>
[ 4422.052303] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4422.053909] wlan0: authenticated
[ 4422.124040] wlan0: associate with <MAC address removed> (try 1/3)
[ 4422.127008] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 4422.130756] wlan0: associated
[ 4422.131075] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4467.203855] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4490.985738] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4508.328744] wlan0: authenticate with <MAC address removed>
[ 4508.471243] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4508.473769] wlan0: authenticated
[ 4508.548042] wlan0: associate with <MAC address removed> (try 1/3)
[ 4508.550662] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 4508.554775] wlan0: associated
[ 4508.555088] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4566.242162] wlan0: deauthenticated from <MAC address removed> (Reason: 3)
[ 4568.432837] wlan0: authenticate with <MAC address removed>
[ 4568.571232] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4568.772041] wlan0: send auth to <MAC address removed> (try 2/3)
[ 4568.976040] wlan0: send auth to <MAC address removed> (try 3/3)
[ 4569.180060] wlan0: authentication with <MAC address removed> timed out
[ 4571.939248] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4615.092532] wlan0: authenticate with <MAC address removed>
[ 4615.235245] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4615.237529] wlan0: authenticated
[ 4615.312044] wlan0: associate with <MAC address removed> (try 1/3)
[ 4615.315183] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 4615.318922] wlan0: associated
[ 4615.319230] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4754.203189] wlan0: deauthenticated from <MAC address removed> (Reason: 3)
[ 4756.388812] wlan0: authenticate with <MAC address removed>
[ 4756.527116] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4756.728039] wlan0: send auth to <MAC address removed> (try 2/3)
[ 4756.932697] wlan0: send auth to <MAC address removed> (try 3/3)
[ 4757.136067] wlan0: authentication with <MAC address removed> timed out
[ 4761.157538] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4809.448813] wlan0: authenticate with <MAC address removed>
[ 4809.591282] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4809.595318] wlan0: authenticated
[ 4809.668033] wlan0: associate with <MAC address removed> (try 1/3)
[ 4809.670594] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 4809.674333] wlan0: associated
[ 4809.674645] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4860.882218] wlan0: deauthenticated from <MAC address removed> (Reason: 3)
[ 4863.064796] wlan0: authenticate with <MAC address removed>
[ 4863.203164] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4863.404030] wlan0: send auth to <MAC address removed> (try 2/3)
[ 4863.608042] wlan0: send auth to <MAC address removed> (try 3/3)
[ 4863.812027] wlan0: authentication with <MAC address removed> timed out
[ 4876.252994] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4894.920604] wlan0: authenticate with <MAC address removed>
[ 4895.067139] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4895.069836] wlan0: authenticated
[ 4895.140067] wlan0: associate with <MAC address removed> (try 1/3)
[ 4895.143212] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 4895.148220] wlan0: associated
[ 4895.148547] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4949.841256] wlan0: deauthenticated from <MAC address removed> (Reason: 3)
[ 4965.233242] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5004.344723] wlan0: authenticate with <MAC address removed>
[ 5004.487191] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5004.489488] wlan0: authenticated
[ 5004.560028] wlan0: associate with <MAC address removed> (try 1/3)
[ 5004.565124] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 5004.568611] wlan0: associated
[ 5004.568802] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5250.752313] wlan0: deauthenticated from <MAC address removed> (Reason: 3)
[ 5266.235477] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5284.924636] wlan0: authenticate with <MAC address removed>
[ 5285.071138] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5285.073313] wlan0: authenticated
[ 5285.144132] wlan0: associate with <MAC address removed> (try 1/3)
[ 5285.147320] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 5285.151081] wlan0: associated
[ 5285.151403] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5702.000406] wlan0: deauthenticated from <MAC address removed> (Reason: 3)
[ 5717.249696] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5737.517613] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5742.964493] wlan0: authenticate with <MAC address removed>
[ 5743.119240] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5743.125801] wlan0: authenticated
[ 5743.207018] wlan0: associate with <MAC address removed> (try 1/3)
[ 5743.209912] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=1)
[ 5743.214903] wlan0: associated
[ 5743.215216] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5780.242287] wlan0: deauthenticated from <MAC address removed> (Reason: 3)
[ 5782.424812] wlan0: authenticate with <MAC address removed>
[ 5782.563242] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5782.764037] wlan0: send auth to <MAC address removed> (try 2/3)
[ 5782.968040] wlan0: send auth to <MAC address removed> (try 3/3)
[ 5783.172037] wlan0: authentication with <MAC address removed> timed out
[ 5796.242991] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5814.873055] wlan0: authenticate with <MAC address removed>
[ 5815.011090] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5815.013193] wlan0: authenticated
[ 5815.084047] wlan0: associate with <MAC address removed> (try 1/3)
[ 5815.086561] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=1)
[ 5815.090182] wlan0: associated
[ 5815.090494] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6328.251530] wlan0: deauthenticated from <MAC address removed> (Reason: 3)
[ 6344.238791] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6355.936934] wlan0: authenticate with <MAC address removed>
[ 6356.079229] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6356.280041] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 6356.484052] wlan0: send auth to <MAC address removed> (try 3/3)
[ 6356.487906] wlan0: authenticated
[ 6356.568038] wlan0: associate with <MAC address removed> (try 1/3)
[ 6356.574289] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=1)
[ 6356.577910] wlan0: associated
[ 6356.578219] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6357.036766] wlan0: disassociated from <MAC address removed> (Reason: 8)
[ 6357.117522] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6359.240761] wlan0: authenticate with <MAC address removed>
[ 6359.379226] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6359.580037] wlan0: send auth to <MAC address removed> (try 2/3)
[ 6359.784053] wlan0: send auth to <MAC address removed> (try 3/3)
[ 6359.988038] wlan0: authentication with <MAC address removed> timed out
[ 6362.048873] wlan0: authenticate with <MAC address removed>
[ 6362.187076] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6362.189163] wlan0: authenticated
[ 6362.260037] wlan0: associate with <MAC address removed> (try 1/3)
[ 6362.263023] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=1)
[ 6362.266797] wlan0: associated
[ 6391.062917] wlan0: deauthenticated from <MAC address removed> (Reason: 3)
[ 6406.256616] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6467.516621] wlan0: authenticate with <MAC address removed>
[ 6467.655655] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6467.657668] wlan0: authenticated
[ 6467.728048] wlan0: associate with <MAC address removed> (try 1/3)
[ 6467.730815] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 6467.734671] wlan0: associated
[ 6467.735012] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6514.671191] wlan0: deauthenticated from <MAC address removed> (Reason: 3)
[ 6516.856779] wlan0: authenticate with <MAC address removed>
[ 6516.995135] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6517.196051] wlan0: send auth to <MAC address removed> (try 2/3)
[ 6517.400043] wlan0: send auth to <MAC address removed> (try 3/3)
[ 6517.604041] wlan0: authentication with <MAC address removed> timed out
[ 6530.264817] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6571.288530] wlan0: authenticate with <MAC address removed>
[ 6571.427261] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6571.429691] wlan0: authenticated
[ 6571.504044] wlan0: associate with <MAC address removed> (try 1/3)
[ 6571.506594] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 6571.510369] wlan0: associated
[ 6571.510685] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6728.182111] wlan0: deauthenticated from <MAC address removed> (Reason: 3)
[ 6730.364973] wlan0: authenticate with <MAC address removed>
[ 6730.511165] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6730.712042] wlan0: send auth to <MAC address removed> (try 2/3)
[ 6730.916028] wlan0: send auth to <MAC address removed> (try 3/3)
[ 6731.120037] wlan0: authentication with <MAC address removed> timed out
[ 6744.252704] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6762.908623] wlan0: authenticate with <MAC address removed>
[ 6763.047185] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6763.049493] wlan0: authenticated
[ 6763.124048] wlan0: associate with <MAC address removed> (try 1/3)
[ 6763.127382] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 6763.130991] wlan0: associated
[ 6763.131300] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6791.235912] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6796.320492] wlan0: authenticate with <MAC address removed>
[ 6796.459211] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6796.461740] wlan0: authenticated
[ 6796.532022] wlan0: associate with <MAC address removed> (try 1/3)
[ 6796.535110] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 6796.538622] wlan0: associated
[ 6819.217253] wlan0: deauthenticated from <MAC address removed> (Reason: 3)
[ 6821.408678] wlan0: authenticate with <MAC address removed>
[ 6821.547197] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6821.748037] wlan0: send auth to <MAC address removed> (try 2/3)
[ 6821.952041] wlan0: send auth to <MAC address removed> (try 3/3)
[ 6822.156037] wlan0: authentication with <MAC address removed> timed out
[ 6835.256517] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6853.940931] wlan0: authenticate with <MAC address removed>
[ 6854.087202] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6854.089246] wlan0: authenticated
[ 6854.160057] wlan0: associate with <MAC address removed> (try 1/3)
[ 6854.163123] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 6854.166612] wlan0: associated
[ 6854.166797] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6943.915276] wlan0: deauthenticated from <MAC address removed> (Reason: 3)
[ 6946.096787] wlan0: authenticate with <MAC address removed>
[ 6946.235224] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6946.436029] wlan0: send auth to <MAC address removed> (try 2/3)
[ 6946.640019] wlan0: send auth to <MAC address removed> (try 3/3)
[ 6946.844044] wlan0: authentication with <MAC address removed> timed out
[ 6959.242413] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6977.912901] wlan0: authenticate with <MAC address removed>
[ 6978.056230] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6978.260827] wlan0: send auth to <MAC address removed> (try 2/3)
[ 6978.262414] wlan0: authenticated
[ 6978.332049] wlan0: associate with <MAC address removed> (try 1/3)
[ 6978.336284] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 6978.339905] wlan0: associated
[ 6978.340233] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6995.724751] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 7000.424544] wlan0: authenticate with <MAC address removed>
[ 7000.567107] wlan0: send auth to <MAC address removed> (try 1/3)
[ 7000.570775] wlan0: authenticated
[ 7000.640041] wlan0: associate with <MAC address removed> (try 1/3)
[ 7000.642668] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 7000.646164] wlan0: associated
[ 7881.923598] wlan0: deauthenticated from <MAC address removed> (Reason: 3)
[ 7897.242497] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7927.589692] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7945.140587] wlan0: authenticate with <MAC address removed>
[ 7945.283192] wlan0: send auth to <MAC address removed> (try 1/3)
[ 7945.285997] wlan0: authenticated
[ 7945.356050] wlan0: associate with <MAC address removed> (try 1/3)
[ 7945.358513] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=1)
[ 7945.362370] wlan0: associated
[ 7945.362678] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 8004.386109] wlan0: deauthenticated from <MAC address removed> (Reason: 3)
[ 8006.572840] wlan0: authenticate with <MAC address removed>
[ 8006.711161] wlan0: send auth to <MAC address removed> (try 1/3)
[ 8006.912048] wlan0: send auth to <MAC address removed> (try 2/3)
[ 8007.116033] wlan0: send auth to <MAC address removed> (try 3/3)
[ 8007.320037] wlan0: authentication with <MAC address removed> timed out
[ 8020.242545] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8058.677575] wlan0: authenticate with <MAC address removed>
[ 8058.823171] wlan0: send auth to <MAC address removed> (try 1/3)
[ 8058.826338] wlan0: authenticated
[ 8058.904052] wlan0: associate with <MAC address removed> (try 1/3)
[ 8058.906740] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 8058.910216] wlan0: associated
[ 8058.910412] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 8106.430077] wlan0: deauthenticated from <MAC address removed> (Reason: 3)
[ 8108.624822] wlan0: authenticate with <MAC address removed>
[ 8108.763221] wlan0: send auth to <MAC address removed> (try 1/3)
[ 8108.964047] wlan0: send auth to <MAC address removed> (try 2/3)
[ 8109.168033] wlan0: send auth to <MAC address removed> (try 3/3)
[ 8109.372038] wlan0: authentication with <MAC address removed> timed out
[ 8122.262833] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8175.272812] wlan0: authenticate with <MAC address removed>
[ 8175.415233] wlan0: send auth to <MAC address removed> (try 1/3)
[ 8175.417778] wlan0: authenticated
[ 8175.488024] wlan0: associate with <MAC address removed> (try 1/3)
[ 8175.490536] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 8175.494159] wlan0: associated
[ 8175.494400] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[10957.504050] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[10959.552888] wlan0: authenticate with <MAC address removed>
[10959.691151] wlan0: send auth to <MAC address removed> (try 1/3)
[10959.693815] wlan0: authenticated
[10959.764048] wlan0: associate with <MAC address removed> (try 1/3)
[10959.767079] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[10959.770956] wlan0: associated
[11186.920071] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[11189.032806] wlan0: authenticate with <MAC address removed>
[11189.171196] wlan0: send auth to <MAC address removed> (try 1/3)
[11189.173877] wlan0: authenticated
[11189.244051] wlan0: associate with <MAC address removed> (try 1/3)
[11189.253018] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[11189.256755] wlan0: associated
[11229.504107] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[11238.528804] wlan0: authenticate with <MAC address removed>
[11238.667202] wlan0: send auth to <MAC address removed> (try 1/3)
[11238.671995] wlan0: authenticated
[11238.744042] wlan0: associate with <MAC address removed> (try 1/3)
[11238.752403] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[11238.756035] wlan0: associated
[11846.488099] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[11855.476739] wlan0: authenticate with <MAC address removed>
[11855.615198] wlan0: send auth to <MAC address removed> (try 1/3)
[11855.618003] wlan0: authenticated
[11855.688043] wlan0: associate with <MAC address removed> (try 1/3)
[11855.693271] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[11855.697258] wlan0: associated
[11859.504062] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[11861.576754] wlan0: authenticate with <MAC address removed>
[11861.715200] wlan0: send auth to <MAC address removed> (try 1/3)
[11861.717405] wlan0: authenticated
[11861.788026] wlan0: associate with <MAC address removed> (try 1/3)
[11861.794024] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[11861.797654] wlan0: associated


**************** done ********************

---

### Post by chili555 on 2013-03-21
I notice you have both wireless and wired connected; both have IP addresses and nm-tool reports that they are connected. It is useless to try to troubleshoot wireless problems when wired is connected. We have no way to know if your inability to reach the internet is through wired or wireless. When you run diagnostics for us from now on, please be sure the ethernet is detached.

You have two pretty interesting addresses; 192.168.1.100 and x.200. Where did they come from? Did you set static IP addresses in Network Manager?

I notice your ethernet gateway is:> - Device: eth0 [Wired connection 1] -------------------------------------------
Type: Wired
Driver: r8169
State: connected
Default: yes
<snip>
IPv4 Settings:
Address: 192.168.1.200
Prefix: 24 (255.255.255.0)
[COLOR="#FF0000"]Gateway: 192.168.1.20[/COLOR]

[COLOR="#FF0000"]DNS: 192.168.1.20[/COLOR]

Are those settings you filled in? Isn't the address of your router 192.168.1.1?

---

### Post by HelpMeJo on 2013-03-21
[**[COLOR=#000000]chili555[/COLOR]**]("http://ubuntuforums.org/member.php?u=35909"),
I edited the info as you said without the eth. Yes, it should be 192.168.1.1. I reset the settings of my router again and now everything works fine. That's my faulth and the problem was from the router.
Yes, I access the router using 192.168.1.1 but my Internet comes from WiFi Antenna (Nano Station M5) and with 192.168.1.20 I access the antenna (so maybe that's the reason, I am not sure.)

---

### Post by chili555 on 2013-03-21
Generally, it is best to set Network Manager to use Automatic (DHCP) and let NM do all the hard work. 

So you are saying all is well and Solved??

---

### Post by HelpMeJo on 2013-03-21
It is already on Automatic(DHCP), but everythings is well now and the solved. 
THank you for your help and time!

---

### Post by chili555 on 2013-03-21
> **HelpMeJo said:**
> It is already on Automatic(DHCP), but everythings is well now and the solved. 
THank you for your help and time!Happy to do so. Call on us any time.

---

