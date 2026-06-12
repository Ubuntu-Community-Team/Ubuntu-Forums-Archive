---
title: "Broadcom BCM43227 driver activated but not in use"
date: 2012-09-02
forum: Networking &amp; Wireless
---

### Post by teacup123123 on 2012-09-02
Hello everyone. I am new to linux.
The last time I successfully used my wireless card was 2 weeks ago.
I must have done something(upgrade/network setting...) which led to the disappearence of the enable wireless option in my KDE module.

Upon running 
```
sudo lshw -C network
```
I got:

```
*-network               
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: b8:70:f4:a8:a0:3b
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=sb ip=129.104.224.11 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:d1830000-d183ffff memory:d1840000-d184ffff memory:d1850000-d18507ff
  *-network UNCLAIMED
       description: Network controller
       product: BCM43227 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d1a00000-d1a03fff
```

and
Additional drivers:

Broadcom STA proprietary wireless driver

This driver is activated but not currently in use

how do I fix this??
please help!
Thanx a lot

---

### Post by chili555 on 2012-09-02
How about letting us see:```
lspci -nn | grep 0280
rfkill list all
```Thanks.

---

### Post by teacup123123 on 2012-09-02
Here you go
To give you a precision, I'm on the net using ethernet cable, I also activated openvpn, and I have a wireless usb connected to the PC as a substitution. But the problem is about the wireless card inside my laptop

lspci -nn | grep 0280

```
03:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]
```

rfkill list all
```
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: acer-wireless: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: acer-bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
5: phy2: Wireless LAN
        Soft blocked: no
        Hard blocked: no
```

---

### Post by chili555 on 2012-09-02
> Broadcom Corporation BCM43227 802.11b/g/n [[COLOR="Red"]14e4:4358[/COLOR]]Your device is supposed to work with the STA driver. Let's load it and see what interesting messages we find:```
sudo modprobe wl
dmesg | grep wl
iwconfig
```Thanks.

---

### Post by teacup123123 on 2012-09-02
teacup123123@ubuntu:~$ sudo modprobe wl
```
FATAL: Error inserting wl (/lib/modules/3.2.0-29-generic/updates/dkms/wl.ko): Invalid argument
```
teacup123123@ubuntu:~$ dmesg | grep wl
```
[   24.231375] wl: module license 'MIXED/Proprietary' taints kernel.
[   24.232709] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   24.232713] wl: Unknown symbol lib80211_get_crypto_ops (err -22)
[   26.760902] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.761316] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   59.037263] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   59.040243] wlan0: Trigger new scan to find an IBSS to join
[   62.966103] wlan0: Trigger new scan to find an IBSS to join
[   66.963128] wlan0: Trigger new scan to find an IBSS to join
[   68.192997] wlan0: Creating new IBSS network, BSSID 66:13:39:18:16:b9
[   68.245826] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  129.524109] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  129.524591] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  129.968221] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  129.971241] wlan0: Trigger new scan to find an IBSS to join
[  133.928319] wlan0: Trigger new scan to find an IBSS to join
[  137.733348] wlan0: Trigger new scan to find an IBSS to join
[  138.968318] wlan0: Creating new IBSS network, BSSID 1e:b3:b8:26:e6:c4
[  139.041261] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  149.750316] wlan0: no IPv6 routers present
[  564.529617] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  564.530992] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  564.957372] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  564.960488] wlan0: Trigger new scan to find an IBSS to join
[  569.710882] wlan0: Trigger new scan to find an IBSS to join
[  572.918059] wlan0: Creating new IBSS network, BSSID c6:b7:4b:01:dc:ff
[  572.948139] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  583.855508] wlan0: no IPv6 routers present
[  592.644516] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 1
[  592.644533] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 2
[  592.644545] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 3
[ 1208.908451] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1242.972143] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 2
[ 1242.972152] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 1
[ 1242.972158] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 0
[ 1243.005387] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1277.186394] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1317.566525] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1350.309771] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1397.130367] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1453.490011] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1486.916511] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1522.675215] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1561.195640] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1602.613115] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1634.720725] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1666.823861] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1699.968920] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 1
[ 1699.968923] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 2
[ 1699.968925] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 3
[ 1886.281123] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1942.434434] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2422.157526] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2476.613557] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 2
[ 2476.613568] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 1
[ 2476.613575] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 0
[ 2476.632072] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2477.966182] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 1
[ 2477.966194] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 2
[ 2477.966201] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 3
[ 5244.582087] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5275.534191] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 2
[ 5275.534199] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 1
[ 5275.534204] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 0
[ 5296.253097] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5332.786233] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5364.522301] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5371.588628] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 1
[ 5371.588640] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 2
[ 5371.588647] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 3
[ 5614.635067] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5766.551171] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5788.004637] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 2
[ 5788.004646] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 1
[ 5788.004650] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 0
[ 5811.859037] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5844.279321] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5886.477526] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5931.785880] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5964.218681] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6015.911273] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6032.947323] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 1
[ 6032.947334] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 2
[ 6032.947339] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 3
[ 6080.054543] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6113.015670] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 2
[ 6113.015681] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 1
[ 6113.015688] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 0
[ 6113.061338] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6144.337411] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6180.331541] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6219.628353] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6255.796839] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6290.321151] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6324.037257] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6355.551547] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6387.693471] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6401.421278] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 1
[ 6401.421288] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 2
[ 6401.421293] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 3
[ 6443.976493] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6475.916199] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 2
[ 6475.916207] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 1
[ 6475.916212] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 0
[ 6475.955106] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6507.630983] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6549.451528] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6585.811268] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6596.207084] wlan0: Trigger new scan to find an IBSS to join
[ 6599.631529] wlan0: Trigger new scan to find an IBSS to join
[ 6603.629427] wlan0: Trigger new scan to find an IBSS to join
[ 6604.881988] wlan0: Creating new IBSS network, BSSID 46:af:73:75:a8:67
[ 6615.767142] wlan0: no IPv6 routers present
[ 6635.393233] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6669.128025] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6714.436115] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6747.505909] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6781.382739] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6821.297298] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6855.509760] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6887.292157] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6919.570022] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6954.772683] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6986.282154] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7020.671500] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7067.199512] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7068.651019] wl: disagrees about version of symbol lib80211_get_crypto_ops
[ 7068.651025] wl: Unknown symbol lib80211_get_crypto_ops (err -22)
[ 7075.080776] wl: disagrees about version of symbol lib80211_get_crypto_ops
[ 7075.080782] wl: Unknown symbol lib80211_get_crypto_ops (err -22)
[ 7092.815361] wl: disagrees about version of symbol lib80211_get_crypto_ops
[ 7092.815365] wl: Unknown symbol lib80211_get_crypto_ops (err -22)
```
teacup123123@ubuntu:~$ iwconfig
```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Shared_Wireless_Connection"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 46:AF:73:75:A8:67   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.


