---
title: "Unsecured Wireless"
date: 2011-08-04
forum: Networking &amp; Wireless
---

### Post by Bothorth on 2011-08-04
I'm trying to connect to a wireless network with Ubuntu Desktop 11.04, recently installed in a partition alongside Windows XP on an old laptop (Toshiba Satellite A10 ~ 8 yrs old).

On starting Ubuntu, or whenever I clock on a network name, the icon shows flashing arcs for about 30s and scans reveals:

```

bothorth@Bothorth:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0B:86:24:88:B4
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"Guest@LC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000000514fa24219
                    Extra: Last beacon: 360ms ago
                    IE: Unknown: 00084775657374404C43
                    IE: Unknown: 010482840B16
                    IE: Unknown: 030101
                    IE: Unknown: 2A0107
                    IE: Unknown: DD0A00037F04010000000000
          Cell 02 - Address: 00:0B:86:27:8C:04
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:off
                    ESSID:"Guest@LC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000044ca0f23c73
                    Extra: Last beacon: 328ms ago
                    IE: Unknown: 00084775657374404C43
                    IE: Unknown: 010482840B16
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: DD0A00037F04010000000000
          Cell 03 - Address: 00:0B:86:27:90:B4
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"Guest@LC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000001e384420a95
                    Extra: Last beacon: 5520ms ago
                    IE: Unknown: 00084775657374404C43
                    IE: Unknown: 010482840B16
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: DD0A00037F04010000000000
          Cell 04 - Address: 00:0B:86:24:88:B1
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"LCWireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000000514fa236ff
                    Extra: Last beacon: 360ms ago
                    IE: Unknown: 000A4C43576972656C657373
                    IE: Unknown: 010482840B16
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD0A00037F04010000000000
          Cell 05 - Address: 00:0B:86:24:88:B2
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"LCC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000000514fa23c5f
                    Extra: Last beacon: 360ms ago
                    IE: Unknown: 00034C4343
                    IE: Unknown: 010482840B16
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: Unknown: DD0A00037F04010000000000
          Cell 06 - Address: 00:0B:86:27:8C:01
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"LCWireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000044ca0f232e6
                    Extra: Last beacon: 328ms ago
                    IE: Unknown: 000A4C43576972656C657373
                    IE: Unknown: 010482840B16
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD0A00037F04010000000000
          Cell 07 - Address: 00:0B:86:27:8C:02
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"LCC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000044ca0f23830
                    Extra: Last beacon: 328ms ago
                    IE: Unknown: 00034C4343
                    IE: Unknown: 010482840B16
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: DD0A00037F04010000000000

```and

```

bothorth@Bothorth:~$ nm-tool

NetworkManager Tool

State: connecting

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             unavailable
  Default:           no
  HW Address:        00:00:39:77:B8:D5

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: eth1  [Auto Guest@LC] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            orinoco_cs
  State:             connecting (configuring)
  Default:           no
  HW Address:        00:02:2D:7E:55:B3

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes

  Wireless Access Points 
    Guest@LC:        Infra, 00:0B:86:27:90:B4, Freq 2462 MHz, Rate 11 Mb/s, Strength 31
    Guest@LC:        Infra, 00:0B:86:24:88:B4, Freq 2412 MHz, Rate 11 Mb/s, Strength 41
    Guest@LC:        Infra, 00:0B:86:27:8C:04, Freq 2437 MHz, Rate 11 Mb/s, Strength 54
    LCC:             Infra, 00:0B:86:27:90:B2, Freq 2462 MHz, Rate 11 Mb/s, Strength 30 WEP
    LCC:             Infra, 00:0B:86:27:8C:02, Freq 2437 MHz, Rate 11 Mb/s, Strength 52 WEP
    LCC:             Infra, 00:0B:86:24:88:B2, Freq 2412 MHz, Rate 11 Mb/s, Strength 52 WEP
    LCWireless:      Infra, 00:0B:86:27:90:B1, Freq 2462 MHz, Rate 11 Mb/s, Strength 30 WPA2 Enterprise
    LCWireless:      Infra, 00:0B:86:24:88:B1, Freq 2412 MHz, Rate 11 Mb/s, Strength 41 WPA2 Enterprise
    LCWireless:      Infra, 00:0B:86:27:8C:01, Freq 2437 MHz, Rate 11 Mb/s, Strength 54 WPA2 Enterprise

```After a while, the connection gives up and the arcs go black. The same scans give:

