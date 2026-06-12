---
title: "No WPA/WPA2: Atheros AR928X, Jaunty, Acer Extensa 4630Z"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by Andropopolips on 2009-07-09
Hi there,

I've been trawling forums all day but I still can't get WPA1/2 authentication working on my laptop, insanely frustrating. I can connect on WEP or no encryption and my wired controllers working without a hitch but everything I've tried with the wifi has failed.

I'm using 9.04

Here's my system info:

lspci:
```
04:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
```

ifconfig:
```
wlan0     Link encap:Ethernet  HWaddr 00:23:4d:28:69:21  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

iwconfig:
```
wlan0     IEEE 802.11bgn  ESSID:"ranga-net"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lsmod:
```
ath_pci                99224  0 
wlan                  210288  1 ath_pci
ath_hal               198864  1 ath_pci

```

dmesg:
```
[ 8828.550203] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8829.825726] wlan0: authenticate with AP f48256b8
[ 8829.825757] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 8829.827756] wlan0: authenticated
[ 8829.827760] wlan0: associate with AP f48256b8
[ 8829.827766] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
[ 8830.024074] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate

```

lshw:
```
  *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 01
       serial: 00:23:4d:28:69:21
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn

wlan0     Scan completed :
          Cell 01 - Address: 00:22:6B:E9:6C:B5
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"ranga-net"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000022316b180
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 000972616E67612D6E6574
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B071B00000000000000000000000000000000000000
                    IE: Unknown: 3D160B071B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010001000000
                    IE: Unknown: DD7D0050F204104A0001101044000102103B00010210470010E7FE1B918CD5031098DD00226BE96CB5102100074C494E4B535953102300075741473136304E10240007575343303030311042000C3030323236424539364342351054000800060050F20400011011000F4C494E4B5359532D5741473136304E100800020084
```

There you go! Really hope someone can help me out with this, it's been driving me absolutely bonkers.

Cheers!

---

### Post by Andropopolips on 2009-07-09
.

---

### Post by cetheriel on 2009-07-10
same thing here, it used to work until today.
seems to be driver-related.
lspci: ```
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

---

### Post by cooldudei06 on 2009-07-15
I just installed Jaunty on a Toshiba 350 with a AR928X and I couldn't connect to any wireless networks even though it could see them. It would ask for the wireless network password, attempt to connect, and then ask for password again. After searching around the forums I found this post:
[http://ubuntuforums.org/showpost.php?p=7200293&postcount=6](http://ubuntuforums.org/showpost.php?p=7200293&postcount=6)

and after installing linux-backports-modules-jaunty it started working flawlessly. It might help you too.

---

### Post by Andropopolips on 2009-07-18
Looks like my biggest issue was that I'd been playing around with the configuration too much. Did a fresh install and reinstalled wicd and the backports and all is well.

Cheers!

---

### Post by Andropopolips on 2009-08-01
Seems that I was wrong, there wasn't anything wrong with my wireless setup, it seems that the Linksys WAG160N fails hardcore with *nix wifi drivers. I had a chat the the Linksys tech support and they didn't have an answer for me.

Here's my advice:

[SIZE="6"]
IF YOU WANT TO RUN ANYTHING OTHER THAN AN M$ OS DON'T BUY A LINKSYS WAG160N[/SIZE]

---

### Post by wjamoore on 2009-08-24
The problem appears to be related to Wireless N and the ability of wireless abg to connect to it.  (I am speculating but I see nothing else)

I read that wireless N is backwards compatible, but I cannot get it to work.

The clue for me is iwlist scanning

I get:
        Scan completed :
        Cell 01 - Address 00:1F blah blah
        ESSID "NETGEAR"
        mode:Master
        Channel :1
        Frequency:2.412 Ghz (Channel 1)
        Quality 93/100 Signal level: -39dBm  Noise level=-99dBm
        Encryption key:off
       [B] [U]IE:  Unknown:  00074E4554474515  

Repeat with IE Unknown and what looks like Hex for about 16 line[/U]s[/B]
   
        Bit rates: 1 Mb/s --------  to 54 Mb/s
        Extra: tsf=0000000cc4b82c52
        Extra: Last Beacon: 5276ms ago

So far I have seen no information about what IE: unknown is about.

I'd be very grateful if someone could tell me at least that.. Then maybe I can figure out some more

My PC is Acer 2480 with Atheros AR242x 802.11abg wireless card

I have no trouble to get onto wifi hotspots.. just my wireless router..  which is a netgear WRN 2000  802.11N protocol.  I suspect hotspots don't use wireless N (YET), but that doesn't help... with routers now mostly adopting wireless N, the problem will get worse if my hunch is right



Aaron

---

