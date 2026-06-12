---
title: "New Router, wireless problem"
date: 2010-11-08
forum: Networking &amp; Wireless
---

### Post by ramhanuman on 2010-11-08
I am running Ubuntu 10.10 maverick netbook edition on my Dell Latitude D830. I am dual booting windows 7 and ubuntu and recently I bought a Cisco Linksys E2000 router. I set it up with a WPA/WPA2 mixed mode security and My friends are all able to connect to it with no problems. I've been running Ubuntu for a while now and i've never had wireless problems until now. Right now ubuntu is able to connect to the wireless just fine, but once every 10 boots or something the wireless will just not connect no matter what i do. What is the problem?

I have a  Broadcom Corporation:
1)Ethernet Controller: NetXtreme BCM5755M Gigabit ethernet PCI Express (rev 02)
2) Network Controller: BCM4312 802.11b/g LP-PHY (rev 01)

---

### Post by chili555 on 2010-11-08
> I set it up with a WPA/WPA2 mixed modeA lot of drivers, or perhaps Network Manager, have trouble with mixed mode. I suspect you will have better luck with WPA *OR* WPA2.

---

### Post by ramhanuman on 2010-11-09
I've tried wpa2 and wpa, none of them work. Now, it doesn't even connect to the router, I have to use a LAN cable. My computer is able to connect to everyone else's wireless but not my own. What is the problem and how do i fix it?

---

### Post by chili555 on 2010-11-09
Is your router set to automatically use 802.11B, G or N? What does this tell us?```
sudo iwlist wlan0 scan
```Substitute your wireless interface if it's not wlan0.

Do you see your network? Please post the details.

---

### Post by ramhanuman on 2010-11-09
I went to the settings page and the network mode is set to mixed.
I set my Security Mode to WPA.
What do you mean wireless interface? My network card (NetXtreme)?

For some reason when i go to the additional drivers, the B43/STA (i always use the B43 driver) is disabled. I enable the B43, restart and check additional drivers and its disabled again.

---

### Post by ramhanuman on 2010-11-09
bump

---

### Post by chili555 on 2010-11-09
> For some reason when i go to the additional drivers, the B43/STA (i always use the B43 driver) is disabled. Let's try to fix that first. Let's find out if b43 is indeed the correct driver. Please post:```
lspci -nn | grep 4312
dmesg | grep b43
```Thanks.

---

### Post by grahammechanical on 2010-11-09
What chili555 means by network interface is the shorten name for the networking electronics inside the computer. On my machine I have two ethernet or wired network interfaces or devices. They show up as eth0 and eth1. I also have a wireless device built in to the motherboard. It shows up wlan0 = wireless lan 0. LAN = Local Area Network. This is in contrast to WAN, which = Wide Area Network. The Internet is a Wide Area Network. Our computer first forms part of a Local Area Network. Computer connecting to modem. Then it becomes part of a Wide Area Network when we access the Internet through the modem. On some systems the wireless device/interface/network card would show up as rad0 = radio 0. Or may be something else.

Chili555 is saying type in a terminal the code sudo iwlist wlan0 scan or sudo iwlist rad0 scan or whatever your wireless networking device is called. The code instructs the computer to scan for nearby wireless networks and list the information it finds about them. At this moment I have 9 wireless networks transmitting within range of my computer. Two of the are unsecured.

Regards.

---

### Post by ramhanuman on 2010-11-09
lspci -nn | grep 4312
Result:```
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
```

dmesg | grep b43
Result: Nothing


sudo iwlist eth1 scan
Result: ```
eth1    No scan results
```

---

### Post by chili555 on 2010-11-09
Your wireless card is supported by the module *wl*.> BCM4312 802.11b/g LP-PHY [[COLOR="Red"]14e4:4315[/COLOR]]Here is what modinfo has to say:```
modinfo wl | grep 4315
alias:          pci:v0000[COLOR="Red"]14E4[/COLOR]d0000[COLOR="Red"]4315[/COLOR]sv*sd*bc*sc*i*
```Your system won't activate b43 because it's not correct for the device. 

Let's see what kernel messages relate to your problem:```

dmesg | grep -e wl -e wlan
```We're getting closer.

---

### Post by ramhanuman on 2010-11-09
dmesg | grep -e wl -e wlan
```
[   14.697197] wl: module license 'MIXED/Proprietary' taints kernel.
[   14.775067] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.775082] wl 0000:0c:00.0: setting latency timer to 64

