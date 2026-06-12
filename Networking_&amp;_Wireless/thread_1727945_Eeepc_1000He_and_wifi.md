---
title: "Eeepc 1000He and wifi"
date: 2011-04-13
forum: Networking &amp; Wireless
---

### Post by LeXav on 2011-04-13
hi !

I was enjoying my Eeepc 1000HE on Ubuntu 10.10, and wifi used to works fine. Then, I've upgraded to Natty (11.04) and troubles arrived.

The connection can't keep alive more than 10 minutes...sometimes less. After few connection up/connection down, the network manager ask me for WPA code.
When connection is up, speed is not very good. Sometimes surf is normal, many times is slow or impossible.
It's impossible to get connected to msn with Amsn or empathy. Amsn crashes after a while and empathy give me a message error.(But, network manager told me that connection is up...) 
Bit Rate goes from 1m to 54m, even if the pc is very close to wifi router. 

Please find below more informations :




```
~$ cat /etc/lsb-release

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu Natty (development branch)"
``````
:~$ uname -r -m

2.6.38-8-generic i686
``````
~$ cat  /etc/network/interfaces

auto lo
iface lo inet loopback
``````
:~$ ifconfig


eth0      Link encap:Ethernet  HWaddr 00:24:8c:88:0e:e5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:44 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:76 erreurs:0 :0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:5552 (5.5 KB) Octets transmis:5552 (5.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:43:6f:25:6b  
          inet adr:192.168.1.44  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::222:43ff:fe6f:256b/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:1510 erreurs:0 :0 overruns:0 frame:0
          TX packets:2069 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:679501 (679.5 KB) Octets transmis:361967 (361.9 KB)
``````
~$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"NEUF_8E4C"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:25:15:3B:8E:50   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:152  Invalid misc:33   Missed beacon:0
``````
~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
01:00.0 Network controller: Ralink corp. RT2860
03:00.0 Ethernet controller: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
xavier@petite-chose:~$ lspci -nn | grep -i net
01:00.0 Network controller [0280]: Ralink corp. RT2860 [1814:0781]
03:00.0 Ethernet controller [0200]: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
xavier@petite-chose:~$ sudo lshw -C network
[sudo] password for xavier: 
  *-network               
       description: Ethernet interface
       product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:24:8c:88:0e:e5
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:fbfc0000-fbffffff ioport:ec00(size=128)
  *-network
       description: Wireless interface
       product: RT2860
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:43:6f:25:6b
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-8-generic firmware=0.11 ip=192.168.1.44 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:fbef0000-fbefffff
``````
:~$ lsmod

Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255820  1 
rt2860sta             494649  0 
arc4                   12473  2 
snd_hda_intel          24140  3 
i915                  450944  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
rt2800pci              18159  0 
rt2800lib              43824  1 rt2800pci
joydev                 17322  0 
crc_ccitt              12595  2 rt2860sta,rt2800lib
rt2x00pci              13986  1 rt2800pci
rt2x00lib              39075  3 rt2800pci,rt2800lib,rt2x00pci
snd_seq_midi           13132  0 
mac80211              257001  3 rt2800lib,rt2x00pci,rt2x00lib
drm_kms_helper         40745  1 i915
drm                   180037  3 i915,drm_kms_helper
snd_rawmidi            25269  1 snd_seq_midi
uvcvideo               66851  0 
videodev               75143  1 uvcvideo
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73312  0 
snd                    55295  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              156212  2 rt2x00lib,mac80211
serio_raw              12990  0 
i2c_algo_bit           13184  1 i915
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
eeepc_laptop           19417  0 
video                  18951  1 i915
eeprom_93cx6           12653  1 rt2800pci
sparse_keymap          13666  1 eeepc_laptop
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
atl1e                  32576  0 
``````
~$ nm-tool


NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            ATL1E
  State:             unavailable
  Default:           no
  HW Address:        00:24:8C:88:0E:E5

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto NEUF_8E4C] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        00:22:43:6F:25:6B

  Capabilities:
    Speed:           18 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    FreeWifi:        Infra, DA:2D:B6:75:DA:22, Freq 2462 MHz, Rate 54 Mb/s, Strength 34
    freebox_Ralouk:  Infra, DA:2D:B6:75:DA:20, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA
    Wanadoo_eed5:    Infra, 00:16:41:03:80:F5, Freq 2457 MHz, Rate 54 Mb/s, Strength 28 WPA
    *NEUF_8E4C:      Infra, 00:25:15:3B:8E:50, Freq 2412 MHz, Rate 54 Mb/s, Strength 94 WPA
    SFR WiFi FON:    Infra, 02:25:15:3B:8E:52, Freq 2412 MHz, Rate 54 Mb/s, Strength 91
    Neuf WiFi FON:   Infra, 02:25:15:3B:8E:51, Freq 2412 MHz, Rate 54 Mb/s, Strength 91
    Livebox-CB24:    Infra, 00:18:E7:2F:33:F9, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA
    Livebox-473c:    Infra, 5C:33:8E:E8:95:EB, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.44
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

``````
~$ sudo iwlist scan


lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:25:15:3B:8E:50
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"NEUF_8E4C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000d050e299
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 00094E4555465F38453443
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 02:25:15:3B:8E:51
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:off
                    ESSID:"Neuf WiFi FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000d03a4bab
                    Extra: Last beacon: 1552ms ago
                    IE: Unknown: 000D4E657566205769466920464F4E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 02:25:15:3B:8E:52
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:off
                    ESSID:"SFR WiFi FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000d03a418c
                    Extra: Last beacon: 1556ms ago
                    IE: Unknown: 000C534652205769466920464F4E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: 5C:33:8E:E8:95:EB
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Livebox-473c"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003cc40638850
                    Extra: Last beacon: 1248ms ago
                    IE: Unknown: 000C4C697665626F782D34373363
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
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
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: DD880050F204104A000110104400010210570001001041000100103B00010310470010E8BE8128473CE8BE8128473C8128473C10210005536167656D102300084C697665626F7832102400084C697665626F78321042000A4C4B31303237334450331054000800060050F20400011011000D4C697665626F78322D3437334310080002000A103C000101


```

