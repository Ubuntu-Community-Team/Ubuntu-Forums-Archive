---
title: "WNDA 3100 v2 Questions"
date: 2012-09-17
forum: Networking &amp; Wireless
---

### Post by Rippey574 on 2012-09-17
Does any one know if there is any other option then ndiswrapper? Or a way to get it to support monitor mode?

I am also having an issue with it seeing 5ghz networks. It will not see them at all.

```
ndiswrapper -l
```bcmn43xx32 : driver installed
    device (0846:9011) present

```
iwconfig
```wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
airmon-ng
```Interface    Chipset        Driver

wlan1        Unknown        ndiswrapper
wlan0        Broadcom 4318    b43 - [phy0]

```
airodump-ng
```Ndiswrapper doesn't support monitor mode.

```
dmesg | grep ndis
```

[  250.292351] ndiswrapper version 1.58rc1 loaded (smp=yes, preempt=no)
[  250.686181] ndiswrapper: driver bcmn43xx32 (,08/26/2009, 5.10.79.30) loaded
[  251.222507] usbcore: registered new interface driver ndiswrapper
[ 2194.374332] ndiswrapper (mp_reset:58): wlan1 is being rese

---

