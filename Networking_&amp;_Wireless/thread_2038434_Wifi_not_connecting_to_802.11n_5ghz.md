---
title: "Wifi not connecting to 802.11n 5ghz"
date: 2012-08-06
forum: Networking &amp; Wireless
---

### Post by Ev1L on 2012-08-06
Hi,
although on Windows I connect to the 5ghz freq at 150mbps nominal, it does not work on linux.
I can see it with sudo iwlist scan, but don't know how to connect to it (plus it tells me 54mbps, is it right?).

Asus N51V
Ubuntu Precise 12.04
Intel 5100
Router Asus RT-N66U

```
lspci
03:00.0 Network controller: Intel Corporation WiFi Link 5100

```

```
iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"Kripo"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 10:BF:48:53:88:78   
          Bit Rate=72.2 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1791  Invalid misc:216   Missed beacon:0

```

```
lsmod |grep iwlwifi
iwlwifi               291847  0 
mac80211              436455  1 iwlwifi
cfg80211              178679  2 iwlwifi,mac80211

```

```
dmesg |grep iwlwifi
[   16.398549] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.398558] iwlwifi 0000:03:00.0: setting latency timer to 64
[   16.398578] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[   16.398580] iwlwifi 0000:03:00.0: pci_resource_base = f8454000
[   16.398582] iwlwifi 0000:03:00.0: HW Revision ID = 0x0
[   16.398664] iwlwifi 0000:03:00.0: irq 49 for MSI/MSI-X
[   16.398698] iwlwifi 0000:03:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   16.398754] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   16.420383] iwlwifi 0000:03:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   16.420385] iwlwifi 0000:03:00.0: Device SKU: 0Xf0
[   16.421352] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   16.823982] iwlwifi 0000:03:00.0: loaded firmware version 8.83.5.1 build 33692
[   18.671613] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   18.674609] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   18.793952] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   18.796944] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   32.123585] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = 10:bf:48:53:88:78 tid = 0
[  108.584215] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = 10:bf:48:53:88:78 tid = 6

```

```
lshw -C network
  *-network               
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:5d:c4:93:b4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-24-generic-pae-phc firmware=8.83.5.1 build 33692 ip=192.168.2.69 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:49 memory:fdffe000-fdffffff
```

```
sudo iwlist scan
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 10:BF:48:53:88:78
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"Kripo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000007a2fb183
                    Extra: Last beacon: 296ms ago
                    IE: Unknown: 00054B7269706F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFD191BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001F00000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180204F03C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:1A:2A:0E:71:D7
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"WLAN-0E7187"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000fdb4cdc7f
                    Extra: Last beacon: 4192ms ago
                    IE: Unknown: 000B574C414E2D304537313837
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030103
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:26:5A:37:CB:C3
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"Porsche"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001d38e92a33c
                    Extra: Last beacon: 4340ms ago
                    IE: Unknown: 0007506F7273636865
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F01010060FF7F
          Cell 04 - Address: 00:24:FE:04:DD:1C
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"WLAN-0024FE04DD1C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001648cbac1
                    Extra: Last beacon: 4056ms ago
                    IE: Unknown: 0011574C414E2D303032344645303444443143
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010A
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340A071900000000000000000000000000000000000000
                    IE: Unknown: 3D160A071900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: DD5B0050F204104A0001101044000102103B00010010470010000A000024FE04DD1C000024FE214BDE1021000341564D1023000341564D10240000104200001054000800000000000000001011000341564D100800020188103C000103
          Cell 05 - Address: 00:D0:DE:6B:77:27
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"ALICE-WLAN17"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f1975c397a
                    Extra: Last beacon: 4060ms ago
                    IE: Unknown: 000C414C4943452D574C414E3137
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 07064E4149010D14
                    IE: Unknown: 200100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010020FF7F
          Cell 06 - Address: 02:2B:BB:4C:C4:C8
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"HP4F1FD9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=000005719d7121d6
                    Extra: Last beacon: 4080ms ago
                    IE: Unknown: 00084850344631464439
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010A
                    IE: Unknown: 06020000
                    IE: Unknown: 0706455520010D14
          Cell 07 - Address: 10:BF:48:53:88:7C
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"Kripo"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000079f900b8
                    Extra: Last beacon: 3584ms ago
                    IE: Unknown: 00054B7269706F
                    IE: Unknown: 01088C129824B048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AFF091BFFFFFF0001000000000000000000000000000000000000
                    IE: Unknown: 3D16240D0000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F03C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

eth0      Interface doesn't support scanning.

```
without sudo i would see only cell 01

```
lsb_release -d
Description:	Ubuntu 12.04 LTS
```

```
uname -mr
3.2.0-24-generic-pae-phc i686
```

---

### Post by wildmanne39 on 2012-08-06
Hi, try this please:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
you will not get above 54 with this driver but unless you have a super fast connection it will not make any difference.
Thanks

---

### Post by Ev1L on 2012-08-06
> **wildmanne39 said:**
> Hi, try this please:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
you will not get above 54 with this driver but unless you have a super fast connection it will not make any difference.
Thanks

wouldn't this do the opposite, disabling 802.11n?
networking works fine except for the 5ghz.
normally is stable and fast enough at 2.4ghz (i have a 50mbit and i reach at least 4.5MBsec), but i thought i could squeeze more by using my laptop with 5ghz and leaving slower devices on the 2.4.

---

### Post by wildmanne39 on 2012-08-06
Hi, yes it will disable N speed with is usually needed for this driver with few exceptions, I misunderstood it looked from > I can see it with sudo iwlist scan, but don't know how to connect to it (plus it tells me 54mbps, is it right?).
That it was not connecting at all.

I am sorry I can not help with the speed issue.

---

### Post by Ev1L on 2012-08-06
thanks anyway, hopefully someone else will jump in :)

---

### Post by fbicknel on 2013-01-03
Same situation here, but with an Asus K53SV.  I have the same router (RT-N66U) - I really like this router.

The iDevices in the house connect to the 5GHz network just fine, so I know it's working.

My iwlist scan output is similar to yours in that it shows the 2.4 GHz connection (connections - the neighbors, too), but no 5GHz connection shows.  So you're one step ahead of me, there.  

Did you do anything interesting to get the 5GHz connection to show up?

If I were you, I would try messing around in Network Manager, manually inserting my 5GHz SSID (I've tried here).  But I imagine you've done that already.

```
fbicknel@brit-ubtu2:~$ lsb_release -d
Description:    Ubuntu 12.04.1 LTS
fbicknel@brit-ubtu2:~$ uname -mr
3.2.0-35-generic x86_6
```

---

