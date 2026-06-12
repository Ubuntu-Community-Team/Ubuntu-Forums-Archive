---
title: "WICD DHCP Problems"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by YWELLC on 2009-02-20
I'm having a problem connecting to dhcp enabled networks with WICD.  I run a wpa encrypted network at home w/static ip, and WICD connects perfectly with the profile setup for that mac address.

When I leave the house and use WICD to connect to unsecured networks in Wi-Fi hotspots, it hangs on "Obtaining IP address."  I have manged to get around this by using WICD's gui to collect ESSID's in range and then running a simple bash script:

#!/bin/bash
echo Enter name of unsecured wireless network in range
read ID
iwconfig eth1 essid $ID
/sbin/dhclient eth1

While this works, it would be much easier for me to connect via the GUI, especially if the networks' setup require more settings, IE encryption key/channel etc. (I am not a command line guru, though I'm sure it is completely possible to use w/o the gui at all).  I have read several other posts about people having problems with DHCP networking and WICD under 8.04, but haven't found a working solution.  It seems everything else is setup properly and the program works just fine under static ip using the saved config file for my home network or via the command line option above on an unsecured DHCP enabled network.  

Any help would be greatly appreciated!

---

### Post by YWELLC on 2009-02-23
bump...

---

### Post by imdano on 2009-02-23
Could you enable debug mode, try connecting to one of the networks not working, and post the contents of /var/log/wicd/wicd.log?

---

### Post by YWELLC on 2009-02-23
I don't have the box with me here at work, will try as soon as I get home.  

Can I enable debug mode from the GUI or must I invoke it from the command line?

---

### Post by imdano on 2009-02-23
It's in the preferences menu of the GUI.

---

