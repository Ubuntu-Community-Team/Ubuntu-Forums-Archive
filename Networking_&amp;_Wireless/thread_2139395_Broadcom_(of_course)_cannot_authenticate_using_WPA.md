---
title: "Broadcom (of course) cannot authenticate using WPA2 Personal"
date: 2013-04-26
forum: Networking &amp; Wireless
---

### Post by too_tall on 2013-04-26
Hi all.

Feeling a little silly because I cannot suss this out.  That means I am really missing something (probably basic) and great minds will point me in the right direction.

I just installed 13.04 on my laptop.  I see all the appropriate SSIDs around so the card is at least listening.  I can connect to unsecured wireless APs.  I cannot connect to my AP Using WPA WAP2 Personal.

Here's what I know about my machine:

HP G72 laptop

```
lspci | grep Network
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

iwconfig
eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"dewireless-guest"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 48:F8:B3:11:68:AF   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

sudo lshw -C network
[sudo] password for tim: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 68:b5:99:5c:df:96
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:40 ioport:2000(size=256) memory:b0410000-b0410fff memory:b0400000-b040ffff memory:b0420000-b043ffff
  *-network
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: c0:cb:38:2a:0e:6a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) ip=192.168.33.105 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:18 memory:b2400000-b2403fff

rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

So clearly there is a lot I don't know.  But googling this has led to minor variations of the same commmnd sets.  And none have made any difference.  

Can one of you big-brained people help me?

Thanks,

Tim

---

### Post by praseodym on 2013-04-26
Disable the driver, then uninstall it and install the firmware for the native driver:
```

sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
wget http://media.cdn.ubuntu-de.org/forum/attachments/39/45/5007272-Broadcom_Firmware_fae7121.tar.gz
sudo tar xvf 5007272-Broadcom_Firmware_fae7121.tar.gz -C /lib/firmware 
```
Reboot

---

### Post by too_tall on 2013-04-26
Thanks for the reply.  Unfortunately that made no difference.  I do see that it is now using a different driver  (driver=brcmsmac) but other than that it is the same issue.

---

### Post by praseodym on 2013-04-26
Now check
```

iwconfig
lsmod
sudo iwlist scan
rfkill list
dmesg | egrep 'bcma|brcm'
```

---

### Post by ahallubuntu on 2013-04-26
~

---

### Post by too_tall on 2013-04-26
Changing the router to WPA2 Personal and no longer on mixed mode made no difference.

Here is the newest output:

```
sudo iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"dewireless-guest"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 48:F8:B3:11:68:AF   
          Bit Rate=1 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:52   Missed beacon:0

lsmod | grep brc
brcmsmac              550698  0 
cordic                 12574  1 brcmsmac
brcmutil               14755  1 brcmsmac
mac80211              606457  1 brcmsmac
cfg80211              510937  2 brcmsmac,mac80211
bcma                   41051  1 brcmsmac

 sudo iwlist scan
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 48:F8:B3:11:68:AF
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:off
                    ESSID:"dewireless-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000014cdc178
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 00106465776972656C6573732D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001300000000000000000000000000000000000000
                    IE: Unknown: DD090010180202F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:1B:2F:0E:E3:A0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"mertz household"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000010c7a8e1964
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 000F6D6572747A20686F757365686F6C64
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD0900037F0101000CFF7F
                    IE: Unknown: DD0C00037F020101000002A34000
                    IE: Unknown: DD1A00037F0301000000001B2F0EE3A0021B2F0EE3A064002C010C08
          Cell 03 - Address: C4:3D:C7:85:08:AE
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"MERTZ2708"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b0269a3b49
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 00094D4552545A32373038
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
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
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402080800000000000000000000000000000000000000
                    IE: Unknown: 3D1602080800000000000000000000000000000000000000
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD7F0050F204104A0001101044000102103B0001031047001000000000000010000000C43DC78508AE102100044E54475210230009776E72323030307633102400016E104200046E6F6E651054000800060050F20400011011001B574E5232303030763328576972656C6573732041502D322E344729100800020086103C000103
          Cell 04 - Address: 20:AA:4B:BB:93:F1
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"sabotnet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000029fd570f7e4
                    Extra: Last beacon: 1076ms ago
                    IE: Unknown: 00087361626F746E6574
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
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD270050F204104A000110104400010210470010FAF2B34D3DD060CE961542B3C2F3910C103C000103
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: 48:F8:B3:11:68:AD
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-33 dBm  
                    Encryption key:on
                    ESSID:"dewireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000014cdb43e
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 000A6465776972656C657373
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001300000000000000000000000000000000000000
                    IE: Unknown: DD840050F204104A0001101044000102103B000103104700101ABF97A133A41CE18BB7C0CC111B017610210005436973636F1023000D4C696E6B7379732045323530301024000776312E302E30371042000234321054000800060050F20400011011000D4C696E6B737973204532353030100800022688103C0001031049000600372A000120
                    IE: Unknown: DD090010180202F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: 00:1F:33:C8:59:0C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f81fec0183
                    Extra: Last beacon: 552ms ago
                    IE: Unknown: 00074E455447454152
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: 00:1D:7E:FE:52:A2
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"CFS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000009509e74e31d
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 0003434653
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020015000000
          Cell 08 - Address: B2:B2:DC:8F:4D:34
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"CenturyLink3303"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a5c0aa815c
                    Extra: Last beacon: 692ms ago
                    IE: Unknown: 000F43656E747572794C696E6B33333033
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030108
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD310050F204104A000110104400010210470010BC329E001DD811B28601B2B2DC8F4D34103C0001011049000600372A000120
                    IE: Unknown: 050400010000
                    IE: Unknown: DD310050F204104A000110104400010210470010BC329E001DD811B28601B2B2DC8F4D34103C0001011049000600372A000120
                    IE: Unknown: DD050050F20500
                    IE: Unknown: 2A0104
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020016127A
                    IE: Unknown: DD07000C4300000000
          Cell 09 - Address: 00:18:39:D7:2F:C8
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"boeshans"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000984c2c2436
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 0008626F657368616E73
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32048C129860
                    IE: Unknown: DD09001018020014000000
          Cell 10 - Address: 00:19:7E:73:CC:E2
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"a76e"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000068aa3d15f9
                    Extra: Last beacon: 628ms ago
                    IE: Unknown: 000461373665
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020200
          Cell 11 - Address: 00:1C:10:C8:53:5A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"linksys007"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002c8cbc8185
                    Extra: Last beacon: 496ms ago
                    IE: Unknown: 000A6C696E6B737973303037
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F4000000
          Cell 12 - Address: 00:00:00:00:00:00
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b7a38c425d
                    Extra: Last beacon: 224ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 050C020300000000000000000000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 13 - Address: 00:1E:2A:4F:58:3E
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009f6388b1e9
                    Extra: Last beacon: 352ms ago
                    IE: Unknown: 00074E455447454152
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 14 - Address: E8:40:F2:E6:50:95
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"11ea45"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000043c3913f198
                    Extra: Last beacon: 340ms ago
                    IE: Unknown: 0006313165613435
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
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 15 - Address: 00:24:7B:B9:0E:B0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"myqwest7919"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b7a38ab248
                    Extra: Last beacon: 304ms ago
                    IE: Unknown: 000B6D79717765737437393139
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 050C000300000000000000000000
                    IE: Unknown: 2A0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

 rfkill list
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