tun0      no wireless extensions.

```
(wlan0 is the sb wireless card, not what Im'm trying to fix)

---

### Post by chili555 on 2012-09-02
> [   24.232709] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   24.232713] wl: Unknown symbol lib80211_get_crypto_ops (err -22)Uh oh...

By any chance, did you install linux-backports-modules-cw? The 80211 parts there are slightly different from the parts used in the STA driver. As you can see, they conflict and don't allow STA to load and operate.

Do you have Synaptic installed? Search and remove all instances of linux-backports-modules-cw as needed. Then try again:```
sudo modprobe wl
dmesg | grep wl
```

---

### Post by teacup123123 on 2012-09-02
I opened Synaptic Package Manager; typed in the filter  linux-backports-modules-cw
I then saw one box checked and I marked it for complete removal.
and I applied.
It didn't ask me for reboot,
I retyped the same things but I think there is always the problem.

teacup123123@ubuntu:~$ sudo modprobe wl
[sudo] password for teacup123123: 
```
FATAL: Error inserting wl (/lib/modules/3.2.0-29-generic/updates/dkms/wl.ko): Invalid argument
```
teacup123123@ubuntu:~$ dmesg | grep wl
```
[   24.231375] wl: module license 'MIXED/Proprietary' taints kernel.
[   24.232709] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   24.232713] wl: Unknown symbol lib80211_get_crypto_ops (err -22)
[   26.760902] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.761316] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   59.037263] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   59.040243] wlan0: Trigger new scan to find an IBSS to join
[   62.966103] wlan0: Trigger new scan to find an IBSS to join
[   66.963128] wlan0: Trigger new scan to find an IBSS to join
[   68.192997] wlan0: Creating new IBSS network, BSSID 66:13:39:18:16:b9
[   68.245826] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  129.524109] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  129.524591] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  129.968221] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  129.971241] wlan0: Trigger new scan to find an IBSS to join
[  133.928319] wlan0: Trigger new scan to find an IBSS to join
[  137.733348] wlan0: Trigger new scan to find an IBSS to join
[  138.968318] wlan0: Creating new IBSS network, BSSID 1e:b3:b8:26:e6:c4
[  139.041261] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  149.750316] wlan0: no IPv6 routers present
[  564.529617] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  564.530992] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  564.957372] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  564.960488] wlan0: Trigger new scan to find an IBSS to join
[  569.710882] wlan0: Trigger new scan to find an IBSS to join
[  572.918059] wlan0: Creating new IBSS network, BSSID c6:b7:4b:01:dc:ff
[  572.948139] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  583.855508] wlan0: no IPv6 routers present
[  592.644516] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 1
[  592.644533] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 2
[  592.644545] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 3
[ 1208.908451] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1242.972143] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 2
[ 1242.972152] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 1
[ 1242.972158] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 0
[ 1243.005387] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1277.186394] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1317.566525] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1350.309771] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1397.130367] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1453.490011] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1486.916511] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1522.675215] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1561.195640] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1602.613115] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1634.720725] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1666.823861] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1699.968920] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 1
[ 1699.968923] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 2
[ 1699.968925] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 3
[ 1886.281123] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1942.434434] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2422.157526] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2476.613557] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 2
[ 2476.613568] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 1
[ 2476.613575] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 0
[ 2476.632072] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 2477.966182] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 1
[ 2477.966194] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 2
[ 2477.966201] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 3
[ 5244.582087] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5275.534191] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 2
[ 5275.534199] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 1
[ 5275.534204] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 0
[ 5296.253097] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5332.786233] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5364.522301] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5371.588628] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 1
[ 5371.588640] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 2
[ 5371.588647] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 3
[ 5614.635067] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5766.551171] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5788.004637] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 2
[ 5788.004646] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 1
[ 5788.004650] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 0
[ 5811.859037] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5844.279321] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5886.477526] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5931.785880] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5964.218681] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6015.911273] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6032.947323] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 1
[ 6032.947334] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 2
[ 6032.947339] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 3
[ 6080.054543] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6113.015670] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 2
[ 6113.015681] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 1
[ 6113.015688] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 0
[ 6113.061338] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6144.337411] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6180.331541] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6219.628353] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6255.796839] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6290.321151] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6324.037257] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6355.551547] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6387.693471] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6401.421278] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 1
[ 6401.421288] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 2
[ 6401.421293] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 3
[ 6443.976493] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6475.916199] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 2
[ 6475.916207] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 1
[ 6475.916212] wlan0: moving STA 44:2a:60:f6:e0:c8 to state 0
[ 6475.955106] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6507.630983] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6549.451528] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6585.811268] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6596.207084] wlan0: Trigger new scan to find an IBSS to join
[ 6599.631529] wlan0: Trigger new scan to find an IBSS to join
[ 6603.629427] wlan0: Trigger new scan to find an IBSS to join
[ 6604.881988] wlan0: Creating new IBSS network, BSSID 46:af:73:75:a8:67
[ 6615.767142] wlan0: no IPv6 routers present
[ 6635.393233] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6669.128025] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6714.436115] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6747.505909] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6781.382739] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6821.297298] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6855.509760] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6887.292157] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6919.570022] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6954.772683] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 6986.282154] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7020.671500] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7067.199512] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7068.651019] wl: disagrees about version of symbol lib80211_get_crypto_ops
[ 7068.651025] wl: Unknown symbol lib80211_get_crypto_ops (err -22)
[ 7075.080776] wl: disagrees about version of symbol lib80211_get_crypto_ops
[ 7075.080782] wl: Unknown symbol lib80211_get_crypto_ops (err -22)
[ 7092.815361] wl: disagrees about version of symbol lib80211_get_crypto_ops
[ 7092.815365] wl: Unknown symbol lib80211_get_crypto_ops (err -22)
[ 7099.468804] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7132.615339] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7167.287356] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7198.632228] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7247.105527] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7279.370103] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7335.300568] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7367.043521] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 7399.304754] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8019.427629] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8019.429062] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8019.886959] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8019.890144] wlan0: Trigger new scan to find an IBSS to join
[ 8024.899896] wlan0: Trigger new scan to find an IBSS to join
[ 8028.897824] wlan0: Trigger new scan to find an IBSS to join
[ 8030.161692] wlan0: Creating new IBSS network, BSSID f6:11:d6:24:c9:f5
[ 8030.190876] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 8041.107267] wlan0: no IPv6 routers present
[ 8063.157664] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8096.644601] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8135.650425] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8174.880921] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8217.390815] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8248.824661] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8288.794937] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8325.226447] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8357.081208] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8397.291325] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8436.236407] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8474.738048] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8506.456631] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8538.651534] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8581.703629] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8614.917862] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8654.655348] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8685.996372] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 8708.632624] wl: disagrees about version of symbol lib80211_get_crypto_ops
[ 8708.632630] wl: Unknown symbol lib80211_get_crypto_ops (err -22)
[ 8718.549540] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
```

*Thanx a lot pal! I would never have known how to do all this on reading previous posts

---

### Post by chili555 on 2012-09-02
> [   24.232709] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   24.232713] wl: Unknown symbol lib80211_get_crypto_ops (err -22)These are the same messages as before. Please reboot.

---

### Post by teacup123123 on 2012-09-02
Wowwwww! It worked. Thanks a lot mate!:p

---

### Post by chili555 on 2012-09-02
Glad it's working! Please use thread tools at the top to mark Solved.

---

### Post by JohnDragonash on 2012-12-31
I have same problem, with the same Broadcom BCM43227, but don´t work:
sudo lshw -C network
*-network UNCLAIMED
 description:Network controller
 product: BCM43227 802.11b/g/n
 vendor: Boradcom Corporation
 physical id: 0
 bus info: pci@0000:02:00.0
 version: 00
 width: 64 bits
 clock: 33Mhz
 capabilities: bus_master cap_list
 configuration: latency=0
 resources: memory:f0500000-f0503fff
*-network
 desciption: Ethernet interface
 product: NetLink BCM57785 Gigabit Ethernet PCIe
 vendor: Boradcom Corporation
 physical id: 0
 bus info: pci@0000:03:00.0
 logical name: eth0
 version: 10
 serial: 20:6a:8a:6e:df:fb
 capacity: 1Gbit/s
 Width: 64 bits
 clock: 33MHz
 capabilities: bus_master cap_list rom ethernet physical tp 10bt-fd 100bt 100bt-fs 1000bt-fd autonegotiation
 configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 firmware=sb latency=0 multicast=yes port=twisted pair
 resources: irq:19 memory:f0400000-f040ffff memory:f0410000-f041ffff memory:f0450000-f04507ff

sudo modprobe wl
FATAL: Module wl not found
dmesg | grep wl

Hope you can help me, by the way i´m a newbie please treat me well

---

### Post by chili555 on 2012-12-31
> by the way i´m a newbie please treat me wellWe will do our very best. Please get a temporary wired ethernet connection. Open a terminal and do:```
sudo apt-get install linux-headers-generic 
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Is it working now?

