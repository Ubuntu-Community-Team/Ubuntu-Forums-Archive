---
title: "No network connection when waking from sleep"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by DancesWithWinnebagos on 2009-03-04
Whenever I wake from sleep, I no longer have a network connection. 
I think these are the appropriate logs:
Mar  4 19:50:53 john-ubuntu NetworkManager: <info>  Sleeping... 
Mar  4 19:50:53 john-ubuntu NetworkManager: <info>  (eth57): now unmanaged 
Mar  4 19:50:53 john-ubuntu NetworkManager: <info>  (eth57): device state change: 2 -> 1 
Mar  4 19:50:53 john-ubuntu NetworkManager: <info>  (eth57): cleaning up... 
Mar  4 19:50:53 john-ubuntu NetworkManager: <info>  (eth57): taking down device. 
Mar  4 19:50:53 john-ubuntu NetworkManager: <info>  (eth58): now unmanaged 
Mar  4 19:50:53 john-ubuntu NetworkManager: <info>  (eth58): device state change: 2 -> 1 
Mar  4 19:50:53 john-ubuntu NetworkManager: <info>  (eth58): cleaning up... 
Mar  4 19:50:53 john-ubuntu NetworkManager: <info>  (eth58): taking down device. 
Mar  4 19:50:53 john-ubuntu NetworkManager: <info>  (eth2): now unmanaged 
Mar  4 19:50:53 john-ubuntu NetworkManager: <info>  (eth2): device state change: 3 -> 1 
Mar  4 19:50:53 john-ubuntu NetworkManager: <info>  (eth2): cleaning up... 
Mar  4 19:50:53 john-ubuntu NetworkManager: <info>  (eth2): taking down device. 
Mar  4 19:50:53 john-ubuntu avahi-daemon[5804]: Withdrawing address record for [SNIP] on eth2.
Mar  4 19:50:53 john-ubuntu NetworkManager: <info>  (eth2): carrier now OFF (device state 1) 
Mar  4 19:50:56 john-ubuntu NetworkManager: <info>  Waking up... 
Mar  4 19:50:56 john-ubuntu NetworkManager: <info>  (eth57): now managed 
Mar  4 19:50:56 john-ubuntu NetworkManager: <info>  (eth57): device state change: 1 -> 2 
Mar  4 19:50:56 john-ubuntu NetworkManager: <info>  (eth57): bringing up device. 
Mar  4 19:50:56 john-ubuntu kernel: [ 2700.149684] eth57: no link during initialization.
Mar  4 19:50:56 john-ubuntu NetworkManager: <info>  (eth57): preparing device. 
Mar  4 19:50:56 john-ubuntu kernel: [ 2700.150646] ADDRCONF(NETDEV_UP): eth57: link is not ready
Mar  4 19:50:56 john-ubuntu NetworkManager: <info>  (eth57): deactivating device (reason: 2). 
Mar  4 19:50:56 john-ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Mar  4 19:50:56 john-ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Mar  4 19:50:56 john-ubuntu NetworkManager: <info>  (eth58): now managed 
Mar  4 19:50:56 john-ubuntu NetworkManager: <info>  (eth58): device state change: 1 -> 2 
Mar  4 19:50:56 john-ubuntu NetworkManager: <info>  (eth58): bringing up device. 
Mar  4 19:50:56 john-ubuntu kernel: [ 2700.152928] eth58: no link during initialization.
Mar  4 19:50:56 john-ubuntu NetworkManager: <info>  (eth58): preparing device. 
Mar  4 19:50:56 john-ubuntu kernel: [ 2700.153879] ADDRCONF(NETDEV_UP): eth58: link is not ready
Mar  4 19:50:56 john-ubuntu NetworkManager: <info>  (eth58): deactivating device (reason: 2). 
Mar  4 19:50:56 john-ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Mar  4 19:50:56 john-ubuntu NetworkManager: <info>  (eth2): now managed 
Mar  4 19:50:56 john-ubuntu NetworkManager: <info>  (eth2): device state change: 1 -> 2 
Mar  4 19:50:56 john-ubuntu NetworkManager: <info>  (eth2): bringing up device. 
Mar  4 19:50:56 john-ubuntu NetworkManager: <info>  (eth2): preparing device. 
Mar  4 19:50:56 john-ubuntu kernel: [ 2700.156783] ADDRCONF(NETDEV_UP): eth2: link is not ready
Mar  4 19:50:56 john-ubuntu NetworkManager: <info>  (eth2): deactivating device (reason: 2). 
Mar  4 19:50:56 john-ubuntu kernel: [ 2700.157907] e1000: eth2: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Mar  4 19:50:56 john-ubuntu kernel: [ 2700.158609] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
Mar  4 19:50:56 john-ubuntu NetworkManager: <info>  (eth2): carrier now ON (device state 2) 
Mar  4 19:50:56 john-ubuntu NetworkManager: <info>  (eth2): device state change: 2 -> 3 
Mar  4 19:50:57 john-ubuntu avahi-daemon[5804]: Registering new address record for [snip] on eth2.*.
Mar  4 19:51:06 john-ubuntu NetworkManager: <info>  Activation (eth2) starting connection 'Auto eth2' 
Mar  4 19:51:06 john-ubuntu NetworkManager: <info>  (eth2): device state change: 3 -> 4 
Mar  4 19:51:06 john-ubuntu NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) scheduled... 
Mar  4 19:51:06 john-ubuntu NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) started... 
Mar  4 19:51:06 john-ubuntu NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) scheduled... 
Mar  4 19:51:06 john-ubuntu NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) complete. 
Mar  4 19:51:06 john-ubuntu NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) starting... 
Mar  4 19:51:06 john-ubuntu NetworkManager: <info>  (eth2): device state change: 4 -> 5 
Mar  4 19:51:06 john-ubuntu NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) successful. 
Mar  4 19:51:06 john-ubuntu NetworkManager: <info>  Activation (eth2) Stage 3 of 5 (IP Configure Start) scheduled. 
Mar  4 19:51:06 john-ubuntu NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) complete. 
Mar  4 19:51:06 john-ubuntu NetworkManager: <info>  Activation (eth2) Stage 3 of 5 (IP Configure Start) started... 
Mar  4 19:51:06 john-ubuntu NetworkManager: <info>  (eth2): device state change: 5 -> 7 
Mar  4 19:51:06 john-ubuntu NetworkManager: <info>  Activation (eth2) Beginning DHCP transaction. 
Mar  4 19:51:06 john-ubuntu NetworkManager: <info>  dhclient started with pid 9995 
Mar  4 19:51:06 john-ubuntu NetworkManager: <info>  Activation (eth2) Stage 3 of 5 (IP Configure Start) complete. 
Mar  4 19:51:06 john-ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.1
Mar  4 19:51:06 john-ubuntu dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar  4 19:51:06 john-ubuntu dhclient: All rights reserved.
Mar  4 19:51:06 john-ubuntu dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Mar  4 19:51:06 john-ubuntu dhclient: 
Mar  4 19:51:06 john-ubuntu NetworkManager: <info>  DHCP: device eth2 state changed normal exit -> preinit 
Mar  4 19:51:06 john-ubuntu dhclient: Listening on LPF/eth2/[snip]
Mar  4 19:51:06 john-ubuntu dhclient: Sending on   LPF/eth2/[snip]
Mar  4 19:51:06 john-ubuntu dhclient: Sending on   Socket/fallback
Mar  4 19:51:06 john-ubuntu kernel: [ 2710.896021] eth2: no IPv6 routers present
Mar  4 19:51:07 john-ubuntu dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 8
Mar  4 19:51:15 john-ubuntu dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 10
Mar  4 19:51:25 john-ubuntu dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 15
Mar  4 19:51:40 john-ubuntu dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 15
Mar  4 19:51:51 john-ubuntu NetworkManager: <info>  Device 'eth2' DHCP transaction took too long (>45s), stopping it. 
Mar  4 19:51:51 john-ubuntu NetworkManager: <info>  eth2: canceled DHCP transaction, dhcp client pid 9995 
Mar  4 19:51:51 john-ubuntu NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Mar  4 19:51:51 john-ubuntu NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP Configure Timeout) started... 
Mar  4 19:51:51 john-ubuntu NetworkManager: <info>  (eth2): device state change: 7 -> 9 
Mar  4 19:51:51 john-ubuntu NetworkManager: <info>  Marking connection 'Auto eth2' invalid. 
Mar  4 19:51:51 john-ubuntu NetworkManager: <info>  Activation (eth2) failed. 
Mar  4 19:51:51 john-ubuntu NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP Configure Timeout) complete. 
Mar  4 19:51:51 john-ubuntu NetworkManager: <info>  (eth2): device state change: 9 -> 3 
Mar  4 19:51:51 john-ubuntu NetworkManager: <info>  (eth2): deactivating device (reason: 0). 