```

bothorth@Bothorth:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

```and nm-tool results just change to disconnected. 

The ESSIDs "Guest@LC", "LCWireless", and "LCC" are wireless networks at my college and are always detected in Windows and on my iPod. I always connect them both to "Guest@LC" (unsecured) with no problem. The signal strength can vary but is usually "Excellent" (11 Mb/s) in Windows.

Here is some more information:

```

bothorth@Bothorth:~$ sudo lshw -C network
[sudo] password for bothorth: 
  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 83
       serial: 00:00:39:77:b8:d5
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
       resources: irq:11 memory:cffff000-cfffffff ioport:cf40(size=64)
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:7e:55:b3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco_cs driverversion=2.6.38-8-generic firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b

```and

```

bothorth@Bothorth:~$ sudo lspci -nn
[sudo] password for bothorth: 
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 01)
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 01)
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 01)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 01)
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 83)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 03)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 03)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 03)
01:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 83)
01:0a.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 01)
01:0b.0 CardBus bridge [0607]: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support [1179:0617] (rev 33)

```Something must be working for the correct network names to appear, but the connection always gives up and disconnects for some reason.

---

### Post by bkratz on 2011-08-05
I notice two things in your outputs

First, the signal level on all three is not very good. Perhaps you are to far away to get a good connection.

Second, your controller shows up as being in the Master Mode. Example:

 Cell 05 - Address: 00:0B:86:24:88:B2
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"LCC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:[COLOR="Red"]Master[/COLOR]

From "man iwconfig" in the terminal
"

[COLOR="Teal"] mode   Set the operating mode of the device, which depends on the  net&#8208;
              work  topology. The mode can be Ad-Hoc (network composed of only
              one cell and without Access Point), Managed (node connects to  a
              network  composed  of  many Access Points, with roaming), Master
              (the node is the synchronisation master or  acts  as  an  Access
              Point),  Repeater (the node forwards packets between other wire&#8208;
              less  nodes),  Secondary  (the  node  acts  as  a  backup   mas&#8208;
              ter/repeater), Monitor (the node is not associated with any cell
              and passively monitor all packets on the frequency) or Auto.
              Example :
                   iwconfig eth0 mode Managed
                   iwconfig eth0 mode Ad-Hoc
[/COLOR]

You  might also try

sudo iwconfig eth1 mode Managed

---

### Post by chili555 on 2011-08-05
I suspect that the hostap drivers will work better than orinoco_cs. bkratz may suggest an experiment and blacklisting.> Cell 05 - Address: 00:0B:86:24:88:B2
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=28/70 Signal level=-82 dBm
Encryption keyn
ESSID:"LCC"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
Mode:Master
Routers and other wireless access points *should* be in Master mode. Their clients; i.e.our wireless cards, are usually in Managed mode.

---

### Post by Bothorth on 2011-08-08
bkratz: I tried > sudo iwconfig eth1 mode Managed and moved to another building where (Windows says) strength is 'Excellent'. It still won't stay connected.

