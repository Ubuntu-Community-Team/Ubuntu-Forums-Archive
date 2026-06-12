---
title: "Wireless card (ISL3886 Prism) doesn't work upgrading to Ubuntu 10 - Celeron 400"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by gcmelzi on 2010-10-22
Yes, that's correct, it's a Celeron 400 running Xubuntu. And the card was working on 9.10, but not working anymore in 10.04 neither in 10.10

**Wireless Brand, Model and Wireless Chipset**:
```
01:0a.0 Network controller [0280]: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] [1260:3890] (rev 01)
```

**check interface:**
```
wlan0     Link encap:Ethernet  HWaddr 00:60:b3:08:0e:03  
          indirizzo inet:192.168.1.98  Bcast:192.168.1.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::260:b3ff:fe08:e03/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:7309 (7.3 KB)

``````
wlan0     IEEE 802.11bg  ESSID:"SalamediVarzi"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:13:64:17:17:BB   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

**Check for modules:**
```
p54pci                  7571  0 
p54common              25426  1 p54pci
led_class               2633  1 p54common
mac80211              231541  2 p54pci,p54common
cfg80211              144470  2 p54common,mac80211

```
[B]
Kernel boot messages for 'p54'[/B]
```
[   33.149103] p54pci 0000:01:0a.0: enabling device (0014 -> 0016)
[   33.149142] p54pci 0000:01:0a.0: found PCI INT A -> IRQ 11
[   33.149224] p54pci 0000:01:0a.0: sharing IRQ 11 with 0000:01:09.1
[   33.234397] phy0: p54 detected a LM86 firmware
[   33.234420] p54: rx_mtu reduced from 3240 to 2376
[   35.335238] Registered led device: p54-phy0::assoc
[   35.336161] Registered led device: p54-phy0::tx
[   35.337037] Registered led device: p54-phy0::rx
[   35.339740] Registered led device: p54-phy0::radio
[   35.339794] p54pci 0000:01:0a.0: is registered as 'phy0'
```
**Kernel boot messages for 'phy0'**
```
[   33.234397] phy0: p54 detected a LM86 firmware
[   33.234437] phy0: FW rev 2.13.22.0 - Softmac protocol 5.9
[   33.234453] phy0: cryptographic accelerator WEP:YES, TKIP:YES, CCMP:YES
[   34.922225] phy0: hwaddr 00:60:b3:08:0e:03, MAC:isl3890 RF:Frisbee
[   35.319532] phy0: Selected rate control algorithm 'minstrel'
[   35.335238] Registered led device: p54-phy0::assoc
[   35.336161] Registered led device: p54-phy0::tx
[   35.337037] Registered led device: p54-phy0::rx
[   35.339740] Registered led device: p54-phy0::radio
[   35.339794] p54pci 0000:01:0a.0: is registered as 'phy0'
[   37.735265] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
```
[B]
Network configuration[/B]
```
 *-network:0
       description: Wireless interface
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: a
       bus info: pci@0000:01:0a.0
       logical name: wlan0
       version: 01
       serial: 00:60:b3:08:0e:03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=p54pci driverversion=2.6.35-22-generic firmware=N/A ip=192.168.1.98 latency=64 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:11 memory:e1800000-e1801fff
  *-network:1
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: b
       bus info: pci@0000:01:0b.0
       logical name: eth1
       version: 74
       serial: 00:01:02:9e:92:c2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.1.108 latency=64 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
       resources: irq:9 ioport:b400(size=128) memory:e1000000-e100007f memory:e3f00000-e3f1ffff

```

**Scan for networks:**
```
wlan0     Scan completed :
          Cell 01 - Address: 00:13:64:17:17:BB
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"SalamediVarzi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ccdae4fe3
                    Extra: Last beacon: 8168ms ago
                    IE: Unknown: 000D53616C616D6564695661727A69
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD0A0800280101000200FF0F
```

**Ubuntu Version:** ```
Description:    Ubuntu 10.10
```
**Kernel/architecture (including 32 vs. 64 bit):** ```
2.6.35-22-generic i686
```

**Describe the issue:**
My card was working on 9.10 until I decided to upgrade to 10.04. Upgrade showed up 2 main problems: grub -> grub2 and Wireless Card not working, so I decided to make a fresh install with 10.10 (fortunately I've /home on sdb1). 
Initially Wireless Card didn't show up at all even with 10.10: looking into DMESG output I found out a module was missing:
```
 (31.354152] p54pci 0000:01:0a.0: Cannot find firmware (isl3886pci)
