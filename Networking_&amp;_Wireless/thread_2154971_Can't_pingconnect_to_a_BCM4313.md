---
title: "Can't ping/connect to a BCM4313"
date: 2013-06-16
forum: Networking &amp; Wireless
---

### Post by sushi80 on 2013-06-16
Hi All,

I couldn't find a solution in other topic so here my problem

I have a Lenovo G580 with a fresh Ubuntu 13.04 install 

Ethernet works fine, and after activate the Additional Drivers Broadcom linux STA i can connect and download with my wifi BCM4313

The problem is that i can't connect to my wifi, it dosn't reply to ping or any network service!! 

This is not a Firewall issue (is not running at the moment) and i can connect to the cable Lan!


here some details of my laptop

```


*************** info trace ***************


***** uname -a *****


Linux ivan-Lenovo-G580 3.8.0-25-generic #37-Ubuntu SMP Thu Jun 6 20:47:07 UTC 20
13 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Linux-Secure-Remix-64bit 20may2013
Release:    13.04
Codename:    raring


***** lspci *****


02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wire
less LAN Controller [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0587]
    Kernel driver in use: wl
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8162 Fast Ethernet [1969:
1090] (rev 10)
    Subsystem: Lenovo Device [17aa:3978]
    Kernel driver in use: alx


***** lsusb *****


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0489:e032 Foxconn / Hon Hai 
Bus 001 Device 004: ID 5986:0295 Acer, Inc 
Bus 002 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader


***** iwconfig *****


eth1      IEEE 802.11abg  ESSID:"TP-LINK_POCKET"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>
   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


***** rfkill *****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


***** lsmod *****


wl                   3074449  0 
lib80211               14352  2 wl,lib80211_crypt_tkip
cfg80211              510937  1 wl


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         off




- Device: eth1  [TP-LINK_POCKET] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           58 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    UPC453404:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, 
Strength 50 WPA
    UPC732899:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, 
Strength 45 WPA
    HP-Print-4B-LaserJet M1217: Infra, <MAC address removed>, Freq 2437 MHz, Rat
e 54 Mb/s, Strength 39
    *TP-LINK_POCKET: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, 
Strength 82 WPA WPA2
    UPC306012:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, 
Strength 12 WPA
    TP-LINK_7817DE:  Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, 
Strength 24 WPA WPA2
    UPC1382336:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, 
Strength 22 WPA WPA2
    UPC869042:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, 
Strength 17 WPA


  IPv4 Settings:
    Address:         192.168.0.105
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.254


    DNS:             192.168.0.254






***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


***** iwlist *****




***** resolv.conf *****


nameserver 127.0.1.1


***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


***** dmesg *****


[   13.661588] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.702824] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   13.976385] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.20.155
.1 (r326264)
[ 4889.818280] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[ 4889.818284] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[ 4889.818289] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[ 4889.818290] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[ 4889.818294] ERROR @wl_dev_intvar_get : error (-1)
[ 4889.818296] ERROR @wl_cfg80211_get_tx_power : error (-1)


****************** done ******************


```

---

### Post by chili555 on 2013-06-16
I believe 'Additional Drivers' is the incorrect driver for your device. Please open a terminal and do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -r wl
sudo modprobe brcmsmac
```Any improvement? It may take a reboot.

---

### Post by sushi80 on 2013-06-16
hi chili555

thanks for you replay

i tried removing [COLOR=#000000][FONT=Ubuntu Mono]bcmwl-kernel-source but now the wifi connection is completely gone!!

after the reboot i can only connect using the cable!

by the way it seems that i can't ping any device on my network but the other devices dont have any problem[/FONT][/COLOR]

---

### Post by chili555 on 2013-06-16
Please run and post:```
iwconfig
nm-tool
lsmod | grep -e wl -e brcmsmac
cat /etc/resolv.conf
```Thanks.

---

### Post by sushi80 on 2013-06-17
Hi Chili555

Now the connection goes up and down, sometimes i can connect and get an ip from my router but after few seconds is gone again!


iwconfig
```
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"TP-LINK_POCKET"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: F8:D1:11:9E:80:A8   
          Bit Rate=1 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:2   Missed beacon:0



```
```

NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        3C:97:0E:37:88:11


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




- Device: wlan0  [TP-LINK_POCKET] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:        C0:14:3D:C7:88:35


  Capabilities:
    Speed:           26 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *TP-LINK_POCKET: Infra, F8:D1:11:9E:80:A8, Freq 2412 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2


  IPv4 Settings:
    Address:         192.168.0.105
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.254


    DNS:             192.168.0.254

```
```
 
lsmod | grep -e wl -e brcmsmac
brcmsmac              550698  0 
cordic                 12574  1 brcmsmac
brcmutil               14755  1 brcmsmac
mac80211              606457  1 brcmsmac
cfg80211              510937  2 brcmsmac,mac80211
wl                   2573614  0 
lib80211               14352  1 wl
bcma                   41051  1 brcmsmac

```


cat /etc/resolv.conf
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
```

---