```
root@Bothorth:~# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1A:1E:9E:D9:82
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:off
                    ESSID:"Guest@LC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000003392336779
                    Extra: Last beacon: 244ms ago
                    IE: Unknown: 00084775657374404C43
                    IE: Unknown: 010482840B16
                    IE: Unknown: 030101
                    IE: Unknown: 2A0107
                    IE: Unknown: DD0A00037F04010000000000
          Cell 02 - Address: 00:0B:86:24:65:F4
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"Guest@LC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000003382e4008c
                    Extra: Last beacon: 1064ms ago
                    IE: Unknown: 00084775657374404C43
                    IE: Unknown: 010482840B16
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: DD0A00037F04010000000000
          Cell 03 - Address: 00:1A:1E:9E:FB:22
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"Guest@LC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000000027b96d8da
                    Extra: Last beacon: 11460ms ago
                    IE: Unknown: 00084775657374404C43
                    IE: Unknown: 010482840B16
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: DD0A00037F04010000000000
          Cell 04 - Address: 00:1A:1E:9E:D9:80
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"LCWireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000003392335220
                    Extra: Last beacon: 248ms ago
                    IE: Unknown: 000A4C43576972656C657373
                    IE: Unknown: 010482840B16
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD0A00037F04010000000000
          Cell 05 - Address: 00:1A:1E:9E:D9:81
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"LCC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000003392336321
                    Extra: Last beacon: 244ms ago
                    IE: Unknown: 00034C4343
                    IE: Unknown: 010482840B16
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: Unknown: DD0A00037F04010000000000
          Cell 06 - Address: 02:00:87:A6:FF:6B
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"SETUP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=000002928e2e947b
                    Extra: Last beacon: 168ms ago
                    IE: Unknown: 00055345545550
                    IE: Unknown: 010482840B16
                    IE: Unknown: 03010A
                    IE: Unknown: 06020000
                    IE: Unknown: DD09001018020010000000
          Cell 07 - Address: 00:0B:86:24:65:F2
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"LCC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000003382e3f8ea
                    Extra: Last beacon: 1068ms ago
                    IE: Unknown: 00034C4343
                    IE: Unknown: 010482840B16
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: DD0A00037F04010000000000
          Cell 08 - Address: 00:0B:86:24:65:F1
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"LCWireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000003382e3f158
                    Extra: Last beacon: 1068ms ago
                    IE: Unknown: 000A4C43576972656C657373
                    IE: Unknown: 010482840B16
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD0A00037F04010000000000
          Cell 09 - Address: 00:0B:86:24:87:94
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"Guest@LC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000003e47bb2063
                    Extra: Last beacon: 196ms ago
                    IE: Unknown: 00084775657374404C43
                    IE: Unknown: 010482840B16
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: DD0A00037F04010000000000
          Cell 10 - Address: 00:1A:1E:9E:FB:21
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"LCC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000000027c351e8f
                    Extra: Last beacon: 1088ms ago
                    IE: Unknown: 00034C4343
                    IE: Unknown: 010482840B16
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: DD0A00037F04010000000000
          Cell 11 - Address: 00:1A:1E:9E:FB:20
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"LCWireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000000027c43508d
                    Extra: Last beacon: 156ms ago
                    IE: Unknown: 000A4C43576972656C657373
                    IE: Unknown: 010482840B16
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD0A00037F04010000000000
          Cell 12 - Address: 00:0B:86:24:87:91
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"LCWireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000003e47bb16d7
                    Extra: Last beacon: 200ms ago
                    IE: Unknown: 000A4C43576972656C657373
                    IE: Unknown: 010482840B16
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD0A00037F04010000000000
          Cell 13 - Address: 00:0B:86:24:87:92
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"LCC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000003e47bb1c21
                    Extra: Last beacon: 200ms ago
                    IE: Unknown: 00034C4343
                    IE: Unknown: 010482840B16
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: DD0A00037F04010000000000
``````
root@Bothorth:~# nm-tool

NetworkManager Tool

State: connecting

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             unavailable
  Default:           no
  HW Address:        00:00:39:77:B8:D5

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: eth1  [Auto Guest@LC] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            orinoco_cs
  State:             connecting (configuring)
  Default:           no
  HW Address:        00:02:2D:7E:55:B3

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes

  Wireless Access Points 
    Guest@LC:        Infra, 00:0B:86:24:80:D4, Freq 2437 MHz, Rate 11 Mb/s, Strength 35
    LCC:             Infra, 00:0B:86:28:04:C2, Freq 2462 MHz, Rate 11 Mb/s, Strength 30 WEP
    LCWireless:      Infra, 00:0B:86:24:80:D1, Freq 2437 MHz, Rate 11 Mb/s, Strength 31 WPA2 Enterprise
    Guest@LC:        Infra, 00:1A:1E:9E:FB:22, Freq 2462 MHz, Rate 11 Mb/s, Strength 38
    LCC:             Infra, 00:0B:86:24:88:A2, Freq 2412 MHz, Rate 11 Mb/s, Strength 22 WEP
    Guest@LC:        Infra, 00:0B:86:22:8E:94, Freq 2437 MHz, Rate 11 Mb/s, Strength 30
    LCC:             Infra, 00:0B:86:24:87:92, Freq 2437 MHz, Rate 11 Mb/s, Strength 32 WEP
    LCC:             Infra, 00:0B:86:22:8E:92, Freq 2437 MHz, Rate 11 Mb/s, Strength 31 WEP
    LCWireless:      Infra, 00:0B:86:22:8E:91, Freq 2437 MHz, Rate 11 Mb/s, Strength 30 WPA2 Enterprise
    Guest@LC:        Infra, 00:0B:86:28:04:C4, Freq 2462 MHz, Rate 11 Mb/s, Strength 31
    LCC:             Infra, 00:1A:1E:9E:FB:21, Freq 2462 MHz, Rate 11 Mb/s, Strength 41 WEP
    Guest@LC:        Infra, 00:0B:86:24:87:94, Freq 2437 MHz, Rate 11 Mb/s, Strength 32
    SETUP:           Ad-Hoc, 02:00:87:A6:FF:6B, Freq 2457 MHz, Rate 11 Mb/s, Strength 34
    Guest@LC:        Infra, 00:0B:86:24:65:F4, Freq 2462 MHz, Rate 11 Mb/s, Strength 48
    Guest@LC:        Infra, 00:1A:1E:9E:D9:82, Freq 2412 MHz, Rate 11 Mb/s, Strength 88
    LCC:             Infra, 00:0B:86:24:65:F2, Freq 2462 MHz, Rate 11 Mb/s, Strength 47 WEP
    LCC:             Infra, 00:1A:1E:9E:D9:81, Freq 2412 MHz, Rate 11 Mb/s, Strength 91 WEP
    LCWireless:      Infra, 00:0B:86:24:87:91, Freq 2437 MHz, Rate 11 Mb/s, Strength 31 WPA2 Enterprise
    LCWireless:      Infra, 00:1A:1E:9E:FB:20, Freq 2462 MHz, Rate 11 Mb/s, Strength 35 WPA2 Enterprise
    LCWireless:      Infra, 00:0B:86:24:65:F1, Freq 2462 MHz, Rate 11 Mb/s, Strength 48 WPA2 Enterprise
    LCWireless:      Infra, 00:1A:1E:9E:D9:80, Freq 2412 MHz, Rate 11 Mb/s, Strength 91 WPA2 Enterprise

``````
root@Bothorth:~# lshw -C network
  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 83
       serial: 00:00:39:77:b8:d5
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100  driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no  maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
       resources: irq:11 memory:cffff000-cfffffff ioport:cf40(size=64)
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:7e:55:b3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco_cs  driverversion=2.6.38-8-generic firmware=Lucent/Agere 9.48 link=no  multicast=yes wireless=IEEE 802.11b

```Is it:
1) A driver problem, being a fresh Ubuntu installation? Do I need ndiswrapper?
2) A problem with low signal strength? Why should it be a problem in Ubuntu and not Windows?
3) The fact that it's unsecured? 