I'd really like to just try restarting the network manager but that never works. I try this command:
 sudo invoke-rc.d NetworkManager restart
It responds in the terminal window with this feedback:
 * Stopping NetworkManager...                                            
 * Starting NetworkManager... 

But in the daemon.log I have this entry:
Mar  4 21:13:20 john-ubuntu NetworkManager: <info>  starting... 
Mar  4 21:13:20 john-ubuntu NetworkManager: <WARN>  nm_dbus_manager_start_service(): Could not acquire the NetworkManager service as it is already taken. 
Mar  4 21:13:20 john-ubuntu NetworkManager: <info>  disconnected by the system bus. 
Mar  4 21:13:20 john-ubuntu NetworkManager: <WARN>  main(): Failed to start the dbus manager.

---

### Post by ben2talk on 2009-04-10
Bump - I gave up on sleep/hibernate a few months ago, and came back happy it's apparently working - but the Network manager is very dead and apparently only restarts on reboot (simply restarting the session isn't enough).

Wireless Networking died in it's sleep - I tried making an entry to tell it to kill networking before sleep - it still won't come back afterwards. This is an old problem I think - and there don't seem to be any solutions - please guys, if you can help out here - just ask for whatever you need and I'll let you have it.

[http://identi.ca/ben2talk/](http://identi.ca/ben2talk/)

---

### Post by michiedo on 2009-04-17
have you seen gib2800 suggestion in 
[http://ubuntuforums.org/showthread.php?t=779338&highlight=hibernate](http://ubuntuforums.org/showthread.php?t=779338&highlight=hibernate)

?

it worked for me.

good luck
:-)

---

