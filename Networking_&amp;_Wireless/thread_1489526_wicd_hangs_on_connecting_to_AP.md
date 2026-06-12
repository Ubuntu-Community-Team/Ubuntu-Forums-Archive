---
title: "wicd hangs on connecting to AP"
date: 2010-05-21
forum: Networking &amp; Wireless
---

### Post by bangmalley on 2010-05-21
I'm trying to connect through GUI, because having problem with the tray icon too.
So, after I type the password of the AP (AP using WEP), then it just hangs there.

This is the output of wicd.log
```
2010/05/21 18:50:04 :: [Wireless ESSID] has profile
2010/05/21 18:50:04 :: trying to automatically connect to...[Wireless ESSID]
2010/05/21 18:50:04 :: Connecting to wireless network [Wireless ESSID]
2010/05/21 18:50:04 :: iwconfig eth2
2010/05/21 18:50:04 :: attempting to set hostname with dhclient
2010/05/21 18:50:04 :: using dhcpcd or another supported client may work better
2010/05/21 18:50:04 :: /sbin/dhclient -r eth2
2010/05/21 18:50:05 :: ifconfig eth2 0.0.0.0 
2010/05/21 18:50:05 :: /sbin/ip route flush dev eth2
2010/05/21 18:50:05 :: ifconfig eth2 down
2010/05/21 18:50:05 :: ifconfig eth2 up
2010/05/21 18:50:05 :: wpa_cli -i eth2 terminate
2010/05/21 18:50:05 :: attempting to set hostname with dhclient
2010/05/21 18:50:05 :: using dhcpcd or another supported client may work better
2010/05/21 18:50:05 :: /sbin/dhclient -r eth0
2010/05/21 18:50:05 :: ifconfig eth0 0.0.0.0 
2010/05/21 18:50:05 :: /sbin/ip route flush dev eth0
2010/05/21 18:50:05 :: ifconfig eth0 down
2010/05/21 18:50:05 :: ifconfig eth0 up
2010/05/21 18:50:05 :: Putting interface down
2010/05/21 18:50:05 :: ifconfig eth2 down
2010/05/21 18:50:05 :: Releasing DHCP leases...
2010/05/21 18:50:05 :: attempting to set hostname with dhclient
2010/05/21 18:50:05 :: using dhcpcd or another supported client may work better
2010/05/21 18:50:05 :: /sbin/dhclient -r eth2
2010/05/21 18:50:05 :: Setting false IP...
2010/05/21 18:50:05 :: ifconfig eth2 0.0.0.0 
2010/05/21 18:50:05 :: Stopping wpa_supplicant
2010/05/21 18:50:05 :: wpa_cli -i eth2 terminate
2010/05/21 18:50:05 :: Flushing the routing table...
2010/05/21 18:50:05 :: /sbin/ip route flush dev eth2
2010/05/21 18:50:05 :: iwconfig eth2 mode Managed
2010/05/21 18:50:06 :: Putting interface up...
2010/05/21 18:50:06 :: ifconfig eth2 up
2010/05/21 18:50:08 :: enctype is wpa
2010/05/21 18:50:08 :: Generating psk...
2010/05/21 18:50:08 :: ['/usr/bin/wpa_passphrase', '[Wireless ESSID]', '[Wireless password]']
2010/05/21 18:50:08 :: Attempting to authenticate...
2010/05/21 18:50:08 :: ['wpa_supplicant', '-B', '-i', 'eth2', '-c', '/var/lib/wicd/configurations/001ac1204c80', '-D', 'wext']
2010/05/21 18:50:08 :: ['iwconfig', 'eth2', 'essid', '--', '[Wireless ESSID]']
2010/05/21 18:50:08 :: iwconfig eth2 channel 4
2010/05/21 18:50:08 :: iwconfig eth2 ap 00:1A:C1:20:4C:80
2010/05/21 18:50:08 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:09 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:10 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:11 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:12 :: iwconfig eth2
2010/05/21 18:50:12 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:13 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:14 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:15 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:16 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:17 :: iwconfig eth2
2010/05/21 18:50:17 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:18 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:19 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:20 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:21 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:22 :: iwconfig eth2
2010/05/21 18:50:22 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:23 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:24 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:25 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:26 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:27 :: iwconfig eth2
2010/05/21 18:50:27 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:28 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:29 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:30 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:31 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:32 :: iwconfig eth2
2010/05/21 18:50:32 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:33 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:34 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:35 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:36 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:37 :: iwconfig eth2
2010/05/21 18:50:37 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:38 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:39 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:40 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:41 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:42 :: iwconfig eth2
2010/05/21 18:50:42 :: WPA_CLI RESULT IS SCANNING
2010/05/21 18:50:43 :: wpa_supplicant authentication may have failed.
2010/05/21 18:50:43 :: connect result is Failed
2010/05/21 18:50:43 :: exiting connection thread
2010/05/21 18:50:47 :: Sending connection attempt result bad_pass
2010/05/21 18:50:47 :: ifconfig eth0
2010/05/21 18:50:47 :: ifconfig eth2
2010/05/21 18:50:47 :: iwconfig eth2
2010/05/21 18:50:47 :: GetCurrentNetworkID: Returning -1, current network not found
2010/05/21 18:50:47 :: Autoconnecting...
2010/05/21 18:50:47 :: Starting wireless autoconnect...
2010/05/21 18:50:47 :: No wired connection present, attempting to autoconnect to wireless network
2010/05/21 18:50:47 :: scanning start
2010/05/21 18:50:47 :: ifconfig eth2 up
2010/05/21 18:50:47 :: iwlist eth2 scan
2010/05/21 18:50:48 :: scanning done
2010/05/21 18:50:48 :: found 0 networks:
2010/05/21 18:50:48 :: Unable to autoconnect, you'll have to manually connect
2010/05/21 18:50:48 :: Forced disconnect on
2010/05/21 18:50:48 :: attempting to set hostname with dhclient
2010/05/21 18:50:48 :: using dhcpcd or another supported client may work better
2010/05/21 18:50:48 :: /sbin/dhclient -r eth2
2010/05/21 18:50:48 :: ifconfig eth2 0.0.0.0 
2010/05/21 18:50:48 :: /sbin/ip route flush dev eth2
2010/05/21 18:50:48 :: ifconfig eth2 down
2010/05/21 18:50:48 :: ifconfig eth2 up
2010/05/21 18:50:48 :: wpa_cli -i eth2 terminate
2010/05/21 18:50:48 :: attempting to set hostname with dhclient
2010/05/21 18:50:48 :: using dhcpcd or another supported client may work better
2010/05/21 18:50:48 :: /sbin/dhclient -r eth0
2010/05/21 18:50:48 :: ifconfig eth0 0.0.0.0 
2010/05/21 18:50:48 :: /sbin/ip route flush dev eth0
2010/05/21 18:50:48 :: ifconfig eth0 down
2010/05/21 18:50:48 :: ifconfig eth0 up
```

I attached the full wicd.log for reference.

---

