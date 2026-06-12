---
title: "CLI Bigpond Ultimate"
date: 2011-12-10
forum: Networking &amp; Wireless
---

### Post by Rexhunt on 2011-12-10
On my server rig I'm attempting to set up some form of sharing for our bigpond ultimate(sierra aircard 312u) mobile broadband as our netgear router doesn't want to talk to it...

The rig is headless without an x server or anything like that which means that I can't use network manager. When I put the modem in the computer it powers up but doesn't search for the network. The output of lsusb is:
```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1199:0fff Sierra Wireless, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

This makes it look to me like the modem is powered up on the usb. However after using pppconfig to setup a connection entering pon Bigpond gives (in the system log):
```
Dec 11 18:29:46 Rex-Server pppd[1252]: pppd 2.4.5 started by root, uid 0
Dec 11 18:29:47 Rex-Server chat[1255]: abort on (BUSY)
Dec 11 18:29:47 Rex-Server chat[1255]: abort on (NO CARRIER)
Dec 11 18:29:47 Rex-Server chat[1255]: abort on (VOICE)
Dec 11 18:29:47 Rex-Server chat[1255]: abort on (NO DIALTONE)
Dec 11 18:29:47 Rex-Server chat[1255]: abort on (NO DIAL TONE)
Dec 11 18:29:47 Rex-Server chat[1255]: abort on (NO ANSWER)
Dec 11 18:29:47 Rex-Server chat[1255]: abort on (DELAYED)
Dec 11 18:29:47 Rex-Server chat[1255]: send (ATZ^M)
Dec 11 18:29:47 Rex-Server chat[1255]: expect (OK)
Dec 11 18:29:48 Rex-Server chat[1255]: ATZ^M^M
Dec 11 18:29:48 Rex-Server chat[1255]: OK
Dec 11 18:29:48 Rex-Server chat[1255]:  -- got it
Dec 11 18:29:48 Rex-Server chat[1255]: send (ATDT*99#^M)
Dec 11 18:29:48 Rex-Server chat[1255]: expect (CONNECT)
Dec 11 18:29:48 Rex-Server chat[1255]: ^M
Dec 11 18:29:48 Rex-Server chat[1255]: ATDT*99#^M^M
Dec 11 18:29:48 Rex-Server chat[1255]: NO CARRIER
Dec 11 18:29:48 Rex-Server chat[1255]:  -- failed
Dec 11 18:29:48 Rex-Server chat[1255]: Failed (NO CARRIER)
Dec 11 18:29:48 Rex-Server pppd[1252]: Script /usr/sbin/chat -v -f /etc/chatscripts/Bigpond finished (pid 1254), status = 0x5
Dec 11 18:29:48 Rex-Server pppd[1252]: Connect script failed
Dec 11 18:29:49 Rex-Server pppd[1252]: Exit.

```

I know that the date/time are wrong... that is an issue that is going to be fixed soonish...

This is saying no carrier which to me means that it is talking to the modem and the modem is saying "That's all fine and good, but I can't talk to anyone else... so sorry about that..."

When I connect using network manager on my laptop the output of the system log is:
[HTML]Dec 10 19:23:13 rex-laptop kernel: [ 9699.071468] usb 1-1.2: new high speed USB device number 22 using ehci_hcd
Dec 10 19:23:13 rex-laptop kernel: [ 9699.182911] usb 1-1.2: config 1 has an invalid interface number: 9 but max is 0
Dec 10 19:23:13 rex-laptop kernel: [ 9699.182918] usb 1-1.2: config 1 has no interface number 0
Dec 10 19:23:13 rex-laptop kernel: [ 9699.188093] usb-storage: probe of 1-1.2:1.9 failed with error -5
Dec 10 19:23:16 rex-laptop kernel: [ 9701.630567] usb 1-1.2: USB disconnect, device number 22
Dec 10 19:23:16 rex-laptop kernel: [ 9701.986463] usb 1-1.2: new high speed USB device number 23 using ehci_hcd
Dec 10 19:23:16 rex-laptop kernel: [ 9702.098009] usb 1-1.2: config 1 has an invalid interface number: 7 but max is 4
Dec 10 19:23:16 rex-laptop kernel: [ 9702.098016] usb 1-1.2: config 1 has no interface number 2
Dec 10 19:23:16 rex-laptop kernel: [ 9702.101609] sierra 1-1.2:1.0: Sierra USB modem converter detected
Dec 10 19:23:16 rex-laptop kernel: [ 9702.103469] usb 1-1.2: APM supported, enabling autosuspend.
Dec 10 19:23:16 rex-laptop kernel: [ 9702.103605] usb 1-1.2: Sierra USB modem converter now attached to ttyUSB0
Dec 10 19:23:16 rex-laptop kernel: [ 9702.103749] sierra 1-1.2:1.1: Sierra USB modem converter detected
Dec 10 19:23:16 rex-laptop kernel: [ 9702.104591] usb 1-1.2: APM supported, enabling autosuspend.
Dec 10 19:23:16 rex-laptop kernel: [ 9702.104719] usb 1-1.2: Sierra USB modem converter now attached to ttyUSB1
Dec 10 19:23:16 rex-laptop kernel: [ 9702.104859] sierra 1-1.2:1.3: Sierra USB modem converter detected
Dec 10 19:23:16 rex-laptop kernel: [ 9702.105535] usb 1-1.2: APM supported, enabling autosuspend.
Dec 10 19:23:16 rex-laptop kernel: [ 9702.105645] usb 1-1.2: Sierra USB modem converter now attached to ttyUSB2
Dec 10 19:23:16 rex-laptop kernel: [ 9702.105794] sierra 1-1.2:1.4: Sierra USB modem converter detected
Dec 10 19:23:16 rex-laptop kernel: [ 9702.106657] usb 1-1.2: APM supported, enabling autosuspend.
Dec 10 19:23:16 rex-laptop kernel: [ 9702.106775] usb 1-1.2: Sierra USB modem converter now attached to ttyUSB3
Dec 10 19:23:16 rex-laptop kernel: [ 9702.108750] sierra_net 1-1.2:1.7: wwan0: register 'sierra_net' at usb-0000:00:1a.0-1.2, Sierra Wireless USB-to-WWAN Modem, 2a:a2:ef:dd:0a:07
Dec 10 19:23:16 rex-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.7/net/wwan0, iface: wwan0)
Dec 10 19:23:16 rex-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.7/net/wwan0, iface: wwan0): no ifupdown configuration found.
Dec 10 19:23:16 rex-laptop NetworkManager: <info>  (wwan0): carrier is OFF
Dec 10 19:23:16 rex-laptop NetworkManager: <info>  (wwan0): new Ethernet device (driver: 'sierra_net')
Dec 10 19:23:16 rex-laptop NetworkManager: <info>  (wwan0): exported as /org/freedesktop/NetworkManager/Devices/14
Dec 10 19:23:16 rex-laptop NetworkManager: <info>  (wwan0): now managed
Dec 10 19:23:16 rex-laptop NetworkManager: <info>  (wwan0): device state change: 1 -> 2 (reason 2)
Dec 10 19:23:16 rex-laptop NetworkManager: <info>  (wwan0): bringing up device.
Dec 10 19:23:16 rex-laptop NetworkManager: <info>  (wwan0): preparing device.
Dec 10 19:23:16 rex-laptop NetworkManager: <info>  (wwan0): deactivating device (reason: 2).
Dec 10 19:23:16 rex-laptop NetworkManager: Added default wired connection 'Auto wwan0' for /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.7/net/wwan0
Dec 10 19:23:16 rex-laptop kernel: [ 9702.146860] ADDRCONF(NETDEV_UP): wwan0: link is not ready
Dec 10 19:23:16 rex-laptop modem-manager: (ttyUSB1) opening serial device...
Dec 10 19:23:16 rex-laptop modem-manager: (ttyUSB1): probe requested by plugin 'Sierra'
Dec 10 19:23:16 rex-laptop modem-manager: (ttyUSB3) opening serial device...
Dec 10 19:23:16 rex-laptop modem-manager: (ttyUSB3): probe requested by plugin 'Sierra'
Dec 10 19:23:16 rex-laptop modem-manager: (ttyUSB2) opening serial device...
Dec 10 19:23:16 rex-laptop modem-manager: (ttyUSB2): probe requested by plugin 'Sierra'
Dec 10 19:23:16 rex-laptop modem-manager: (ttyUSB0) opening serial device...
Dec 10 19:23:16 rex-laptop modem-manager: (ttyUSB0): probe requested by plugin 'Sierra'
Dec 10 19:23:20 rex-laptop modem-manager: Got failure code 100: Unknown error
Dec 10 19:23:22 rex-laptop modem-manager: (ttyUSB2) closing serial device...
Dec 10 19:23:23 rex-laptop modem-manager: (Sierra): GSM modem /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2 claimed port ttyUSB2
Dec 10 19:23:23 rex-laptop modem-manager: Added modem /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2
Dec 10 19:23:23 rex-laptop modem-manager: Exported modem /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2 as /org/freedesktop/ModemManager/Modems/8
Dec 10 19:23:24 rex-laptop modem-manager: (ttyUSB3) closing serial device...
Dec 10 19:23:24 rex-laptop modem-manager: (Sierra): GSM modem /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2 claimed port ttyUSB3
Dec 10 19:23:24 rex-laptop NetworkManager: <info>  (ttyUSB2): new GSM device (driver: 'sierra')
Dec 10 19:23:24 rex-laptop NetworkManager: <info>  (ttyUSB2): exported as /org/freedesktop/NetworkManager/Devices/15
Dec 10 19:23:24 rex-laptop NetworkManager: <info>  (ttyUSB2): now managed
Dec 10 19:23:24 rex-laptop NetworkManager: <info>  (ttyUSB2): device state change: 1 -> 2 (reason 2)
Dec 10 19:23:24 rex-laptop NetworkManager: <info>  (ttyUSB2): deactivating device (reason: 2).
Dec 10 19:23:24 rex-laptop NetworkManager: <info>  (ttyUSB2): device state change: 2 -> 3 (reason 0)
Dec 10 19:23:27 rex-laptop NetworkManager: <info>  Activation (ttyUSB2) starting connection 'Telstra connection 1'
Dec 10 19:23:27 rex-laptop NetworkManager: <info>  (ttyUSB2): device state change: 3 -> 4 (reason 0)
Dec 10 19:23:27 rex-laptop NetworkManager: <info>  Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) scheduled...
Dec 10 19:23:27 rex-laptop NetworkManager: <info>  Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) started...
Dec 10 19:23:27 rex-laptop NetworkManager: <info>  Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) complete.
Dec 10 19:23:27 rex-laptop modem-manager: (ttyUSB2) opening serial device...
Dec 10 19:23:27 rex-laptop modem-manager: Modem /org/freedesktop/ModemManager/Modems/8: state changed (disabled -> enabling)
Dec 10 19:23:28 rex-laptop modem-manager: Modem /org/freedesktop/ModemManager/Modems/8: state changed (enabling -> enabled)
Dec 10 19:23:31 rex-laptop modem-manager: (ttyUSB1) closing serial device...
Dec 10 19:23:32 rex-laptop modem-manager: (ttyUSB0) closing serial device...
Dec 10 19:23:39 rex-laptop modem-manager: Registration state changed: 1
Dec 10 19:23:39 rex-laptop modem-manager: Modem /org/freedesktop/ModemManager/Modems/8: state changed (enabled -> registered)
Dec 10 19:23:39 rex-laptop modem-manager: Modem /org/freedesktop/ModemManager/Modems/8: state changed (registered -> connecting)
Dec 10 19:23:39 rex-laptop modem-manager: Modem /org/freedesktop/ModemManager/Modems/8: state changed (connecting -> connected)
Dec 10 19:23:39 rex-laptop NetworkManager: <info>  Activation (ttyUSB2) Stage 2 of 5 (Device Configure) scheduled...
Dec 10 19:23:39 rex-laptop NetworkManager: <info>  Activation (ttyUSB2) Stage 2 of 5 (Device Configure) starting...
Dec 10 19:23:39 rex-laptop NetworkManager: <info>  (ttyUSB2): device state change: 4 -> 5 (reason 0)
Dec 10 19:23:39 rex-laptop NetworkManager: <info>  Activation (ttyUSB2) Stage 2 of 5 (Device Configure) successful.
Dec 10 19:23:39 rex-laptop NetworkManager: <info>  Activation (ttyUSB2) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 10 19:23:39 rex-laptop NetworkManager: <info>  Activation (ttyUSB2) Stage 2 of 5 (Device Configure) complete.
Dec 10 19:23:39 rex-laptop NetworkManager: <info>  Activation (ttyUSB2) Stage 3 of 5 (IP Configure Start) started...
Dec 10 19:23:39 rex-laptop NetworkManager: <info>  (ttyUSB2): device state change: 5 -> 7 (reason 0)
Dec 10 19:23:39 rex-laptop NetworkManager: <info>  Starting pppd connection
Dec 10 19:23:39 rex-laptop NetworkManager: <debug> [1323505419.175817] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute user oregans2@bigpond.com ttyUSB2 noipdefault noauth usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/4 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so
Dec 10 19:23:39 rex-laptop NetworkManager: <debug> [1323505419.176965] nm_ppp_manager_start(): ppp started with pid 7754
Dec 10 19:23:39 rex-laptop NetworkManager: <info>  Activation (ttyUSB2) Stage 4 of 5 (IP6 Configure Get) scheduled...
Dec 10 19:23:39 rex-laptop NetworkManager: <info>  Activation (ttyUSB2) Stage 3 of 5 (IP Configure Start) complete.
Dec 10 19:23:39 rex-laptop NetworkManager: <info>  Activation (ttyUSB2) Stage 4 of 5 (IP6 Configure Get) started...
Dec 10 19:23:39 rex-laptop NetworkManager: <info>  Activation (ttyUSB2) Stage 4 of 5 (IP6 Configure Get) complete.
Dec 10 19:23:39 rex-laptop pppd[7754]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Dec 10 19:23:39 rex-laptop pppd[7754]: pppd 2.4.5 started by root, uid 0
Dec 10 19:23:39 rex-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Dec 10 19:23:39 rex-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Dec 10 19:23:39 rex-laptop pppd[7754]: Using interface ppp0
Dec 10 19:23:39 rex-laptop pppd[7754]: Connect: ppp0 <--> /dev/ttyUSB2
Dec 10 19:23:39 rex-laptop pppd[7754]: PAP authentication succeeded
Dec 10 19:23:48 rex-laptop pppd[7754]: Could not determine remote IP address: defaulting to 10.64.64.64
Dec 10 19:23:48 rex-laptop pppd[7754]: Cannot determine ethernet address for proxy ARP
Dec 10 19:23:48 rex-laptop pppd[7754]: local  IP address 124.183.143.98
Dec 10 19:23:48 rex-laptop pppd[7754]: remote IP address 10.64.64.64
Dec 10 19:23:48 rex-laptop pppd[7754]: primary   DNS address 61.9.195.193
Dec 10 19:23:48 rex-laptop pppd[7754]: secondary DNS address 61.9.134.49
Dec 10 19:23:48 rex-laptop NetworkManager: <info>  PPP manager(IP Config Get) reply received.
Dec 10 19:23:48 rex-laptop NetworkManager: <info>  Activation (ttyUSB2) Stage 4 of 5 (IP4 Configure Get) scheduled...
Dec 10 19:23:48 rex-laptop NetworkManager: <info>  Activation (ttyUSB2) Stage 4 of 5 (IP4 Configure Get) started...
Dec 10 19:23:48 rex-laptop NetworkManager: <info>  Activation (ttyUSB2) Stage 5 of 5 (IP Configure Commit) scheduled...
Dec 10 19:23:48 rex-laptop NetworkManager: <info>  Activation (ttyUSB2) Stage 4 of 5 (IP4 Configure Get) complete.
Dec 10 19:23:48 rex-laptop NetworkManager: <info>  Activation (ttyUSB2) Stage 5 of 5 (IP Configure Commit) started...
Dec 10 19:23:49 rex-laptop NetworkManager: <info>  (ppp0): writing resolv.conf to /sbin/resolvconf
Dec 10 19:23:49 rex-laptop NetworkManager: <info>  (ttyUSB2): device state change: 7 -> 8 (reason 0)
Dec 10 19:23:49 rex-laptop NetworkManager: <info>  (ppp0): writing resolv.conf to /sbin/resolvconf
Dec 10 19:23:49 rex-laptop NetworkManager: <info>  Policy set 'Telstra connection 1' (ppp0) as default for routing and DNS.
Dec 10 19:23:49 rex-laptop NetworkManager: <info>  Activation (ttyUSB2) successful, device activated.
Dec 10 19:23:49 rex-laptop NetworkManager: <info>  Activation (ttyUSB2) Stage 5 of 5 (IP Configure Commit) complete.
Dec 10 19:23:55 rex-laptop ntpdate[7876]: adjust time server 91.189.94.4 offset 0.033567 sec
[/HTML]

This looks like modem manager needs to enable the modem before the modem will search for a network, also the modem performs exactly the same as in the server rig until I manually tell network manager to connect(stopped it autoconnecting to allow some tests)

I know there is a lot of output there and I'm not a fan of people making this sort of post but I can't think of what else to do to allow me to share our internet.

---

### Post by Rexhunt on 2011-12-11
I think that if I can work out a way to send the command to modem manager manually or using a script or something then I can adapt that to work in my system

---

### Post by Rexhunt on 2011-12-22
bump

---

### Post by Mark F on 2012-01-22
Hi Rex. Been battling with a Sierra 312U myself. I have managed to get it to connect to the internet using wvdial. The successful wvdial.conf file reads:
```
[Dialer telstra]
Stupid Mode = on
Init = AT+CGDCONT=1,"IP","telstra.bigpond"
New PPPD = yes
Modem = /dev/ttyUSB2
Password = <password>
Username = <username)@bigpond.com
Phone = *99#

```

Hope this helps in some way
M

---

### Post by Rexhunt on 2012-01-22
Cool, thanks for that, it worked perfectly the first time...

Now to setup the proxy server on there...:evil:

---