I could find this on logs  : 

```
Apr 11 19:31:30 petite-chose wpa_supplicant[867]: CTRL-EVENT-DISCONNECTED bssid=00:25:15:3b:8e:50 reason=0
Apr 11 19:31:31 petite-chose wpa_supplicant[867]: Trying to associate with 00:25:15:3b:8e:50 (SSID='NEUF_8E4C' freq=2462 MHz)
Apr 11 19:31:31 petite-chose wpa_supplicant[867]: Associated with 00:25:15:3b:8e:50
Apr 11 19:31:39 petite-chose wpa_supplicant[867]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Apr 11 19:31:42 petite-chose wpa_supplicant[867]: Trying to associate with 00:25:15:3b:8e:50 (SSID='NEUF_8E4C' freq=2462 MHz)
Apr 11 19:31:42 petite-chose wpa_supplicant[867]: Associated with 00:25:15:3b:8e:50
Apr 11 19:31:43 petite-chose wpa_supplicant[867]: WPA: Key negotiation completed with 00:25:15:3b:8e:50 [PTK=CCMP GTK=TKIP]
Apr 11 19:31:43 petite-chose wpa_supplicant[867]: CTRL-EVENT-CONNECTED - Connection to 00:25:15:3b:8e:50 completed (reauth) [id=0 id_str=]
Apr 11 19:33:16 petite-chose wpa_supplicant[867]: CTRL-EVENT-DISCONNECTED bssid=00:25:15:3b:8e:50 reason=0
Apr 11 19:33:17 petite-chose wpa_supplicant[867]: Trying to associate with 00:25:15:3b:8e:50 (SSID='NEUF_8E4C' freq=2462 MHz)
Apr 11 19:33:17 petite-chose wpa_supplicant[867]: Associated with 00:25:15:3b:8e:50
Apr 11 19:33:17 petite-chose wpa_supplicant[867]: WPA: Key negotiation completed with 00:25:15:3b:8e:50 [PTK=CCMP GTK=TKIP]
Apr 11 19:33:17 petite-chose wpa_supplicant[867]: CTRL-EVENT-CONNECTED - Connection to 00:25:15:3b:8e:50 completed (reauth) [id=0 id_str=]
Apr 11 19:34:16 petite-chose wpa_supplicant[867]: CTRL-EVENT-DISCONNECTED bssid=00:25:15:3b:8e:50 reason=0
Apr 11 19:34:17 petite-chose wpa_supplicant[867]: Trying to associate with 00:25:15:3b:8e:50 (SSID='NEUF_8E4C' freq=2462 MHz)
Apr 11 19:34:17 petite-chose wpa_supplicant[867]: Associated with 00:25:15:3b:8e:50
Apr 11 19:34:26 petite-chose wpa_supplicant[867]: CTRL-EVENT-DISCONNECTED bssid=00:25:15:3b:8e:50 reason=0
Apr 11 19:34:27 petite-chose wpa_supplicant[867]: Trying to associate with 00:25:15:3b:8e:50 (SSID='NEUF_8E4C' freq=2462 MHz)
Apr 11 19:34:27 petite-chose wpa_supplicant[867]: Associated with 00:25:15:3b:8e:50
Apr 11 19:34:31 petite-chose wpa_supplicant[867]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Apr 11 19:34:33 petite-chose wpa_supplicant[867]: Trying to associate with 00:25:15:3b:8e:50 (SSID='NEUF_8E4C' freq=2462 MHz)
Apr 11 19:34:35 petite-chose wpa_supplicant[867]: Associated with 00:25:15:3b:8e:50
Apr 11 19:34:43 petite-chose wpa_supplicant[867]: CTRL-EVENT-DISCONNECTED bssid=00:25:15:3b:8e:50 reason=0
Apr 11 19:34:44 petite-chose wpa_supplicant[867]: Trying to associate with 00:25:15:3b:8e:50 (SSID='NEUF_8E4C' freq=2462 MHz)
Apr 11 19:34:44 petite-chose wpa_supplicant[867]: Associated with 00:25:15:3b:8e:50
Apr 11 19:34:53 petite-chose wpa_supplicant[867]: CTRL-EVENT-DISCONNECTED bssid=00:25:15:3b:8e:50 reason=0
Apr 11 19:34:54 petite-chose wpa_supplicant[867]: Trying to associate with 00:25:15:3b:8e:50 (SSID='NEUF_8E4C' freq=2462 MHz)
Apr 11 19:34:54 petite-chose wpa_supplicant[867]: Associated with 00:25:15:3b:8e:50
Apr 11 19:35:03 petite-chose wpa_supplicant[867]: CTRL-EVENT-DISCONNECTED bssid=00:25:15:3b:8e:50 reason=0
Apr 11 19:35:04 petite-chose wpa_supplicant[867]: Trying to associate with 00:25:15:3b:8e:50 (SSID='NEUF_8E4C' freq=2462 MHz)
Apr 11 19:35:04 petite-chose wpa_supplicant[867]: Associated with 00:25:15:3b:8e:50
Apr 11 19:35:13 petite-chose wpa_supplicant[867]: CTRL-EVENT-DISCONNECTED bssid=00:25:15:3b:8e:50 reason=0
Apr 11 19:35:14 petite-chose wpa_supplicant[867]: Trying to associate with 00:25:15:3b:8e:50 (SSID='NEUF_8E4C' freq=2462 MHz)
Apr 11 19:35:14 petite-chose wpa_supplicant[867]: Associated with 00:25:15:3b:8e:50
Apr 11 19:35:23 petite-chose wpa_supplicant[867]: CTRL-EVENT-DISCONNECTED bssid=00:25:15:3b:8e:50 reason=0
Apr 11 19:35:24 petite-chose wpa_supplicant[867]: Trying to associate with 00:25:15:3b:8e:50 (SSID='NEUF_8E4C' freq=2462 MHz)
Apr 11 19:35:24 petite-chose wpa_supplicant[867]: Associated with 00:25:15:3b:8e:50
Apr 11 19:35:24 petite-chose wpa_supplicant[867]: WPA: Key negotiation completed with 00:25:15:3b:8e:50 [PTK=CCMP GTK=TKIP]
Apr 11 19:35:24 petite-chose wpa_supplicant[867]: CTRL-EVENT-CONNECTED - Connection to 00:25:15:3b:8e:50 completed (reauth) [id=0 id_str=]
Apr 11 19:36:16 petite-chose wpa_supplicant[867]: CTRL-EVENT-DISCONNECTED bssid=00:25:15:3b:8e:50 reason=0
Apr 11 19:36:17 petite-chose wpa_supplicant[867]: Trying to associate with 00:25:15:3b:8e:50 (SSID='NEUF_8E4C' freq=2462 MHz)
Apr 11 19:36:17 petite-chose wpa_supplicant[867]: Associated with 00:25:15:3b:8e:50

```some  'connected' and then  'disconnected'....  Strange, no ? 