### Post by chili555 on 2013-06-17
>  
lsmod | grep -e wl -e brcmsmac
brcmsmac              550698  0 
cordic                 12574  1 brcmsmac
brcmutil               14755  1 brcmsmac
mac80211              606457  1 brcmsmac
cfg80211              510937  2 brcmsmac,mac80211
[COLOR="#FF0000"]wl[/COLOR]                   2573614  0 
lib80211               14352  1 [COLOR="#FF0000"]wl[/COLOR]
bcma                   41051  1 brcmsmac

It looks like wl is not cleanly removed and is probably interfering. Please try again:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -r wl
```How about now?

---

### Post by sushi80 on 2013-06-18
So i tried again to remove bcmwl kernel and there was nothing to remove but wl was still showing in in lsmod so i've added a line in blacklist

blacklist wl
blacklist lib80211

now the result of lsmod | grep -e wl -e brcmsmac is this:


brcmsmac              550698  0 
cordic                 12574  1 brcmsmac
brcmutil               14755  1 brcmsmac
mac80211              606457  1 brcmsmac
cfg80211              510937  2 brcmsmac,mac80211
bcma                   41051  1 brcmsmac


but still no connection!

---

### Post by chili555 on 2013-06-18
Let's see:```
iwconfig
dmesg | grep wlan
nm-tool
```Thanks.

---

### Post by sushi80 on 2013-06-18
Ok so now after 3/4 min the wifi connects to my AP, i get an IP but the connection is very weak and goes up and down.

 iwconfig
```
 
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off



```

dmesg |grep wlan
```

