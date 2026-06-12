---
title: "Wifi connection dies every few hours; Reboot required every time to reconnect."
date: 2009-08-19
forum: Networking &amp; Wireless
---

### Post by roguenoir on 2009-08-19
I'm using WICD for my network manager and NDISWRAPPER for the wireless driver functionality in Jaunty 64-bit (and have the Win64 drivers installed in ndiswrapper for my wifi.)  This is a desktop system running a usb wifi card btw.

My wifi connection seems to "die" every several hours.  And when it does, I can't easily reconnect.  I try to disconnect and reconnect to the hotspot but WICD hangs on "Validating Authentication" forever. I've tried restarting my networking with the following to hopefully restore my connection:

sudo /etc/init.d/networking restart

but that hangs once it mentions something about DHCPDISCOVER and 255.255.255.255 (I'll try to save the output next time this happens and post it here.)

The only way to reliably restore my Wifi is to completely reboot..

Does anyone have any idea where to begin if I want to troubleshoot this problem?

Btw, here's a snippet of the wicd.log:

```
2009/08/19 16:56:33 :: Connecting to wireless network 2WIRE888
2009/08/19 16:56:33 :: ifconfig eth0
2009/08/19 16:56:33 :: Putting interface down
2009/08/19 16:56:33 :: ifconfig wlan0 down
2009/08/19 16:56:33 :: ifconfig wlan0
2009/08/19 16:56:33 :: Releasing DHCP leases...
2009/08/19 16:56:33 :: Setting false IP...
2009/08/19 16:56:33 :: ifconfig wlan0 0.0.0.0 
2009/08/19 16:56:33 :: ifconfig eth0 0.0.0.0 
2009/08/19 16:56:33 :: Stopping wpa_supplicant and any DHCP clients
2009/08/19 16:56:33 :: killall wpa_supplicant
2009/08/19 16:56:33 :: Flushing the routing table...
2009/08/19 16:56:33 :: ip route flush dev wlan0
2009/08/19 16:56:33 :: ip route flush dev eth0
2009/08/19 16:56:33 :: Generating psk...
2009/08/19 16:56:33 :: ['/usr/bin/wpa_passphrase', '2WIRE888', '*************']
2009/08/19 16:56:33 :: Attempting to authenticate...
2009/08/19 16:56:33 :: ['wpa_supplicant', '-B', '-i', 'wlan0', '-c', '/var/lib/wicd/configurations/001b5b81b1b9', '-D', 'wext']
2009/08/19 16:56:33 :: Putting interface up...
2009/08/19 16:56:33 :: ifconfig wlan0 up
2009/08/19 16:56:33 :: iwconfig wlan0 mode Managed
2009/08/19 16:56:34 :: ['iwconfig', 'wlan0', 'essid', '2WIRE888', 'channel', '3', 'ap', '00:1B:5B:81:B1:B9']
2009/08/19 16:56:34 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:56:35 :: iwconfig wlan0
2009/08/19 16:56:35 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:56:36 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:56:37 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:56:38 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:56:39 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:56:40 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:56:41 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:56:42 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:56:43 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:56:44 :: WPA_CLI RESULT IS SCANNING
2009/08/19 16:56:45 :: WPA_CLI RESULT IS SCANNING
2009/08/19 16:56:46 :: WPA_CLI RESULT IS SCANNING
2009/08/19 16:56:47 :: WPA_CLI RESULT IS SCANNING
2009/08/19 16:56:48 :: WPA_CLI RESULT IS SCANNING
2009/08/19 16:56:49 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:56:50 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:56:51 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:56:52 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:56:53 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:56:54 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:56:55 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:56:56 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:56:57 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:56:58 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:56:59 :: WPA_CLI RESULT IS SCANNING
2009/08/19 16:57:00 :: WPA_CLI RESULT IS SCANNING
2009/08/19 16:57:01 :: WPA_CLI RESULT IS SCANNING
2009/08/19 16:57:02 :: WPA_CLI RESULT IS SCANNING
2009/08/19 16:57:03 :: WPA_CLI RESULT IS SCANNING
2009/08/19 16:57:04 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:57:05 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:57:06 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:57:07 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:57:08 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:57:09 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:57:10 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:57:11 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:57:12 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:57:13 :: WPA_CLI RESULT IS ASSOCIATING
2009/08/19 16:57:14 :: wpa_supplicant authentication may have failed.
```

and here's a snippet of the output when restarting networking after the wifi fails:

```
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth1=eth1.
Ignoring unknown interface eth2=eth2.
Ignoring unknown interface ath0=ath0.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1e:58:b3:8e:5d
Sending on   LPF/wlan0/00:1e:58:b3:8e:5d
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by roguenoir on 2009-08-20
any ideas?

---

### Post by roguenoir on 2009-08-21
Hmm..  problem doesn't seem to occur anymore when I switched from Ndiswrapper to the native drivers..  I'll keep you posted in the next few days if it still occurs.

---

### Post by Faz1 on 2009-08-21
Probably unrelated, but you never know...

I had a similar issue a while back with my Acer Aspire 9500 series' built-in Centrino chipset & Draytek Vigor 2800 router.

It would connect just fine, then gradually degrade, increasing in ping latency and dropped packets, directly proportianal to amount of data transfer.  e.g. If I connected and just did the occasional ping it would be fine for hours, whereas repeated pings (just 1/sec) would degrade connection faster.

When rebooting laptop didn't work I had to power-cycle the router.  Turned out being a firmware issue with the Draytek, difficulties talking to Centrino.  I was forced to use USB until firmware update came out.

---