```

---

### Post by chili555 on 2010-11-09
It's evidently not creating an interface named wlan0. How about:```
dmesg | grep eth
```

---

### Post by ramhanuman on 2010-11-09
dmesg | grep eth
```
[    2.264654] tg3 0000:09:00.0: eth0: Tigon3 [partno(BCM95755m) rev a002] (PCI Express) MAC address 00:21:70:7b:ad:e3
[    2.264660] tg3 0000:09:00.0: eth0: attached PHY is 5755 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    2.264663] tg3 0000:09:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.264667] tg3 0000:09:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   15.003771] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.60.48.36 
[   16.414720] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.551964] tg3 0000:09:00.0: eth0: Link is up at 1000 Mbps, full duplex
[   19.551969] tg3 0000:09:00.0: eth0: Flow control is on for TX and on for RX
[   19.552222] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   26.952073] eth1: no IPv6 routers present
[   29.616066] eth0: no IPv6 routers present
[16039.328793] tg3 0000:09:00.0: eth0: Link is down
[16059.186483] tg3 0000:09:00.0: eth0: Link is up at 1000 Mbps, full duplex
[16059.186493] tg3 0000:09:00.0: eth0: Flow control is on for TX and on for RX

```

---

### Post by chili555 on 2010-11-09
Please try, temporarily:```
sudo rmmod -f ssb
sudo iwlist eth1 scan
```Let me know the result.




______________

Note for chili555: [http://wiki.debian.org/wl](http://wiki.debian.org/wl)

---

### Post by ramhanuman on 2010-11-09
sudo rmmod -f ssb
```
ERROR: Removing 'ssb': Resource temporarily unavailable

```

sudo iwlist eth1 scan
```
eth1      Interface doesn't support scanning.

```

Which driver should I use, B43 or STA*?
*When I use STA, no wireless connections show up. But when i use B43 i can see all the wireless connections nearby. Also, I'm able to connect to my friend's wireless with no hitch.

---

### Post by chili555 on 2010-11-09
That's the whole question, isn't it. Let's try one and blacklist the other and see if we can solve this. Let's try b43 first. Please do:```
sudo su
echo b43 >> /etc/modules
echo "blacklist wl" >> /etc/modprobe.d/blacklist.conf
exit
```Now reboot and tell me how it works.

---

### Post by ramhanuman on 2010-11-09
i copy pasted that all in but nothing seemed to happen after hitting enter. But i rebooted anyways and there doesn't seem to be any change (when i went into additional drivers, neither b43 or sta is active but i'm connected to my friend's wireless right now). How would I check for change or am i entering in something wrong?

---

### Post by chili555 on 2010-11-09
Let's see what modules are actually loaded:```
lsmod | grep -e wl -e b43 -e ssb
```If you get no output from some of these, they are not loaded. Can you scan for networks and see yours?```
sudo iwlist eth1 scan
sudo iwlist wlan0 scan
```

---

### Post by ramhanuman on 2010-11-09
lsmod | grep -e wl -e b43 -e ssb
```
b43                   169225  0 
mac80211              231541  1 b43
cfg80211              144470  2 b43,mac80211
led_class               2633  1 b43
ssb                    39320  1 b43

```

sudo iwlist eth1 scan
```
eth1      Interface doesn't support scanning.

