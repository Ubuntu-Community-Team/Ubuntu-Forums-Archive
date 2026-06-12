---
title: "WPA/Wifi problem under 11.10 and Intel Pro"
date: 2011-10-17
forum: Networking &amp; Wireless
---

### Post by sioban on 2011-10-17
Hello,

Since I've upgraded my laptop to Ubuntu 11.10, I have problems connecting to my Wifi.
The main problem was that Network manager keeping asking password. This has been solved by removing and recreating the entry in NM.

But in fact it's the Wifi connection which is unstable on my laptop since 11.10, I loose connection them it reconnects.

I have a Intel Pro 3945ABG (iwl3945 module).

I've tried disabling disable_hw_scan with no success :
```
rmmod iwl3945
modprobe iwl3945 disable_hw_scan=1
```I've also tried fresher drivers (compat-wireless-3.1-rc8-1) but it's still the same.

The only thing that change things is if I switch on a cleartext channel without WPA/WPA2.
So it's maybe a WPA problem however it was working perfectly under 11.04

Can you help ?

Below, you'll find some info on my config :

* lspci
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

```* lsmod
```
Module                  Size  Used by
des_generic            21191  0
md4                    12523  0
bnep                   17923  2
rfcomm                 38408  0
bluetooth             148839  10 bnep,rfcomm
autofs4                27924  0
parport_pc             32114  0
ppdev                  12849  0
vesafb                 13489  1
nls_utf8               12493  7
cifs                  248817  6
binfmt_misc            17292  1
joydev                 17393  0
nvidia               7098131  35
snd_hda_codec_si3054    12864  1
snd_hda_codec_realtek   254125  1
snd_hda_intel          24262  5
snd_hda_codec          91754  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  5 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
pcmcia                 39822  0
snd_seq_midi           13132  0
video                  18908  0
tifm_7xx1              12937  0
arc4                   12473  2
tifm_core              15040  1 tifm_7xx1
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  18 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwl3945                73329  0
sparse_keymap          13658  0
iwl_legacy             71499  1 iwl3945
mac80211              272785  2 iwl3945,iwl_legacy
yenta_socket           27428  0
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
cfg80211              172392  3 iwl3945,iwl_legacy,mac80211
soundcore              12600  1 snd
psmouse                73673  0
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
serio_raw              12990  0
lp                     17455  0
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
e100                   36289  0
sdhci_pci              13658  0
sdhci                  27360  1 sdhci_pci

```* rfkill list 
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```* dmesg | grep iwl
```
[   22.000734] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   22.000739] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   22.000834] iwl3945 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   22.000855] iwl3945 0000:05:00.0: setting latency timer to 64
[   22.060080] iwl3945 0000:05:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   22.060085] iwl3945 0000:05:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   22.060247] iwl3945 0000:05:00.0: irq 44 for MSI/MSI-X
[   22.119995] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   24.201283] iwl3945 0000:05:00.0: loaded firmware version 15.32.2.9

```* iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"landes" 
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:21:1B:E8:28:30  
          Bit Rate=54 Mb/s   Tx-Power=15 dBm  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:68   Missed beacon:0
```* cat /etc/lsb-release
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
```* lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```* lspci -nn | grep -i net
```
05:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
07:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 02)
```* lshw -C network
```
  *-network              
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 02
       serial: 00:19:d2:4b:32:9d
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=3.0.0-12-generic firmware=15.32.2.9 ip=10.10.10.22 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:44 memory:f0800000-f0800fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:07:08.0
       logical name: eth0
       version: 02
       serial: 00:a0:d1:68:d7:92
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=10.10.10.38 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:f0905000-f0905fff ioport:4000(size=64)
```* ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:68:d7:92 
          inet adr:10.10.10.38  Bcast:10.10.10.255  Masque:255.255.255.0
          adr inet6: fe80::2a0:d1ff:fe68:d792/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:77286 erreurs:0 :0 overruns:0 frame:0
          TX packets:72582 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:79600273 (79.6 MB) Octets transmis:52220085 (52.2 MB)

lo        Link encap:Boucle locale 
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:4684 erreurs:0 :0 overruns:0 frame:0
          TX packets:4684 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          Octets reçus:373390 (373.3 KB) Octets transmis:373390 (373.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:4b:32:9d 
          inet adr:10.10.10.22  Bcast:10.10.10.255  Masque:255.255.255.0
          adr inet6: fe80::219:d2ff:fe4b:329d/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:25161 erreurs:0 :0 overruns:0 frame:0
          TX packets:32520 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:5828625 (5.8 MB) Octets transmis:34806529 (34.8 MB)
```* iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:21:1B:E8:28:30
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm 
                    Encryption key:on
                    ESSID:"landes"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000012e50afe1be
                    Extra: Last beacon: 84ms ago
                    IE: Unknown: 00066C616E646573
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD06004096010100
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
                    IE: Unknown: DD180050F2020101810003A4000027A400004243BC0062326600
          Cell 02 - Address: EA:75:6A:DC:37:55
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=32/70  Signal level=-78 dBm 
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000011eeec5ea7c
                    Extra: Last beacon: 5628ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030105
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1605050000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000017127A
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3405050000000000000000000000000000000000000000
                    IE: Unknown: DD07000C4300000000
          Cell 03 - Address: EA:75:6A:DC:37:57
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=32/70  Signal level=-78 dBm 
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000011eeec5fc7f
                    Extra: Last beacon: 5624ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030105
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1605050000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000017127A
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3405050000000000000000000000000000000000000000
                    IE: Unknown: DD07000C4300000000
          Cell 04 - Address: EA:75:6A:DC:37:54
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=33/70  Signal level=-77 dBm 
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000011eeec5e142
                    Extra: Last beacon: 5628ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030105
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1605050000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000017127A
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3405050000000000000000000000000000000000000000
                    IE: Unknown: DD07000C4300000000
          Cell 05 - Address: EA:75:6A:DC:37:56
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=32/70  Signal level=-78 dBm 
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000011eeec5f3b5
                    Extra: Last beacon: 5624ms ago
                    IE: Unknown: 00084672656557696669
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030105
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1605050000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3405050000000000000000000000000000000000000000
          Cell 06 - Address: 00:1D:6A:9A:49:5B
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm 
                    Encryption key:on
                    ESSID:"Livebox-A988"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005baa24d181
                    Extra: Last beacon: 5040ms ago
                    IE: Unknown: 000C4C697665626F782D41393838
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201018A0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
```* uname -r -m
```
3.0.0-12-generic i686
```* cat  /etc/network/interfaces
```
auto lo
iface lo inet loopback
```* nm-tool
```
NetworkManager Tool

