---
title: "Rosewill (Ralink 2800) sees networks but cannot join."
date: 2010-07-09
forum: Networking &amp; Wireless
---

### Post by macdudeosx on 2010-07-09
I have a PCI Rosewill RNX-N300X wireless N card on Ubuntu 10.04 Kernel 2.6.32-23. The card can see wireless networks, but it cannot join my network with a WPA password (yes I am putting the right password in) and I do have wpasupplicant installed.  Any help appreciated! 

lspci -v | less gives:
```
  04:03.0 Network controller: RaLink RT2800 802.11n PCI
        Subsystem: RaLink Device 2860
        Flags: bus master, slow devsel, latency 32, IRQ 16
        Memory at fdaf0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: rt2860
        Kernel modules: rt2860sta
 
```That "Capabilities: <access denied>" does not look good. Is that supposed to be denied?

iwconfig gives:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.462 GHz  Access Point: 00:24:36:A6:57:B9   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-60 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```ifconfig gives:

```
wlan0     Link encap:Ethernet  HWaddr 00:1a:ef:09:16:9a  
          inet6 addr: fe80::21a:efff:fe09:169a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:15984 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3147 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3617118 (3.6 MB)  TX bytes:0 (0.0 B)
          Interrupt:16 
```sudo lshw -C network gives:

```
*-network
       description: Wireless interface
       product: RT2800 802.11n PCI
       vendor: RaLink
       physical id: 3
       bus info: pci@0000:04:03.0
       logical name: wlan0
       version: 00
       serial: 00:1a:ef:09:16:9a
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=32 maxlatency=4 mingnt=2 multicast=yes wireless=RT2860 Wireless
       resources: irq:16 memory:fdaf0000-fdafffff

```iwlist scan gives:
```

wlan0     Scan completed :
          Cell 01 - Address: 00:22:A4:76:C5:49
                    Protocol:802.11b/g
                    ESSID:"2WIRE266"
                    Mode:Managed
                    Channel:5
                    Quality:20/100  Signal level:-82 dBm  Noise level:-87 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
          Cell 02 - Address: 00:24:36:A6:57:B9
                    Protocol:802.11b/g/n
                    ESSID:"Richardson Net"
                    Mode:Managed
                    Channel:11
                    Quality:76/100  Signal level:-60 dBm  Noise level:-87 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 06:24:36:A6:57:B9
                    Protocol:802.11b/g/n
                    ESSID:"Richardson's Guest Network"
                    Mode:Managed
                    Channel:11
                    Quality:76/100  Signal level:-60 dBm  Noise level:-87 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK



```

---

### Post by macdudeosx on 2010-07-11
Ok, it works 1 out of 15 boots, but even then it will drop out of the network after 5 minutes of use. Its not interference as I am right next to the router.

---

### Post by macdudeosx on 2010-07-13
Anyone? This is getting really annoying. There is no reason it should not work.

I also tried RutilT but it only gives me the option to use WEP encryption even though it should give me WPA encryption options too. Apparently it has something to do with newer kernels.

---

### Post by bazzal1941 on 2010-07-13
Didn't go through all your logs but there appears to be a problem with RealTek chips in 10.04 when trying to connect with WPA.

Have a look at this as it helped me.

[http://ubuntuforums.org/showthread.php?t=1476007]("http://ubuntuforums.org/showthread.php?t=1476007")

If not there are several forums on this topic.

---

### Post by macdudeosx on 2010-07-14
Yeah, that post completely fixed it, thanks. 

I dont know how I missed it, I looked all over the internet :P.

---