```

sudo iwlist wlan0 scan
```
wlan0     Scan completed :
          Cell 01 - Address: C0:3F:0E:82:09:35
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"CJ"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000b2dd0d80
                    Extra: Last beacon: 704ms ago
                    IE: Unknown: 0002434A
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406051B00000000000000000000000000000000000000
                    IE: Unknown: 3D1606051B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD870050F204104A0001101044000102103B0001031047001000000000000010000000C03F0E8209351021000D4E6574676561722C20496E632E1023000757504E3832344E1024000456324831104200046E6F6E651054000800060050F20400011011001957504E3832344E28576972656C6573732041502D322E344729100800020086103C000103
          Cell 02 - Address: 68:7F:74:88:28:8C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Ainsley"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000062061b5e
                    Extra: Last beacon: 824ms ago
                    IE: Unknown: 000741696E736C6579
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD930050F204104A00011010440001021041000100103B0001031047001000000000000000011000687F7488288C102100134C696E6B73797320436F72706F726174696F6E102300075752543132304E1024000776312E302E30341042000C4A555430304B3541373538301054000800060050F204000110110014576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 03 - Address: C0:3F:0E:2C:04:B8
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"room310"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000028ccdf80438
                    Extra: Last beacon: 820ms ago
                    IE: Unknown: 0007726F6F6D333130
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B00010310470010203B9A93C3AEE2A8C7ABE1F8BBBBA73C1021000D4E4554474541522C20496E632E10230009574752363134763130102400095747523631347631301042000538333235381054000800060050F204000110110009574752363134763130100800020084
                    IE: Unknown: DD090010180201F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: E6:38:8C:79:8F:27
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:off
                    ESSID:"hpsetup"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0001619f936e11da
                    Extra: Last beacon: 1024ms ago
                    IE: Unknown: 000768707365747570
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 06020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: DD09001018020000010000
          Cell 05 - Address: 68:7F:74:C5:43:14
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"jn316"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001d81c84319e
                    Extra: Last beacon: 316ms ago
                    IE: Unknown: 00056A6E333136
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD6B0050F204104A00011010440001021041000100103B0001031047001000767719EA5275340F0A9F13DB6916DB102100074C696E6B737973102300054531303030102400063132333435361042000234321054000800060050F2040001101100054531303030100800020084
                    IE: Unknown: DD090010180205F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001700000000000000000000000000000000000000
          Cell 06 - Address: 00:0F:66:95:70:5A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"NataliaM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000902bef418b
                    Extra: Last beacon: 812ms ago
                    IE: Unknown: 00084E6174616C69614D
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018010401
          Cell 07 - Address: 68:7F:74:CE:42:8C
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-8 dBm  
                    Encryption key:on
                    ESSID:"GreenLantern"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000076999f189
                    Extra: Last beacon: 248ms ago
                    IE: Unknown: 000C477265656E4C616E7465726E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD810050F204104A00011010440001021041000100103B0001031047001088500070FB30DFB1A28BDA3197C887761021000C4C696E6B73797320496E632E1023000D4C696E6B7379732045323030301024000776312E302E30311042000234321054000800060050F20400011011000D4C696E6B737973204532303030100800020084
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 08 - Address: D8:30:62:33:C0:73
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Chris's Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000463fef9994e
                    Extra: Last beacon: 416ms ago
                    IE: Unknown: 000F43687269732773204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B12
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A2C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C332C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001300000000000000000000000000000000000000
                    IE: Unknown: DD07000393016B0120
          Cell 09 - Address: 00:21:29:AF:F0:B2
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"MEENAggie11"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f013c1ed69
                    Extra: Last beacon: 1136ms ago
                    IE: Unknown: 000B4D45454E41676769653131
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001300000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD720050F204104A0001101044000102103B00010310470010002129AFF0B0002129AFF0B00400E8001021000C4C696E6B73797320496E632E102300075752543136304E1024000876312E30312E3232104200033030301054000800060050F2040001101100075752543136304E100800020088
                    IE: Unknown: DD090010180200F4010000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C331C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001300000000000000000000000000000000000000
          Cell 10 - Address: 00:22:3F:65:B7:D2
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"SLYMER"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000034f79ae3181
                    Extra: Last beacon: 1296ms ago
                    IE: Unknown: 0006534C594D4552
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400030000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101850003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010037FF7F
          Cell 11 - Address: C0:3F:0E:72:B9:DA
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"High-Speed Internet-2.4G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000003107239
                    Extra: Last beacon: 1288ms ago
                    IE: Unknown: 0018486967682D537065656420496E7465726E65742D322E3447
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001B00000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD270050F204104A00011010440001021047001000000000000010000000C03F0E72B9DA103C000103
```

I see my wireless. It's under cell 07, GreenLantern

---

### Post by chili555 on 2010-11-10
I read a post somewhere about Network Manager seeing all networks except your own. A reply suggested you click the Network Manager icon and select set up hidden network; fill in all your details and try to connect.

Another resource I read said to remove Network Manager and install Wicd.

Yet another post said that with Wicd, he sees all networks except his own!

I suggest you try the hidden network technique first, before we perform surgery. If this is a stay-at-home computer, we could always remove NM and hard-code your details in /etc/network/interfaces. 

It looks like b43 is loaded and doing the job for you. I have to believe the underlying problem is actually Network Manager.

---

### Post by ramhanuman on 2010-11-10
see the thing is neither B43 or STA is ACTIVE, both of them are disabled but i can still connect to my friends and other wireless networks. Everyone else can connect to my wireless except me and I'm able to see my wireless through the terminal scan and it shows it to me in the list. I'll try the hidden network method see if that works.

---

### Post by ramhanuman on 2010-11-10
No solutions? bump

---

### Post by chili555 on 2010-11-10
According to lsmod, b43 ***is*** active. What about the hidden network method?

---

### Post by ramhanuman on 2010-11-10
It didn't work. Then why does the additional driver window say neither of them are active? Why am I able to connect to everyone else's wireless except mine?

---

### Post by chili555 on 2010-11-10
> Then why does the additional driver window say neither of them are active?I have no idea. You can see that, according to lsmod, b43 ***is*** active. You know it's working because you can connect.> Why am I able to connect to everyone else's wireless except mine? I suspect Network Manager is not working correctly. See post #20.

---

### Post by ramhanuman on 2010-11-11
i don't know if im using wicd right but it doesn't detect any wireless networks at all, at least network manager can see my wireless.

---