dmesg | egrep 'bcma|brcm'
[    9.126216] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[    9.126262] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[    9.126300] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[    9.126376] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[    9.139419] bcma: bus0: Bus registered
[   10.179173] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 18
[   12.571511] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   12.571573] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   14.382879] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   14.382884] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[   14.382887] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   14.459850] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[  169.036549] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  169.044077] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  169.044092] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[  169.044098] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  170.037480] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  170.037485] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  170.037488] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  217.852121] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  217.852133] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[  217.852136] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  221.507847] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  221.507852] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  221.507855] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  221.569682] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[  473.460798] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  473.467960] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  473.467976] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[  473.467982] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  474.421904] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  474.421909] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  474.421912] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  482.892507] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  482.892519] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[  482.892522] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  483.770436] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  483.770441] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  483.770444] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  532.163372] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  532.163384] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[  532.163386] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  538.032651] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  538.032657] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  538.032659] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  538.099504] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[ 2016.273553] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2016.273568] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[ 2016.273573] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2017.243686] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2017.243696] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[ 2017.243702] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 8234.517946] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 8234.517961] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[ 8234.517967] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 8241.368051] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 8241.368057] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[ 8241.368059] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 8258.860071] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[ 8258.871295] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 8258.871310] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[ 8258.871316] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 8259.848501] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 8259.848507] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[ 8259.848509] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 8307.770400] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 8307.770411] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[ 8307.770413] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 8311.429545] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 8311.429555] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[ 8311.429560] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 8311.490049] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
```

I left all the APs found just in case something there might trigger a thought.

Thank you again for your help!  I'll owe you a beer if we can figure this out!

---

### Post by too_tall on 2013-04-26
More confused by the moment.

I have set my router to WPA2 Personal and back to Mixed mode.  I have made no further changes to the config of Ubuntu.  I have simply retried connecting to the dewireless AP several more times.  

It finally connected?  How the heck?  I was taught to never question success, but success for no earthly reason worries me.

---

### Post by ahallubuntu on 2013-04-26
~

---

### Post by lx3r on 2013-04-27
tried it.
signal is extremely weak. 
doesnt work.

---

### Post by praseodym on 2013-04-27
There are a lot of networks around, try a fixed channel.

---

### Post by too_tall on 2013-04-27
Thank you all fro your help and input.  I did change AES to TKIP and back again at the same time as I went mixed mode to WPA2 and back...Something triggered the fix.  In any case I will try to lock me wireless channel down.  It is a very chatty neighborhood.

Thanks again.

---

### Post by Neo Dagger on 2013-04-27
brilliant, praseodym, I had the same issue and followed your instructions. Thanks for the posts, I have my wi-fi back online as well!

---

