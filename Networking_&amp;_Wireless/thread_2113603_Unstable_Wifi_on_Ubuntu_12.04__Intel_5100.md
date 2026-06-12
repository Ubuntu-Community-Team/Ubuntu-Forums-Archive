---
title: "Unstable Wifi on Ubuntu 12.04 / Intel 5100"
date: 2013-02-07
forum: Networking &amp; Wireless
---

### Post by Shenghai on 2013-02-07
Hi, I am having mainting a stable connection on my school's WiFi network. I was wondering if there were any solutions to this.

lspci -```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
	Subsystem: Dell Device [1028:02aa]
	Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
	Subsystem: Dell Device [1028:02aa]
	Kernel driver in use: i915
	Kernel modules: i915
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
	Subsystem: Dell Device [1028:02aa]
00:1a.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
	Subsystem: Dell Device [1028:02aa]
	Kernel driver in use: uhci_hcd
00:1a.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
	Subsystem: Dell Device [1028:02aa]
	Kernel driver in use: uhci_hcd
00:1a.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
	Subsystem: Dell Device [1028:02aa]
	Kernel driver in use: uhci_hcd
00:1a.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
	Subsystem: Dell Device [1028:02aa]
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
	Subsystem: Dell Device [1028:02aa]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
	Subsystem: Dell Device [1028:02aa]
	Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
	Subsystem: Dell Device [1028:02aa]
	Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
	Subsystem: Dell Device [1028:02aa]
	Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
	Subsystem: Dell Device [1028:02aa]
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
	Subsystem: Dell Device [1028:02aa]
	Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] [8086:2929] (rev 03)
	Subsystem: Dell Device [1028:02aa]
	Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
	Subsystem: Dell Device [1028:02aa]
	Kernel modules: i2c-i801
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
	Subsystem: Dell Device [1028:02aa]
	Kernel driver in use: sky2
	Kernel modules: sky2
0c:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
	Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1321]
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi

```

ifconfig```
eth0      Link encap:Ethernet  HWaddr f0:4d:a2:87:ae:ea  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3088 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3088 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:284134 (284.1 KB)  TX bytes:284134 (284.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:d6:9d:4d:10  
          inet addr:128.238.163.1  Bcast:128.238.163.255  Mask:255.255.252.0
          inet6 addr: fe80::224:d6ff:fe9d:4d10/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21325 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21498 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8690051 (8.6 MB)  TX bytes:3274621 (3.2 MB)


```

iwconfig```
lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Poly-Guest"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: 00:24:97:F2:B2:BC   
          Bit Rate=54 Mb/s   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

```

route -n```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         128.238.160.1   0.0.0.0         UG    0      0        0 wlan0
128.238.160.0   0.0.0.0         255.255.252.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0

```

---

### Post by chili555 on 2013-02-07
You might try this: [http://ubuntuforums.org/showthread.php?t=2077293&highlight=11n_disable](http://ubuntuforums.org/showthread.php?t=2077293&highlight=11n_disable)

---

### Post by Shenghai on 2013-02-10
Sorry for the long delay, it did not solve my problem.

---

### Post by ahallubuntu on 2013-02-10
~

---

### Post by Shenghai on 2013-02-11
Hi, I am indeed using a Dell inspiron 1545. Also, I am using ubuntu 12.04lts.

the output of iwlist scan -
```
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:24:97:F5:FC:5E
                    Channel:153
                    Frequency:5.765 GHz (Channel 153)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"Poly-WiFi"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005b68432c035
                    Extra: Last beacon: 15832ms ago
                    IE: Unknown: 0009506F6C792D57694669
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 071255532024041134041864051884031895051E
                    IE: Unknown: 0B050B00088D5B
                    IE: Unknown: 2D1A6E181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3D1699000700000000000000000000000000000000000000
                    IE: Unknown: 851E06008F000F00FF0359004469626E657230342D303100000000000B000035
                    IE: Unknown: 9606004096000E00
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404

eth0      Interface doesn't support scanning.

```

edit - Also, the issue has occur with public networks as I has occur more than once in different locations.

---

### Post by ahallubuntu on 2013-02-11
~

---

### Post by Shenghai on 2013-02-13
Hi,
Thanks for the help but it seems the problem all along was that I would always suspend my computer instead of properly shutting it down. That seems to have caused the problem, now that I am properly shutting and opening my computer the problem is gone.

---

### Post by Shenghai on 2013-02-15
Seems like I spoke too soon, as the problem has popped up again.
The connections always seems to be fine for a few seconds but then I lose connection even though it states that I am connected still. This seems to be a random event as occasionally I can stay connected for hours while other times, I lose it after 5 seconds.

---