[   22.515064] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.515332] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  176.509093] wlan0: authenticate with f8:d1:11:9e:80:a8
[  176.510574] wlan0: send auth to f8:d1:11:9e:80:a8 (try 1/3)
[  176.711945] wlan0: send auth to f8:d1:11:9e:80:a8 (try 2/3)
[  176.915722] wlan0: send auth to f8:d1:11:9e:80:a8 (try 3/3)
[  176.917831] wlan0: authenticated
[  176.919726] wlan0: associate with f8:d1:11:9e:80:a8 (try 1/3)
[  176.923522] wlan0: RX AssocResp from f8:d1:11:9e:80:a8 (capab=0x431 status=0 aid=1)
[  176.924079] wlan0: associated
[  176.924115] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  180.538736] wlan0: deauthenticated from f8:d1:11:9e:80:a8 (Reason: 6)
[  185.000850] wlan0: authenticate with f8:d1:11:9e:80:a8
[  185.002135] wlan0: send auth to f8:d1:11:9e:80:a8 (try 1/3)
[  185.203549] wlan0: send auth to f8:d1:11:9e:80:a8 (try 2/3)
[  185.407349] wlan0: send auth to f8:d1:11:9e:80:a8 (try 3/3)
[  185.611145] wlan0: authentication with f8:d1:11:9e:80:a8 timed out
[  186.574682] wlan0: authenticate with f8:d1:11:9e:80:a8
[  186.576535] wlan0: send auth to f8:d1:11:9e:80:a8 (try 1/3)
[  186.777992] wlan0: send auth to f8:d1:11:9e:80:a8 (try 2/3)
[  186.981762] wlan0: send auth to f8:d1:11:9e:80:a8 (try 3/3)
[  187.185567] wlan0: authentication with f8:d1:11:9e:80:a8 timed out
[  188.149629] wlan0: authenticate with f8:d1:11:9e:80:a8
[  188.150985] wlan0: send auth to f8:d1:11:9e:80:a8 (try 1/3)
[  188.352406] wlan0: send auth to f8:d1:11:9e:80:a8 (try 2/3)
[  188.556231] wlan0: send auth to f8:d1:11:9e:80:a8 (try 3/3)
[  188.759997] wlan0: authentication with f8:d1:11:9e:80:a8 timed out
[  189.723597] wlan0: authenticate with f8:d1:11:9e:80:a8
[  189.725392] wlan0: send auth to f8:d1:11:9e:80:a8 (try 1/3)
[  189.727985] wlan0: authenticated
[  189.731063] wlan0: associate with f8:d1:11:9e:80:a8 (try 1/3)
[  189.934846] wlan0: associate with f8:d1:11:9e:80:a8 (try 2/3)
[  190.138664] wlan0: associate with f8:d1:11:9e:80:a8 (try 3/3)
[  190.342468] wlan0: association with f8:d1:11:9e:80:a8 timed out
[  197.164532] wlan0: authenticate with f8:d1:11:9e:80:a8
[  197.166106] wlan0: send auth to f8:d1:11:9e:80:a8 (try 1/3)
[  197.367547] wlan0: send auth to f8:d1:11:9e:80:a8 (try 2/3)
[  197.571317] wlan0: send auth to f8:d1:11:9e:80:a8 (try 3/3)
[  197.775082] wlan0: authentication with f8:d1:11:9e:80:a8 timed out
[  198.739200] wlan0: authenticate with f8:d1:11:9e:80:a8
[  198.740576] wlan0: send auth to f8:d1:11:9e:80:a8 (try 1/3)
[  198.941969] wlan0: send auth to f8:d1:11:9e:80:a8 (try 2/3)
[  199.145762] wlan0: send auth to f8:d1:11:9e:80:a8 (try 3/3)
[  199.349568] wlan0: authentication with f8:d1:11:9e:80:a8 timed out
[  200.313550] wlan0: authenticate with f8:d1:11:9e:80:a8
[  200.314990] wlan0: send auth to f8:d1:11:9e:80:a8 (try 1/3)
[  200.516377] wlan0: send auth to f8:d1:11:9e:80:a8 (try 2/3)
[  200.720169] wlan0: send auth to f8:d1:11:9e:80:a8 (try 3/3)
[  200.924007] wlan0: authentication with f8:d1:11:9e:80:a8 timed out
[  201.887748] wlan0: authenticate with f8:d1:11:9e:80:a8
[  201.889582] wlan0: send auth to f8:d1:11:9e:80:a8 (try 1/3)
[  202.090832] wlan0: send auth to f8:d1:11:9e:80:a8 (try 2/3)
[  202.294652] wlan0: send auth to f8:d1:11:9e:80:a8 (try 3/3)
[  202.498414] wlan0: authentication with f8:d1:11:9e:80:a8 timed out
[  215.178560] wlan0: authenticate with f8:d1:11:9e:80:a8
[  215.180252] wlan0: send auth to f8:d1:11:9e:80:a8 (try 1/3)
[  215.381709] wlan0: send auth to f8:d1:11:9e:80:a8 (try 2/3)
[  215.585492] wlan0: send auth to f8:d1:11:9e:80:a8 (try 3/3)
[  215.789273] wlan0: authentication with f8:d1:11:9e:80:a8 timed out
[  216.753438] wlan0: authenticate with f8:d1:11:9e:80:a8
[  216.754720] wlan0: send auth to f8:d1:11:9e:80:a8 (try 1/3)
[  216.956149] wlan0: send auth to f8:d1:11:9e:80:a8 (try 2/3)
[  217.159951] wlan0: send auth to f8:d1:11:9e:80:a8 (try 3/3)
[  217.363757] wlan0: authentication with f8:d1:11:9e:80:a8 timed out
[  224.186019] wlan0: authenticate with f8:d1:11:9e:80:a8
[  224.187387] wlan0: direct probe to f8:d1:11:9e:80:a8 (try 1/3)
[  224.388806] wlan0: direct probe to f8:d1:11:9e:80:a8 (try 2/3)
[  224.592608] wlan0: direct probe to f8:d1:11:9e:80:a8 (try 3/3)
[  224.796371] wlan0: authentication with f8:d1:11:9e:80:a8 timed out
[  225.764056] wlan0: authenticate with f8:d1:11:9e:80:a8
[  225.765790] wlan0: send auth to f8:d1:11:9e:80:a8 (try 1/3)
[  225.967275] wlan0: send auth to f8:d1:11:9e:80:a8 (try 2/3)
[  226.171032] wlan0: send auth to f8:d1:11:9e:80:a8 (try 3/3)
[  226.374847] wlan0: authentication with f8:d1:11:9e:80:a8 timed out
[  227.338938] wlan0: authenticate with f8:d1:11:9e:80:a8
[  227.340308] wlan0: direct probe to f8:d1:11:9e:80:a8 (try 1/3)
[  227.541692] wlan0: direct probe to f8:d1:11:9e:80:a8 (try 2/3)
[  227.745488] wlan0: direct probe to f8:d1:11:9e:80:a8 (try 3/3)
[  227.949287] wlan0: authentication with f8:d1:11:9e:80:a8 timed out
[  238.587182] wlan0: authenticate with f8:d1:11:9e:80:a8
[  238.589020] wlan0: send auth to f8:d1:11:9e:80:a8 (try 1/3)
[  238.790539] wlan0: send auth to f8:d1:11:9e:80:a8 (try 2/3)
[  238.994324] wlan0: send auth to f8:d1:11:9e:80:a8 (try 3/3)
[  239.198124] wlan0: authentication with f8:d1:11:9e:80:a8 timed out
[  240.161560] wlan0: authenticate with f8:d1:11:9e:80:a8
[  240.163475] wlan0: send auth to f8:d1:11:9e:80:a8 (try 1/3)
[  240.365013] wlan0: send auth to f8:d1:11:9e:80:a8 (try 2/3)
[  240.568796] wlan0: send auth to f8:d1:11:9e:80:a8 (try 3/3)
[  240.772564] wlan0: authentication with f8:d1:11:9e:80:a8 timed out
[  259.318776] wlan0: authenticate with f8:d1:11:9e:80:a8
[  259.320524] wlan0: direct probe to f8:d1:11:9e:80:a8 (try 1/3)
[  259.522040] wlan0: direct probe to f8:d1:11:9e:80:a8 (try 2/3)
[  259.725828] wlan0: direct probe to f8:d1:11:9e:80:a8 (try 3/3)
[  259.929619] wlan0: authentication with f8:d1:11:9e:80:a8 timed out
[  260.893080] wlan0: authenticate with f8:d1:11:9e:80:a8
[  260.894989] wlan0: send auth to f8:d1:11:9e:80:a8 (try 1/3)
[  261.096494] wlan0: send auth to f8:d1:11:9e:80:a8 (try 2/3)
[  261.300321] wlan0: send auth to f8:d1:11:9e:80:a8 (try 3/3)
[  261.504245] wlan0: authentication with f8:d1:11:9e:80:a8 timed out
[  268.326163] wlan0: authenticate with f8:d1:11:9e:80:a8
[  268.327712] wlan0: send auth to f8:d1:11:9e:80:a8 (try 1/3)
[  268.529182] wlan0: send auth to f8:d1:11:9e:80:a8 (try 2/3)
[  268.732956] wlan0: send auth to f8:d1:11:9e:80:a8 (try 3/3)
[  268.936730] wlan0: authentication with f8:d1:11:9e:80:a8 timed out
[  269.900978] wlan0: authenticate with f8:d1:11:9e:80:a8
[  269.902249] wlan0: send auth to f8:d1:11:9e:80:a8 (try 1/3)
[  270.103616] wlan0: send auth to f8:d1:11:9e:80:a8 (try 2/3)
[  270.307404] wlan0: send auth to f8:d1:11:9e:80:a8 (try 3/3)
[  270.511231] wlan0: authentication with f8:d1:11:9e:80:a8 timed out
[  271.475452] wlan0: authenticate with f8:d1:11:9e:80:a8
[  271.476600] wlan0: direct probe to f8:d1:11:9e:80:a8 (try 1/3)
[  271.678010] wlan0: direct probe to f8:d1:11:9e:80:a8 (try 2/3)
[  271.881859] wlan0: direct probe to f8:d1:11:9e:80:a8 (try 3/3)
[  272.085625] wlan0: authentication with f8:d1:11:9e:80:a8 timed out
[  284.769927] wlan0: authenticate with f8:d1:11:9e:80:a8
[  284.771436] wlan0: send auth to f8:d1:11:9e:80:a8 (try 1/3)
[  284.972890] wlan0: send auth to f8:d1:11:9e:80:a8 (try 2/3)
[  285.176706] wlan0: send auth to f8:d1:11:9e:80:a8 (try 3/3)
[  285.380476] wlan0: authentication with f8:d1:11:9e:80:a8 timed out
[  286.344178] wlan0: authenticate with f8:d1:11:9e:80:a8
[  286.345827] wlan0: send auth to f8:d1:11:9e:80:a8 (try 1/3)
[  286.347805] wlan0: authenticated
[  286.351551] wlan0: associate with f8:d1:11:9e:80:a8 (try 1/3)
[  286.357216] wlan0: RX AssocResp from f8:d1:11:9e:80:a8 (capab=0x431 status=0 aid=1)
[  286.357802] wlan0: associated
[  290.645437] wlan0: deauthenticating from f8:d1:11:9e:80:a8 by local choice (reason=3)
[  291.623461] wlan0: authenticate with f8:d1:11:9e:80:a8
[  291.624735] wlan0: send auth to f8:d1:11:9e:80:a8 (try 1/3)
[  291.826127] wlan0: send auth to f8:d1:11:9e:80:a8 (try 2/3)
[  291.828315] wlan0: authenticated
[  291.830138] wlan0: associate with f8:d1:11:9e:80:a8 (try 1/3)
[  291.834074] wlan0: RX AssocResp from f8:d1:11:9e:80:a8 (capab=0x431 status=0 aid=1)
[  291.834778] wlan0: associated
[  621.081660] wlan0: authenticate with f8:d1:11:9e:80:a8
[  621.082939] wlan0: send auth to f8:d1:11:9e:80:a8 (try 1/3)
[  621.284413] wlan0: send auth to f8:d1:11:9e:80:a8 (try 2/3)
[  621.315629] wlan0: authenticated
[  621.316376] wlan0: associate with f8:d1:11:9e:80:a8 (try 1/3)
[  621.520138] wlan0: associate with f8:d1:11:9e:80:a8 (try 2/3)
[  621.723973] wlan0: associate with f8:d1:11:9e:80:a8 (try 3/3)
[  621.927755] wlan0: association with f8:d1:11:9e:80:a8 timed out
[  635.574062] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  640.470456] wlan0: authenticate with f8:d1:11:9e:80:a8
[  640.471884] wlan0: send auth to f8:d1:11:9e:80:a8 (try 1/3)
[  640.673210] wlan0: send auth to f8:d1:11:9e:80:a8 (try 2/3)
[  640.877036] wlan0: send auth to f8:d1:11:9e:80:a8 (try 3/3)
[  641.080811] wlan0: authentication with f8:d1:11:9e:80:a8 timed out
[  642.044873] wlan0: authenticate with f8:d1:11:9e:80:a8
[  642.046267] wlan0: send auth to f8:d1:11:9e:80:a8 (try 1/3)
[  642.247650] wlan0: send auth to f8:d1:11:9e:80:a8 (try 2/3)
[  642.451466] wlan0: send auth to f8:d1:11:9e:80:a8 (try 3/3)
[  642.456607] wlan0: authenticated
[  642.459439] wlan0: associate with f8:d1:11:9e:80:a8 (try 1/3)
[  642.465671] wlan0: RX AssocResp from f8:d1:11:9e:80:a8 (capab=0x431 status=0 aid=1)
[  642.466219] wlan0: associated
[  642.466271] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  647.090615] wlan0: deauthenticated from f8:d1:11:9e:80:a8 (Reason: 6)
[  648.058791] wlan0: authenticate with f8:d1:11:9e:80:a8
[  648.060276] wlan0: send auth to f8:d1:11:9e:80:a8 (try 1/3)
[  648.261764] wlan0: send auth to f8:d1:11:9e:80:a8 (try 2/3)
[  648.272954] wlan0: authenticated
[  648.273729] wlan0: associate with f8:d1:11:9e:80:a8 (try 1/3)
[  648.477483] wlan0: associate with f8:d1:11:9e:80:a8 (try 2/3)
[  648.681288] wlan0: associate with f8:d1:11:9e:80:a8 (try 3/3)
[  648.686876] wlan0: RX AssocResp from f8:d1:11:9e:80:a8 (capab=0x431 status=0 aid=1)
[  648.687514] wlan0: associated
[  767.425153] wlan0: authenticate with f8:d1:11:9e:80:a8
[  767.426355] wlan0: send auth to f8:d1:11:9e:80:a8 (try 1/3)
[  767.627669] wlan0: send auth to f8:d1:11:9e:80:a8 (try 2/3)
[  767.831374] wlan0: send auth to f8:d1:11:9e:80:a8 (try 3/3)
[  768.035084] wlan0: authentication with f8:d1:11:9e:80:a8 timed out
[  768.998803] wlan0: authenticate with f8:d1:11:9e:80:a8
[  769.000098] wlan0: send auth to f8:d1:11:9e:80:a8 (try 1/3)
[  769.201326] wlan0: send auth to f8:d1:11:9e:80:a8 (try 2/3)
[  769.405001] wlan0: send auth to f8:d1:11:9e:80:a8 (try 3/3)
[  769.608724] wlan0: authentication with f8:d1:11:9e:80:a8 timed out
[  770.571944] wlan0: authenticate with f8:d1:11:9e:80:a8
[  770.573609] wlan0: send auth to f8:d1:11:9e:80:a8 (try 1/3)
[  770.774999] wlan0: send auth to f8:d1:11:9e:80:a8 (try 2/3)
[  770.978685] wlan0: send auth to f8:d1:11:9e:80:a8 (try 3/3)
[  771.182354] wlan0: authentication with f8:d1:11:9e:80:a8 timed out
[  772.145603] wlan0: authenticate with f8:d1:11:9e:80:a8
[  772.147359] wlan0: send auth to f8:d1:11:9e:80:a8 (try 1/3)
[  772.348615] wlan0: send auth to f8:d1:11:9e:80:a8 (try 2/3)
[  772.552357] wlan0: send auth to f8:d1:11:9e:80:a8 (try 3/3)
[  772.756015] wlan0: authentication with f8:d1:11:9e:80:a8 timed out
[  779.578892] wlan0: authenticate with f8:d1:11:9e:80:a8
[  779.580223] wlan0: send auth to f8:d1:11:9e:80:a8 (try 1/3)
[  779.781579] wlan0: send auth to f8:d1:11:9e:80:a8 (try 2/3)
[  779.985278] wlan0: send auth to f8:d1:11:9e:80:a8 (try 3/3)
[  780.188964] wlan0: authentication with f8:d1:11:9e:80:a8 timed out
[  782.414326] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