### Post by YWELLC on 2009-02-24
Sorry for the delay, there were no unsecured wireless networks in range at my house all night (I didn't want to disable my entire network to try it).  Here is the /var/log/wicd/wicd.log from initialization and connection attempts on 2 separate unsecured networks.  I have removed a bunch of:

```
ifconfig eth0
ifconfig eth1
```

For the sake of length.  Also, I was able to connect manually with DHCP to both of these networks via the bash script above (I am posting this on one of them)

```

2009/02/24 08:41:58 :: ---------------------------
2009/02/24 08:41:58 :: wicd initializing...
2009/02/24 08:41:58 :: ---------------------------
2009/02/24 08:41:58 :: Couldn't detect a wireless interface.
2009/02/24 08:41:58 :: found wireless_interface in configuration eth1
2009/02/24 08:41:58 :: setting wireless interface eth1
2009/02/24 08:41:58 :: automatically detected wired interface eth0
2009/02/24 08:41:58 :: found wired_interface in configuration eth0
2009/02/24 08:41:58 :: setting wired interface eth0
2009/02/24 08:41:58 :: found wpa_driver in configuration wext
2009/02/24 08:41:58 :: setting wpa driver wext
2009/02/24 08:41:58 :: found always_show_wired_interface in configuration False
2009/02/24 08:41:58 :: found use_global_dns in configuration True
2009/02/24 08:41:58 :: setting use global dns to True
2009/02/24 08:41:58 :: setting use global dns to boolean True
2009/02/24 08:41:58 :: found global_dns_1 in configuration 208.67.222.222
2009/02/24 08:41:58 :: found global_dns_2 in configuration 208.67.220.220
2009/02/24 08:41:58 :: found global_dns_3 in configuration None
2009/02/24 08:41:58 :: setting global dns
2009/02/24 08:41:58 :: global dns servers are 208.67.222.222 208.67.220.220 None
2009/02/24 08:41:58 :: found auto_reconnect in configuration True
2009/02/24 08:41:58 :: setting automatically reconnect when connection drops
2009/02/24 08:41:58 :: found debug_mode in configuration 1
2009/02/24 08:41:58 :: found wired_connect_mode in configuration 1
2009/02/24 08:41:58 :: found signal_display_type in configuration 0
2009/02/24 08:41:58 :: found dhcp_client in configuration 0
2009/02/24 08:41:58 :: Setting dhcp client to 0
2009/02/24 08:41:58 :: found link_detect_tool in configuration 0
2009/02/24 08:41:58 :: found flush_tool in configuration 0
2009/02/24 08:41:58 :: Wireless configuration file found...
2009/02/24 08:41:58 :: Wired configuration file found...
2009/02/24 08:41:58 :: chmoding configuration files 0600...
2009/02/24 08:41:58 :: chowning configuration files root:root...
2009/02/24 08:41:58 :: Using wired interface...eth0
2009/02/24 08:41:58 :: Using wireless interface...eth1
2009/02/24 08:41:58 :: autoconnecting... eth1
2009/02/24 08:41:58 :: scanning start
2009/02/24 08:41:58 :: ifconfig eth1 up
2009/02/24 08:41:59 :: iwlist eth1 scan
2009/02/24 08:41:59 :: scanning done
2009/02/24 08:41:59 :: found 0 networks:
2009/02/24 08:41:59 :: ifconfig eth0 up
2009/02/24 08:42:01 :: No wired connection present, attempting to autoconnect to wireless network
2009/02/24 08:42:01 :: Unable to autoconnect, you'll have to manually connect
2009/02/24 08:42:08 :: ifconfig eth0
2009/02/24 08:42:08 :: ifconfig eth1
2009/02/24 08:42:08 :: returning automatically reconnect when connection drops True
2009/02/24 08:42:08 :: iwconfig eth1
2009/02/24 08:42:08 :: GetCurrentNetworkID: Returning -1, current network not found
2009/02/24 08:42:08 :: scanning start
2009/02/24 08:42:08 :: ifconfig eth1 up
2009/02/24 08:42:08 :: iwlist eth1 scan
2009/02/24 08:42:08 :: scanning done
2009/02/24 08:42:08 :: found 0 networks:
2009/02/24 08:42:08 :: No wired connection present, attempting to autoconnect to wireless network
2009/02/24 08:42:08 :: Unable to autoconnect, you'll have to manually connect
2009/02/24 08:42:12 :: ifconfig eth0
2009/02/24 08:42:12 :: ifconfig eth1
2009/02/24 08:42:12 :: returning automatically reconnect when connection drops True
2009/02/24 08:42:12 :: iwconfig eth1
2009/02/24 08:42:12 :: GetCurrentNetworkID: Returning -1, current network not found
2009/02/24 08:42:12 :: scanning start
2009/02/24 08:42:12 :: ifconfig eth1 up
2009/02/24 08:42:12 :: iwlist eth1 scan
2009/02/24 08:42:12 :: scanning done
2009/02/24 08:42:12 :: found 0 networks:
2009/02/24 08:42:12 :: No wired connection present, attempting to autoconnect to wireless network
2009/02/24 08:42:12 :: Unable to autoconnect, you'll have to manually connect
2009/02/24 08:42:16 :: ifconfig eth0
2009/02/24 08:42:16 :: ifconfig eth1
2009/02/24 08:42:16 :: returning automatically reconnect when connection drops True
2009/02/24 08:42:16 :: iwconfig eth1
2009/02/24 08:42:16 :: GetCurrentNetworkID: Returning -1, current network not found
2009/02/24 08:42:16 :: scanning start
2009/02/24 08:42:16 :: ifconfig eth1 up
2009/02/24 08:42:16 :: iwlist eth1 scan
2009/02/24 08:42:16 :: scanning done
2009/02/24 08:42:16 :: found 0 networks:
2009/02/24 08:42:16 :: No wired connection present, attempting to autoconnect to wireless network
2009/02/24 08:42:16 :: Unable to autoconnect, you'll have to manually connect

2009/02/24 09:12:36 :: returning automatically reconnect when connection drops True
2009/02/24 09:12:36 :: GetCurrentNetworkID: Returning -1, current network not found
2009/02/24 09:12:36 :: scanning start
2009/02/24 09:12:36 :: ifconfig eth1 up
2009/02/24 09:12:36 :: iwlist eth1 scan
2009/02/24 09:12:36 :: scanning done
2009/02/24 09:12:36 :: found 16 networks:
2009/02/24 09:12:36 :: 00:1E:BE:A8:75:B0
2009/02/24 09:12:36 :: 00:13:10:EB:F5:60
2009/02/24 09:12:36 :: 00:1E:52:7A:6A:EB
2009/02/24 09:12:36 :: 00:18:F8:B5:90:78
2009/02/24 09:12:36 :: 00:18:39:52:D4:90
2009/02/24 09:12:36 :: 00:1E:E5:74:EB:70
2009/02/24 09:12:36 :: 00:E0:98:E7:B2:75
2009/02/24 09:12:37 :: 82:71:00:6C:5A:EC
2009/02/24 09:12:37 :: 00:18:01:82:CC:70
2009/02/24 09:12:37 :: 6A:A9:C9:0E:EA:4E
2009/02/24 09:12:37 :: 00:17:3F:67:2D:BA
2009/02/24 09:12:37 :: 06:C8:D7:BF:40:01
2009/02/24 09:12:37 :: 00:14:A5:99:42:0A
2009/02/24 09:12:37 :: FA:76:EE:96:F8:9B
2009/02/24 09:12:37 :: 00:E0:98:53:EB:14
2009/02/24 09:12:37 :: 00:1C:10:4C:0F:DF
2009/02/24 09:12:37 :: No wired connection present, attempting to autoconnect to wireless network
2009/02/24 09:12:37 :: Unable to autoconnect, you'll have to manually connect

2009/02/24 09:14:14 :: returning automatically reconnect when connection drops True
2009/02/24 09:14:15 :: ifconfig eth0

2009/02/24 09:15:42 :: Connecting to wireless network linksys
2009/02/24 09:15:42 :: Putting interface down
2009/02/24 09:15:42 :: ifconfig eth1 down
2009/02/24 09:15:42 :: Releasing DHCP leases...
2009/02/24 09:15:43 :: Setting false IP...
2009/02/24 09:15:43 :: ifconfig eth1 0.0.0.0 
2009/02/24 09:15:43 :: ifconfig eth0 0.0.0.0 
2009/02/24 09:15:43 :: Stopping wpa_supplicant and any DHCP clients
2009/02/24 09:15:43 :: killall wpa_supplicant
2009/02/24 09:15:43 :: Flushing the routing table...
2009/02/24 09:15:43 :: ip route flush dev eth1
2009/02/24 09:15:43 :: ip route flush dev eth0
2009/02/24 09:15:43 :: Putting interface up...
2009/02/24 09:15:43 :: ifconfig eth1 up
2009/02/24 09:15:43 :: iwconfig eth1 mode Managed
2009/02/24 09:15:43 :: iwconfig eth1 essid "linksys" channel 6 ap 00:13:10:EB:F5:60
2009/02/24 09:15:43 :: Running DHCP
2009/02/24 09:15:43 :: /sbin/dhclient eth1
2009/02/24 09:15:43 :: There is already a pid file /var/run/dhclient.pid with pid 134519072
2009/02/24 09:15:43 :: Internet Systems Consortium DHCP Client V3.0.6
2009/02/24 09:15:43 :: Copyright 2004-2007 Internet Systems Consortium.
2009/02/24 09:15:43 :: All rights reserved.
2009/02/24 09:15:43 :: For info, please visit http://www.isc.org/sw/dhcp/
2009/02/24 09:15:43 :: 
2009/02/24 09:15:44 :: iwconfig eth1
2009/02/24 09:15:44 :: iwconfig eth1
2009/02/24 09:15:44 :: iwconfig eth1
2009/02/24 09:15:44 :: iwconfig eth1
2009/02/24 09:15:44 :: iwconfig eth1
2009/02/24 09:15:44 :: iwconfig eth1
2009/02/24 09:15:44 :: iwconfig eth1
2009/02/24 09:15:44 :: iwconfig eth1
2009/02/24 09:15:44 :: iwconfig eth1
2009/02/24 09:15:44 :: iwconfig eth1
2009/02/24 09:15:44 :: iwconfig eth1
2009/02/24 09:15:44 :: iwconfig eth1
2009/02/24 09:15:44 :: iwconfig eth1
2009/02/24 09:15:44 :: Listening on LPF/eth1/00:23:08:4f:71:a3
2009/02/24 09:15:44 :: Sending on   LPF/eth1/00:23:08:4f:71:a3
2009/02/24 09:15:44 :: Sending on   Socket/fallback
2009/02/24 09:15:44 :: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
2009/02/24 09:15:44 :: iwconfig eth1
2009/02/24 09:15:44 :: iwconfig eth1
2009/02/24 09:15:44 :: iwconfig eth1
2009/02/24 09:15:44 :: iwconfig eth1
2009/02/24 09:15:47 :: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
2009/02/24 09:15:53 :: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
2009/02/24 09:16:08 :: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
2009/02/24 09:16:15 :: No DHCPOFFERS received.
2009/02/24 09:16:15 :: Trying recorded lease 192.168.0.5
2009/02/24 09:16:18 :: PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
2009/02/24 09:16:18 :: 
2009/02/24 09:16:18 :: --- 192.168.0.1 ping statistics ---
2009/02/24 09:16:18 :: 1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms
2009/02/24 09:16:18 :: 
2009/02/24 09:16:27 :: No working leases in persistent database - sleeping.
2009/02/24 09:16:28 :: DHCP connection failed
2009/02/24 09:16:28 :: exiting connection thread
2009/02/24 09:16:28 :: ifconfig eth0
2009/02/24 09:16:28 :: ifconfig eth1

2009/02/24 09:17:05 :: ifconfig eth0
2009/02/24 09:17:05 :: ifconfig eth1
2009/02/24 09:17:06 :: Connecting to wireless network DCSuperiorCourt
2009/02/24 09:17:06 :: Putting interface down
2009/02/24 09:17:06 :: ifconfig eth1 down
2009/02/24 09:17:06 :: Releasing DHCP leases...
2009/02/24 09:17:06 :: Setting false IP...
2009/02/24 09:17:06 :: ifconfig eth1 0.0.0.0 
2009/02/24 09:17:06 :: ifconfig eth0 0.0.0.0 
2009/02/24 09:17:06 :: Stopping wpa_supplicant and any DHCP clients
2009/02/24 09:17:06 :: killall wpa_supplicant
2009/02/24 09:17:06 :: Flushing the routing table...
2009/02/24 09:17:06 :: ip route flush dev eth1
2009/02/24 09:17:06 :: ip route flush dev eth0
2009/02/24 09:17:06 :: Putting interface up...
2009/02/24 09:17:06 :: ifconfig eth1 up
2009/02/24 09:17:06 :: iwconfig eth1 mode Managed
2009/02/24 09:17:06 :: iwconfig eth1 essid "DCSuperiorCourt" channel 11 ap 00:1E:BE:A8:75:B0
2009/02/24 09:17:06 :: Running DHCP
2009/02/24 09:17:06 :: /sbin/dhclient eth1
2009/02/24 09:17:06 :: There is already a pid file /var/run/dhclient.pid with pid 134519072
2009/02/24 09:17:06 :: Internet Systems Consortium DHCP Client V3.0.6
2009/02/24 09:17:06 :: Copyright 2004-2007 Internet Systems Consortium.
2009/02/24 09:17:06 :: All rights reserved.
2009/02/24 09:17:06 :: For info, please visit http://www.isc.org/sw/dhcp/
2009/02/24 09:17:06 :: 
2009/02/24 09:17:07 :: Listening on LPF/eth1/00:23:08:4f:71:a3
2009/02/24 09:17:07 :: Sending on   LPF/eth1/00:23:08:4f:71:a3
2009/02/24 09:17:07 :: Sending on   Socket/fallback
2009/02/24 09:17:07 :: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
2009/02/24 09:17:08 :: iwconfig eth1
2009/02/24 09:17:08 :: iwconfig eth1
2009/02/24 09:17:08 :: iwconfig eth1
2009/02/24 09:17:08 :: iwconfig eth1
2009/02/24 09:17:08 :: iwconfig eth1
2009/02/24 09:17:08 :: iwconfig eth1
2009/02/24 09:17:08 :: iwconfig eth1
2009/02/24 09:17:08 :: iwconfig eth1
2009/02/24 09:17:08 :: iwconfig eth1
2009/02/24 09:17:08 :: iwconfig eth1
2009/02/24 09:17:08 :: iwconfig eth1
2009/02/24 09:17:08 :: iwconfig eth1
2009/02/24 09:17:08 :: iwconfig eth1
2009/02/24 09:17:08 :: iwconfig eth1
2009/02/24 09:17:08 :: iwconfig eth1
2009/02/24 09:17:08 :: iwconfig eth1
2009/02/24 09:17:08 :: iwconfig eth1
2009/02/24 09:17:11 :: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
2009/02/24 09:17:21 :: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
2009/02/24 09:17:31 :: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
2009/02/24 09:17:38 :: No DHCPOFFERS received.
2009/02/24 09:17:38 :: Trying recorded lease 192.168.0.5
2009/02/24 09:17:41 :: PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
2009/02/24 09:17:41 :: 
2009/02/24 09:17:41 :: --- 192.168.0.1 ping statistics ---
2009/02/24 09:17:41 :: 1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms
2009/02/24 09:17:41 :: 
2009/02/24 09:17:50 :: No working leases in persistent database - sleeping.
2009/02/24 09:17:50 :: DHCP connection failed
2009/02/24 09:17:50 :: exiting connection thread
2009/02/24 09:17:51 :: ifconfig eth0
2009/02/24 09:17:51 :: ifconfig eth1
2009/02/24 09:17:52 :: ifconfig eth0
2009/02/24 09:17:52 :: ifconfig eth1
2009/02/24 09:17:52 :: returning automatically reconnect when connection drops True
2009/02/24 09:17:52 :: GetCurrentNetworkID: Returning -1, current network not found
2009/02/24 09:17:52 :: scanning start
2009/02/24 09:17:52 :: ifconfig eth1 up
2009/02/24 09:17:52 :: iwlist eth1 scan
2009/02/24 09:17:52 :: scanning done
2009/02/24 09:17:52 :: found 15 networks:
2009/02/24 09:17:52 :: 00:1E:BE:A8:75:B0
2009/02/24 09:17:52 :: 00:13:10:EB:F5:60
2009/02/24 09:17:52 :: 00:17:3F:67:2D:BA
2009/02/24 09:17:52 :: 00:1C:10:4C:0F:DF
2009/02/24 09:17:52 :: 6A:A9:C9:0E:EA:4E
2009/02/24 09:17:52 :: 00:15:6D:A6:D7:F3
2009/02/24 09:17:52 :: 82:71:00:6C:5A:EC
2009/02/24 09:17:52 :: 00:1E:52:7A:6A:EB
2009/02/24 09:17:52 :: 00:21:91:D1:6C:E1
2009/02/24 09:17:52 :: 00:18:F8:B5:90:78
2009/02/24 09:17:52 :: 00:1E:E5:74:EB:70
2009/02/24 09:17:52 :: 06:C8:D7:BF:40:01
2009/02/24 09:17:52 :: 00:0B:33:01:87:4C
2009/02/24 09:17:52 :: 00:1B:D5:96:B8:70
2009/02/24 09:17:53 :: 00:1D:7E:D8:AF:6F
2009/02/24 09:17:53 :: No wired connection present, attempting to autoconnect to wireless network
2009/02/24 09:17:53 :: Unable to autoconnect, you'll have to manually connect
2009/02/24 09:17:53 :: ifconfig eth0
2009/02/24 09:17:53 :: ifconfig eth1


```

---

### Post by imdano on 2009-02-24
Try creating a script that  runs exactly what wicd does, and see what happens (taken from the log file):
```

2009/02/24 09:17:06 :: ifconfig eth1 down
2009/02/24 09:17:06 :: ifconfig eth1 0.0.0.0 
2009/02/24 09:17:06 :: ifconfig eth0 0.0.0.0 
2009/02/24 09:17:06 :: ip route flush dev eth1
2009/02/24 09:17:06 :: ip route flush dev eth0
2009/02/24 09:17:06 :: ifconfig eth1 up
2009/02/24 09:17:06 :: iwconfig eth1 mode Managed
2009/02/24 09:17:06 :: iwconfig eth1 essid "DCSuperiorCourt" channel 11 ap 00:1E:BE:A8:75:B0
2009/02/24 09:17:06 :: /sbin/dhclient eth1
```

---

### Post by YWELLC on 2009-02-25
When I run the script using the same commands from the wicd.log file, I can connect to the unsecured network and be assigned an IP via DHCP.  Everything works - really strange.

---

### Post by Reiger on 2009-02-25
I've experienced the same, and I figure that this is because WICD keeps its own wicd-version of the /etc/wpa_supplicant.conf. Try removing /etc/wpa_supplicant.conf (it will be regenerated by WICD). If that doesn't fix it, try removing both that file and /etc/wicd/wireless-settings.conf. (That too will be regenerated.) Unfortunately the latter means you will have to retype authentication info.) Another but more convoluted approach might be to back up the wireless-settings.conf, and use a script to substitute a backup for wireless-settings.conf; this is rather more involved, though.