The same there  :

```
Apr 11 19:35:03 petite-chose kernel: [  591.992001] wlan0: deauthenticated from 00:25:15:3b:8e:50 (Reason: 7)
Apr 11 19:35:03 petite-chose NetworkManager[709]: <info> (wlan0): supplicant connection state:  associated -> disconnected
Apr 11 19:35:03 petite-chose NetworkManager[709]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 11 19:35:04 petite-chose NetworkManager[709]: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr 11 19:35:04 petite-chose kernel: [  593.248839] wlan0: authenticate with 00:25:15:3b:8e:50 (try 1)
Apr 11 19:35:04 petite-chose kernel: [  593.250446] wlan0: authenticated
Apr 11 19:35:04 petite-chose kernel: [  593.251104] wlan0: associate with 00:25:15:3b:8e:50 (try 1)
Apr 11 19:35:04 petite-chose kernel: [  593.253415] wlan0: RX AssocResp from 00:25:15:3b:8e:50 (capab=0x411 status=0 aid=1)
Apr 11 19:35:04 petite-chose kernel: [  593.253427] wlan0: associated
Apr 11 19:35:04 petite-chose NetworkManager[709]: <info> (wlan0): supplicant connection state:  associating -> associated
Apr 11 19:35:13 petite-chose kernel: [  601.992125] wlan0: deauthenticated from 00:25:15:3b:8e:50 (Reason: 7)
Apr 11 19:35:13 petite-chose NetworkManager[709]: <info> (wlan0): supplicant connection state:  associated -> disconnected
Apr 11 19:35:13 petite-chose NetworkManager[709]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 11 19:35:14 petite-chose NetworkManager[709]: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr 11 19:35:14 petite-chose kernel: [  603.237769] wlan0: authenticate with 00:25:15:3b:8e:50 (try 1)
Apr 11 19:35:14 petite-chose kernel: [  603.242384] wlan0: authenticated
Apr 11 19:35:14 petite-chose kernel: [  603.243077] wlan0: associate with 00:25:15:3b:8e:50 (try 1)
Apr 11 19:35:14 petite-chose kernel: [  603.245425] wlan0: RX AssocResp from 00:25:15:3b:8e:50 (capab=0x411 status=0 aid=1)
Apr 11 19:35:14 petite-chose kernel: [  603.245443] wlan0: associated
Apr 11 19:35:14 petite-chose NetworkManager[709]: <info> (wlan0): supplicant connection state:  associating -> associated
Apr 11 19:35:18 petite-chose NetworkManager[709]: <warn> (wlan0): link timed out.
Apr 11 19:35:23 petite-chose kernel: [  611.992042] wlan0: deauthenticated from 00:25:15:3b:8e:50 (Reason: 7)
Apr 11 19:35:23 petite-chose NetworkManager[709]: <info> (wlan0): supplicant connection state:  associated -> disconnected
Apr 11 19:35:23 petite-chose NetworkManager[709]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 11 19:35:24 petite-chose NetworkManager[709]: <info> (wlan0): supplicant connection state:  scanning -> associating

```Et voila !  Someone could help me ?
thanks.
Xavier.

