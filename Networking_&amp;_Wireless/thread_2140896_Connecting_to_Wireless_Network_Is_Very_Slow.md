---
title: "Connecting to Wireless Network Is Very Slow"
date: 2013-05-01
forum: Networking &amp; Wireless
---

### Post by jdorenbush on 2013-05-01
I just got my Netgear USB wireless adapter working and my internet speeds are excellent, but for some reason it takes 2-3 minutes just for the adapter to make the connection to my wireless network.

Below is the output from a [wireless troubleshooting script]("http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385") that I ran:

```
*************** info trace ****************



**** uname -a ****


Linux jeff-desktop 3.5.0-28-generic #48-Ubuntu SMP Tue Apr 23 23:03:38 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"


**** lspci ****


02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8131 Gigabit Ethernet [1969:1063] (rev c0)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7599]
	Kernel driver in use: atl1c


**** lsusb ****


Bus 001 Device 003: ID 1058:1102 Western Digital Technologies, Inc. 
Bus 002 Device 002: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


**** iwconfig ****


wlan1     IEEE 802.11g  ESSID:"BirdsHouse"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: <MAC address removed>   
          Bit Rate=130 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:71/100  Signal level:-50 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:3506   Missed beacon:0



**** rfkill ****




**** lsmod ****


Module                  Size  Used by
nls_iso8859_1          12714  1 
dm_crypt               23012  0 
parport_pc             32689  0 
ppdev                  17074  0 
rfcomm                 46620  0 
bnep                   18141  2 
bluetooth             209249  10 rfcomm,bnep
binfmt_misc            17501  1 
snd_hda_codec_hdmi     32049  4 
kvm_amd                55605  0 
kvm                   414071  1 kvm_amd
snd_hda_codec_via      46676  1 
microcode              22804  0 
ndiswrapper           283324  0 
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
snd_hda_intel          33492  5 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
edac_core              52452  0 
edac_mce_amd           23304  0 
psmouse                95595  0 
serio_raw              13216  0 
snd_seq_midi_event     14900  1 snd_seq_midi
k10temp                13127  0 
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
sp5100_tco             13698  0 
i2c_piix4              13168  0 
snd_timer              29426  2 snd_pcm,snd_seq
nvidia              11309140  40 
joydev                 17458  0 
mac_hid                13206  0 
snd                    78921  20 snd_hda_codec_hdmi,snd_hda_codec_via,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq,snd_pcm,snd_seq_device,snd_timer
wmi                    19071  0 
soundcore              15048  1 snd
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
hid_logitech           26586  0 
ff_memless             13014  1 hid_logitech
hid_generic            12541  0 
usbhid                 46987  1 hid_logitech
hid                   100411  3 hid_logitech,hid_generic,usbhid
usb_storage            48839  1 
atl1c                  41102  0 
pata_atiixp            13205  0 
ahci                   25721  2 
libahci                31192  1 ahci


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: wlan1  [BirdsHouse] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           130 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    BAFamily Network:Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    belkin.eb6:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    Cordova 1:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    myqwest2929:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WEP
    belkin.eb6.guests: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39
    *BirdsHouse:     Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 71 WPA2
    HP-Print-D8-Photosmart 5520: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA2

  IPv4 Settings:
    Address:         192.168.1.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             8.8.8.8
    DNS:             8.8.4.4


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

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

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


**** iwlist ****


wlan1     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    ESSID:"BirdsHouse"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Quality:70/100  Signal level:-51 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 000A4269726473486F757365
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030108
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1608080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD310050F204104A0001101044000102104700103CF57BA23974944412BE042E32753FCB103C0001031049000600372A000120
                    IE: Unknown: DD090010180203F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD890050F204104A0001101044000102103B000103104700103CF57BA23974944412BE042E32753FCB1021000D4E4554474541522C20496E632E1023000A574E44523334303076321024000A574E44523334303076321042000230311054000800060050F20400011011000A574E4452333430307632100800020004103C0001031049000600372A000120
          Cell 02 - Address: <MAC address removed>
                    ESSID:"myqwest2929"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:43/100  Signal level:-68 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 000B6D79717765737432393239
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0107
                    IE: Unknown: 32080C1218243048606C
          Cell 03 - Address: <MAC address removed>
                    ESSID:"BAFamily Network"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:37/100  Signal level:-72 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 0010424146616D696C79204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A2C4017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101050003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000393016A0320
                    IE: Unknown: DD070017F203020180
                    IE: Unknown: DD0E0017F207000101060021E9B976B5
          Cell 04 - Address: <MAC address removed>
                    ESSID:"HP-Print-D8-Photosmart 5520"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:25/100  Signal level:-80 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 001B48502D5072696E742D44382D50686F746F736D6172742035353230
                    IE: Unknown: 010802040B0C12161824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A0055010200050039010400580200007B01040058020000330102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1606000100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    ESSID:"Cordova 1"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:31/100  Signal level:-76 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 0009436F72646F76612031
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 331AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: 341606001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD810050F204104A0001101044000102103B0001031047001039A50C961DD211B28EF9EDB5858F035710210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D383335104200046E6F6E651054000800060050F2040001101100074449522D383335100800020080103C0001011049000600372A000120



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search google.com


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


[   19.470137] wmi: Mapper loaded
[   19.529665] ndiswrapper version 1.58rc1 loaded (smp=yes, preempt=no)
[   20.850431] ndiswrapper: driver bcmwlhigh5 (Netgear,03/28/2011, 5.100.68.46) loaded
[   20.856246] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011f64000, 16000, 4
[   20.856252] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011f67e80, 16000, 5
[   20.856254] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011f6bd00, 16000, 5
[   20.856256] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011f6fb80, 16000, 5
[   20.856258] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011f73a00, 16000, 5
[   20.856260] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011f77880, 16000, 5
[   20.856262] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011f7b700, 16000, 5
[   20.856263] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011f7f580, 16000, 5
[   20.856266] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011f83400, 16000, 5
[   20.856267] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011f87280, 16000, 5
[   20.856269] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011f8b100, 16000, 4
[   20.856271] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011f8ef80, 16000, 5
[   20.856273] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011f92e00, 16000, 5
[   20.856274] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011f96c80, 16000, 5
[   20.856276] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011f9ab00, 16000, 5
[   20.856277] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011f9e980, 16000, 5
[   20.856279] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011fa2800, 16000, 5
[   20.856280] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011fa6680, 16000, 5
[   20.856282] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011faa500, 16000, 5
[   20.856284] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011fae380, 16000, 5
[   20.856286] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011fb2200, 16000, 5
[   20.856287] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011fb6080, 16000, 4
[   20.856289] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011fb9f00, 16000, 5
[   20.856292] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011fbdd80, 16000, 5
[   20.856294] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011fc1c00, 16000, 5
[   20.856296] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011fc5a80, 16000, 5
[   20.856298] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011fc9900, 16000, 5
[   20.856299] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011fcd780, 16000, 5
[   20.856301] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011fd1600, 16000, 5
[   20.856302] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011fd5480, 16000, 5
[   20.856304] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011fd9300, 16000, 5
[   20.856306] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011fdd180, 16000, 4
[   20.856307] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011fe1000, 16000, 4
[   20.856309] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011fe4e80, 16000, 5
[   20.856310] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011fe8d00, 16000, 5
[   20.856312] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011fecb80, 16000, 5
[   20.856313] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011ff0a00, 16000, 5
[   20.856315] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011ff4880, 16000, 5
[   20.856316] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011ff8700, 16000, 5
[   20.856319] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90011ffc580, 16000, 5
[   20.856320] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012000400, 16000, 5
[   20.856322] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012004280, 16000, 5
[   20.856324] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012008100, 16000, 4
[   20.856326] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001200bf80, 16000, 5
[   20.856327] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001200fe00, 16000, 5
[   20.856329] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012013c80, 16000, 5
[   20.856331] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012017b00, 16000, 5
[   20.856332] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001201b980, 16000, 5
[   20.856334] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001201f800, 16000, 5
[   20.856335] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012023680, 16000, 5
[   20.878036] ndiswrapper (ndis_encode_setting:383): unknown type: 3
[   21.157075] wlan0: ethernet device <MAC address removed> using NDIS driver: bcmwlhigh5, version: 0x564442e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9020.F.conf
[   21.164111] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[   21.166434] usbcore: registered new interface driver ndiswrapper
[   21.170674] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[   21.177420] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   44.951537] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready


**************** done ********************
```

