---
title: "Trendnet TEW-423PI, Ubuntu 10.04"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by ChampionSleeper on 2010-09-09
I am new to linux and trying to get my Trendnet TEW-423PI C1.2R card to work.  I have followed the troubleshooting guide except I was unable to get step 7 (reinstall ndiswrapper from source) to work as instructed so I uninstalled and reinstalled with the synaptic package manager.

Right now, the driver and hardware are recognized; but I can't "see" any wireless networks.  I am not sure what is causing this issue, although the output of sudo /etc/init.d/networking restart: seemed to give errors (see bottom of post).

I have spent quite a bit of time googling, but didn't quite find an answer that pertained to my problem.  Any ideas?
Thanks in advance-
Paul

AMD Athlon 64 3500+ w 2 GB RAM

**ndiswrapper -l**:
```
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
net8185 : driver installed
    device (10EC:8185) present

```[B]
lspci:[/B]
```
04:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

```**lsusb:**
```
Bus 002 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```[B]
iwconfig wlan0:[/B]
```
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:46 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```[B]

lsmod | grep ndis:[/B]
```
ndiswrapper           184677  0 
```[B]
dmesg | grep -e ndis -e wlan:[/B]
```
[   14.142254] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   15.084422] ndiswrapper: driver net8185 (Realtek,02/01/2007,5.1097.0201.2007) loaded
[   15.085004] ndiswrapper 0000:04:07.0: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
[   15.179365] ndiswrapper: using IRQ 18
[   17.336653] wlan0: ethernet device ff:ff:ff:ff:ff:ff using NDIS driver: net8185, version: 0x50449, NDIS version: 0x500, vendor: 'Realtek RTL8185 Wireless LAN (Mini-)PCI NIC                                     ', 10EC:8185.5.conf
[   17.777082] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   17.778529] usbcore: registered new interface driver ndiswrapper
[   27.916021] wlan0: no IPv6 routers present

```[B]
sudo lshw -C network:[/B]
  ```
*-network               
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:04:07.0
       logical name: wlan0
       version: 20
       serial: ff:ff:ff:ff:ff:ff
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8185 driverversion=1.55+Realtek,02/01/2007,5.1097.0 latency=64 link=no maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11g
       resources: irq:18 ioport:e800(size=256) memory:feb7fc00-feb7ffff
```**iwlist scan:**
```
wlan0     No scan results
```[B]
lsb_release -d[/B]
```
Description:    Ubuntu 10.04.1 LTS
```[B]
uname -mr[/B]:
```
2.6.32-24-generic i686
```[B]
sudo /etc/init.d/networking restart[/B]:
  ```
* Reconfiguring network interfaces...                                                                           
 /etc/network/interfaces:2: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:2: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"
```

---

### Post by ChampionSleeper on 2010-09-09
Btw, my interface file is as shown below:

```
#The Primary network interface
Iface wlan0 inet dhcp

auto lo
iface lo inet loopback
```

---

### Post by ChampionSleeper on 2010-09-09
Any ideas?

---