---

### Post by chili555 on 2011-04-13
> lsmod

Module                  Size  Used by
--- snip ---
rt2860sta             494649  0 
--- snip ---
rt2800pci              18159  0 
rt2800lib              43824  1 rt2800pci
--- snip ---
crc_ccitt              12595  2 rt2860sta,rt2800lib
rt2x00pci              13986  1 rt2800pci
rt2x00lib              39075  3 rt2800pci,rt2800lib,rt2x00pci
--- snip ---
mac80211              257001  3 rt2800lib,rt2x00pci,rt2x00lib
--- snip ---
cfg80211              156212  2 rt2x00lib,mac80211
--- snip ---Man! That's a lot of drivers for just one little wireless card. Let's blacklist a few:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines at the end:```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Substitute kate or vim or whatever text editor xubuntu 11.04 uses.

Reboot and let us have your report.

---

### Post by LeXav on 2011-04-13
Hi !

Thanks for your help. I've tried 

blacklist rt2860sta

since ths morning and things are better. 
I'm going to change and test your solution.

Thanks !

---

### Post by LeXav on 2011-04-13
> **chili555 said:**
> Man! That's a lot of drivers for just one little wireless card. Let's blacklist a few:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines at the end:```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Substitute kate or vim or whatever text editor xubuntu 11.04 uses.

Reboot and let us have your report.

I changed blacklist.conf as you said and that's all right now !
Thanks again.

Wireless connection works well and fast.

---

### Post by tanaka.jk on 2011-05-01
> **chili555 said:**
> Man! That's a lot of drivers for just one little wireless card. Let's blacklist a few:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines at the end:```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Substitute kate or vim or whatever text editor xubuntu 11.04 uses.

Reboot and let us have your report.

The same solution solved my problem with Asus eeepc 1000H

---

### Post by ntalabertzis on 2011-05-02
> **tanaka.jk said:**
> The same solution solved my problem with Asus eeepc 1000H

i have the same problem with asus eeepc 1000H but i can't solve the problem.
i have rt2700e wifi card, any idea?

---

### Post by ryza on 2011-05-14
this worked for me on 1000he

thank you

---

### Post by kevh on 2011-05-27
Worked for the sony vaio vpcm13m1e.
Thanks
:D

---

### Post by polarisinc on 2011-06-22
Can confirm this fixed the issue on my eee pc 1000H running Ubuntu 11.04. Cheers.

---

