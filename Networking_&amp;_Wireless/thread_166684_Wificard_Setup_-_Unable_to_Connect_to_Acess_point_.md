---
title: "Wificard Setup - Unable to Connect to Acess point Router *"
date: 2006-04-26
forum: Networking &amp; Wireless
---

### Post by pear-i on 2006-04-26
I'm having trouble fully configuring my wireless connection on my laptop. kernel modules, drivers, everything is set up, but I simply can't scan / connect to a wireless access point.

Wireless Card - Truemobile 1150 (native support)

My wifi network is set on 64bit encryption (wep key), 
Channel 1, 
Authentication type is Open

I tried using the GUI network admin thing in gnome - but i'm not able to connect, so i edited the /etc/network/interfaces and this is what i have right now:

iface wlan0 inet dhcp
wireless-essid HHH
wireless-mode managed
wireless-keymode restricted
wireless-key **********

Iwconfig shows:
wifi0     IEEE 802.11b  ESSID:"pearbox-wifi"
          Mode:Managed  Frequency:2.422 GHz  Access Point: None
          Bit Rate:2 Mb/s   Sensitivity=1/3
          Retry limit:4   RTS thr:off
          Power Management:off

wlan0     IEEE 802.11b  ESSID:"pearbox-wifi"
          Mode:Managed  Frequency:2.422 GHz  Access Point: None
          Bit Rate:2 Mb/s   Sensitivity=1/3
          Retry limit:4   RTS thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I only have 1 wireless card, i don't really know what the first entry is...

but yah -- any ideas how i might fix that?

thanks

---

### Post by pear-i on 2006-04-26
This is what happens when I ifdown wlan0 and ifup wlan0

```
**sudo ifdown wlan0**
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wlan0/00:02:2d:7c:e7:7a
Sending on   LPF/wlan0/00:02:2d:7c:e7:7a
Sending on   Socket/fallback
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.


** sudo ifup wlan0**
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wlan0/00:02:2d:7c:e7:7a
Sending on   LPF/wlan0/00:02:2d:7c:e7:7a
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