My only working internet right now comes from "Guest@LC" through Windows. What can I do to get connected through Ubuntu?

---

### Post by bkratz on 2011-08-08
[COLOR="Red"]"I suspect that the hostap drivers will work better than orinoco_cs. bkratz may suggest an experiment and blacklisting."
[/COLOR]

I'm afraid Dr Chili sometimes gives me too much credit-- hopefully he will return. I'll PM him and see if he will. Anyway, I see the mode is still in master

Example
 Cell 11 - Address: 00:1A:1E:9E:FB:20
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"LCWireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    [COLOR="Red"]Mode:Master[/COLOR]

did you receive any errors when you attempted to change it, you might try again.

---

### Post by chili555 on 2011-08-08
Make sure the hostap suite of drivers are installed on your system by running:```
modinfo hostap_cs
```You will either get data or a 'module not found.' I suspect it is present. It generally works better than orinoco so let's blacklist orinoco:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add two lines at the end:```
blacklist orinoco_cs
blacklist orinoco
```Proofread carefully, save and close gedit. Now do:```
sudo gedit /etc/modules
```Add two lines at the end:```
hostap_cs
hostap
```Proofread carefully, save and close gedit. Reboot and let us have your report.

You may have another issue, Network Manager is evidently roaming from among several weak access points with identical ESSIDs. However, let's solve one issue at a time.

---

### Post by chili555 on 2011-08-08
> Example
Cell 11 - Address: 00:1A:1E:9E:FB:20
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=25/70 Signal level=-85 dBm
Encryption keyn
ESSID:"LCWireless"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
Mode:[COLOR="Red"]Master[/COLOR]

did you receive any errors when you attempted to change it, you might try again.Unless you have login access to the router, you won't and shouldn't be able to change its mode.

---

### Post by Bothorth on 2011-08-08
bkratz: This is what happens when I try it:

```
root@Bothorth:~# sudo iwconfig eth1 mode Managed
root@Bothorth:~# 
```Which looks like nothing.

chili555, I did what you said:

```

