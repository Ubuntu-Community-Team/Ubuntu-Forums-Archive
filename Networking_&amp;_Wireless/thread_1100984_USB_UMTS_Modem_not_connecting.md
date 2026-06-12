---
title: "USB UMTS Modem not connecting"
date: 2009-03-19
forum: Networking &amp; Wireless
---

### Post by manku on 2009-03-19
Hello,
I'm running Intrepid Ibex 8.10 LiveCD. I've been trying to set a broadband mobile connection with a USB UMTS Modem.
When I plugged in the modem it was recognized and Network Manager prompted me for configuration and I created a new connection with the same data that I used to configure the connection and successfully connect in Vista.
Unfortunately I couldn't manage to activate the connection. 
After many tries I understood that each time I configure a new connection there's a different behaviour between the first attempt and the others. Here is what was logged during the first try of a new connection: ```

Mar 20 23:30:04 ubuntu NetworkManager: <info>  Activation (ttyUSB0) starting connection 'H3G (pre-paid)' 
Mar 20 23:30:04 ubuntu NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 
Mar 20 23:30:04 ubuntu NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 20 23:30:04 ubuntu NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started... 
Mar 20 23:30:04 ubuntu NetworkManager: <debug> [1237591804.212435] nm_serial_device_open(): (ttyUSB0) opening device... 
Mar 20 23:30:04 ubuntu NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete. 
Mar 20 23:30:04 ubuntu NetworkManager: <info>  (ttyUSB0): GSM pin secret required 
Mar 20 23:30:04 ubuntu NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 6 
Mar 20 23:30:18 ubuntu NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 20 23:30:18 ubuntu NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started... 
Mar 20 23:30:18 ubuntu NetworkManager: <info>  (ttyUSB0): device state change: 6 -> 4 
Mar 20 23:30:18 ubuntu NetworkManager: <debug> [1237591818.171971] nm_serial_device_open(): (ttyUSB0) opening device... 
Mar 20 23:30:18 ubuntu NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete. 
Mar 20 23:30:18 ubuntu NetworkManager: <info>  (ttyUSB0): powering up... 
Mar 20 23:30:19 ubuntu NetworkManager: <info>  Searching for a network... 
Mar 20 23:30:19 ubuntu last message repeated 36 times
Mar 20 23:30:19 ubuntu NetworkManager: <info>  Registered on Home network 
Mar 20 23:30:19 ubuntu NetworkManager: <info>  Associated with network: +COPS: 0,0,"3 ITA",2 
Mar 20 23:30:19 ubuntu NetworkManager: <info>  Connected, Woo! 
Mar 20 23:30:19 ubuntu NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) scheduled... 
Mar 20 23:30:19 ubuntu NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) starting... 
Mar 20 23:30:19 ubuntu NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 5 
Mar 20 23:30:20 ubuntu NetworkManager: <info>  Starting pppd connection 
Mar 20 23:30:20 ubuntu NetworkManager: <debug> [1237591820.040969] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock ttyUSB0 noipdefault usepeerdns ipparam /org/freedesktop/NetworkManager/PPP/0 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so 
Mar 20 23:30:20 ubuntu NetworkManager: <debug> [1237591820.162875] nm_ppp_manager_start(): ppp started with pid 8389 
Mar 20 23:30:20 ubuntu NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) complete. 
Mar 20 23:30:20 ubuntu pppd[8389]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Mar 20 23:30:20 ubuntu kernel: [  328.671848] PPP generic driver version 2.4.2
Mar 20 23:30:20 ubuntu kernel: [  328.871145] NET: Registered protocol family 10
Mar 20 23:30:20 ubuntu kernel: [  328.874166] lo: Disabled Privacy Extensions
Mar 20 23:30:20 ubuntu kernel: [  328.877106] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 20 23:30:20 ubuntu pppd[8389]: pppd 2.4.4 started by root, uid 0
Mar 20 23:30:20 ubuntu kernel: [  328.880326] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 20 23:30:20 ubuntu pppd[8389]: Using interface ppp0
Mar 20 23:30:20 ubuntu pppd[8389]: Connect: ppp0 <--> /dev/ttyUSB0
Mar 20 23:30:20 ubuntu NetworkManager: <info>  (ttyUSB0): device state change: 5 -> 6 
Mar 20 23:30:20 ubuntu pppd[8389]: CHAP authentication succeeded
Mar 20 23:30:20 ubuntu pppd[8389]: CHAP authentication succeeded
Mar 20 23:30:20 ubuntu NetworkManager: <info>  (ttyUSB0): device state change: 6 -> 7 
Mar 20 23:30:20 ubuntu kernel: [  329.140830] PPP BSD Compression module registered
Mar 20 23:30:20 ubuntu kernel: [  329.187628] PPP Deflate Compression module registered
Mar 20 23:30:28 ubuntu pppd[8389]: Modem hangup
Mar 20 23:30:28 ubuntu NetworkManager: <info>  (ttyUSB0): device state change: 7 -> 9 
Mar 20 23:30:28 ubuntu NetworkManager: <debug> [1237591828.140138] nm_serial_device_close(): Closing device 'ttyUSB0' 
Mar 20 23:30:28 ubuntu NetworkManager: <info>  Marking connection 'H3G (pre-paid)' invalid. 
Mar 20 23:30:28 ubuntu NetworkManager: <info>  Activation (ttyUSB0) failed. 
Mar 20 23:30:28 ubuntu NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 
Mar 20 23:30:28 ubuntu pppd[8389]: Connection terminated.
Mar 20 23:30:28 ubuntu NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0). 
Mar 20 23:30:28 ubuntu NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Mar 20 23:30:28 ubuntu NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
Mar 20 23:30:29 ubuntu pppd[8389]: Exit.
Mar 20 23:30:30 ubuntu NetworkManager: <debug> [1237591830.145289] ensure_killed(): waiting for ppp pid 8389 to exit 
Mar 20 23:30:30 ubuntu NetworkManager: <debug> [1237591830.145471] ensure_killed(): ppp pid 8389 cleaned up 