---

### Post by imdano on 2009-02-25
His network doesn't have encryption on it, so wpa_supplicant isn't involved at all.  Even if he was, having /etc/wpa_supplicant.conf around has no affect, because wicd generates its own and puts it in /var/lib/wicd/configurations.  Deleting /etc/wireless-settings.conf will just erase the all his saved settings for wireless networks, which I don't think will help in this situation, though I suppose it won't hurt to try.

YWELLC, try closing the wicd GUI while it's connecting, and just check the tray icon for connection status.  It's a long shot, but wicd 1.5.x polls for network status pretty aggressively while the GUI is open, it's possible (though unlikely) that might be affecting the connection attempt.  Also, which version are you using?  Try upgrading to 1.5.9 if you're not already using it.

---

### Post by YWELLC on 2009-02-26
Actually I do have a WPA network setup at home, which is why I switched to wicd, as NM was giving me a lot of problems.  Wicd works perfectly with my stored settings and WPA on my static IP network at home.  It is when I leave and try to connect to (any) unsecured wi-fi network w/dhcp that it is a problem.

That said, I followed your advice and killed the GUI after pressing connect, no dice.  For good measure I deleted the contents of /etc/wireless-settings.con also to no avail.  

I appreciate your continued assistance in this highly annoying matter.

---

