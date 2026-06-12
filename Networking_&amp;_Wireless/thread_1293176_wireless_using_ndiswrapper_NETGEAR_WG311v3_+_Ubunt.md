---
title: "wireless using ndiswrapper: NETGEAR WG311v3 + Ubuntu 9.04"
date: 2009-10-16
forum: Networking &amp; Wireless
---

### Post by stretch44 on 2009-10-16
[SIZE="3"][B]The heart of the problem:
ndiswrapper seems to work okay, the drivers seem alright.  But iwconfig cannot change essid or key when mode=Managed.[/B][/SIZE]

I've combed through more than a dozen threads on here and LinuxQuestions, following every piece of advice that made sense.  So many promising leads, but still no luck.  (And, yes, I paid special attention to [https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3]("https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3") which speaks directly to my hardware.)

I can get ndiswrapper working.  I load the driver, everything looks good.  But iwconfig commands won't take hold.

[SIZE="4"]My architecture:[/SIZE]
```

> uname -m
i686

```

[SIZE="4"]My wireless card:[/SIZE]
The NetGear WG311v3 54 Mbps PCI
```

> lspci -nn | grep -i wireless
02:02.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless [11ab:1faa] (rev 03)

```

[SIZE="4"]ndiswrapper works:[/SIZE]
```

> ndiswrapper -l
wg311v3 : driver installed
	device (11AB:1FAA) present
> sudo modprobe ndiswrapper
>

```


[SIZE="4"].INF files I have tried[/SIZE]
```

> find . -type f -iname '*.inf' 
./netgear2/WG311v3/WG311v3.INF
./wireless/WG311v3.INF
./netgear/mrv8335.inf
./netgear/WG311v3 V1.0/Driver/Windows 2000/WG311v3.INF
./netgear/WG311v3 V1.0/Driver/Windows XP/WG311v3.INF
./sorbonne/gtnwlan.inf

```
A few mentioned in threads on the forums, 2 from NetGear's homepage.
This last from a search for 88w8335 on [burnthesorbonne.com]("http://www.burnthesorbonne.com/?page_id=32")
None of them caused ndiswrapper or modprobe to complain.

[SIZE="4"]Versions of ndiswrapper I've tried[/SIZE]
Just in case, I tried 2 versions of ndiswrapper, the first from synaptic, the second built from source:
ndiswrapper-utils-1.9
ndiswrapper-1.55 
Both seemed to work fine.

[SIZE="4"]The issue[/SIZE]
```

> ndiswrapper -l
wg311v3 : driver installed
	device (11AB:1FAA) present

> iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:6 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Card is up, scan for the AP:

```

> iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1A:C4:EE:C8:71
                    ESSID:"apt202"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:59/100  Signal level:-58 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