```


And here is what was logged trying again to connect with the same connection.

```

Mar 20 22:34:29 ubuntu NetworkManager: <info>  Activation (ttyUSB0) starting connection 'TRE' 
Mar 20 22:34:29 ubuntu NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 
Mar 20 22:34:29 ubuntu NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 20 22:34:29 ubuntu NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started... 
Mar 20 22:34:29 ubuntu NetworkManager: <debug> [1237588469.317790] nm_serial_device_open(): (ttyUSB0) opening device... 
Mar 20 22:34:29 ubuntu NetworkManager: <WARN>  nm_serial_device_open(): (ttyUSB0) cannot control device (errno 6) 
Mar 20 22:34:29 ubuntu NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 9 
Mar 20 22:34:29 ubuntu NetworkManager: <debug> [1237588469.318013] nm_serial_device_close(): Closing device 'ttyUSB0' 
Mar 20 22:34:29 ubuntu NetworkManager: <info>  Marking connection 'TRE' invalid. 
Mar 20 22:34:29 ubuntu NetworkManager: <info>  Activation (ttyUSB0) failed. 
Mar 20 22:34:29 ubuntu NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete. 
Mar 20 22:34:29 ubuntu NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 
Mar 20 22:34:29 ubuntu NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0). 
Mar 20 22:34:29 ubuntu NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Mar 20 22:34:29 ubuntu NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed


```


If anyone could help I would be very grateful :)

Regards,
manku

---

### Post by motin on 2009-04-25
I have had this issue for several months and it keeps happening after Jaunty upgrade, so it's about time we find the existing bug report on it, or if none found - report a new bug. 

If I suspend and wake the laptop again, the modem becomes available again. Is it the same for you?

---