root@Bothorth:~# modinfo hostap_cs
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/hostap/hostap_cs.ko
license:        GPL
description:    Support for Intersil Prism2-based 802.11 wireless LAN cards (PC Card).
author:         Jouni Malinen
srcversion:     D20051C7F4655BE89C33025
alias:          pcmcia:m*c*f*fn*pfn*pa*pb*pcC9049A39pd*
alias:          pcmcia:m*c*f*fn*pfn*pa*pb*pcDD97A26Bpd*
alias:          pcmcia:m*c*f*fn*pfn*pa*pb*pc630D52B2pd*
alias:          pcmcia:m*c*f*fn*pfn*pa*pb*pc355CB092pd*
alias:          pcmcia:m*c*f*fn*pfn*pa4B8870FFpb70E946D1pc4B74BAA0pd*
alias:          pcmcia:m*c*f*fn*pfn*pa5CD01705pb4271660Fpc9D08EE12pd*
alias:          pcmcia:m*c*f*fn*pfn*paC7B8DF9Dpb1700D087pc4B74BAA0pd*
alias:          pcmcia:m*c*f*fn*pfn*pa1CADD3E5pbE697636Cpc7A5BFCF1pd*
alias:          pcmcia:m*c*f*fn*pfn*pa273FE3DBpb32A1EAEEpc*pd*
alias:          pcmcia:m*c*f*fn*pfn*pa0733CC81pb0C52F395pc*pd*
alias:          pcmcia:m*c*f*fn*pfn*pa74C5E40DpbDB472A18pc*pd*
alias:          pcmcia:m*c*f*fn*pfn*pa54F7C49Cpb15A75E5Bpc*pd*
alias:          pcmcia:m*c*f*fn*pfn*pa2DECECE3pb82067C18pc*pd*
alias:          pcmcia:m*c*f*fn*pfn*paC4F8B18Bpb474A1F2Apc4B74BAA0pd*
alias:          pcmcia:m*c*f*fn*pfn*pa11D901AFpb6E9BD926pc4B74BAA0pd*
alias:          pcmcia:m*c*f*fn*pfn*pa71B18589pbB6F1B0ABpc4B74BAA0pd*
alias:          pcmcia:m*c*f*fn*pfn*paE6EC52CEpb08649AF2pc4B74BAA0pd*
alias:          pcmcia:m*c*f*fn00pfn*pa7A954BD9pb74BE00C6pc*pd*
alias:          pcmcia:m0156c0002f*fn*pfn*pa4B801A17pb*pc*pd*
alias:          pcmcia:m0156c0002f*fn*pfn*pa74C5E40Dpb*pc*pd*
alias:          pcmcia:mD601c0005f*fn*pfn*pa2D858104pb*pc*pd*
alias:          pcmcia:m0126c0002f*fn*pfn*pa*pb*pc*pd*
alias:          pcmcia:mD601c0010f*fn*pfn*pa*pb*pc*pd*
alias:          pcmcia:mD601c0005f*fn*pfn*pa*pb*pc*pd*
alias:          pcmcia:mD601c0002f*fn*pfn*pa*pb*pc*pd*
alias:          pcmcia:mC250c0002f*fn*pfn*pa*pb*pc*pd*
alias:          pcmcia:m50C2c7300f*fn*pfn*pa*pb*pc*pd*
alias:          pcmcia:m50C2c0001f*fn*pfn*pa*pb*pc*pd*
alias:          pcmcia:m02D2c0001f*fn*pfn*pa*pb*pc*pd*
alias:          pcmcia:m02AAc0002f*fn*pfn*pa*pb*pc*pd*
alias:          pcmcia:m028Ac0002f*fn*pfn*pa*pb*pc*pd*
alias:          pcmcia:m0274c1613f*fn*pfn*pa*pb*pc*pd*
alias:          pcmcia:m0274c1612f*fn*pfn*pa*pb*pc*pd*
alias:          pcmcia:m026Fc030Bf*fn*pfn*pa*pb*pc*pd*
alias:          pcmcia:m0250c0002f*fn*pfn*pa*pb*pc*pd*
alias:          pcmcia:m01BFc3301f*fn*pfn*pa*pb*pc*pd*
alias:          pcmcia:m0138c0002f*fn*pfn*pa*pb*pc*pd*
alias:          pcmcia:m0126c8000f*fn*pfn*pa*pb*pc*pd*
alias:          pcmcia:m0101c0777f*fn*pfn*pa*pb*pc*pd*
alias:          pcmcia:m000Bc7300f*fn*pfn*pa*pb*pc*pd*
alias:          pcmcia:m000Bc7100f*fn*pfn*pa*pb*pc*pd*
depends:        pcmcia,hostap,lib80211
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 
parm:           ignore_cis_vcc:Ignore broken CIS VCC entry (int)
parm:           mtu:Maximum transfer unit (int)
parm:           channel:Initial channel (array of int)
parm:           essid:Host AP's ESSID (string)
parm:           iw_mode:Initial operation mode (array of int)
parm:           beacon_int:Beacon interval (1 = 1024 usec) (array of int)
parm:           dtim_period:DTIM period (array of int)
parm:           dev_template:Prefix for network device name (default: wlan%d) (string)

