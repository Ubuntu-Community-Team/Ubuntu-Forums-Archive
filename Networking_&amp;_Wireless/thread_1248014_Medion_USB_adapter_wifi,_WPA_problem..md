---
title: "Medion USB adapter wifi, WPA problem."
date: 2009-08-23
forum: Networking &amp; Wireless
---

### Post by Linaaa on 2009-08-23
Okay so I've been working on this all weekend already and got to the point where I can't think of anything to try anymore.

I got a somewhat older laptop last friday (p4 mobile 1.7ghz) and I thought I'd give Ubuntu a try. Start up and shut down froze at Loading bluetooth, which was caused by my USB Medion wifi adapter being plugged in. After I disconnected it it worked great.

So now I was gonna try get the wifi adapter to work, whenever I plugged it in Ubuntu would start p54usb and it would mess up cause of that. First I tried replacing some firmware related things but that didn't work. So I blacklisted p54usb and installed the windows drivers with ndiswrapper. I could connect to unsecured networks but nothing else. So I replaced Network Manager with Wicd and got WEP to work fine (using wext as WPA Supplicant Driver).

WPA however.. I've installed wpa_gui to see more about where it goes wrong. It associates with macaddress, GROUP_HANDSHAKE mode, but then disconnects.

Hope anyone knows what I could do now to make it work, thanks.

> 
1)
Dell p4 mobile laptop, Medion USB adapter + router.

2)
Bus 001 Device 002: ID 0cde:0006 Z-Com Medion 40900 802.11b Adapter
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

3)
wlan0    IEEE 802.11g  ESSID:off/any
    Mode: Managed  Frequency:2.447 GHz  Access Point: Not-Associated
    Bit Rate:2 Mb/s
    RTS thr=2347 B  Fragment thr=2346 B
    Power Management:off
    Link Quality:0  Signal level:0  Noise level:0
    Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
    Tx excessive retries:0  Invalid misc:0  Missed beacon:0

4)
lsmod: ndiswrapper

5)
[   17.415402] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   17.856097] ndiswrapper: driver wlanuig (,10/31/2003, 1.0.3) loaded
[   20.261473] usbcore: registered new interface driver ndiswrapper
[ 7023.230366] ndiswrapper (iw_get_auth:1615): invalid cmd 4
[ 7023.230377] ndiswrapper (iw_get_auth:1615): invalid cmd 5
[ 7023.230400] ndiswrapper (iw_get_auth:1615): invalid cmd 8
[ 7023.230405] ndiswrapper (iw_get_auth:1615): invalid cmd 9
[ 7023.230410] ndiswrapper (iw_get_auth:1615): invalid cmd 10

6)
*-network:0
     description: Wireless interface
     physical id: 2
     logical name: wlan0
     serial: [macaddress]
     capabilities: ethernet physical wireless
     configuration: broadcast=yes driver=ndiswrapper+wlanuig droverversion=1.53+,10/31/2003, 1.0.3 link=no multicast=yes wireless=IEEE 802.11g

7)
Cell 01 - Address: [macaddress]
          ESSID: "[ROUTERNAME]"
          Protocol:IEEE 802.11b
          Mode:Managed
          Frequency:2.447 Ghz (Channel 8)
          Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm
          Encryption key:on
          Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                    9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                    48 Mb/s; 54 Mb/s
          Extra:bcn_int=100
          Extra:atim=1
          IE: WPA Version 1
              Group Cipher : TKIP
              Pairwise Ciphers (1) : TKIP
              Authentication Suites (1) : PSK

8)
Description:    Ubuntu 9.04

9)
2.6.28-15-generic i686

10)
* Reconfiguring network interfaces... [ OK ]


---