nm-tool - not connected
```

NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             connected
  Default:           yes
  HW Address:        3C:97:0E:37:88:11


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.0.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.254


    DNS:             192.168.0.254




- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        C0:14:3D:C7:88:35


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 

```


nm-tool - connected
```

NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             connected
  Default:           yes
  HW Address:        3C:97:0E:37:88:11


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.0.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.254


    DNS:             192.168.0.254




- Device: wlan0  [TP-LINK_POCKET] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           no
  HW Address:        C0:14:3D:C7:88:35


  Capabilities:
    Speed:           1 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *TP-LINK_POCKET: Infra, F8:D1:11:9E:80:A8, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2


  IPv4 Settings:
    Address:         192.168.0.105
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.254


    DNS:             192.168.0.254

```

---

### Post by chili555 on 2013-06-18
You seem to be connected to both wired and wireless! We won't get far trying to troubleshoot that way! Please detach the ethernet, connect with wireless only and let me see the readings again. Also:```
sudo iw reg get
dmesg | grep cfg80211
```> State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
 [COLOR="#FF0000"] Type:              Wired[/COLOR]
  Driver:            alx
  [COLOR="#FF0000"]State:             connected[/COLOR]
  Default:           yes
  HW Address:        3C:97:0E:37:88:11


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    [COLOR="#FF0000"]Address:         192.168.0.100[/COLOR]
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.254


    DNS:             192.168.0.254




- Device: wlan0  [TP-LINK_POCKET] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  [COLOR="#FF0000"]State:             connected[/COLOR]
  Default:           no
  HW Address:        C0:14:3D:C7:88:35


  Capabilities:
    Speed:           1 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *TP-LINK_POCKET: Infra, F8:D1:11:9E:80:A8, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2


  IPv4 Settings:
   [COLOR="#FF0000"] Address:         192.168.0.105[/COLOR]
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.254


    DNS:             192.168.0.254

---

### Post by sushi80 on 2013-06-18
Sorry chili555 i didn't know that would have been a problem!  


sudo iw reg get
```



