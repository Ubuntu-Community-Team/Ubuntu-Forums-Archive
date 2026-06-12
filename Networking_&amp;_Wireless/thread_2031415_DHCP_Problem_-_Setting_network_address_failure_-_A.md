---
title: "DHCP Problem - Setting network address failure - Atheros AR9285"
date: 2012-07-21
forum: Networking &amp; Wireless
---

### Post by dashinhi on 2012-07-21
Hi folks, I keep dipping my toes into the *nix pool every now and again, but I've never gotten beyond casual wading, so I'm quite definitly a Kubuntu neophyte (in the beginner sense, not the convert sense - I haven't abandoned Windows ... yet.).

I'm having a problem with getting an ip address through DHCP - I can get online if I set a static IP address, but I can't do that for every network I use, so I need to resolve this DHCP issue. I've searched the forums but haven't found this specific issue resolved, perhaps due to lack of information from the OPs, so I'm going to more-or-less faithfully (but not slavishly) follow the "How-To post a Wireless issue" suggestions.

I'm going to mask potentially identifying information - it's not that I don't trust YOU, it's that other guy over there. No, not you, the OTHER other guy. ;-)

I'm running a HP G60-535DX Laptop dual booting with Windows 7/Kubuntu 12.04 LTS (3.2.0-23-generic x86_64), using a Atheros AR9285 with the ath9k driver for wifi. The router I'm attempting to connect to is a Linksys WRT54GS v.7 running DD-WRT v24-sp2 micro. I can connect to it with other computers, and even with the G60 when I boot into Windows. I've tried power cycling the router, but that hasn't done the trick. Tried restarting the network via "sudo /etc/init.d/networking restart" and "sudo ifconfig wlan0 down" followed by "sudo ifconfig wlan0 up". No luck with either. I haven't tested other networks yet, so I don't know if the problem is localized to my home network. This is a fresh install of Kubuntu - with all recent updates applied.

iwconfig output
```

$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"Homenet"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:10:xx:xx:xx
          Bit Rate=54 Mb/s   Tx-Power=15 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:24   Missed beacon:0

```lsmod output
```

$ lsmod | grep ath9k
ath9k                 132390  0
mac80211              506816  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
cfg80211              205544  3 ath9k,mac80211,ath

```dmesg output
```

$ dmesg | grep ath9k
[   12.667482] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.667498] ath9k 0000:02:00.0: setting latency timer to 64
[   12.850575] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   12.895726] Registered led device: ath9k-phy0

$ dmesg | grep wlan0
[   13.472187] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.473253] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.282079] wlan0: authenticate with 00:1C:10:xx:xx:xx (try 1)
[   36.284054] wlan0: authenticated
[   36.284310] wlan0: associate with 00:1C:10:xx:xx:xx (try 1)
[   36.287078] wlan0: RX AssocResp from 00:1C:10:xx:xx:xx (capab=0x411 status=0 aid=3)
[   36.287081] wlan0: associated
[   36.287788] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   46.816031] wlan0: no IPv6 routers present
[   82.212280] wlan0: deauthenticating from 00:1C:10:xx:xx:xx by local choice (reason=3)
[   85.877652] wlan0: authenticate with 00:1C:10:xx:xx:xx (try 1)
[   85.879599] wlan0: authenticated
[   85.898107] wlan0: associate with 00:1C:10:xx:xx:xx (try 1)
[   85.900939] wlan0: RX ReassocResp from 00:1C:10:xx:xx:xx (capab=0x411 status=0 aid=3)
[   85.900943] wlan0: associated
[   96.384045] wlan0: no IPv6 routers present
[  131.207812] wlan0: deauthenticating from 00:1C:10:xx:xx:xx by local choice (reason=3)
[  134.885666] wlan0: authenticate with 00:1C:10:xx:xx:xx (try 1)
[  134.887631] wlan0: authenticated
[  134.906237] wlan0: associate with 00:1C:10:xx:xx:xx (try 1)
[  134.909073] wlan0: RX ReassocResp from 00:1C:10:xx:xx:xx (capab=0x411 status=0 aid=3)
[  134.909076] wlan0: associated

```lshw output
```

$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:26:2d:xx:xx:xx
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:3000(size=256) memory:d0410000-d0410fff memory:d0400000-d040ffff memory:d0420000-d043ffff

  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 90:4c:e5:xx:xx:xx
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-26-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d2600000-d260ffff

```iwlist output
```

$ iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1C:10:xx:xx:xx
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=63/70  Signal level=-47 dBm
                    Encryption key:on
                    ESSID:"Homenet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000420b85183
                    Extra: Last beacon: 24388ms ago
                    IE: Unknown: 000D5379656C6F646F726368617264
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

```So, any suggestions?

Doug

---

### Post by dashinhi on 2012-07-24
A bump and a new bit of info.

I lugged this beastie over to my parents' house and was able to access their network without any trouble using DHCP. Only difference in the networks is that my folks' router is a WRT54GS v.6, while mine is a v.7. Both have the same SSID and passcode. So it only seems to be wonky on this OS on MY laptop on MY network. And I thought I was puzzled before...

Anyone have any thoughts?

---

