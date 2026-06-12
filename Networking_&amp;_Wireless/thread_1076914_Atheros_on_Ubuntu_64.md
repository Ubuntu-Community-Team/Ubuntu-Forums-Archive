---
title: "Atheros on Ubuntu 64"
date: 2009-02-21
forum: Networking &amp; Wireless
---

### Post by Craige on 2009-02-21
Hey guys,

Here's the deal. I've been off Linux for quite a while and now I'm getting back into it with Ubuntu 64bit.  I have a relatively new Toshiba Satellite L300D laptop that I'm installing the system on.  This laptop depends on an Atheros AR5007EG wireless card to connect to the internet.

Now, the fun stuff...

I have installed ndiswrapper as per the [instructions on your forum]("http://ubuntuforums.org/showthread.php?t=512828")...but I guess I failed at it.

Here's what I know.

[LIST]
[*]ndiswrapper is claiming the device, and not some other driver.
[*]My driver is loaded by ndiswrapper
[*]The installed driver is the 64 bit windows version
[/LIST]

```

craige@craige-toshiba:~$ dmesg | grep -e ndis -e wlan
[   42.564165] ndiswrapper version 1.51 loaded (smp=yes, preempt=no)
[   42.653593] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[   42.655286] ndiswrapper: driver net5211 (,06/21/2007,5.3.0.56) loaded
[   42.655701] ndiswrapper (ZwClose:2227): closing handle 0x0 not implemented
[   43.068143] ndiswrapper: using IRQ 18
[   43.267451] wlan0: ethernet device 00:21:63:10:7f:7f using serialized NDIS driver: net5211, version: 0x50003, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf
[   43.271874] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   43.271958] usbcore: registered new interface driver ndiswrapper
[   68.776851] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  169.855628] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  286.785299] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  288.800999] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1366.974638] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6017.004155] ndiswrapper: device wlan0 removed
[ 6017.004311] usbcore: deregistering interface driver ndiswrapper
[   44.444696] ndiswrapper version 1.51 loaded (smp=yes, preempt=no)
[   45.193988] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[   45.195714] ndiswrapper: driver net5211 (,06/21/2007,5.3.0.56) loaded
[   45.196442] ndiswrapper (ZwClose:2227): closing handle 0x0 not implemented
[   45.608747] ndiswrapper: using IRQ 18
[   45.811141] wlan0: ethernet device 00:21:63:10:7f:7f using serialized NDIS driver: net5211, version: 0x50003, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf
[   45.815651] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   45.815743] usbcore: registered new interface driver ndiswrapper
[  390.725343] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  907.714806] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

Don't know where else to go.  Could use some help here. 

Thanks guys

---

### Post by Craige on 2009-02-22
I hate to be the ******* who bumps, but I'd prefer to get this resolved so I could use Ubuntu at work on Monday.

Sorry,
:(

---