---

### Post by slypig on 2013-03-01
@chili555 I am having the same issue, is there anyway to do this without having an internet connection? I only have access to wifi, and am switching between OS's to fix the problem/look for advice.

---

### Post by bellaseem on 2013-03-01
I'm not sure but I think there is... you have to search for the two packages, "linux-headers-generic" and "bcmwl-kernel-source" for  your version of Ubuntu and for your particular system architecture. So if you're running 12.04 go here: 
"http://packages.ubuntu.com/search?keywords=linux-headers-generic" and choose "precise" in the list, if using 12.10 choose "quantal", then download and install them, you might have to also download alot of dependencies if the packages have them so it might be a pain to do it... 
Here's the link for the second package:
[http://packages.ubuntu.com/search?keywords=bcmwl-kernel-source](http://packages.ubuntu.com/search?keywords=bcmwl-kernel-source)
good luck

---

### Post by chili555 on 2013-03-01
> **bellaseem said:**
> I'm not sure but I think there is... you have to search for the two packages, "linux-headers-generic" and "bcmwl-kernel-source" for  your version of Ubuntu and for your particular system architecture. So if you're running 12.04 go here: 
"http://packages.ubuntu.com/search?keywords=linux-headers-generic" and choose "precise" in the list, if using 12.10 choose "quantal", then download and install them, you might have to also download alot of dependencies if the packages have them so it might be a pain to do it... 
Here's the link for the second package:
[http://packages.ubuntu.com/search?keywords=bcmwl-kernel-source](http://packages.ubuntu.com/search?keywords=bcmwl-kernel-source)
good luckCorrect. 

You might also do what I'd do; borrow a USB wireless device from a friend and get connected for a few moments and be done in three minutes. Also, you could simply borrow their ethernet connection!

---

### Post by slypig on 2013-03-01
Thank you both, I wish the cable was an option. I will need to remove both headers and bcm kernel (sudo apt-get remove linux-headers-generic sudo apt-get remove bcmwl-kernel-source)? Or what would be the procedure for doing it this way?

---

### Post by chili555 on 2013-03-01
> **slypig said:**
> Thank you both, I wish the cable was an option. I will need to remove both headers and bcm kernel (sudo apt-get remove linux-headers-generic sudo apt-get remove bcmwl-kernel-source)? Or what would be the procedure for doing it this way?Let's be sure, exactly, what we need. Please post:```
lspci -nn | grep 0280
sudo modprobe wl
dmesg | grep wl
```Let's see if you have a local copy of bcmwl-kernel-source:```
ls /var/cache/apt/archives/ | grep bcmwl
```And let's see if you have the needed headers:```
sudo dpkg -s linux-headers-`uname -r`
```Those tickmarks are on the left side of my US keyboard on the same key with ~.

---

### Post by slypig on 2013-03-01
Ok this is what I got


Also I apologize if I didn't do this correctly, I am not sure how to do this so that it is easier to read. 

lspci -nn | grep 0280
02:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]
sudo modprobe wl
FATAL: Module wl not found.
dmesg | grep wl
nothing
 
ls /var/cache/apt/archives/ | grep bcmwl
nothing
 
sudo dpkg -s linux-headers-`uname -r`
brad@ubuntu:~$ sudo dpkg -s linux-headers-`uname -r`
Package: linux-headers-3.5.0-17-generic
Status: install ok installed
Priority: optional
Section: devel
Installed-Size: 10922
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux
Version: 3.5.0-17.28
Provides: linux-headers, linux-headers-3.0
Depends: linux-headers-3.5.0-17, libc6 (>= 2.14)
Description: Linux kernel headers for version 3.5.0 on 64 bit x86 SMP
 This package provides kernel header files for version 3.5.0 on
 64 bit x86 SMP.
 .
 This is for sites that want the latest kernel headers.  Please read
 /usr/share/doc/linux-headers-3.5.0-17/debian.README.gz for details.


Thank you for the quick response.

---

### Post by chili555 on 2013-03-01
You do have headers, so we're half-way there! You need the 64-bit version of bcmwl-kernel-source: [http://packages.ubuntu.com/quantal/bcmwl-kernel-source](http://packages.ubuntu.com/quantal/bcmwl-kernel-source)

Notice it has several dependencies; the ones I'd be suspicious of are dkms, libc6-dev and linux-libc-dev. You can check if they are installed with:```
sudo dpkg -s <some_package>
```Obviously, substitute the package name in question; for example, dkms. If any are not installed, get them and install them, too. Download the files on a USB drive or similar, drag and drop them to your desktop and install:```
sudo apt-get install Desktop/dkms*.deb
```Continue until the last file to be installed is bcmwl-kernel-source. Then load it and see if your wireless springs to life:```
sudo modprobe wl
```

To enclose text in a code block, highlight it and click the pound sign above. Please see attached. ```
Some code
```

---

### Post by slypig on 2013-03-04
I found out that I needed to install the other files as well. I downloaded the files and transfered them via usb to my Ubuntu desktop when I tried ```
sudo apt-get install Desktop/dkms*.deb
``` I got 

```
brad@ubuntu:~$ sudo apt-get install Desktop/dkms*.deb
Reading package lists... Done
Building dependency tree      
Reading state information... Done
E: Unable to locate package Desktop
```

I feel like I might be making a rookie error here, but I can not figure out what I am doing wrong.

---

### Post by chili555 on 2013-03-04
apt-get is for packages your system will get from the repositories on line. To install a package off-line; that is, on your desktop, use dpkg:```
sudo dpkg -i Desktop/dkms*.deb
```As you might suspect, the -i means 'install.'

---

### Post by insignia92 on 2013-04-24
> **chili555 said:**
> We will do our very best. Please get a temporary wired ethernet connection. Open a terminal and do:```
sudo apt-get install linux-headers-generic 
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Is it working now?


thanks for this one.. I've been looking all over for the right solution.. well to all who are looking for solutions like me, bare in mind that not all shown in the forums are the right solutions for you.. because not all laptops or pc's have the same hardware configuration. etc, etc.. just keep on searching and don't bundle up solutions like doing this solution but didn't work and then added another one.. well it'll just make your problem worse.. well all I have to say is first of all this solution is better when you've just installed Ubuntu.. if it has been weeks already since you've used it.. well this is not the solution go find another because definitely you've done this from the beginning or it has been already configured right after you've installed ubuntu and you've just done something wrong that's why the driver went wrong.. peace to all new ubuntu users! :) Happy bunts!

---

### Post by Venom68 on 2014-02-03
chili555 u r a god! followed ur first instructions and now have my wifi on ubuntu(installed on 8gig flash drive-hrad disk crashed). However, how can get my nvidia graphics working, i am stuck on intel express (switchable graphics card, on acer aspire 5750g)

---

### Post by chili555 on 2014-02-03
You need a graphics god for your video; please check here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

Glad it's working.

---

