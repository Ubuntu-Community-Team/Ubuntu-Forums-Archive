---
title: "Wifi was working 2 days ago...."
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by Brzhk on 2009-02-18
And now it doesnt.

I'm on a Dell Studio 15 centrino 2 laptop which runs the dell tweaked ubuntu 8.10 (2.6.27-11-generic i686)

```

brzhk@gauss:/var/log$ lspci -nn | grep "WiFi"
04:00.0 Network controller [0280]: Intel Corporation Wireless WiFi Link 5100 [8086:4232]


```


I cannot reach my school's network, which doesnt broadcast its ESSID. I had a saved configuration on network manager that worked two days ago so it shouldn't be the problem...



I tried several times to find out what worked wrong, and here's two things i've remarked.
[LIST]
[*]The syslog reveals that the system looks stuck in an auth loop. It associates wlan0 to some kind of address and tries twice to authenticate, then deauth itself.
[*]The networkmanager detected my home wifi network at my school, which is just impossible ( i leave 50km from school). Strange thing is, that it is the only other saved configuration for an invisible network.
[/LIST]


here's a couple of logs that looks to be useful:

```

brzhk@gauss:/var/log$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:21:5d:e7:1e:82  
          inet adr:192.168.0.6  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::221:5dff:fee7:1e82/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:17 erreurs:0 :0 overruns:0 frame:0
          TX packets:424 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:2030 (2.0 KB) Octets transmis:29282 (29.2 KB)

brzhk@gauss:/var/log$ iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"ESIEE"  
          Mode:Ad-Hoc  Frequency:2.457 GHz  Cell: 02:0C:F1:7A:E5:98   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

brzhk@gauss:/var/log$ lsmod | grep "iwlagn"
iwlagn                 99716  0 
iwlcore                94532  1 iwlagn
mac80211              216820  2 iwlagn,iwlcore
cfg80211               32392  3 iwlagn,iwlcore,mac80211

```

```
brzhk@gauss:/var/log$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:5d:e7:1e:82
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.0.6 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 02:25:63:dd:9d:e2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


```
```

brzhk@gauss:/var/log$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:12:44:BA:FE:D0
                    ESSID:""
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=45/100  Signal level:-82 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000004a63c2f18b
                    Extra: Last beacon: 2304ms ago

          Cell 02 - Address: 00:12:44:BB:00:70
                    ESSID:""
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=59/100  Signal level:-72 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000004a63ca018d
                    Extra: Last beacon: 212ms ago
          Cell 03 - Address: 0A:82:27:AD:81:F6
                    ESSID:"Panasonic Display1"
                    Mode:Ad-Hoc
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=45/100  Signal level:-82 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000000420ef1e3
                    Extra: Last beacon: 164ms ago
          Cell 04 - Address: 00:12:44:BB:02:20
                    ESSID:""
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/100  Signal level:-75 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000004a63cc6d8b
                    Extra: Last beacon: 2708ms ago
          Cell 05 - Address: 00:12:44:BE:DB:B0
                    ESSID:""
                    Mode:Master
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=73/100  Signal level:-61 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=0000004a63c96043
                    Extra: Last beacon: 1912ms ago
          Cell 06 - Address: 00:1D:7E:1A:FE:0C
                    ESSID:"AP3"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/100  Signal level:-84 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000375b6046476
                    Extra: Last beacon: 2260ms ago
          Cell 07 - Address: 00:12:44:BB:02:50
                    ESSID:""
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=72/100  Signal level:-62 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=0000004a63c64108
                    Extra: Last beacon: 2812ms ago
          Cell 08 - Address: 00:12:44:BA:E3:50
                    ESSID:""
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=61/100  Signal level:-71 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000004a63d6019a
                    Extra: Last beacon: 2540ms ago
          Cell 09 - Address: 00:12:44:BB:01:70
                    ESSID:""
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/100  Signal level:-70 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=0000004a639a3109
                    Extra: Last beacon: 2260ms ago

```
```

brzhk@gauss:/var/log$ sudo /etc/init.d/networking restart
[sudo] password for brzhk: 
 * Reconfiguring network interfaces...                                                                                   
Ignoring unknown interface eth0=eth0.
                                                          [ OK ]

```


```

brzhk@gauss:/var/log$ dmesg | grep "iwlagn"
[   13.537655] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   13.537658] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   13.537727] iwlagn 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.537736] iwlagn 0000:04:00.0: setting latency timer to 64
[   13.537759] iwlagn: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   13.567482] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
[   13.567679] iwlagn 0000:04:00.0: PCI INT A disabled
[   25.121633] iwlagn 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   25.121725] iwlagn 0000:04:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[  196.405129] iwlagn 0000:04:00.0: PCI INT A disabled
[  196.409221] iwlagn 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  196.409329] iwlagn 0000:04:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)

```

---

### Post by Brzhk on 2009-02-18
here comes the logs and everything asked in the HOWTO ^^

---