---

### Post by praseodym on 2013-05-01
> ```
nameserver 127.0.[COLOR="#FF0000"]1[/COLOR].1
```
Thats a bug, remove the package resolvconf and reboot:
```

sudo apt-get remove --purge resolvconf
```

---

### Post by jdthood on 2013-05-01
> **praseodym said:**
> Thats a bug, remove the package resolvconf and reboot:

No, that is not a bug. Resolvconf is working correctly.

Resolvconf writes "nameserver 127.0.1.1" to resolv.conf and this reflects the fact that the NetworkManager-controlled local forwarding nameserver (an instance of dnsmasq) is listening at the IP address 127.0.1.1.

If you have on the advice of praseodym removed the resolvconf package then you should re-install it before continuing. Make sure that /etc/resolv.conf is a symbolic link to "../run/resolvconf/resolv.conf".

NetworkManager starts a local fowarding nameserver process because /etc/NetworkManager/NetworkManager.conf contains "dns=dnsmasq". If you do not want to use a local forwarding nameserver then comment out the line "dns=dnsmasq" in that file and "sudo restart network-manager".

---

### Post by jdorenbush on 2013-05-01
> **jdthood said:**
> If you have on the advice of praseodym removed the resolvconf package then you should re-install it before continuing. Make sure that /etc/resolv.conf is a symbolic link to "../run/resolvconf/resolv.conf".