country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS



```
dmesg | grep cfg80211
```

[   14.646533] cfg80211: Calling CRDA to update world regulatory domain
[   14.842692] cfg80211: World regulatory domain updated:
[   14.842693] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.842694] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.842695] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.842695] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.842696] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.842697] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  176.924226] cfg80211: Calling CRDA for country: IE
[  176.929940] cfg80211: Regulatory domain changed to country: IE
[  176.929945] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  176.929947] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  176.929950] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  176.929952] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  176.929955] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[  180.540561] cfg80211: Calling CRDA to update world regulatory domain
[  180.545906] cfg80211: World regulatory domain updated:
[  180.545911] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  180.545914] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  180.545917] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  180.545919] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  180.545922] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  180.545924] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  286.357918] cfg80211: Calling CRDA for country: IE
[  286.363392] cfg80211: Regulatory domain changed to country: IE
[  286.363398] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  286.363401] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  286.363404] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  286.363406] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  286.363408] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[  290.656772] cfg80211: Calling CRDA to update world regulatory domain
[  290.663594] cfg80211: World regulatory domain updated:
[  290.663599] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  290.663601] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  290.663604] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  290.663606] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  290.663608] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  290.663610] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  291.834961] cfg80211: Calling CRDA for country: IE
[  291.841276] cfg80211: Regulatory domain changed to country: IE
[  291.841281] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  291.841285] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  291.841287] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  291.841290] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  291.841292] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[  620.121696] cfg80211: Calling CRDA to update world regulatory domain
[  620.127714] cfg80211: World regulatory domain updated:
[  620.127719] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  620.127723] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  620.127726] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  620.127728] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  620.127731] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  620.127733] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  642.466385] cfg80211: Calling CRDA for country: IE
[  642.471970] cfg80211: Regulatory domain changed to country: IE
[  642.471976] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  642.471979] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  642.471981] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  642.471984] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  642.471986] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[  647.096164] cfg80211: Calling CRDA to update world regulatory domain
[  647.101664] cfg80211: World regulatory domain updated:
[  647.101670] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  647.101673] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  647.101676] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  647.101679] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  647.101681] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  647.101683] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  648.687565] cfg80211: Calling CRDA for country: IE
[  648.692997] cfg80211: Regulatory domain changed to country: IE
[  648.693004] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  648.693009] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  648.693013] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  648.693016] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  648.693019] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[  766.465627] cfg80211: Calling CRDA to update world regulatory domain
[  766.472299] cfg80211: World regulatory domain updated:
[  766.472305] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  766.472308] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  766.472311] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  766.472314] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  766.472316] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  766.472319] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2323.625812] cfg80211: Calling CRDA for country: IE
[ 2323.631660] cfg80211: Regulatory domain changed to country: IE
[ 2323.631666] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2323.631669] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 2323.631671] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 2323.631673] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 2323.631676] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[ 3310.170241] cfg80211: Calling CRDA to update world regulatory domain
[ 3310.176114] cfg80211: World regulatory domain updated:
[ 3310.176120] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3310.176123] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3310.176126] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3310.176129] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3310.176131] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3310.176133] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3433.733404] cfg80211: Calling CRDA for country: IE
[ 3433.740462] cfg80211: Regulatory domain changed to country: IE
[ 3433.740468] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3433.740470] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 3433.740473] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 3433.740475] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 3433.740477] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[ 5472.955661] cfg80211: Calling CRDA to update world regulatory domain
[ 5472.961758] cfg80211: World regulatory domain updated:
[ 5472.961765] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 5472.961769] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5472.961773] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 5472.961777] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 5472.961780] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5472.961783] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6206.223671] cfg80211: Calling CRDA for country: IE
[ 6206.229095] cfg80211: Regulatory domain changed to country: IE
[ 6206.229103] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 6206.229108] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 6206.229112] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 6206.229116] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 6206.229119] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[ 6209.840663] cfg80211: Calling CRDA to update world regulatory domain
[ 6209.846393] cfg80211: World regulatory domain updated:
[ 6209.846399] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 6209.846403] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6209.846407] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 6209.846411] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 6209.846414] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6209.846418] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14627.710241] cfg80211: Calling CRDA for country: IE
[14627.716195] cfg80211: Regulatory domain changed to country: IE
[14627.716200] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14627.716204] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14627.716206] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14627.716208] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14627.716211] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[14629.751457] cfg80211: Calling CRDA to update world regulatory domain
[14629.757737] cfg80211: World regulatory domain updated:
[14629.757745] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14629.757749] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14629.757752] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14629.757755] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14629.757757] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14629.757760] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14673.331575] cfg80211: Calling CRDA for country: IE
[14673.335395] cfg80211: Regulatory domain changed to country: IE
[14673.335399] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14673.335401] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14673.335403] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14673.335404] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14673.335406] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[14674.119836] cfg80211: Calling CRDA to update world regulatory domain
[14674.123817] cfg80211: World regulatory domain updated:
[14674.123820] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14674.123823] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14674.123825] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14674.123827] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14674.123829] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14674.123831] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14678.411241] cfg80211: Calling CRDA for country: IE
[14678.417083] cfg80211: Regulatory domain changed to country: IE
[14678.417091] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14678.417096] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14678.417101] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14678.417105] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14678.417108] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[14681.670666] cfg80211: Calling CRDA to update world regulatory domain
[14681.676192] cfg80211: World regulatory domain updated:
[14681.676197] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14681.676200] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14681.676203] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14681.676205] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14681.676208] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14681.676210] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14690.699074] cfg80211: Calling CRDA for country: IE
[14690.706044] cfg80211: Regulatory domain changed to country: IE
[14690.706050] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14690.706054] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14690.706056] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14690.706059] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14690.706061] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[14695.639721] cfg80211: Calling CRDA to update world regulatory domain
[14695.645601] cfg80211: World regulatory domain updated:
[14695.645608] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14695.645613] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14695.645618] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14695.645622] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14695.645627] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14695.645631] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14700.176744] cfg80211: Calling CRDA for country: IE
[14700.182479] cfg80211: Regulatory domain changed to country: IE
[14700.182486] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14700.182491] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14700.182495] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14700.182499] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14700.182502] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[14704.650370] cfg80211: Calling CRDA to update world regulatory domain
[14704.656004] cfg80211: World regulatory domain updated:
[14704.656010] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14704.656013] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14704.656016] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14704.656018] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14704.656021] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14704.656023] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14715.168745] cfg80211: Calling CRDA for country: IE
[14715.179731] cfg80211: Regulatory domain changed to country: IE
[14715.179736] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14715.179738] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14715.179740] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14715.179742] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14715.179744] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[14718.881533] cfg80211: Calling CRDA to update world regulatory domain
[14718.887176] cfg80211: World regulatory domain updated:
[14718.887188] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14718.887192] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14718.887197] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14718.887201] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14718.887204] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14718.887208] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14719.844393] cfg80211: Calling CRDA for country: IE
[14719.850186] cfg80211: Regulatory domain changed to country: IE
[14719.850190] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14719.850192] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14719.850194] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14719.850195] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14719.850197] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[14723.600073] cfg80211: Calling CRDA to update world regulatory domain
[14723.606909] cfg80211: World regulatory domain updated:
[14723.606915] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14723.606919] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14723.606922] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14723.606926] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14723.606930] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14723.606934] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14724.584459] cfg80211: Calling CRDA for country: IE
[14724.589350] cfg80211: Regulatory domain changed to country: IE
[14724.589354] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14724.589357] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14724.589359] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14724.589361] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14724.589363] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[14726.627778] cfg80211: Calling CRDA to update world regulatory domain
[14726.633575] cfg80211: World regulatory domain updated:
[14726.633581] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14726.633584] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14726.633587] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14726.633589] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14726.633592] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14726.633594] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14749.749525] cfg80211: Calling CRDA for country: IE
[14749.755202] cfg80211: Regulatory domain changed to country: IE
[14749.755208] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14749.755213] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14749.755216] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14749.755218] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14749.755220] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[14751.558504] cfg80211: Calling CRDA to update world regulatory domain
[14751.564222] cfg80211: World regulatory domain updated:
[14751.564228] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14751.564232] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14751.564235] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14751.564237] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14751.564239] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14751.564242] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14761.759759] cfg80211: Calling CRDA for country: IE
[14761.765256] cfg80211: Regulatory domain changed to country: IE
[14761.765261] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14761.765264] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14761.765267] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14761.765269] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14761.765271] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[14763.552560] cfg80211: Calling CRDA to update world regulatory domain
[14763.558583] cfg80211: World regulatory domain updated:
[14763.558589] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14763.558592] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14763.558595] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14763.558598] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14763.558600] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14763.558603] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14768.229014] cfg80211: Calling CRDA for country: IE
[14768.235639] cfg80211: Regulatory domain changed to country: IE
[14768.235645] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14768.235649] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14768.235653] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14768.235656] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[14768.235660] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[14772.539176] cfg80211: Calling CRDA to update world regulatory domain
[14772.544673] cfg80211: World regulatory domain updated:
[14772.544679] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14772.544683] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14772.544686] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14772.544688] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14772.544691] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14772.544693] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