### Post by rrwood on 2009-03-27
I'm having the same problem here.

Wicd successfully grabs an IP at boot, but can't do so later on (e.g. if I use the wicd GUI to disconnect and then reconnect to the same wifi router).

Bringing up the connection manually works fine at any time (i.e. by configuring /etc/network/interfaces and doing an "ifup eth1" or by a series of iwconfig and dhclient commands).  Wicd just doesn't seem to like reconnecting.

Anyone have any insight on this?

---

### Post by jisare on 2009-05-04
same problem here..

---

### Post by daniel3ub on 2009-07-04
Same problem here using a wired network with DHCP.
Wicd ver 1.5.9, Ubuntu 8.04 always updated.

Any idea?

---

### Post by bigchrisrogers on 2009-07-06
I'm getting the same problem.  However,  I'm currently on a long business trip in the USA and have been in a different hotel every night.  Most hotels all is fine, some hotels I get exactly this problem.  I don't change any settings between hotels.  If I can't get on with Ubuntu to check web-mail etc, then I dual boot into Windows and all is fine using explorer.  When I'm back home or in the office, all is O.K.

---

### Post by del_diablo on 2009-09-02
[IMG]http://grendelsrevenge.skotos.net//images/120/undead-raisedead-lg.png[/IMG]

Ok, I am going to revive this tread since this is about my issue/problem. At school we use a sort of "hotspot" to get internet access, but I can't connect under Ubuntu using Wicd. It does work under Windows, and during the vacation I had a few weeks ago I could not connect to the wireless hotspot on the hotel I was staying on a few days using Wicd under Ubuntu.
Some nifty searching gave me a link to this: [>link]("http://www.linuxquestions.org/questions/slackware-14/not-able-to-connect-to-wireless-hotspots-583777/"), which I guess is the exact same problem and a solution to it.
I guess it seems related to Ubuntus or Wicds default setting on connecting to wireless networks(wants ip and all that when none is given).

---

### Post by del_diablo on 2009-09-03
Ok, i am at school at the moment. The script in the opening post is not working to get me onto the hotspot.

---

### Post by bmc5311 on 2009-12-14
I have had the same problem with open wifi networks.  i do not have a solution, but am interested in finding one.

---

