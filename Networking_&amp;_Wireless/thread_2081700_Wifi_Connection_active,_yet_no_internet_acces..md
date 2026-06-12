---
title: "Wifi Connection active, yet no internet acces."
date: 2012-11-07
forum: Networking &amp; Wireless
---

### Post by Sayiro on 2012-11-07
Updated with lots of info - 07-10-2012 22:51 (GMT+1)

Hello all,

I recently decided to update my 10.10 installation towards 12.04.1 and embrace the future with Unity. So far, good experience. Though, my WiFi is acting weird, even weirder than the topic title is suggesting.

Pre 12.04 my Wifi worked fine, and that hardware didn't change. 

Now it refuses to get data at all, or when it does it breaks down after a short period. I can connect to 3 different WiFi points here and only 1 works properly, a hotspot made on the first floor through a laptop. All other connections, the routers, will either work for 10 minutes and break down or not work at all even though they have a connection strength of roughly 70/80%. Yet no data is transmitted through these networks anymore.

I checked the routers and they are void of flaws or error's.  

Roaming the net I even found that it might have been a power management issue, edited the line, but alas. So far I have spent 2 days searching and trying for a solution, but I have to come to terms with it.

I would like to ask help.

Below some results of terminal:

```
eth0      Link encap:Ethernet  HWaddr 00:25:22:6f:6c:45  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5574 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5574 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:484664 (484.6 KB)  TX bytes:484664 (484.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0c:f6:43:9a:54  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f6ff:fe43:9a54/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:657484 errors:0 dropped:0 overruns:0 frame:0
          TX packets:370588 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:954880478 (954.8 MB)  TX bytes:35198310 (35.1 MB)

```[SIZE=1]^ All sent data is from HotSpot connection.[/SIZE]

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
``````
network-manager:
  Installed: 0.9.4.0-0ubuntu4.1
  Candidate: 0.9.4.0-0ubuntu4.1
  Version table:
 *** 0.9.4.0-0ubuntu4.1 0
        500 http://nl.archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
        100 /var/lib/dpkg/status
     0.9.4.0-0ubuntu3 0
        500 http://nl.archive.ubuntu.com/ubuntu/ precise/main i386 Packages
``````
; <<>> DiG 9.8.1-P1 <<>> google.com
;; global options: +cmd
;; connection timed out; no servers could be reached
``````
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

``````
  *-network               
       description: Wireless interface
       product: RT2800 802.11n PCI
       vendor: Ralink corp.
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: wlan0
       version: 00
       serial: 00:0c:f6:43:9a:54
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.2.0-32-generic-pae firmware=0.34 ip=192.168.0.101 latency=32 link=yes maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f7ff0000-f7ffffff

```Also added: Netinfo

```

*************** info trace ****************



**** uname -a ****


Linux vince-desktop 3.2.0-32-generic-pae #51-Ubuntu SMP Wed Sep 26 21:54:23 UTC 2012 i686 athlon i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"


**** lspci ****


00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Subsystem: ASRock Incorporation 939NF6G-VSTA Board [1849:03ef]
    Kernel driver in use: forcedeth
--
01:08.0 Network controller [0280]: Ralink corp. RT2800 802.11n PCI [1814:0601]
    Subsystem: SiteCom Europe BV Device [182d:0016]
    Kernel driver in use: rt2800pci


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 002 Device 003: ID 1bcf:0005 Sunplus Innovation Technology Inc. 


**** iwconfig ****


wlan0     IEEE 802.11bgn  ESSID:"ZiggoE9AD4"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=78 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:160  Invalid misc:47   Missed beacon:0



