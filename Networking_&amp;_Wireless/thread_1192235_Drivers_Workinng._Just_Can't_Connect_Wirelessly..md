---
title: "Drivers Workinng. Just Can't Connect Wirelessly."
date: 2009-06-19
forum: Networking &amp; Wireless
---

### Post by Literati on 2009-06-19
Hi there,

I'm trying to get my laptop (Acer Aspire 5002WLMi) to connect to my wireless network :) 
I've disabled any sort of security on the network (WEP, WPA) just to see if I can finally GET a connection :P

Here's a few outputs...

> lshw wrote:
```
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a4:4a:4f:6e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```


> iwconfig wrote:
```
wlan0     IEEE 802.11bg  ESSID:"Alain"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

So I already ran:

```
sudo iwconfig wlan0 essid Alain
```

(Obviously, Alain being the name of our network / broadcast) 

When I try to connect using Wifi-Radar I get this in the terminal:

```
sudo wifi-radar
Error for wireless request "Set Nickname" (8B1C) :
    SET failed on device wlan0 ; Operation not supported.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
can't create /var/run/dhclient.wlan0.leases: Permission denied
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:14:a4:4a:4f:6e
Sending on   LPF/wlan0/00:14:a4:4a:4f:6e
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17

```

And so on... I've tried opening port 67 on my router, but still nothing.

I've determined, and believe to be correct, that this isn't a Driver issue s in Wifi-Radar I am able to scan / see the wireless networks. So I don't think ndiswrapper would help me. But honestly, I'm willing to try anything. :)

Thanks so much in advance.
Matt

---

### Post by papangul on 2009-06-20
> **Literati said:**
> I'm willing to try anything. :)
You may try this:
[http://ubuntuforums.org/showthread.php?t=1150797](http://ubuntuforums.org/showthread.php?t=1150797):D

---