I didn't uninstall resolvconf and I confirmed that the symbolic link is correct.

> **jdthood said:**
> NetworkManager starts a local fowarding nameserver process because /etc/NetworkManager/NetworkManager.conf contains "dns=dnsmasq". If you do not want to use a local forwarding nameserver then comment out the line "dns=dnsmasq" in that file and "sudo restart network-manager".

I commented out "dns=dnsmasq" (after running the restart command the nm-applet icon disappeared from the tray, but was restored after a reboot) but connecting to the wireless network is still taking too long... :(

---

### Post by jdthood on 2013-05-02
> **jdorenbush said:**
> I commented out "dns=dnsmasq" (after running the restart command the nm-applet icon disappeared from the tray, but was restored after a reboot) but connecting to the wireless network is still taking too long... :(

Have you checked on launchpad.net for bugs related to your Wi-Fi hardware's driver?

    [https://bugs.launchpad.net/ubuntu/+source/linux](https://bugs.launchpad.net/ubuntu/+source/linux)

---

### Post by jdorenbush on 2013-05-02
> **jdthood said:**
> Have you checked on launchpad.net for bugs related to your Wi-Fi hardware's driver?

    [https://bugs.launchpad.net/ubuntu/+source/linux](https://bugs.launchpad.net/ubuntu/+source/linux)

I searched for "bcmwlhigh5" and "bcmwlhigh" and didn't find anything. 

PS: I've always used ethernet so this is my first time having to troubleshoot wireless issues on Linux, more specifically, having to deal with installing wireless drivers on Linux. In the past, all of my hardware has worked without having to install additional drivers. So please forgive my lack of knowledge regarding this side of Linux.

---

### Post by jdorenbush on 2013-05-02
Further troubleshooting: I disconnected the USB adapter, rebooted, opened up System Log, and then connected the adapter. Below is everything that happened in the Log from the moment I connected the adapter to the moment it successfully connected to the wireless network.

```
May  2 19:01:46 jeff-desktop kernel: [  136.362298] usb 2-1: new high-speed USB device number 2 using ehci_hcd
May  2 19:01:46 jeff-desktop kernel: [  136.498316] usb 2-1: New USB device found, idVendor=0846, idProduct=9020
May  2 19:01:46 jeff-desktop kernel: [  136.498328] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
May  2 19:01:46 jeff-desktop kernel: [  136.498336] usb 2-1: Product: Remote Download Wireless Adapter
May  2 19:01:46 jeff-desktop kernel: [  136.498343] usb 2-1: Manufacturer: Broadcom
May  2 19:01:46 jeff-desktop kernel: [  136.498348] usb 2-1: SerialNumber: 113
May  2 19:01:46 jeff-desktop mtp-probe: checking bus 2, device 2: "/sys/devices/pci0000:00/0000:00:13.2/usb2/2-1"
May  2 19:01:47 jeff-desktop mtp-probe: bus: 2, device: 2 was not an MTP device
May  2 19:01:47 jeff-desktop kernel: [  137.523644] ndiswrapper version 1.58rc1 loaded (smp=yes, preempt=no)
May  2 19:01:47 jeff-desktop kernel: [  137.673093] usb 2-1: reset high-speed USB device number 2 using ehci_hcd
May  2 19:01:48 jeff-desktop kernel: [  137.862548] ndiswrapper: driver bcmwlhigh5 (Netgear,03/28/2011, 5.100.68.46) loaded
May  2 19:01:48 jeff-desktop kernel: [  138.271460] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90014048000, 16000, 4
May  2 19:01:48 jeff-desktop kernel: [  138.271474] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001404be80, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271482] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001404fd00, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271489] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90014053b80, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271495] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90014057a00, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271501] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001405b880, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271507] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001405f700, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271514] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90014063580, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271519] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90014067400, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271526] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001406b280, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271532] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001406f100, 16000, 4
May  2 19:01:48 jeff-desktop kernel: [  138.271538] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90014072f80, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271546] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90014076e00, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271552] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001407ac80, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271558] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001407eb00, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271566] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90014082980, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271572] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90014086800, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271577] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001408a680, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271583] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001408e500, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271589] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90014092380, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271594] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90014096200, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271600] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001409a080, 16000, 4
May  2 19:01:48 jeff-desktop kernel: [  138.271606] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001409df00, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271611] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900140a1d80, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271617] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900140a5c00, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271623] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900140a9a80, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271628] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900140ad900, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271634] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900140b1780, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271642] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900140b5600, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271647] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900140b9480, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271653] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900140bd300, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271659] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900140c1180, 16000, 4
May  2 19:01:48 jeff-desktop kernel: [  138.271667] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900140c5000, 16000, 4
May  2 19:01:48 jeff-desktop kernel: [  138.271672] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900140c8e80, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271678] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900140ccd00, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271684] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900140d0b80, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271689] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900140d4a00, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271695] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900140d8880, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271701] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900140dc700, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271706] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900140e0580, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271712] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900140e4400, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271718] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900140e8280, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271723] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900140ec100, 16000, 4
May  2 19:01:48 jeff-desktop kernel: [  138.271729] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900140eff80, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271737] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900140f3e00, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271742] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900140f7c80, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271748] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900140fbb00, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271754] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900140ff980, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271759] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90014103800, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.271768] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90014107680, 16000, 5
May  2 19:01:48 jeff-desktop kernel: [  138.290071] ndiswrapper (ndis_encode_setting:383): unknown type: 3
May  2 19:01:48 jeff-desktop kernel: [  138.576220] wlan0: ethernet device <MAC address removed> using NDIS driver: bcmwlhigh5, version: 0x564442e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9020.F.conf
May  2 19:01:48 jeff-desktop kernel: [  138.584488] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
May  2 19:01:48 jeff-desktop kernel: [  138.587267] usbcore: registered new interface driver ndiswrapper
May  2 19:01:48 jeff-desktop NetworkManager[1054]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:13.2/usb2/2-1/2-1:1.0/net/wlan1, iface: wlan1)
May  2 19:01:48 jeff-desktop NetworkManager[1054]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:13.2/usb2/2-1/2-1:1.0/net/wlan1, iface: wlan1): no ifupdown configuration found.
May  2 19:01:48 jeff-desktop NetworkManager[1054]: <warn> failed to allocate link cache: (-10) Operation not supported
May  2 19:01:48 jeff-desktop kernel: [  138.604690] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
May  2 19:01:48 jeff-desktop NetworkManager[1054]: <info> (wlan1): driver does not support SSID scans (scan_capa 0x00).
May  2 19:01:48 jeff-desktop NetworkManager[1054]: <info> (wlan1): using WEXT for WiFi device control
May  2 19:01:48 jeff-desktop NetworkManager[1054]: <error> [1367546508.908922] [nm-device-wifi.c:2683] real_update_permanent_hw_address(): (wlan1): unable to read permanent MAC address (error 0)
May  2 19:01:48 jeff-desktop NetworkManager[1054]: <info> (wlan1): new 802.11 WiFi device (driver: 'ndiswrapper' ifindex: 3)
May  2 19:01:48 jeff-desktop NetworkManager[1054]: <info> (wlan1): exported as /org/freedesktop/NetworkManager/Devices/1
May  2 19:01:48 jeff-desktop NetworkManager[1054]: <info> (wlan1): now managed
May  2 19:01:48 jeff-desktop NetworkManager[1054]: <info> (wlan1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May  2 19:01:48 jeff-desktop NetworkManager[1054]: <info> (wlan1): bringing up device.
May  2 19:01:48 jeff-desktop NetworkManager[1054]: <info> (wlan1): preparing device.
May  2 19:01:48 jeff-desktop NetworkManager[1054]: <info> (wlan1): deactivating device (reason 'managed') [2]
May  2 19:01:48 jeff-desktop kernel: [  138.617277] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
May  2 19:01:48 jeff-desktop dbus[999]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
May  2 19:01:48 jeff-desktop dbus[999]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
May  2 19:01:48 jeff-desktop NetworkManager[1054]: <info> wpa_supplicant started
May  2 19:01:48 jeff-desktop wpa_supplicant[2274]: nl80211: 'nl80211' generic netlink not found
May  2 19:01:48 jeff-desktop wpa_supplicant[2274]: Failed to initialize driver 'nl80211'
May  2 19:01:48 jeff-desktop NetworkManager[1054]: <info> (wlan1) supports 1 scan SSIDs
May  2 19:01:48 jeff-desktop NetworkManager[1054]: <info> (wlan1): supplicant interface state: starting -> ready
May  2 19:01:48 jeff-desktop NetworkManager[1054]: <info> (wlan1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
May  2 19:01:48 jeff-desktop NetworkManager[1054]: <warn> Trying to remove a non-existant call id.
May  2 19:01:48 jeff-desktop NetworkManager[1054]: <info> (wlan1): supplicant interface state: ready -> inactive
May  2 19:01:48 jeff-desktop NetworkManager[1054]: <info> (wlan1) supports 1 scan SSIDs
May  2 19:02:02 jeff-desktop NetworkManager[1054]: <info> Auto-activating connection 'BirdsHouse'.
May  2 19:02:02 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) starting connection 'BirdsHouse'
May  2 19:02:02 jeff-desktop NetworkManager[1054]: <info> (wlan1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May  2 19:02:02 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
May  2 19:02:02 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
May  2 19:02:02 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
May  2 19:02:02 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
May  2 19:02:02 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
May  2 19:02:02 jeff-desktop NetworkManager[1054]: <info> (wlan1): device state change: prepare -> config (reason 'none') [40 50 0]
May  2 19:02:02 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1/wireless): connection 'BirdsHouse' has security, and secrets exist.  No new secrets needed.
May  2 19:02:02 jeff-desktop NetworkManager[1054]: <info> Config: added 'ssid' value 'BirdsHouse'
May  2 19:02:02 jeff-desktop NetworkManager[1054]: <info> Config: added 'scan_ssid' value '1'
May  2 19:02:02 jeff-desktop NetworkManager[1054]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
May  2 19:02:02 jeff-desktop NetworkManager[1054]: <info> Config: added 'psk' value '<omitted>'
May  2 19:02:02 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
May  2 19:02:02 jeff-desktop NetworkManager[1054]: <info> Config: set interface ap_scan to 1
May  2 19:02:02 jeff-desktop NetworkManager[1054]: <info> (wlan1): supplicant interface state: inactive -> scanning
May  2 19:02:12 jeff-desktop wpa_supplicant[2274]: wlan1: Trying to associate with <MAC address removed> (SSID='BirdsHouse' freq=2447 MHz)
May  2 19:02:12 jeff-desktop NetworkManager[1054]: <info> (wlan1): supplicant interface state: scanning -> associating
May  2 19:02:13 jeff-desktop kernel: [  162.865207] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
May  2 19:02:13 jeff-desktop wpa_supplicant[2274]: wlan1: Associated with <MAC address removed>
May  2 19:02:13 jeff-desktop NetworkManager[1054]: <info> (wlan1): supplicant interface state: associating -> associated
May  2 19:02:13 jeff-desktop NetworkManager[1054]: <info> (wlan1): supplicant interface state: associated -> 4-way handshake
May  2 19:02:13 jeff-desktop wpa_supplicant[2274]: wlan1: WPA: Key negotiation completed with <MAC address removed> [PTK=CCMP GTK=CCMP]
May  2 19:02:13 jeff-desktop wpa_supplicant[2274]: wlan1: CTRL-EVENT-CONNECTED - Connection to <MAC address removed> completed (auth) [id=0 id_str=]
May  2 19:02:13 jeff-desktop NetworkManager[1054]: <info> (wlan1): supplicant interface state: 4-way handshake -> completed
May  2 19:02:13 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'BirdsHouse'.
May  2 19:02:13 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) scheduled.
May  2 19:02:13 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) started...
May  2 19:02:13 jeff-desktop NetworkManager[1054]: <info> (wlan1): device state change: config -> ip-config (reason 'none') [50 70 0]
May  2 19:02:13 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Beginning DHCPv4 transaction (timeout in 45 seconds)
May  2 19:02:13 jeff-desktop NetworkManager[1054]: <info> dhclient started with pid 2296
May  2 19:02:13 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) complete.
May  2 19:02:13 jeff-desktop dhclient: Internet Systems Consortium DHCP Client 4.2.4
May  2 19:02:13 jeff-desktop dhclient: Copyright 2004-2012 Internet Systems Consortium.
May  2 19:02:13 jeff-desktop dhclient: All rights reserved.
May  2 19:02:13 jeff-desktop dhclient: For info, please visit https://www.isc.org/software/dhcp/
May  2 19:02:13 jeff-desktop dhclient: 
May  2 19:02:13 jeff-desktop NetworkManager[1054]: <info> (wlan1): DHCPv4 state changed nbi -> preinit
May  2 19:02:13 jeff-desktop dhclient: Listening on LPF/wlan1/<MAC address removed>
May  2 19:02:13 jeff-desktop dhclient: Sending on   LPF/wlan1/<MAC address removed>
May  2 19:02:13 jeff-desktop dhclient: Sending on   Socket/fallback
May  2 19:02:13 jeff-desktop dhclient: DHCPREQUEST of 192.168.1.7 on wlan1 to 255.255.255.255 port 67
May  2 19:02:16 jeff-desktop dhclient: DHCPREQUEST of 192.168.1.7 on wlan1 to 255.255.255.255 port 67
May  2 19:02:21 jeff-desktop wpa_supplicant[2274]: wlan1: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
May  2 19:02:22 jeff-desktop wpa_supplicant[2274]: wlan1: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
May  2 19:02:23 jeff-desktop dhclient: DHCPREQUEST of 192.168.1.7 on wlan1 to 255.255.255.255 port 67
May  2 19:02:23 jeff-desktop wpa_supplicant[2274]: wlan1: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
May  2 19:02:24 jeff-desktop NetworkManager[1054]: <info> (wlan1): supplicant interface state: completed -> 4-way handshake
May  2 19:02:24 jeff-desktop wpa_supplicant[2274]: wlan1: WPA: Key negotiation completed with <MAC address removed> [PTK=CCMP GTK=CCMP]
May  2 19:02:24 jeff-desktop NetworkManager[1054]: <info> (wlan1): supplicant interface state: 4-way handshake -> completed
May  2 19:02:30 jeff-desktop dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3
May  2 19:02:33 jeff-desktop wpa_supplicant[2274]: wlan1: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
May  2 19:02:33 jeff-desktop dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 4
May  2 19:02:34 jeff-desktop wpa_supplicant[2274]: wlan1: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
May  2 19:02:37  wpa_supplicant[2274]: last message repeated 3 times
May  2 19:02:37 jeff-desktop dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 8
May  2 19:02:38 jeff-desktop NetworkManager[1054]: <info> (wlan1): supplicant interface state: completed -> 4-way handshake
May  2 19:02:38 jeff-desktop wpa_supplicant[2274]: wlan1: WPA: Key negotiation completed with <MAC address removed> [PTK=CCMP GTK=CCMP]
May  2 19:02:38 jeff-desktop NetworkManager[1054]: <info> (wlan1): supplicant interface state: 4-way handshake -> completed
May  2 19:02:45 jeff-desktop dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 19
May  2 19:02:47 jeff-desktop wpa_supplicant[2274]: wlan1: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
May  2 19:02:54  wpa_supplicant[2274]: last message repeated 6 times
May  2 19:02:54 jeff-desktop NetworkManager[1054]: <info> (wlan1): supplicant interface state: completed -> 4-way handshake
May  2 19:02:54 jeff-desktop wpa_supplicant[2274]: wlan1: WPA: Key negotiation completed with <MAC address removed> [PTK=CCMP GTK=CCMP]
May  2 19:02:54 jeff-desktop NetworkManager[1054]: <info> (wlan1): supplicant interface state: 4-way handshake -> completed
May  2 19:02:58 jeff-desktop NetworkManager[1054]: <warn> (wlan1): DHCPv4 request timed out.
May  2 19:02:58 jeff-desktop NetworkManager[1054]: <info> (wlan1): canceled DHCP transaction, DHCP client pid 2296
May  2 19:02:58 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
May  2 19:02:58 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 4 of 5 (IPv4 Configure Timeout) started...
May  2 19:02:58 jeff-desktop NetworkManager[1054]: <info> (wlan1): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
May  2 19:02:58 jeff-desktop NetworkManager[1054]: <warn> Activation (wlan1) failed for connection 'BirdsHouse'
May  2 19:02:58 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 4 of 5 (IPv4 Configure Timeout) complete.
May  2 19:02:58 jeff-desktop NetworkManager[1054]: <info> (wlan1): device state change: failed -> disconnected (reason 'none') [120 30 0]
May  2 19:02:58 jeff-desktop NetworkManager[1054]: <info> (wlan1): deactivating device (reason 'none') [0]
May  2 19:02:58 jeff-desktop wpa_supplicant[2274]: wlan1: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
May  2 19:02:58 jeff-desktop NetworkManager[1054]: <info> (wlan1): supplicant interface state: completed -> disconnected
May  2 19:03:01 jeff-desktop NetworkManager[1054]: <info> Auto-activating connection 'BirdsHouse'.
May  2 19:03:01 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) starting connection 'BirdsHouse'
May  2 19:03:01 jeff-desktop NetworkManager[1054]: <info> (wlan1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May  2 19:03:01 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
May  2 19:03:01 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
May  2 19:03:01 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
May  2 19:03:01 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
May  2 19:03:01 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
May  2 19:03:01 jeff-desktop NetworkManager[1054]: <info> (wlan1): device state change: prepare -> config (reason 'none') [40 50 0]
May  2 19:03:01 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1/wireless): access point 'BirdsHouse' has security, but secrets are required.
May  2 19:03:01 jeff-desktop NetworkManager[1054]: <info> (wlan1): device state change: config -> need-auth (reason 'none') [50 60 0]
May  2 19:03:01 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
May  2 19:03:01 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
May  2 19:03:01 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
May  2 19:03:01 jeff-desktop NetworkManager[1054]: <info> (wlan1): device state change: need-auth -> prepare (reason 'none') [60 40 0]
May  2 19:03:01 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
May  2 19:03:01 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
May  2 19:03:01 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
May  2 19:03:01 jeff-desktop NetworkManager[1054]: <info> (wlan1): device state change: prepare -> config (reason 'none') [40 50 0]
May  2 19:03:01 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1/wireless): connection 'BirdsHouse' has security, and secrets exist.  No new secrets needed.
May  2 19:03:01 jeff-desktop NetworkManager[1054]: <info> Config: added 'ssid' value 'BirdsHouse'
May  2 19:03:01 jeff-desktop NetworkManager[1054]: <info> Config: added 'scan_ssid' value '1'
May  2 19:03:01 jeff-desktop NetworkManager[1054]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
May  2 19:03:01 jeff-desktop NetworkManager[1054]: <info> Config: added 'psk' value '<omitted>'
May  2 19:03:01 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
May  2 19:03:01 jeff-desktop NetworkManager[1054]: <info> Config: set interface ap_scan to 1
May  2 19:03:01 jeff-desktop NetworkManager[1054]: <info> (wlan1): supplicant interface state: disconnected -> scanning
May  2 19:03:11 jeff-desktop wpa_supplicant[2274]: wlan1: Trying to associate with <MAC address removed> (SSID='BirdsHouse' freq=2447 MHz)
May  2 19:03:11 jeff-desktop NetworkManager[1054]: <info> (wlan1): supplicant interface state: scanning -> associating
May  2 19:03:12 jeff-desktop wpa_supplicant[2274]: wlan1: Associated with <MAC address removed>
May  2 19:03:12 jeff-desktop NetworkManager[1054]: <info> (wlan1): supplicant interface state: associating -> 4-way handshake
May  2 19:03:12 jeff-desktop wpa_supplicant[2274]: wlan1: WPA: Key negotiation completed with <MAC address removed> [PTK=CCMP GTK=CCMP]
May  2 19:03:12 jeff-desktop wpa_supplicant[2274]: wlan1: CTRL-EVENT-CONNECTED - Connection to <MAC address removed> completed (reauth) [id=1 id_str=]
May  2 19:03:12 jeff-desktop NetworkManager[1054]: <info> (wlan1): supplicant interface state: 4-way handshake -> completed
May  2 19:03:12 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'BirdsHouse'.
May  2 19:03:12 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) scheduled.
May  2 19:03:12 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) started...
May  2 19:03:12 jeff-desktop NetworkManager[1054]: <info> (wlan1): device state change: config -> ip-config (reason 'none') [50 70 0]
May  2 19:03:12 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Beginning DHCPv4 transaction (timeout in 45 seconds)
May  2 19:03:12 jeff-desktop NetworkManager[1054]: <info> dhclient started with pid 2302
May  2 19:03:12 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) complete.
May  2 19:03:12 jeff-desktop dhclient: Internet Systems Consortium DHCP Client 4.2.4
May  2 19:03:12 jeff-desktop dhclient: Copyright 2004-2012 Internet Systems Consortium.
May  2 19:03:12 jeff-desktop dhclient: All rights reserved.
May  2 19:03:12 jeff-desktop dhclient: For info, please visit https://www.isc.org/software/dhcp/
May  2 19:03:12 jeff-desktop dhclient: 
May  2 19:03:12 jeff-desktop NetworkManager[1054]: <info> (wlan1): DHCPv4 state changed nbi -> preinit
May  2 19:03:12 jeff-desktop dhclient: Listening on LPF/wlan1/<MAC address removed>
May  2 19:03:12 jeff-desktop dhclient: Sending on   LPF/wlan1/<MAC address removed>
May  2 19:03:12 jeff-desktop dhclient: Sending on   Socket/fallback
May  2 19:03:12 jeff-desktop dhclient: DHCPREQUEST of 192.168.1.7 on wlan1 to 255.255.255.255 port 67
May  2 19:03:15 jeff-desktop dhclient: DHCPREQUEST of 192.168.1.7 on wlan1 to 255.255.255.255 port 67
May  2 19:03:15 jeff-desktop dhclient: DHCPACK of 192.168.1.7 from 192.168.1.1
May  2 19:03:15 jeff-desktop dhclient: bound to 192.168.1.7 -- renewal in 35061 seconds.
May  2 19:03:15 jeff-desktop NetworkManager[1054]: <info> (wlan1): DHCPv4 state changed preinit -> reboot
May  2 19:03:15 jeff-desktop NetworkManager[1054]: <info>   address 192.168.1.7
May  2 19:03:15 jeff-desktop NetworkManager[1054]: <info>   prefix 24 (255.255.255.0)
May  2 19:03:15 jeff-desktop NetworkManager[1054]: <info>   gateway 192.168.1.1
May  2 19:03:15 jeff-desktop NetworkManager[1054]: <info>   nameserver '192.168.1.1'
May  2 19:03:15 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May  2 19:03:15 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Commit) started...
May  2 19:03:16 jeff-desktop NetworkManager[1054]: <info> (wlan1): device state change: ip-config -> activated (reason 'none') [70 100 0]
May  2 19:03:16 jeff-desktop NetworkManager[1054]: <info> DNS: starting dnsmasq...
May  2 19:03:16 jeff-desktop NetworkManager[1054]: <error> [1367546596.263942] [nm-dns-dnsmasq.c:390] update(): dnsmasq not available on the bus, can't update servers.
May  2 19:03:16 jeff-desktop NetworkManager[1054]: <error> [1367546596.264042] [nm-dns-dnsmasq.c:392] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
May  2 19:03:16 jeff-desktop NetworkManager[1054]: <warn> DNS: plugin dnsmasq update failed
May  2 19:03:16 jeff-desktop NetworkManager[1054]: <info> ((null)): writing resolv.conf to /sbin/resolvconf
May  2 19:03:16 jeff-desktop dnsmasq[2305]: started, version 2.63rc6 cache disabled
May  2 19:03:16 jeff-desktop dnsmasq[2305]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack
May  2 19:03:16 jeff-desktop dnsmasq[2305]: DBus support enabled: connected to system bus
May  2 19:03:16 jeff-desktop dnsmasq[2305]: warning: no upstream servers configured
May  2 19:03:16 jeff-desktop NetworkManager[1054]: <info> Policy set 'BirdsHouse' (wlan1) as default for IPv4 routing and DNS.
May  2 19:03:16 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) successful, device activated.
May  2 19:03:16 jeff-desktop NetworkManager[1054]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Commit) complete.
May  2 19:03:16 jeff-desktop dbus[999]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May  2 19:03:16 jeff-desktop NetworkManager[1054]: <warn> dnsmasq appeared on DBus: :1.71
May  2 19:03:16 jeff-desktop NetworkManager[1054]: <info> ((null)): writing resolv.conf to /sbin/resolvconf
May  2 19:03:16 jeff-desktop dnsmasq[2305]: setting upstream servers from DBus
May  2 19:03:16 jeff-desktop dnsmasq[2305]: using nameserver 8.8.4.4#53
May  2 19:03:16 jeff-desktop dnsmasq[2305]: using nameserver 8.8.8.8#53
May  2 19:03:16 jeff-desktop dbus[999]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May  2 19:03:26 jeff-desktop ntpdate[2420]: step time server 91.189.94.4 offset 1.095536 sec
```

---