```
iwconfig
```

eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off





```
nm-tool
```

NetworkManager Tool


State: connecting


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        3C:97:0E:37:88:11


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         off




- Device: wlan0  [TP-LINK_POCKET] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connecting (need authentication)
  Default:           no
  HW Address:        C0:14:3D:C7:88:35


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    TP-LINK_POCKET:  Infra, F8:D1:11:9E:80:A8, Freq 2412 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2



```

---

### Post by chili555 on 2013-06-18
> Regulatory domain changed to country: IEIs IE your country; that is Ireland, the home of the Dublin Lawyer? If so, let's give a jump start to the system:```
sudo iw reg set IE
```Does it connect now? If so, we can code it into /etc/rc.local.

I'm running low on ideas.

---

### Post by sushi80 on 2013-06-19
I'll give it a try tonight! 

O.T. In 6 years I'm in Dublin i've never heard/seen [COLOR=#000000]the Dublin Lawer!!! I think is some sort of U.S./Irish dish!! :D[/COLOR]

---

### Post by chili555 on 2013-06-19
[http://webcache.googleusercontent.com/search?q=cache:ojTlTXoxOvMJ:www.independent.ie/lifestyle/food-drink/lobster-dublin-lawyer-and-variations-26556737.html+&cd=7&hl=en&ct=clnk&gl=us](http://webcache.googleusercontent.com/search?q=cache:ojTlTXoxOvMJ:www.independent.ie/lifestyle/food-drink/lobster-dublin-lawyer-and-variations-26556737.html+&cd=7&hl=en&ct=clnk&gl=us)

It looks pretty Irish to me! 

Mrs. Chili and I will be out today enjoying a South Carlina favorite, barbecue, so my response may be delayed.

---

### Post by sushi80 on 2013-06-19
[FONT=Ubuntu Mono, monospace][COLOR=#000000]nothing good with [/COLOR][/FONT][COLOR=#000000][FONT=Ubuntu Mono]sudo iw reg set IE!! 

i'll try another driver....[/FONT][/COLOR]

---

### Post by chili555 on 2013-06-19
> **sushi80 said:**
> [FONT=Ubuntu Mono, monospace][COLOR=#000000]nothing good with [/COLOR][/FONT][COLOR=#000000][FONT=Ubuntu Mono]sudo iw reg set IE!! 

i'll try another driver....[/FONT][/COLOR]The STA driver? I look forward to your report.

---

### Post by sushi80 on 2013-06-19
I really don't understand what's wrong with this wireless card! The STA driver works great going outside but i can't connect from other devices! 

if i try to ping ssh or telnet from another pc i get host unreachable ( no firewall issue)!!!

if i try to ping another pc on my network i get 100% lost packages

i've also monitored the card but there is no traffic coming in or coming back vs my lan. No problems connecting outside!! 

this problem is only with wifi, eth works fine!

---

### Post by chili555 on 2013-06-19
> No problems connecting outside!! Meaning what? Meaning that you can connect at the internet cafe, neighbors, library, etc., but not at home? Doesn't that suggest that we look at the router settings?

---

### Post by sushi80 on 2013-06-20
Sorry I wasn't clear...
I mean that i can download from internet, surf the web, use skype...so i can connect to the outside world!

The problem is that i can't connect to an internal server, and any other pc in my lan can't connect to my laptop! I don't think has anything to do with my router because the problem started when i update from 12.10 to 13.04.

a difference that I've noticed is that with 12.10 my ethernet never worked but my wireless was ok while now on 13.10 my ethernet it's working!

Another strange behavior is that if i disable the wireless my ethernet can go on internet but within my lan gives me the same problem( i can't ping or receive connection from other pc!!)

I don't know what to think...maybe some conflict between the 2 network interfaces

---

### Post by chili555 on 2013-06-20
> The problem is that i can't connect to an internal server, and any other pc in my lan can't connect to my laptop! Do you mean for file sharing, because that's a samba problem and not a driver problem. Or do you mean ping? Can you ping the router?> while now on 13.10 my ethernet it's working!I think you mean 13.04. That's pretty normal; new drivers are introduced and old drivers are debugged.

Let's stick to one device, hopefully wireless, until we narrow down the problem. Being old, stubborn and set in my ways, I find it difficult to answer a question about wireless and find out it was really about ethernet. Hey, that's just me!

---

### Post by sushi80 on 2013-06-22
I have an ftp server, I have serviio server on my laptop so my xbox can stream movies and so on but nothing can connect to my laptop, and from my laptop i can't ping any device or my router.

Anyway yesterday i got a second hand wifi card ([COLOR=#333333][FONT=Georgia]WLAN, WiFi 1×1 BGN, Liteon AR9285 HB95 BGN MOW NB, FRU 20002357) from ebay for £3, is an atheros,  plugged in and fixed all my problems!!! [/FONT][/COLOR]:D

I dont have bluetooth anymore but I don't use it! 

It's a shame because is a new laptop but those Broadcam cards are a pain on ubuntu (on Mageia worked like a charm)

---