```Blacklisted orinoco, added hostap and restarted. Network icon stays dark, and the menu under it doesn't show the networks, or even "Enable Wireless".

```

root@Bothorth:~# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
``````

root@Bothorth:~# nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             unavailable
  Default:           no
  HW Address:        00:00:39:77:B8:D5

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off

``````
root@Bothorth:~# lshw -C network
  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 83
       serial: 00:00:39:77:b8:d5
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
       resources: irq:11 memory:cffff000-cfffffff ioport:cf40(size=64)

```

---

### Post by chili555 on 2011-08-09
What exactly is your wireless device? You have submitted a lot of information, but I haven't seen the identity of the device yet. Is it a PCMCIA device? If so, please post:```
sudo lspcmcia ident
```I have never been aware of a device that orinoco claimed that hostap didn't. I learn something new every day! May I also see:```
dmesg | grep host
sudo modprobe orinoco_cs
dmesg | grep orin
```Thanks.

---

### Post by Bothorth on 2011-08-09
Windows calls it "Toshiba Wireless LAN Mini PCI Card" (a search leads to the ORiNOCO page on Wikipedia.)

```
root@Bothorth:~# sudo lspcmcia ident
Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:01:0a.0)
Socket 0 Device 0:    [-- no driver --]    (bus ID: 0.0)
Socket 1 Bridge:       [yenta_cardbus]     (bus ID: 0000:01:0b.0)
root@Bothorth:~# 
```(where [-- no driver --] is replaced by [orinoco_cs] when it's not blacklisted.)

```
root@Bothorth:~# dmesg | grep host
[    0.049534] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.049684] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.049690] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.049696] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.049701] pci_root PNP0A03:00: host bridge window [mem 0x000d8000-0x000dffff] (ignored)
[    0.049707] pci_root PNP0A03:00: host bridge window [mem 0x40100000-0xfec0ffff] (ignored)
[    0.049712] pci_root PNP0A03:00: host bridge window [mem 0xfec20000-0xfed9ffff] (ignored)
[    0.049718] pci_root PNP0A03:00: host bridge window [mem 0xfedc0000-0xffafffff] (ignored)
[    0.049723] pci_root PNP0A03:00: host bridge window [mem 0xffc00000-0xffdfffff] (ignored)
root@Bothorth:~# 
``````
root@Bothorth:~# sudo modprobe orinoco_cs
root@Bothorth:~#
``````
root@Bothorth:~# dmesg | grep orin
[    0.049534] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[  302.632541] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[  302.725922] orinoco_cs 0.0: Hardware identity 0005:0004:0005:0000
[  302.726052] orinoco_cs 0.0: Station identity  001f:0001:0008:000a
[  302.726062] orinoco_cs 0.0: Firmware determined as Lucent/Agere 8.10
[  302.863692] orinoco_cs 0.0: Hardware identity 0005:0004:0005:0000
[  302.863822] orinoco_cs 0.0: Station identity  001f:0002:0009:0030
[  302.863833] orinoco_cs 0.0: Firmware determined as Lucent/Agere 9.48
[  302.863841] orinoco_cs 0.0: Ad-hoc demo mode supported
[  302.863848] orinoco_cs 0.0: IEEE standard IBSS ad-hoc mode supported
[  302.863855] orinoco_cs 0.0: WEP supported, 104-bit key
[  302.863862] orinoco_cs 0.0: WPA-PSK supported
root@Bothorth:~# 
```"Agere" looks familiar; in fact, the drivers are on my Toshiba CDs and show up in Windows as:

[IMG]http://i836.photobucket.com/albums/zz290/AGNewton/Agere.png[/IMG]

---

### Post by chili555 on 2011-08-10
This is still a mystery. Let's try:```
sudo pccardctl ident
```Here is a sample form my computer:> $ sudo pccardctl ident
Socket 0:
  product info: "INTERSIL", "HFA384x/IEEE", "Version 01.02", ""
  manfid: 0x[COLOR="Red"]0156[/COLOR], 0x[COLOR="Red"]0002[/COLOR]
  function: 6 (network)We are very interested in the highlighted data.

I hope we are not going to be forced to work with the clunky orinoco suite.

---

### Post by Bothorth on 2011-08-10
```
root@Bothorth:~# sudo pccardctl ident
Socket 0:
  product info: "TOSHIBA", "Wireless LAN Card", "Version 01.01", ""
  manfid: 0x0156, 0x0002
  function: 6 (network)
