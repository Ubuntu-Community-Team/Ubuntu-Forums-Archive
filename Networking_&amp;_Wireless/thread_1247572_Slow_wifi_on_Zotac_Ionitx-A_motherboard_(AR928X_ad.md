---
title: "Slow wifi on Zotac Ionitx-A motherboard (AR928X adapter)"
date: 2009-08-23
forum: Networking &amp; Wireless
---

### Post by Gizmonty on 2009-08-23
I have a new motherboard that should be giving me some speedy 802.11n goodness but the wifi is going very slowly. The fastest file transfer I've managed has been 1.5 MB/s, and I more typically see below 0.5 MB/s. I'm using this as a MythTV frontend (Mythbuntu 9.04) and this just isn't fast enough. I have another frontend that had a card requiring the Ath9K drivers and it performed poorly too. I ended up replacing the card with an external wireless bridge. This has worked well and lets me stream HDTV nicely but I really don't want to buy another one.

I've done some reading about this and can't find a definite solution that I'm prepared to try yet. Additionally, the wifi connection seems to drop out fairly frequently, especially during heavy network activity.

I get the following outputs;

lspci -nnv
```
04:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
	Subsystem: Device [1a3b:1067]
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at febf0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

```

lshw -C Network
```
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:01:2e:27:1b:09
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 01
       serial: 00:24:23:07:ce:ed
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.0.199 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 26:5c:42:c0:6a:4b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

uname -rm
```
2.6.28-14-generic x86_64
```

sudo iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1F:B3:09:78:D9
                    ESSID:"BigPond2584"
                    Mode:Master
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=20/100  Signal level:-108 dBm  Noise level=-121 dBm
                    Encryption key:on
                    IE: Unknown: 000B426967506F6E6432353834
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030103
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000008fe9d42e149
                    Extra: Last beacon: 564ms ago
          Cell 02 - Address: 00:1C:F0:FB:71:EA
                    ESSID:"Tony Harrison"
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=104/100  Signal level:-54 dBm  Noise level=-121 dBm
                    Encryption key:on
                    IE: Unknown: 000D546F6E79204861727269736F6E
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 32088C129824B048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340900040000000F000000000000000000000000000000
                    IE: Unknown: 2D1A4C101FFFFF000000000000000000000000000004000000000000
                    IE: Unknown: 3D160900000000000F000000000000000000000000000000
                    IE: Unknown: DD7F0050F204104A0001101044000102103B00010310470010EA59B958DA7832D49F2821D0EF775BF91021000E442D4C696E6B2053797374656D73102300074449522D363535102400024133104200046E6F6E651054000800060050F204000110110017587472656D65204E204749474142495420526F75746572100800020004
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000003285a7a042d
                    Extra: Last beacon: 44ms ago
          Cell 03 - Address: 00:0F:66:59:D8:0E
                    ESSID:"adams family"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/100  Signal level:-109 dBm  Noise level=-121 dBm
                    Encryption key:off
                    IE: Unknown: 000C6164616D732066616D696C79
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020104
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000004e254afd36
                    Extra: Last beacon: 364ms ago

pan0      Interface doesn't support scanning.

```

dmesg | grep -e ath -e wlan
```
[    4.848994] device-mapper: multipath: version 1.0.5 loaded
[    4.849002] device-mapper: multipath round-robin: version 1.0.0 loaded
[    9.285722] ath9k: 0.1
[    9.287633] ath9k 0000:04:00.0: PCI INT A -> Link[LN3A] -> GSI 19 (level, low) -> IRQ 19
[    9.287655] ath9k 0000:04:00.0: setting latency timer to 64
[    9.716401] phy0: Selected rate control algorithm 'ath9k_rate_control'
[    9.768985] Registered led device: ath9k-phy0:radio
[    9.769064] Registered led device: ath9k-phy0:assoc
[    9.769102] Registered led device: ath9k-phy0:tx
[    9.769142] Registered led device: ath9k-phy0:rx
[   30.383411] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.090987] wlan0: authenticate with AP 00:0f:66:59:d8:0e
[   31.092612] wlan0: authenticated
[   31.092620] wlan0: associate with AP 00:0f:66:59:d8:0e
[   31.099074] wlan0: RX AssocResp from 00:0f:66:59:d8:0e (capab=0x401 status=0 aid=1)
[   31.099082] wlan0: associated
[   31.111240] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   31.418216] wlan0: disassociating by local choice (reason=3)
[   42.012014] wlan0: no IPv6 routers present
[   50.601670] wlan0: authenticate with AP 00:1c:f0:fb:71:ea
[   50.603216] wlan0: authenticated
[   50.603228] wlan0: associate with AP 00:1c:f0:fb:71:ea
[   50.606889] wlan0: RX AssocResp from 00:1c:f0:fb:71:ea (capab=0x431 status=0 aid=4)
[   50.606897] wlan0: associated

```

Is there anything obvious I should try?

---

### Post by excogitation on 2009-08-27
try installing
```
sudo aptitude install linux-backports-modules-jaunty-generic
```
[taken from here]("http://ubuntuforums.org/showthread.php?t=1205318")

Also - feel free to join in: [333730]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/333730").

---

### Post by Gizmonty on 2009-09-07
That's great, the problem of the connections dropping is solved by this. 

The speed of the connection is still fairly slow however (about 8 Mb/s).

This is adequate for me to stream SD video, but not HD. I can live with this for the short-term. Hopefully these drivers will mature with time.

---

