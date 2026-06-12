---
title: "Can't connect to wireless networks"
date: 2011-09-11
forum: Networking &amp; Wireless
---

### Post by handbasket on 2011-09-11
I have a wireless network that works fine with my laptop (which also currently has Ubuntu studio 10.04 installed), but it has never worked with my desktop despite years and years of wasting the occasional weekend trying...

Today, I got further than usual by updating the firmware (to 1.8.2) following the instructions at [http://linux.junsun.net/intersil-prism/](http://linux.junsun.net/intersil-prism/)  

This finally allowed the Network Manager to see my wireless network! (Though strangely, it does not show the other available networks in the neighborhood that my laptop can see.  It's clearly doing something right since it detects changes in the name and security settings of my network -- maybe the range of the wireless card is just less?)  However, even when I set the wireless security to 'None,' the connection fails. 

The /var/log/daemon.log shows errors along the line of
```

home wpa_supplicant[831]: Association request to the driver failed
```

I'm about ready to give up (or at least try a new wireless card or an ethernet adapter), but thought I'd ask first if anyone has any ideas about what's going wrong?    

Here's some possibly useful diagnostic stuff:
```
$ sudo lspci -v
01:06.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
	Subsystem: Intersil Corporation Prism 2.5 Wavelan chipset
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at fdeff000 (32-bit, prefetchable) [size=4K]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: hostap_pci
	Kernel modules: hostap_pci, orinoco_pci

$sudo lshw -C network
  *-network               
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: wifi0
       version: 01
       serial: 00:09:5b:2f:19:10
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=hostap firmware=1.8.2 latency=32 multicast=yes wireless=IEEE 802.11b
       resources: irq:16 memory:fdeff000-fdefffff(prefetchable)

$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Scan completed :
          Cell 01 - Address: 00:23:69:B0:E5:8B
                    ESSID:"LinkSass2"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off

wlan0     Scan completed :
          Cell 01 - Address: 00:23:69:B0:E5:8B
                    ESSID:"LinkSass2"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off


```

---

### Post by shubham1 on 2011-09-11
try using wicd

---

### Post by handbasket on 2011-09-11
Ok, with wicd I get some error messages: 

When I started it up, this message popped up:

```

Could not connect to wicd's D-Bus interface.  Check the wicd log for
error messages.
```

Despite that, the program seems to work -- I can use it to connect and disconnect the wired connection. (Also, when I later quit and restarted wicd, I didn't get the same error message again.) It sees the wireless network, but fails to connect since it can't obtain an IP address.  After an unsuccessful attempt,  /var/log/wicd/wicd.log shows the following:

```

2011/09/11 15:35:49 :: Connecting to wireless network LinkSass2
2011/09/11 15:35:49 :: attempting to set hostname with dhclient
2011/09/11 15:35:49 :: using dhcpcd or another supported client may work better
2011/09/11 15:35:49 :: attempting to set hostname with dhclient
2011/09/11 15:35:49 :: using dhcpcd or another supported client may work better
2011/09/11 15:35:49 :: Putting interface down
2011/09/11 15:35:49 :: Sending connection attempt result Failed
2011/09/11 15:35:49 :: Releasing DHCP leases...
2011/09/11 15:35:49 :: attempting to set hostname with dhclient
2011/09/11 15:35:49 :: using dhcpcd or another supported client may work better
2011/09/11 15:35:49 :: Setting false IP...
2011/09/11 15:35:50 :: Stopping wpa_supplicant
2011/09/11 15:35:50 :: Flushing the routing table...
2011/09/11 15:35:50 :: Putting interface up...
2011/09/11 15:35:52 :: Running DHCP with hostname home

2011/09/11 15:35:52 :: attempting to set hostname with dhclient
2011/09/11 15:35:52 :: using dhcpcd or another supported client may work better
2011/09/11 15:35:52 :: Internet Systems Consortium DHCP Client V3.1.3
2011/09/11 15:35:52 :: Copyright 2004-2009 Internet Systems Consortium.
2011/09/11 15:35:52 :: All rights reserved.
2011/09/11 15:35:52 :: For info, please visit https://www.isc.org/software/dhcp/
2011/09/11 15:35:52 ::
2011/09/11 15:35:52 :: wifi0: unknown hardware address type 801
2011/09/11 15:35:52 :: wifi0: unknown hardware address type 801
2011/09/11 15:35:52 :: Listening on LPF/wlan0/00:09:5b:2f:19:10
2011/09/11 15:35:52 :: Sending on   LPF/wlan0/00:09:5b:2f:19:10

2011/09/11 15:35:52 :: Sending on   Socket/fallback
2011/09/11 15:35:55 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interva$
2011/09/11 15:35:59 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interva$
2011/09/11 15:36:08 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interva$
2011/09/11 15:36:23 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interva$
2011/09/11 15:36:32 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interva$
2011/09/11 15:36:46 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interva$
2011/09/11 15:36:56 :: No DHCPOFFERS received.
2011/09/11 15:36:56 :: No working leases in persistent database - sleeping.
2011/09/11 15:37:05 :: DHCP connection failed

2011/09/11 15:37:05 :: exiting connection thread
2011/09/11 15:37:06 :: Sending connection attempt result dhcp_failed
2011/09/11 15:37:06 :: attempting to set hostname with dhclient
2011/09/11 15:37:06 :: using dhcpcd or another supported client may work better
2011/09/11 15:37:06 :: attempting to set hostname with dhclient
2011/09/11 15:37:06 :: using dhcpcd or another supported client may work better
```

---

