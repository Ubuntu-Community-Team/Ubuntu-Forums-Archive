---
title: "Wifi  disconnecting on p5q3 deluxe"
date: 2012-05-16
forum: Networking &amp; Wireless
---

### Post by sombaht on 2012-05-16
Hi,
Have installed Ubuntu 12.04 on a desktop machine. Motherboard is a Asus P5Q3 Deluxe, with built in wifi. While there were no issues with the install as such, the wifi is constantly dropping its connection requiring a restart every few minutes.
I know the wifi adapter and the router are not the issue as the same machine has Win7 installed and there are no issues when running win7.
 
Some details of the wifi adapter included here:

lsusb
Bus 001 Device 002: ID 0b05:1742 ASUSTek Computer, Inc. 802.11n Network Adapter

iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"siam"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 38:60:77:6D:2D:90   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:937  Invalid misc:389   Missed beacon:0

sudo lshw -C network

  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:5
       logical name: wlan0
       serial: 00:15:af:9d:0a:86
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.2.0-24-generic firmware=0.29 ip=192.168.1.17 link=yes multicast=yes wireless=IEEE 802.11bgn

Appreciate if anyone can resolve this issue.

Thanks,
sombaht

---

### Post by groggyleeky on 2012-05-16
Hey
I can sympathise with you. I have the same P5B Deluxe with on board Wifi.
I spent far too many hours, and evenings, and weekend tryign to get ti tto work.
I did manage to get a better connection but nothgin liek the speeds of windows.
In then end I bought a Dlink wireless card. Worked out of the box!
My pennies worth anyway.

---

### Post by sombaht on 2012-05-16
Groggy, 
Do you mind telling me what DLink card you get? I've wasted nearly 2 weeks trying to get this to work. Looks like I may have to shell out for a new wifi adapter :(
Cheers,
sombaht

---

