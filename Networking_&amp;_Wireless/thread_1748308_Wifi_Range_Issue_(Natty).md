---
title: "Wifi Range Issue (Natty)"
date: 2011-05-03
forum: Networking &amp; Wireless
---

### Post by khampal on 2011-05-03
Hello,
With most Linux distributions, I can only get a short range to connect my laptop to the wifi. However, when using Ubuntu 10.10, this issue seemed to cure itself and I was able to use wifi in my room. I recently installed Ubuntu 11.04, but suddenly my wifi issues have come back again - I can only connect if I am near my router.

I am using an Intel Wifi 5100. I should also note I can get a wifi connection if I boot into Windows 7.

If anyone has any ideas, I would be most grateful.

---

### Post by jnorthr on 2011-05-03
does it make any difference where your system is located in your room when the reception goes bad.i have found poor reception when in the vicinity of other electrical appliances, TV, microwaves and metal beams in walls that sort of thing. Try different locations to see if that improves your signal .

---

### Post by josephmills on 2011-05-03
ok lets make sure you got a  good driver and all that jazz could we please see a 
```
lspci -nn
```
and a 
```
lshw -c network
```
thanks

---

### Post by khampal on 2011-05-03
Hello, thanks for the replies.

jnorthr: Yes, if I am close to the router I can connect. The problem is that I could get a connection fine when I was on maverick, and on Windows 7 if I was in my room - but not when I switched to natty.

josephmills: thanks, I have attached the files with output of these commands

---

### Post by josephmills on 2011-05-03
Could you please just post copy and paste the them here thanks again 
Jospeh

---

### Post by jnorthr on 2011-05-03
jo - see .txt attachments on rev post.
lshw.txt shows
product: WiFi Link 5100
configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=8.83.5.1 build 33692 ip=192.168.1.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn

and

description: Ethernet interface
configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair

note firmware=N/A does this make any diff on the ethernet interface or is that just unused ?

---

### Post by khampal on 2011-05-03
[QUOTE=josephmills]Could you please just post copy and paste the them here thanks again 
Jospeh[/QUOTE]

Here you go:
```

00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G96 [GeForce 9600M GS] [10de:0648] (rev a1)
02:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
06:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller [11ab:4363] (rev 13)

00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G96 [GeForce 9600M GS] [10de:0648] (rev a1)
02:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
06:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller [11ab:4363] (rev 13)


```
```

  *-network
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:5d:35:56:98
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=8.83.5.1 build 33692 ip=192.168.1.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:46 memory:f6000000-f6001fff
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 13
       serial: 00:13:77:ab:6e:97
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:fa000000-fa003fff ioport:5000(size=256) memory:f4000000-f401ffff


```

---

### Post by josephmills on 2011-05-03
go in your room and do a 
```

iwlist scan 

```
thanks

---

### Post by khampal on 2011-05-03
Thanks, here are the results:
(The network I am trying to connect to is "HMPLWRLSS")
```

wlan0     Scan completed :
          Cell 01 - Address: C4:3D:C7:37:C5:B4
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"virginmedia2471396"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003efb0a7eae
                    Extra: Last beacon: 3244ms ago
                    IE: Unknown: 001276697267696E6D6564696132343731333936
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16010D1100000000000000000000000000000000000000
                    IE: Unknown: DD6F0050F204104A0001101044000102103B000103104700104D73C5C27E6B5243D6440AAB1719670B102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F20400011011000743473331303144100800020088
                    IE: Unknown: DD090010180200F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34010D1100000000000000000000000000000000000000
          Cell 02 - Address: 00:1B:2F:E4:1E:F8
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"HMPLWRLSS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000cb227d4f09
                    Extra: Last beacon: 3204ms ago
                    IE: Unknown: 0009484D504C57524C5353
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1E181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1603051300000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD760050F204104A00011010440001021041000100103B0001031047001086598C149E0C8CCF3A6CDF45CACC46C7102100074E45544745415210230009574E5238333442763210240009574E523833344276321042000230311054000800060050F204000110110009574E52383334427632100800020000
                    IE: Unknown: DD090010180201F0010000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C331E181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3403051300000000000000000000000000000000000000

```

---

### Post by khampal on 2011-05-04
Also, I should note that the network is found in my room - just I cannot connect to it.

---

### Post by josephmills on 2011-05-04
sounds like one of the four handshakes are not touching run traceroute and see if it is your router or your isp or whatever [http://en.wikipedia.org/wiki/Traceroute](http://en.wikipedia.org/wiki/Traceroute)

---

### Post by josephmills on 2011-05-04
you could also run aircrack-ng with cowpatty to see if you can get the four way that way?
[http://www.backtrack-linux.org/forums/backtrack-videos/2394-%5Bvideo%5D-cracking-wifi-wpa-wpa2-aircrack-ng-vs-cowpatty.html](http://www.backtrack-linux.org/forums/backtrack-videos/2394-%5Bvideo%5D-cracking-wifi-wpa-wpa2-aircrack-ng-vs-cowpatty.html)

---

### Post by khampal on 2011-05-06
> **josephmills said:**
> you could also run aircrack-ng with cowpatty to see if you can get the four way that way?
[http://www.backtrack-linux.org/forums/backtrack-videos/2394-%5Bvideo%5D-cracking-wifi-wpa-wpa2-aircrack-ng-vs-cowpatty.html](http://www.backtrack-linux.org/forums/backtrack-videos/2394-%5Bvideo%5D-cracking-wifi-wpa-wpa2-aircrack-ng-vs-cowpatty.html)

Thanks for your help, but I'm a little unsure what you want me to do.

Also, it appears someone else is having the same issue:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/778174](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/778174)

---

### Post by slipp3ryWhippit on 2012-11-01
Hello, Sorry jospehmills I know this is an old thread but I am experiencing the same issues with 12.10 and Intel Centrino wireless-N 2230

I was wondering how you determined the problem from the stack trace from iwlist scan?

I dumped mine below:

iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 00:8E:F2:A5:92:E4
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"cookiemonster"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000067c56000d5
                    Extra: Last beacon: 88288ms ago
                    IE: Unknown: 000D636F6F6B69656D6F6E73746572
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010B9323EDBE7E1DFB3C6F9271B6C875AF5102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F20400011011000743473331303144100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180207F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


Thanks for any help in advance,
Slip

---