Socket 1:
  no product info available
root@Bothorth:~# 
```

---

### Post by chili555 on 2011-08-10
Fascinating. Your device and mine have the same chipset. This is even more fascinating:```
$ modinfo hostap_cs | grep 0002
alias:          pcmcia:m[COLOR="Red"]0156[/COLOR]c[COLOR="Red"]0002[/COLOR]f*fn*pfn*pa4B801A17pb*pc*pd*
alias:          pcmcia:m[COLOR="Red"]0156[/COLOR]c[COLOR="Red"]0002[/COLOR]f*fn*pfn*pa74C5E40Dpb*pc*pd*
```I wonder why, then, that hostap_cs doesn't grab your device. Let's look at one more thing before I resort to "medicine." With the device inserted, please do:```
sudo modprobe hostap_cs
sudo cat /var/log/syslog | grep hostap | tail -n20
```Post the result so we can perhaps see why hostap isn't working.

---

### Post by Bothorth on 2011-08-10
Nothing?

```
root@Bothorth:~# sudo modprobe hostap_cs
root@Bothorth:~# sudo cat /var/log/syslog | grep hostap | tail -n20
root@Bothorth:~# 
```Tried this and got

```
root@Bothorth:~# modinfo hostap_cs | grep 0002
alias:          pcmcia:m0156c0002f*fn*pfn*pa4B801A17pb*pc*pd*
alias:          pcmcia:m0156c0002f*fn*pfn*pa74C5E40Dpb*pc*pd*
alias:          pcmcia:m0126c0002f*fn*pfn*pa*pb*pc*pd*
alias:          pcmcia:mD601c0002f*fn*pfn*pa*pb*pc*pd*
alias:          pcmcia:mC250c0002f*fn*pfn*pa*pb*pc*pd*
alias:          pcmcia:m02AAc0002f*fn*pfn*pa*pb*pc*pd*
alias:          pcmcia:m028Ac0002f*fn*pfn*pa*pb*pc*pd*
alias:          pcmcia:m0250c0002f*fn*pfn*pa*pb*pc*pd*
alias:          pcmcia:m0138c0002f*fn*pfn*pa*pb*pc*pd*
root@Bothorth:~# 
```which is in the data from before.

---

### Post by Bothorth on 2011-08-18
Need some of that 'medicine'!

---

### Post by chili555 on 2011-08-18
I have been playing with my orinoco/hostap/Prism card for an hour or so. I never, given all the power of the doctor's grey beard, got it to connect!

Here is a case I worked on where the poster removed Network Manager and set a static IP address and says he has a working wireless: [http://ubuntuforums.org/showthread.php?t=1786254&page=2](http://ubuntuforums.org/showthread.php?t=1786254&page=2)

I tried a static IP address, both within and outside NM; that is, /etc/network/interfaces. I removed NM entirely. Neither orinoco or hostap worked for me. Whatever method I use, I get:> Aug 18 10:13:06 LAPTOP60 kernel: [171930.103226] wifi0: LinkStatus=2 (Disconnected)
Aug 18 10:13:06 LAPTOP60 kernel: [171930.103475] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
Aug 18 10:13:06 LAPTOP60 kernel: [171930.126530] wifi0: LinkStatus=2 (Disconnected)
Aug 18 10:13:06 LAPTOP60 kernel: [171930.126757] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
Aug 18 10:13:06 LAPTOP60 kernel: [171930.164977] wifi0: LinkStatus=1 (Connected)
Aug 18 10:13:06 LAPTOP60 kernel: [171930.165222] wifi0: LinkStatus: BSSID=00:24:56:2a:d7:29
Aug 18 10:13:09 LAPTOP60 kernel: [171933.186291] wifi0: LinkStatus=2 (Disconnected)
Aug 18 10:13:09 LAPTOP60 kernel: [171933.186518] wifi0: LinkStatus: BSSID=00:24:56:2a:d7:29
Aug 18 10:13:21 LAPTOP60 kernel: [171945.156053] wifi0: LinkStatus=2 (Disconnected)
Aug 18 10:13:21 LAPTOP60 kernel: [171945.156281] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
Aug 18 10:13:21 LAPTOP60 kernel: [171945.179336] wifi0: LinkStatus=2 (Disconnected)
Aug 18 10:13:21 LAPTOP60 kernel: [171945.191694] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
Aug 18 10:13:21 LAPTOP60 kernel: [171945.218082] wifi0: LinkStatus=1 (Connected)
I am not quite sure what else I can suggest.

The 'medicine' I referred to was a tranquilizer and adult beverage for me.

When you remove hostap from /etc/modules and remove orinoco from blacklist, what does this tell us?```
sudo cat /var/log/syslog | grep etwork | tail -n25
```

---

### Post by Bothorth on 2011-08-18
```
bothorth@Bothorth:~$ sudo cat /var/log/syslog | grep etwork | tail -n25
Aug 18 20:24:30 Bothorth NetworkManager[509]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Aug 18 20:24:30 Bothorth NetworkManager[509]: <info> (eth1): supplicant connection state:  scanning -> associating
Aug 18 20:24:36 Bothorth NetworkManager[509]: <info> (eth1): supplicant connection state:  associating -> disconnected
Aug 18 20:24:36 Bothorth NetworkManager[509]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Aug 18 20:24:36 Bothorth NetworkManager[509]: <info> (eth1): supplicant connection state:  scanning -> associating
Aug 18 20:24:41 Bothorth NetworkManager[509]: <info> (eth1): supplicant connection state:  associating -> disconnected
Aug 18 20:24:41 Bothorth NetworkManager[509]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Aug 18 20:24:41 Bothorth NetworkManager[509]: <info> (eth1): supplicant connection state:  scanning -> associating
Aug 18 20:24:46 Bothorth NetworkManager[509]: <info> (eth1): supplicant connection state:  associating -> disconnected
Aug 18 20:24:46 Bothorth NetworkManager[509]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Aug 18 20:24:46 Bothorth NetworkManager[509]: <info> (eth1): supplicant connection state:  scanning -> associating
Aug 18 20:24:50 Bothorth NetworkManager[509]: <warn> (eth1): link timed out.
Aug 18 20:24:51 Bothorth NetworkManager[509]: <info> (eth1): supplicant connection state:  associating -> disconnected
Aug 18 20:24:51 Bothorth NetworkManager[509]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Aug 18 20:24:51 Bothorth NetworkManager[509]: <info> (eth1): supplicant connection state:  scanning -> associating
Aug 18 20:24:56 Bothorth NetworkManager[509]: <info> (eth1): supplicant connection state:  associating -> disconnected
Aug 18 20:24:56 Bothorth NetworkManager[509]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Aug 18 20:24:56 Bothorth NetworkManager[509]: <info> (eth1): supplicant connection state:  scanning -> associating
Aug 18 20:24:58 Bothorth NetworkManager[509]: <warn> Activation (eth1/wireless): association took too long, failing activation.
Aug 18 20:24:58 Bothorth NetworkManager[509]: <info> (eth1): device state change: 5 -> 9 (reason 11)
Aug 18 20:24:58 Bothorth NetworkManager[509]: <warn> Activation (eth1) failed for access point (Guest@LC)
Aug 18 20:24:58 Bothorth NetworkManager[509]: <info> Marking connection 'Auto Guest@LC' invalid.
Aug 18 20:24:58 Bothorth NetworkManager[509]: <warn> Activation (eth1) failed.
Aug 18 20:24:58 Bothorth NetworkManager[509]: <info> (eth1): device state change: 9 -> 3 (reason 0)
Aug 18 20:24:58 Bothorth NetworkManager[509]: <info> (eth1): deactivating device (reason: 0).
bothorth@Bothorth:~$ 


```

---

### Post by chili555 on 2011-08-19
Basically, the same result as mine. Today, I got out my old Maverick 10.10 harddrive and played some more. I tried orinoco and hostap. I tried with and without Network Manager. I tried DHCP and static IP addresses. I can't get the device to work in any circumstance. I am very sorry. I wish I had a better answer.

---

### Post by Bothorth on 2011-09-09
I don't know how but ... I tried the method in the link two posts ago and removed Network Manager with no luck. Tried to reinstall it using a .deb (downloaded through Windows) and now the Network icon shows no activity, no networks listed, but somehow Firefox IS getting a connection in Ubuntu. I'm typing this from Ubuntu right now. If this posts, I have wireless.

---