State: connected (global)

- Device: wlan0  [Auto landes] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             connected
  Default:           no
  HW Address:        00:19:D2:4B:32:9D

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *landes:         Infra, 00:21:1B:E8:28:30, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA2
    FreeWifi:        Infra, EA:75:6A:DC:37:56, Freq 2432 MHz, Rate 54 Mb/s, Strength 27
    Livebox-A988:    Infra, 00:1D:6A:9A:49:5B, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA
    Livebox-1585:    Infra, 00:21:86:43:59:D4, Freq 2457 MHz, Rate 54 Mb/s, Strength 14 WPA

  IPv4 Settings:
    Address:         10.10.10.22
    Prefix:          24 (255.255.255.0)
    Gateway:         10.10.10.254

    DNS:             10.10.12.1
    DNS:             212.27.40.240


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connected
  Default:           yes
  HW Address:        00:A0:D1:68:D7:92

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.10.10.38
    Prefix:          24 (255.255.255.0)
    Gateway:         10.10.10.254

    DNS:             10.10.12.1
    DNS:             212.27.40.240
```

---

### Post by sioban on 2011-10-18
No one ?

---

### Post by Crunchiness on 2011-10-20
Same problem here :/

---

### Post by Duncan J Murray on 2011-10-20
Exact same problem with Intel 3945 on a Dell Precision M2300 running Ubuntu 11.10 via the live CD.

It will recognise networks, but cannot connect via WPA2 - it will just keep requesting the password.  It seems to connect via ethernet without a problem.

Oddly, the exact same problem occurs in Fedora 15 after a recent update (which is why I was looking into whether 11.10 would work).

Duncan

---

### Post by Bernie53 on 2011-10-20
Hello,

I was having the same problem. I started to play around and found that the password for my wifi was not set. I guess it was lost in the upgrade. It is important to note that I did not change any driver or settings of the default upgrade installation.

I did the following steps:

1. Go to the Dash home (the first button of the left bar with the Ubuntu symbol)
2. Type the word **net** in the search box
3. Click on **network connections**
4. Go to the **wireless** tab
5. Click on the name of your home wifi and then click on edit
5. Go to the **wireless security** tab, set your password and save it
6. Go to the Dash home again
7. Type the word **net** again
8. Click on** network**
9. Click on **wireless** and select your home wifi from the list

This is how I got it to work for me.

Regards

---

### Post by sioban on 2011-10-21
@bernie53 : didn't miss that point, I even had to delete my wifi from Network Monitor to make him stop asking password. But the wifi still disconnect after a while and so on. I've replaced NM with WICD and now, the wifi connection is stable.

---

### Post by Duncan J Murray on 2011-10-22
I am a moron!  I came this close to reinstalling a totally different operating system, when actually, I was using a password for another wifi network, and had somewhat forgotten I'd not changed this one yet.  Doh!

D

---

### Post by hero1900 on 2011-10-30
i have same issue too i tried everything on the net i even downgrade the kernel to the natty one also not working
the only thing i have to do is to shift back to 11.04 and thats what i gona do
each new version of ubuntu keep getting worse and worse i like my ugly ubuntu which really works, its better than shiny and pretty which not work

---

### Post by wildmanne39 on 2011-10-30
Hi sioban, have a look at this it may help.
[http://ubuntuforums.org/showthread.php?t=1865420&page=2](http://ubuntuforums.org/showthread.php?t=1865420&page=2)
Post 12 and
[http://ubuntuforums.org/showthread.php?t=1859558&page=3](http://ubuntuforums.org/showthread.php?t=1859558&page=3)
Post 21.
Thank you

---