**** rfkill ****


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
rfcomm                 38139  12 
bnep                   17830  2 
snd_hda_codec_via      46138  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
ppdev                  12849  0 
snd_rawmidi            25424  1 snd_seq_midi
arc4                   12473  2 
snd_seq_midi_event     14475  1 snd_seq_midi
rt2800pci              18340  0 
rt2800lib              53264  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48836  3 rt2800pci,rt2800lib,rt2x00pci
serio_raw              13027  0 
k10temp                12990  0 
mac80211              436455  3 rt2800lib,rt2x00pci,rt2x00lib
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
cfg80211              178679  2 rt2x00lib,mac80211
usbhid                 41906  0 
hid                    77367  1 usbhid
btusb                  17912  2 
nouveau               712356  3 
snd_timer              28931  2 snd_pcm,snd_seq
eeprom_93cx6           12653  1 rt2800pci
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
bluetooth             158438  23 rfcomm,bnep,btusb
ttm                    65344  1 nouveau
drm_kms_helper         45466  1 nouveau
drm                   197599  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
wmi                    18744  1 mxm_wmi
video                  19068  1 nouveau
parport_pc             32114  1 
snd                    62064  15 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
pata_amd               13750  0 
forcedeth              58096  0 
sata_nv                23360  2 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [ZiggoE9AD4] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           78 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    PS3-1915822:     Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 74 WPA
    SitecomP:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WPA
    Hans Hoog:       Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Ziggo67A00:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA2
    SitecomC9AC08:   Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 66 WPA2
    *ZiggoE9AD4:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 53 WPA2

  IPv4 Settings:
    Address:         192.168.178.20
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.178.1

    DNS:             212.54.40.25
    DNS:             212.54.35.25




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
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"ZiggoE9AD4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000188b3922958
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 000A5A6967676F4539414434
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD6D0050F204104A0001101044000102103B000103104700104D73C5C27E6B5243D6440AAB1719670B102100045562656510230004556265651024000631323334353610420007303030303030311054000800060050F204000110110006556265654150100800020088103C000101
                    IE: Unknown: DD090010180202F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"SitecomC9AC08"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001872cca5ab
                    Extra: Last beacon: 1320ms ago
                    IE: Unknown: 000D53697465636F6D433941433038
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030105
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1605070700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020011127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3405070700000000000000000000000000000000000000
                    IE: Unknown: DDB10050F204104A0001101044000102103B000103104700102880288028801880A880000CF6C9AC081021001A53697465636F6D20546563686E6F6C6F676965732C20496E632E1023001A53697465636F6D20576972656C65737320415020526F7574657210240008574C522D343030301042000A313137333633343334201054000800060050F20400011011001953697465636F6D203830322E31316E20415020526F75746572100800020084103C000101
          Cell 03 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"PS3-1915822"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000e02aaea1c3
                    Extra: Last beacon: 1320ms ago
                    IE: Unknown: 000B5053332D31393135383232
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Ziggo67A00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000035725fa7e61
                    Extra: Last beacon: 1252ms ago
                    IE: Unknown: 000A5A6967676F3637413030
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD6D0050F204104A0001101044000102103B000103104700104D73C5C27E6B5243D6440AAB1719670B102100045562656510230004556265651024000631323334353610420007303030303030311054000800060050F204000110110006556265654150100800020088103C000101
                    IE: Unknown: DD090010180200F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Hans Hoog"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002cbdee0e17f
                    Extra: Last beacon: 836ms ago
                    IE: Unknown: 000948616E7320486F6F67
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E101EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1609050000000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD9E0050F204104A0001101044000102103B0001031047001063041253101920061228AABBCCDDEEFF1021001B5265616C74656B2053656D69636F6E647563746F7220436F72702E1023000752544C387878781024000D45562D323030392D30322D30361042000F3132333435363738393031323334371054000800060050F2040001101100135265616C74656B20576972656C657373204150100800020086
                    IE: Unknown: DD1E00904C336E101EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3409050000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
          Cell 06 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"SitecomP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b6be19caf4
                    Extra: Last beacon: 712ms ago
                    IE: Unknown: 000853697465636F6D50
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B070700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340B070700000000000000000000000000000000000000
                    IE: Unknown: DDAB0050F204104A0001101044000102103B000103104700102880288028801880A880000CF646146C1021001153697465636F6D204575726F70652042561023001F53697465636F6D20576972656C65737320415020526F75746572203330304E10240006574C2D3330331042000A303833323435353132201054000800060050F20400011011001953697465636F6D203830322E31316E20415020526F75746572100800020008103C000101



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1


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


[   13.842747] wmi: Mapper loaded
[   13.881186] rt2800pci 0000:01:08.0: PCI INT A -> Link[LNKA] -> GSI 18 (level, low) -> IRQ 18
[   13.906989] Registered led device: rt2800pci-phy0::radio
[   13.907004] Registered led device: rt2800pci-phy0::assoc
[   13.907017] Registered led device: rt2800pci-phy0::quality
[   14.896234] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
[   14.920430] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.920950] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.980090] wlan0: authenticate with <MAC address removed> (try 1)
[   17.981537] wlan0: authenticated
[   17.996082] wlan0: associate with <MAC address removed> (try 1)
[   18.001416] wlan0: RX AssocResp from <MAC address removed> (capab=0x831 status=0 aid=2)
[   18.001421] wlan0: associated
[   18.008328] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   23.555816] wlan0: deauthenticated from <MAC address removed> (Reason: 3)
[   24.812155] wlan0: authenticate with <MAC address removed> (try 1)
[   24.813527] wlan0: authenticated
[   24.813810] wlan0: associate with <MAC address removed> (try 1)
[   24.817366] wlan0: RX ReassocResp from <MAC address removed> (capab=0x831 status=0 aid=2)
[   24.817370] wlan0: associated
[   28.640038] wlan0: no IPv6 routers present
[   51.488119] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   52.888095] wlan0: authenticate with <MAC address removed> (try 1)
[   52.889710] wlan0: authenticated
[   52.904090] wlan0: associate with <MAC address removed> (try 1)
[   52.907147] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   52.907152] wlan0: associated
[   64.288025] wlan0: no IPv6 routers present


**************** done ********************


```

```
1:08.0 Network controller: Ralink corp. RT2800 802.11n PCI
    Subsystem: SiteCom Europe BV Device 0016
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (500ns min, 1000ns max), Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at f7ff0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rt2800pci
    Kernel modules: rt2800pci

```

---

### Post by Sayiro on 2012-11-09
Hate to repost, but help please?

---

### Post by Arcesius on 2012-11-18
Hey

I've had a similar problem and in my case the problem was that the wireless router was set to 802.11n mode, as also in your case (visible in one of the outputs). 
So maybe it would help if you enter the config site of your router and set 802.11n to off... 


Hope it helps.

---

