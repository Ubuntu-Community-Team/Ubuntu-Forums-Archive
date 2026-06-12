---
title: "[closed]"
date: 2013-06-15
forum: Networking &amp; Wireless
---

### Post by amazinggrace on 2013-06-15
Hello, I have a wireless network adapter modelled Belkin F5D7050 v4000. How to check which one is the suitable patch for this adapter and how to patch the driver? Thanks.

---

### Post by ahallubuntu on 2013-06-15
~

---

### Post by amazinggrace on 2013-06-15
After [COLOR=#000000]"sudo lshw -C network", I got this:[/COLOR]

description: Wireless interface
       physical id: 1
       bus info: usb@2:1
       logical name: wlan0
       serial: 00:2d:eg:80:eg:80
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=zd1211rw driverversion=3.2.0-29-generic-pae firmware=4725 link=no multicast=yes wireless=IEEE 802.11bg

When "lsusb", I got this:
Bus 002 Device 003: ID 050d:705c Belkin Components F5D7050 Wireless G Adapter v4000 [Zydas ZD1211B]

---

### Post by ahallubuntu on 2013-06-15
~

---

### Post by amazinggrace on 2013-06-15
Output after "[COLOR=#000000][FONT=Ubuntu Mono]iwconfig[/FONT][/COLOR]":

lo        no wireless extensions.


wlan0     IEEE 802.11bg  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thrff
          Power Management: off


eth0      no wireless extensions.

----------------------------------------------


Output after "fkill list all":


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

----------------------------------------------

Yup, it's "ubuntu 12.04.1 LTS". How to update to [COLOR=#000000]12.04.2?[/COLOR]

---

### Post by ahallubuntu on 2013-06-15
~

---

### Post by ahallubuntu on 2013-06-15
~

---

### Post by amazinggrace on 2013-06-15
So the suitable patch for aircrack is [COLOR=#000000][FONT=Ubuntu Mono]zd1211rw?[/FONT][/COLOR]

---------------------------------------------------------------------------
[B]Output after "sudo modprobe zd1211rw", "iwconfig",
[/B]

lo        no wireless extensions.


wlan0     IEEE 802.11bg  ESSID:"TNCAP46E783"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: A4:B1:E9:46:E7:83   
          Bit Rate=24 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=50/100  Signal level=50/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:42   Missed beacon:0


eth0      no wireless extensions.

----------------------------------------------------------------
[B]Output after "dmesg | grep -e wlan -e zd12",
[/B]

[   17.001346] zd1211rw 2-1:1.0: phy0
[   17.001368] usbcore: registered new interface driver zd1211rw
[   17.952189] zd1211rw 2-1:1.0: firmware version 4725
[   17.992191] zd1211rw 2-1:1.0: zd1211b chip 050d:705c v4810 high 00-1c-df AL2230_RF pa0 g--N-
[   18.013968] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.014237] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.787718] wlan0: authenticate with a4:b1:e9:46:e7:83 (try 1)
[   20.789334] wlan0: authenticated
[   20.809599] wlan0: associate with a4:b1:e9:46:e7:83 (try 1)
[   20.812099] wlan0: RX AssocResp from a4:b1:e9:46:e7:83 (capab=0x411 status=0 aid=1)
[   20.812104] wlan0: associated
[   20.812845] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   33.861784] wlan0: deauthenticating from a4:b1:e9:46:e7:83 by local choice (reason=3)
[  851.829055] wlan0: authenticate with a4:b1:e9:46:e7:83 (try 1)
[  851.830793] wlan0: authenticated
[  851.855060] wlan0: associate with a4:b1:e9:46:e7:83 (try 1)
[  851.859164] wlan0: RX ReassocResp from a4:b1:e9:46:e7:83 (capab=0x411 status=0 aid=1)
[  851.859168] wlan0: associated

---

### Post by ahallubuntu on 2013-06-15
~

---

### Post by amazinggrace on 2013-07-03
why you erase all your comments?

---

