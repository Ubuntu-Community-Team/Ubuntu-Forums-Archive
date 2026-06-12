---
title: "Yet another FSD7050 USB stick thread"
date: 2009-08-29
forum: Networking &amp; Wireless
---

### Post by wullymonster on 2009-08-29
Hello all.

I have a Belkin FSD7050 wireless G USB stick ver 4002 that came with my Belkin 54g router.

I have gone through many of the procedures outlined in other threads for getting this working and I'm nearly there but I have one more problem.

I have gone the Ndiswrapper route and got the BLKWGU.inf driver installed. Ubuntu does recognise the stick now and it can see a nearby Linksys router but not my Belkin router. I have no trouble connecting automatically to my Belkin using an ethernet cable.

The annoying thing I did have this working a couple of days ago but had to re-install Ubuntu due to knackered hard drive, and I have no idea why it worked the first time.

Here are the uusual outputs.

lsusb
```
Bus 001 Device 003: ID 050d:705c Belkin Components F5D7050 v4000 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0734 Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```dmesg | grep -e wlan -e rtl
```
[   11.215225] wlan0: ethernet device 00:17:3f:fa:d3:09 using NDIS driver: blkwgu, version: 0x6030210, NDIS version: 0x501, vendor: 'Belkin Wireless G USB Network Adapter', 050D:705C.F.conf
[   11.218978] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   17.743954] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```lshw -C network
```
  *-network               
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: a1
       serial: 00:0e:a6:6d:3f:34
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.2.4 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:17:3f:fa:d3:09
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+blkwgu driverversion=1.53+Belkin,11/10/2005,6.3.2.16 multicast=yes wireless=IEEE 802.11g
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 92:75:15:7f:fb:22
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```sudo iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1E:E5:6D:EF:36
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:28/100  Signal level:-78 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

pan0      Interface doesn't support scanning.

```I did try using native drivers and network mnager but had no joy at all so I went with Ndiswrapper and WICD. I have no idea why it can't see the Belkin router.

Thanks

---

### Post by Cuba71 on 2009-08-29
I just bought a Belkin F5D7050 (050d:705a) and it works fine with the Ubuntu native **rt37usb** driver.  Tested under 9.04 Jaunty and 9.10 Karmic and they pick the USB adapter automatically.

---

### Post by wullymonster on 2009-08-30
It does seem as if the ndiswrapper driver is working as it can see wireless networks, just not mine.

Where would I get  rt37usb driver from ?Thanks

---

### Post by Cuba71 on 2009-08-30
rt37usb is a native linux driver bundled within Ubuntu 9.04 and 9.10 Alpha-4.
In my case, all I did was insert the driver in the USB port and boot up the system.  It was recognized by ubuntu without problems.

I tested this adapter in two different computers, a desktop and a laptop with same results.

---

### Post by wullymonster on 2009-09-05
Well I didn't touch it for  a week because I was busy and when I booted it up today it can now see my network without any alterations from me. It can see it using the ralink legacy driver and the ndiswrapper driver, however it( and a neighbouring network) show up as unsecured under the ralink but have the crrect WPA2 info under the ndiswrapper driver.....

But neither of them will connect. I have enabled the encryption and provided the correct passphrase. The ralink driver just says obtaining IP address constantly, and the ndiswrapper say 'putting down network' and then stops and goes back to the WICD manager unconnected.

Aargh!!!.

sudo iwlist scan

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:17:3F:E0:37:D5
                    ESSID:"crotigia"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:100/100  Signal level:-32 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:1E:E5:6D:EF:36
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

pan0      Interface doesn't support scanning.

```dmesg | grep -e wlan -e rtl


```
[   11.451194] wlan0: ethernet device 00:17:3f:fa:d3:09 using NDIS driver: blkwgu, version: 0x6030210, NDIS version: 0x501, vendor: 'Belkin Wireless G USB Network Adapter', 050D:705C.F.conf
[   11.455190] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   18.818357] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   75.874223] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  176.558875] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  189.153338] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  305.187630] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  308.100611] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  309.125145] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  310.170951] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  311.029056] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  312.017992] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  313.216964] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  313.987291] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  315.046390] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  316.050574] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  332.698662] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  334.188115] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  335.007791] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  336.149201] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  350.885893] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  365.904388] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  645.037935] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```lshw -C network

```
  *-network               
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: a1
       serial: 00:0e:a6:6d:3f:34
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.2.4 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:17:3f:fa:d3:09
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+blkwgu driverversion=1.53+Belkin,11/10/2005,6.3.2.16 multicast=yes wireless=IEEE 802.11g
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 96:fe:64:b9:e1:37
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```
Can anyone tell me why this is?.

---

### Post by wullymonster on 2009-09-05
Removed Wicd and put Network manager back on and it connected first time. I'm happy that it works now but I wish it was less of a hassle to set up, a big minus for linux.

---

### Post by NoobieDoobieDo on 2010-03-12
This wifi thing is a total piece.  I've tried for two days and no change.

- linux recognizes it
- i can configure it with iwconfig
- dhcp fails to get an ip address (every single time)

people should know that this isn't a linux problem this thing is just a pos.  i tried the install cd + win2k ("supported" according to the box) and it does the exact same thing.

ima say that again for effect : ** **even with the official drivers / software inside windows this thing does not connect** **

some people have no problem with this thing but spend some time googling and you'll see a *ton* of people cant connect with this pos.  im taking it back tomorrow.

---

### Post by inobe on 2010-03-12
i have two pc's **two** with the same belkin usb sticks and they are flawless each and every time i install linux regardless of flavor !

there is something more sinister happening here

```
Bus 001 Device 002: ID 050d:705c Belkin Components F5D7050 v4000 Wireless Adapter

```

i have no trouble, none

why ndswrapper ? :o

---