Great! It sees my network (ESSID:apt202) (and, not listed, it sees a few of my neighbors')

Since that all looks good, lets try and use iwconfig to access my network

```

> sudo iwconfig wlan0 mode Managed key restricted s:[ten-digit-numeric-passcode] ESSID apt202
> iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

> sudo iwconfig wlan0 mode Managed key open s:[ten-digit-numeric-passcode] ESSID apt202
> iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

And **here** is the issue!  I can't get iwconfig to permanently effect changes for wlan0.

I've tried directly editing /etc/network/interfaces, to no avail.
(Note: I can set wlan0 to mode: Ad-Hoc, and change the ESSID, but when I revert to mode: Managed, ESSID flips right back to "off/any")

[SIZE="4"]More information about my setup[/SIZE]

lshw -C Network
```

> lshw -C Network
  *-network:0             
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wlan0
       version: 03
       serial: 00:1e:2a:42:d1:35
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wg311v3 driverversion=1.55+NETGEAR,02/22/2005,3.1.1.7 latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:07:e9:b2:ab:62
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=full firmware=N/A ip=192.168.1.66 latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 96:b5:43:f5:c5:ad
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

dmesg | grep -e ndis -e wlan
```

> dmesg | grep -e ndis -e wlan
[  169.253934] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  169.337753] ndiswrapper: driver mrv8335 (TRENDnet,08/22/2005,3.2.1.3) loaded
[  169.338128] ndiswrapper 0000:02:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  169.341868] ndiswrapper: using IRQ 18
[  169.607193] wlan0: ethernet device 00:1e:2a:42:d1:35 using NDIS driver: mrv8335, version: 0x3020002, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 11AB:1FAA.5.conf
[  169.607227] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  169.607331] usbcore: registered new interface driver ndiswrapper
[  175.406862] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  376.641585] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  387.500025] wlan0: no IPv6 routers present
[ 2020.868545] ndiswrapper: device wlan0 removed
[ 2020.868577] ndiswrapper 0000:02:02.0: PCI INT A disabled
[ 2020.868702] usbcore: deregistering interface driver ndiswrapper
[ 2020.894799] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[ 2020.923364] usbcore: registered new interface driver ndiswrapper
[ 2123.449066] usbcore: deregistering interface driver ndiswrapper
[ 2299.793443] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[ 2299.815819] usbcore: registered new interface driver ndiswrapper
[ 2374.255715] usbcore: deregistering interface driver ndiswrapper
[ 3367.502489] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[ 3367.532486] ndiswrapper: driver wg311v3 (NETGEAR,02/22/2005,3.1.1.7) loaded
[ 3367.533647] ndiswrapper 0000:02:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 3367.533669] ndiswrapper 0000:02:02.0: setting latency timer to 64
[ 3367.537057] ndiswrapper: using IRQ 18
[ 3367.797826] wlan0: ethernet device 00:1e:2a:42:d1:35 using NDIS driver: wg311v3, version: 0x3000036, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 11AB:1FAA.5.conf
[ 3367.797855] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 3367.797970] usbcore: registered new interface driver ndiswrapper
[ 3373.408656] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3373.424920] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3384.368020] wlan0: no IPv6 routers present
[ 5575.284434] ndiswrapper: device wlan0 removed
[ 5575.284463] ndiswrapper 0000:02:02.0: PCI INT A disabled
[ 5575.284578] usbcore: deregistering interface driver ndiswrapper
[ 5575.356905] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[ 5575.389449] usbcore: registered new interface driver ndiswrapper
[ 5859.207158] usbcore: deregistering interface driver ndiswrapper
[ 6094.301061] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[ 6094.371764] ndiswrapper: driver wg311v3 (NETGEAR,02/22/2005,3.1.1.7) loaded
[ 6094.372677] ndiswrapper 0000:02:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 6094.372699] ndiswrapper 0000:02:02.0: setting latency timer to 64
[ 6094.375647] ndiswrapper: using IRQ 18
[ 6094.637364] wlan0: ethernet device 00:1e:2a:42:d1:35 using NDIS driver: wg311v3, version: 0x3000036, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 11AB:1FAA.5.conf
[ 6094.637390] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 6094.637489] usbcore: registered new interface driver ndiswrapper
[ 6100.408238] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6100.422866] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6111.136021] wlan0: no IPv6 routers present

```


Any help for this would be so greatly appreciated!  Thanks for your attention!

---

### Post by Trent T on 2009-10-18
I got the Netgear Wg311v3 to work with NDISWrapper under Ubuntu 9.04, by following these instructions at cyberciti;

[http://www.cyberciti.biz/faq/marvell-88w8335-chipset-netgear-wg311-pcicard-driver/](http://www.cyberciti.biz/faq/marvell-88w8335-chipset-netgear-wg311-pcicard-driver/)

This got the LED on the board to light up, AND 
when I checked System --> Administration --> Windows Wireless Drivers, the board showed up with drivers present;

I tried using a terminal command to link it up (details here):
[http://ubuntuforums.org/showthread.php?t=449049&highlight=enpwi-g](http://ubuntuforums.org/showthread.php?t=449049&highlight=enpwi-g)

iwlist wlan0 scan

sudo iwconfig wlan0 ap 00:11:22:33:44:55
(substitute your router address)

but that seemed not to work.

I restarted the computer, entered

sudo modprobe ndiswrapper

and it started up.  The bars show a low speed, but it seems to work well.

Next step is to see if Ubuntu loads my driver when I restart.

Best of luck with your installation!

--Trent T;

PS--
I also tried the procedure outlined by chenxiaolong here;
[http://ubuntuforums.org/showthread.php?t=1266620](http://ubuntuforums.org/showthread.php?t=1266620)

I had hoped to apply it to the Marvell 88w8335 [libertas] chipset vs Broadcomm; Possibly something I did with that process helped me in a way I didn't understand....:confused:
  
PPS--
If you give up on Netgear completely, I had very good luck with a Belkin USB plug-in.  It connected me within minutes after plugging it into a USB port on my machine.  Here is the product info if you are interested;

Belkin Wireless G USB Network Adapter
Model FSD7050
IC:4711A-WN4501H
FCCID: RAXWIN4501H

---