```
Searching for **isl3886pci** I found this link [http://wireless.kernel.org/en/users/Drivers/p54](http://wireless.kernel.org/en/users/Drivers/p54) and tried almost all of the suggested drivers, even those not suggested for my kernel version, loading them into the /lib/firmare folder as isl3886pci and modprobing the p54pci module.
This worked, as WLAN0 came up, but I never got connected to any network. 
Through Network Manager I can see SSIDs and configure the card, but it never starts any session. Output from ifcong and iwconfig already posted (it has assigned IP, but it doesn't work even if I specify DHCP).
You see: RX packets:0
Currently I'm playing with 2.13.22.0.arm
Desperate, I removed Network Manager and installed WICD: same exactly result!
I suspected a card fault, but in 15 mins I was able to get it working with Puppy, downloading and mastering time included. 

Below verbose details for the card:  
```
01:0a.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
	Subsystem: Z-Com, Inc. XG-900 and clones Wireless Adapter
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at e1800000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: p54pci
	Kernel modules: p54pci, prism54

```  
prism54 is (obviously) blacklisted in /etc/modprobe.d/blacklist.conf.

I've no other idea and I'm really considering moving back to 9.10
Is there anything else I can check, or you see in posted details, please? 
Thanks a lot in advance.

---

### Post by flash63 on 2010-10-23
Hello,
```
 (31.354152] p54pci 0000:01:0a.0: [COLOR="DarkOrange"]Cannot find firmware[/COLOR] (isl3886pci)
```
you must install the firmware-package
```
sudo apt-get install linux-firmware-nonfree
```

Link:
[http://packages.ubuntu.com/lucid/linux-firmware-nonfree](http://packages.ubuntu.com/lucid/linux-firmware-nonfree)

---

### Post by gcmelzi on 2010-10-23
Thanks for taking care of my post
I gave it a try, but it stull doesnt work: everything looks fine, but RX counter stays on 0 and session doesnt' start, whether I use DHCP or Static IP. 
See below ifconfig output```
wlan0     Link encap:Ethernet  HWaddr 00:60:b3:08:0e:03  
          indirizzo inet6: fe80::260:b3ff:fe08:e03/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:336 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:67682 (67.6 KB)

```
and dmesg output```
[ 1289.747040] wlan0: deauthenticating from 00:13:64:17:17:bb by local choice (reason=3)
[ 1289.758313] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1289.758350] cfg80211: Restoring regulatory settings
[ 1289.758372] cfg80211: Calling CRDA to update world regulatory domain
[ 1289.999781] cfg80211: World regulatory domain updated:
[ 1289.999813]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1289.999835]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1289.999855]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1289.999874]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1289.999893]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1289.999912]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1290.013397] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1291.135311] wlan0: authenticate with 00:13:64:17:17:bb (try 1)
[ 1291.137825] wlan0: authenticated
[ 1291.138331] wlan0: associate with 00:13:64:17:17:bb (try 1)
[ 1291.140534] wlan0: RX AssocResp from 00:13:64:17:17:bb (capab=0x471 status=0 aid=2)
[ 1291.140561] wlan0: associated
[ 1291.143456] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1301.914935] wlan0: no IPv6 routers present

```

Thanks.

---

### Post by flash63 on 2010-10-24
Please scan again and let us schow the output
```
sudo iwlist wlan0 scan
```
Change the Encryption of your Router to
 * WPA-TKIP
or
 * WPA2-AES (CCMP)
and always try to establish a connection. Don't use WPA1/WPA2 or WPA2 with AES/TKIP mixed ecryption.

---

### Post by gcmelzi on 2010-10-24
Here you are the scan output:```
wlan0     Scan completed :
          Cell 01 - Address: 00:13:64:17:17:BB
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"SalamediVarzi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000008659c0121
                    Extra: Last beacon: 644ms ago
                    IE: Unknown: 000D53616C616D6564695661727A69
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD0A0800280101000200FF0F
          Cell 02 - Address: 00:1D:6A:A8:ED:6E
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"Alice-78842990"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002cf95ad81
                    Extra: Last beacon: 120ms ago
                    IE: Unknown: 000E416C6963652D3738383432393930
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010D
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: DD5B0050F204104A0001101044000102103B0001031047001011223344556677889900ABCDEF010203102100001023000010240000104200001054000800060050F2040001101100044147494610080002000110570001001041000100
          Cell 03 - Address: 00:24:89:15:B7:AF
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Vodafone-10629851"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001344ee20af
                    Extra: Last beacon: 1036ms ago
                    IE: Unknown: 0011566F6461666F6E652D3130363239383531
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD760050F204104A00011010440001021041000100103B00010310470010000102030405060708090A0B0C0D0EBB1021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020088
                    IE: Unknown: DD090010180201F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


```
Encryption is normally WEP-128: to avoid any problem I made a test without encryption, but result doesn't change.

---

### Post by gcmelzi on 2010-10-24
Moved back to Network Manager (removing WICD): it started working with no encryption. 
Returned to WEP-128, still working. 

Moving the thread to SOLVED, but I'm still unsure what really solved it. 
Thanks.

---

### Post by Merritt.kr on 2010-12-06
I had the same problem with: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)

Installing linux-firmware-nonfree fixed the problem for me, after rebooting. Thanks!

---

