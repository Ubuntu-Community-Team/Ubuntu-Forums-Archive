---
title: "Networking &amp; Sleep/Hibernate Modes"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by wacky.banana on 2009-10-31
Hello,

I have searched before I posted but can't find what I am looking for.

Problem I have is that if I put Ubuntu 9.10 desktop into either sleep or hibernate modes then, on resume, the network connection does not come back up. The only way out is to reboot the machine.

Now I had this problem with 9.04 and spent weeks searching these forums for a solution. Nothing I tried worked, including altering/amending various config files.

I was really hoping that a permanent solution would have been found for this iteration of Ubuntu. Has anyone cracked this problem yet/come up with a failsafe solution?

Thanks in advance for any help or guidance offered.

WB

---

### Post by mpokrywka on 2009-11-01
Important question:
Have you installed 9.10 from scratch or you upgraded 9.04 with "altered/amended various config files"?

---

### Post by wacky.banana on 2009-11-01
Installed from scratch. I have enough experience of OS installation to know that one should NEVER do an upgrade. Clean install is always the way to go.

Now you have this information can you help?

Thanks

WB

---

### Post by mpokrywka on 2009-11-01
I wanted to know if there are any differences from default configuration.

Now, try to suspend, and after resume run from terminal:
```
grep -A9999 'Waking up' < /var/log/daemon.log | tee wakeup.txt
```

This will show what happens with network manager after waking form suspend.
Log will also be saved to 'wakeup.txt'

Paste output here or attach wakeup.txt if it is too long to copy.

---

### Post by wacky.banana on 2009-11-02
Hi again,

Please see attached output file as requested below (could not upload it as a text file). Look forward to your comments.

Thanks

WB

_**File Output**_:

~$ grep -A9999 'Waking up' < /var/log/daemon.log | tee wakeup.txt
Nov  2 17:22:16 ko1-desktop NetworkManager: <info>  Waking up...
Nov  2 17:22:16 ko1-desktop NetworkManager: <info>  (eth0): now managed
Nov  2 17:22:16 ko1-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Nov  2 17:22:16 ko1-desktop NetworkManager: <info>  (eth0): bringing up device.
Nov  2 17:22:16 ko1-desktop NetworkManager: <info>  (eth0): preparing device.
Nov  2 17:22:16 ko1-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Nov  2 17:22:16 ko1-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Nov  2 17:22:16 ko1-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Nov  2 17:22:16 ko1-desktop NetworkManager: <info>  (eth1): now managed
Nov  2 17:22:16 ko1-desktop NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
Nov  2 17:22:16 ko1-desktop NetworkManager: <info>  (eth1): bringing up device.
Nov  2 17:22:16 ko1-desktop NetworkManager: <info>  (eth1): preparing device.
Nov  2 17:22:16 ko1-desktop NetworkManager: <info>  (eth1): deactivating device (reason: 2).
Nov  2 17:22:16 ko1-desktop NetworkManager: <info>  (eth1): carrier now ON (device state 2)
Nov  2 17:22:16 ko1-desktop NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 40)

---

### Post by mpokrywka on 2009-11-02
Hmm, log is very short. Network manager ignores eth0 device (probably manually configured in /etc/network/interfaces), and log does not tell why eth1 does not start configuration.

Try waiting a bit longer (I don't know, 2 minutes?) after resuming, and then get again this log, and maybe also report of:
```
nm-tool
```

---

### Post by wacky.banana on 2009-11-03
I will get on it and get back to you as soon as I have fixed another problem which is my grub2 boot loader is broken (I have a separate thread out on this). I will pm you when I have the new output file.

Again thanks for your help so far; very much appreciate it.

All the best.

WB

---

### Post by wacky.banana on 2009-11-04
Now have a bigger file for you to look at. 

Sorry but even with the file split in 2, the forum website won't let me upload them so I have had to list the file here.

Thanks

WB

_**File Output:**_
/var/log/daemon.log-Nov  4 23:05:58 KO1 dhclient: Listening on LPF/eth0/00:13:8f:db:33:1d
/var/log/daemon.log-Nov  4 23:05:58 KO1 dhclient: Sending on   LPF/eth0/00:13:8f:db:33:1d
/var/log/daemon.log-Nov  4 23:05:58 KO1 dhclient: Sending on   Socket/fallback
/var/log/daemon.log-Nov  4 23:05:59 KO1 avahi-daemon[921]: Registering new address record for fe80::213:8fff:fedb:331d on eth0.*.
/var/log/daemon.log-Nov  4 23:06:02 KO1 dhclient: DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
/var/log/daemon.log-Nov  4 23:06:02 KO1 dhclient: DHCPACK of 192.168.2.2 from 192.168.2.1
/var/log/daemon.log-Nov  4 23:06:02 KO1 dhclient: bound to 192.168.2.2 -- renewal in 41148 seconds.
/var/log/daemon.log-Nov  4 23:06:02 KO1 NetworkManager: <info>  DHCP: device eth0 state changed preinit -> reboot
/var/log/daemon.log-Nov  4 23:06:02 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
/var/log/daemon.log-Nov  4 23:06:02 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
/var/log/daemon.log-Nov  4 23:06:02 KO1 NetworkManager: <info>    address 192.168.2.2
/var/log/daemon.log-Nov  4 23:06:02 KO1 NetworkManager: <info>    prefix 24 (255.255.255.0)
/var/log/daemon.log-Nov  4 23:06:02 KO1 NetworkManager: <info>    gateway 192.168.2.1
/var/log/daemon.log-Nov  4 23:06:02 KO1 NetworkManager: <info>    nameserver '192.168.2.1'
/var/log/daemon.log-Nov  4 23:06:02 KO1 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
/var/log/daemon.log-Nov  4 23:06:02 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
/var/log/daemon.log-Nov  4 23:06:02 KO1 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
/var/log/daemon.log-Nov  4 23:06:02 KO1 avahi-daemon[921]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
/var/log/daemon.log-Nov  4 23:06:02 KO1 avahi-daemon[921]: New relevant interface eth0.IPv4 for mDNS.
/var/log/daemon.log-Nov  4 23:06:02 KO1 avahi-daemon[921]: Registering new address record for 192.168.2.2 on eth0.IPv4.
/var/log/daemon.log-Nov  4 23:06:03 KO1 NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
/var/log/daemon.log-Nov  4 23:06:03 KO1 NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
/var/log/daemon.log-Nov  4 23:06:03 KO1 NetworkManager: <info>  Activation (eth0) successful, device activated.
/var/log/daemon.log-Nov  4 23:06:03 KO1 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
/var/log/daemon.log-Nov  4 23:06:05 KO1 ntpdate[3718]: step time server 91.189.94.4 offset 1.485555 sec
/var/log/daemon.log-Nov  4 23:08:21 KO1 avahi-daemon[1110]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
/var/log/daemon.log-Nov  4 23:08:21 KO1 avahi-daemon[1110]: Successfully dropped root privileges.
/var/log/daemon.log-Nov  4 23:08:21 KO1 avahi-daemon[1110]: avahi-daemon 0.6.25 starting up.
/var/log/daemon.log-Nov  4 23:08:21 KO1 avahi-daemon[1110]: Successfully called chroot().
/var/log/daemon.log-Nov  4 23:08:21 KO1 avahi-daemon[1110]: Successfully dropped remaining capabilities.
/var/log/daemon.log-Nov  4 23:08:21 KO1 avahi-daemon[1110]: No service file found in /etc/avahi/services.
/var/log/daemon.log-Nov  4 23:08:21 KO1 avahi-daemon[1110]: Network interface enumeration completed.
/var/log/daemon.log-Nov  4 23:08:21 KO1 avahi-daemon[1110]: Registering HINFO record with values 'I686'/'LINUX'.
/var/log/daemon.log-Nov  4 23:08:21 KO1 avahi-daemon[1110]: Server startup complete. Host name is KO1.local. Local service cookie is 2404406176.
/var/log/daemon.log-Nov  4 23:08:22 KO1 NetworkManager: <info>  starting...
/var/log/daemon.log-Nov  4 23:08:22 KO1 NetworkManager: <info>  Trying to start the modem-manager...
/var/log/daemon.log-Nov  4 23:08:22 KO1 NetworkManager:    SCPlugin-Ifupdown: init!
/var/log/daemon.log-Nov  4 23:08:22 KO1 NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
/var/log/daemon.log-Nov  4 23:08:22 KO1 NetworkManager:    SCPluginIfupdown: management mode: unmanaged
/var/log/daemon.log-Nov  4 23:08:22 KO1 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0b.0/net/eth1, iface: eth1)
/var/log/daemon.log-Nov  4 23:08:22 KO1 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0b.0/net/eth1, iface: eth1): no ifupdown configuration found.
/var/log/daemon.log-Nov  4 23:08:22 KO1 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/net/eth0, iface: eth0)
/var/log/daemon.log-Nov  4 23:08:22 KO1 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/net/eth0, iface: eth0): no ifupdown configuration found.
/var/log/daemon.log-Nov  4 23:08:22 KO1 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
/var/log/daemon.log-Nov  4 23:08:22 KO1 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
/var/log/daemon.log-Nov  4 23:08:22 KO1 NetworkManager:    SCPlugin-Ifupdown: end _init.
/var/log/daemon.log-Nov  4 23:08:22 KO1 NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
/var/log/daemon.log-Nov  4 23:08:22 KO1 NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
/var/log/daemon.log-Nov  4 23:08:22 KO1 modem-manager: Loaded plugin Option
/var/log/daemon.log-Nov  4 23:08:22 KO1 modem-manager: Loaded plugin Ericsson MBM
/var/log/daemon.log-Nov  4 23:08:22 KO1 modem-manager: Loaded plugin Gobi
/var/log/daemon.log-Nov  4 23:08:22 KO1 modem-manager: Loaded plugin MotoC
/var/log/daemon.log-Nov  4 23:08:22 KO1 modem-manager: Loaded plugin Nokia
/var/log/daemon.log-Nov  4 23:08:22 KO1 modem-manager: Loaded plugin ZTE
/var/log/daemon.log-Nov  4 23:08:22 KO1 modem-manager: Loaded plugin Option High-Speed
/var/log/daemon.log-Nov  4 23:08:22 KO1 modem-manager: Loaded plugin Novatel
/var/log/daemon.log-Nov  4 23:08:22 KO1 modem-manager: Loaded plugin Generic
/var/log/daemon.log-Nov  4 23:08:22 KO1 modem-manager: Loaded plugin Huawei
/var/log/daemon.log-Nov  4 23:08:22 KO1 modem-manager: Loaded plugin Sierra
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  Wireless now enabled by radio killswitch
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager:    SCPlugin-Ifupdown: (152042224) ... get_connections.
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager:    SCPlugin-Ifupdown: (152042224) ... get_connections (managed=false): return empty list.
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager:    Ifupdown: get unmanaged devices count: 0
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  (eth1): carrier is OFF
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  (eth1): new Ethernet device (driver: 'tulip')
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  (eth1): now managed
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  (eth1): bringing up device.
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  (eth1): preparing device.
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  (eth1): deactivating device (reason: 2).
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: Added default wired connection 'Auto eth1' for /sys/devices/pci0000:00/0000:00:0b.0/net/eth1
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  (eth0): carrier is OFF
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  (eth0): new Ethernet device (driver: 'via-rhine')
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  (eth0): now managed
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  (eth0): bringing up device.
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  (eth0): preparing device.
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  (eth0): deactivating device (reason: 2).
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:12.0/net/eth0
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  (eth1): carrier now ON (device state 2)
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 40)
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  (eth0): carrier now ON (device state 2)
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  modem-manager is now available
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  Trying to start the supplicant...
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  Activation (eth1) starting connection 'Auto eth1'
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
/var/log/daemon.log-Nov  4 23:08:23 KO1 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful.
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  (eth1): device state change: 5 -> 7 (reason 0)
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction (timeout in 45 seconds)
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  dhclient started with pid 1374
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) scheduled...
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  dhclient started with pid 1384
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
/var/log/daemon.log-Nov  4 23:08:24 KO1 dhclient: Internet Systems Consortium DHCP Client V3.1.2
/var/log/daemon.log-Nov  4 23:08:24 KO1 dhclient: Copyright 2004-2008 Internet Systems Consortium.
/var/log/daemon.log-Nov  4 23:08:24 KO1 dhclient: All rights reserved.
/var/log/daemon.log-Nov  4 23:08:24 KO1 dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
/var/log/daemon.log-Nov  4 23:08:24 KO1 dhclient: 
/var/log/daemon.log-Nov  4 23:08:24 KO1 dhclient: Internet Systems Consortium DHCP Client V3.1.2
/var/log/daemon.log-Nov  4 23:08:24 KO1 dhclient: Copyright 2004-2008 Internet Systems Consortium.
/var/log/daemon.log-Nov  4 23:08:24 KO1 dhclient: All rights reserved.
/var/log/daemon.log-Nov  4 23:08:24 KO1 dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
/var/log/daemon.log-Nov  4 23:08:24 KO1 dhclient: 
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) started...
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) complete.
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
/var/log/daemon.log-Nov  4 23:08:24 KO1 NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
/var/log/daemon.log-Nov  4 23:08:24 KO1 acpid: client connected from 1408[107:114]
/var/log/daemon.log-Nov  4 23:08:24 KO1 dhclient: Listening on LPF/eth0/00:13:8f:db:33:1d
/var/log/daemon.log-Nov  4 23:08:24 KO1 dhclient: Listening on LPF/eth1/00:04:5a:7d:5a:e2
/var/log/daemon.log-Nov  4 23:08:24 KO1 dhclient: Sending on   LPF/eth1/00:04:5a:7d:5a:e2
/var/log/daemon.log-Nov  4 23:08:24 KO1 dhclient: Sending on   LPF/eth0/00:13:8f:db:33:1d
/var/log/daemon.log-Nov  4 23:08:24 KO1 dhclient: Sending on   Socket/fallback
/var/log/daemon.log-Nov  4 23:08:24 KO1 dhclient: Sending on   Socket/fallback
/var/log/daemon.log-Nov  4 23:08:25 KO1 avahi-daemon[1110]: Registering new address record for fe80::213:8fff:fedb:331d on eth0.*.
/var/log/daemon.log-Nov  4 23:08:25 KO1 avahi-daemon[1110]: Registering new address record for fe80::204:5aff:fe7d:5ae2 on eth1.*.
/var/log/daemon.log-Nov  4 23:08:25 KO1 gdm-binary[1443]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
/var/log/daemon.log-Nov  4 23:08:25 KO1 gdm-binary[1443]: WARNING: Unable to find users: no seat-id found
/var/log/daemon.log-Nov  4 23:08:25 KO1 gdm-simple-slave[1558]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
/var/log/daemon.log-Nov  4 23:08:26 KO1 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
/var/log/daemon.log-Nov  4 23:08:26 KO1 NetworkManager: <info>  (eth1): carrier now OFF (device state 7, deferring action for 4 seconds)
/var/log/daemon.log-Nov  4 23:08:26 KO1 acpid: client connected from 1578[0:0]
/var/log/daemon.log-Nov  4 23:08:27 KO1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
/var/log/daemon.log-Nov  4 23:08:27 KO1 dhclient: DHCPOFFER of 192.168.2.2 from 192.168.2.1
/var/log/daemon.log-Nov  4 23:08:27 KO1 dhclient: DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
/var/log/daemon.log-Nov  4 23:08:27 KO1 dhclient: DHCPACK of 192.168.2.2 from 192.168.2.1
/var/log/daemon.log-Nov  4 23:08:27 KO1 dhclient: bound to 192.168.2.2 -- renewal in 35083 seconds.
/var/log/daemon.log-Nov  4 23:08:27 KO1 NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
/var/log/daemon.log-Nov  4 23:08:27 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
/var/log/daemon.log-Nov  4 23:08:27 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
/var/log/daemon.log-Nov  4 23:08:27 KO1 NetworkManager: <info>    address 192.168.2.2
/var/log/daemon.log-Nov  4 23:08:27 KO1 NetworkManager: <info>    prefix 24 (255.255.255.0)
/var/log/daemon.log-Nov  4 23:08:27 KO1 NetworkManager: <info>    gateway 192.168.2.1
/var/log/daemon.log-Nov  4 23:08:27 KO1 NetworkManager: <info>    nameserver '192.168.2.1'
/var/log/daemon.log-Nov  4 23:08:27 KO1 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
/var/log/daemon.log-Nov  4 23:08:27 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
/var/log/daemon.log-Nov  4 23:08:27 KO1 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
/var/log/daemon.log-Nov  4 23:08:27 KO1 avahi-daemon[1110]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
/var/log/daemon.log-Nov  4 23:08:27 KO1 avahi-daemon[1110]: New relevant interface eth0.IPv4 for mDNS.
/var/log/daemon.log-Nov  4 23:08:27 KO1 avahi-daemon[1110]: Registering new address record for 192.168.2.2 on eth0.IPv4.
/var/log/daemon.log-Nov  4 23:08:28 KO1 NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
/var/log/daemon.log-Nov  4 23:08:28 KO1 NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
/var/log/daemon.log-Nov  4 23:08:28 KO1 NetworkManager: <info>  Activation (eth0) successful, device activated.
/var/log/daemon.log-Nov  4 23:08:28 KO1 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
/var/log/daemon.log-Nov  4 23:08:28 KO1 acpid: client connected from 1578[0:0]
/var/log/daemon.log-Nov  4 23:08:29 KO1 ntpdate[1710]: adjust time server 91.189.94.4 offset -0.400605 sec
/var/log/daemon.log-Nov  4 23:08:29 KO1 console-kit-daemon[1163]: WARNING: Couldn't read /proc/1129/environ: Failed to open file '/proc/1129/environ': No such file or directory
/var/log/daemon.log-Nov  4 23:08:31 KO1 NetworkManager: <info>  (eth1): device state change: 7 -> 2 (reason 40)
/var/log/daemon.log-Nov  4 23:08:31 KO1 NetworkManager: <info>  (eth1): deactivating device (reason: 40).
/var/log/daemon.log-Nov  4 23:08:31 KO1 NetworkManager: <info>  (eth1): canceled DHCP transaction, dhcp client pid 1374
/var/log/daemon.log-Nov  4 23:08:31 KO1 NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
/var/log/daemon.log-Nov  4 23:08:45 KO1 gdm-session-worker[1810]: pam_sm_authenticate: Called
/var/log/daemon.log-Nov  4 23:08:45 KO1 gdm-session-worker[1810]: pam_sm_authenticate: username = [wackyb]
/var/log/daemon.log-Nov  4 23:09:54 KO1 NetworkManager: <info>  Sleeping...
/var/log/daemon.log-Nov  4 23:09:54 KO1 NetworkManager: <info>  (eth1): now unmanaged
/var/log/daemon.log-Nov  4 23:09:54 KO1 NetworkManager: <info>  (eth1): device state change: 2 -> 1 (reason 37)
/var/log/daemon.log-Nov  4 23:09:54 KO1 NetworkManager: <info>  (eth1): cleaning up...
/var/log/daemon.log-Nov  4 23:09:54 KO1 NetworkManager: <info>  (eth1): taking down device.
/var/log/daemon.log-Nov  4 23:09:54 KO1 avahi-daemon[1110]: Withdrawing address record for fe80::204:5aff:fe7d:5ae2 on eth1.
/var/log/daemon.log-Nov  4 23:09:54 KO1 NetworkManager: <info>  (eth0): now unmanaged
/var/log/daemon.log-Nov  4 23:09:54 KO1 NetworkManager: <info>  (eth0): device state change: 8 -> 1 (reason 37)
/var/log/daemon.log-Nov  4 23:09:54 KO1 NetworkManager: <info>  (eth0): deactivating device (reason: 37).
/var/log/daemon.log-Nov  4 23:09:54 KO1 NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 1384
/var/log/daemon.log-Nov  4 23:09:54 KO1 NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess#012
/var/log/daemon.log-Nov  4 23:09:54 KO1 avahi-daemon[1110]: Withdrawing address record for 192.168.2.2 on eth0.
/var/log/daemon.log-Nov  4 23:09:54 KO1 avahi-daemon[1110]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
/var/log/daemon.log-Nov  4 23:09:54 KO1 avahi-daemon[1110]: Interface eth0.IPv4 no longer relevant for mDNS.
/var/log/daemon.log-Nov  4 23:09:54 KO1 NetworkManager: <info>  (eth0): cleaning up...
/var/log/daemon.log-Nov  4 23:09:54 KO1 NetworkManager: <info>  (eth0): taking down device.
/var/log/daemon.log-Nov  4 23:09:54 KO1 avahi-daemon[1110]: Withdrawing address record for fe80::213:8fff:fedb:331d on eth0.
/var/log/daemon.log-Nov  4 23:09:54 KO1 NetworkManager: <info>  (eth0): carrier now OFF (device state 1)
/var/log/daemon.log-Nov  4 23:10:23 KO1 acpid: client 1578[0:0] has disconnected
/var/log/daemon.log-Nov  4 23:10:23 KO1 acpid: client 1578[0:0] has disconnected
/var/log/daemon.log-Nov  4 23:10:23 KO1 acpid: client connected from 1578[0:0]
/var/log/daemon.log-Nov  4 23:10:24 KO1 acpid: client connected from 1578[0:0]
/var/log/daemon.log:Nov  4 23:10:24 KO1 NetworkManager: <info>  Waking up...
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  (eth1): now managed
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  (eth1): bringing up device.
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  (eth1): preparing device.
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  (eth1): deactivating device (reason: 2).
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  (eth0): now managed
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  (eth0): bringing up device.
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  (eth0): preparing device.
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  (eth0): deactivating device (reason: 2).
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  (eth0): carrier now ON (device state 2)
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
/var/log/daemon.log-Nov  4 23:10:24 KO1 dhclient: Internet Systems Consortium DHCP Client V3.1.2
/var/log/daemon.log-Nov  4 23:10:24 KO1 dhclient: Copyright 2004-2008 Internet Systems Consortium.
/var/log/daemon.log-Nov  4 23:10:24 KO1 dhclient: All rights reserved.
/var/log/daemon.log-Nov  4 23:10:24 KO1 dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
/var/log/daemon.log-Nov  4 23:10:24 KO1 dhclient: 
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  dhclient started with pid 2428
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
/var/log/daemon.log-Nov  4 23:10:24 KO1 NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
/var/log/daemon.log-Nov  4 23:10:24 KO1 dhclient: Listening on LPF/eth0/00:13:8f:db:33:1d
/var/log/daemon.log-Nov  4 23:10:24 KO1 dhclient: Sending on   LPF/eth0/00:13:8f:db:33:1d
/var/log/daemon.log-Nov  4 23:10:24 KO1 dhclient: Sending on   Socket/fallback
/var/log/daemon.log-Nov  4 23:10:25 KO1 avahi-daemon[1110]: Registering new address record for fe80::213:8fff:fedb:331d on eth0.*.
/var/log/daemon.log-Nov  4 23:10:27 KO1 dhclient: DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
/var/log/daemon.log-Nov  4 23:10:30 KO1 dhclient: DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
/var/log/daemon.log-Nov  4 23:10:33 KO1 dhclient: DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
/var/log/daemon.log-Nov  4 23:10:40 KO1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
/var/log/daemon.log-Nov  4 23:10:45 KO1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
/var/log/daemon.log-Nov  4 23:10:51 KO1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
/var/log/daemon.log-Nov  4 23:11:06 KO1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
/var/log/daemon.log-Nov  4 23:11:09 KO1 NetworkManager: <info>  (eth0): DHCP transaction took too long, stopping it.
/var/log/daemon.log-Nov  4 23:11:10 KO1 NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 2428
/var/log/daemon.log-Nov  4 23:11:10 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
/var/log/daemon.log-Nov  4 23:11:10 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
/var/log/daemon.log-Nov  4 23:11:10 KO1 NetworkManager: <info>  (eth0): device state change: 7 -> 9 (reason 5)
/var/log/daemon.log-Nov  4 23:11:10 KO1 NetworkManager: <info>  Marking connection 'Auto eth0' invalid.
/var/log/daemon.log-Nov  4 23:11:10 KO1 NetworkManager: <info>  Activation (eth0) failed.
/var/log/daemon.log-Nov  4 23:11:10 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
/var/log/daemon.log-Nov  4 23:11:10 KO1 NetworkManager: <info>  (eth0): device state change: 9 -> 3 (reason 0)
/var/log/daemon.log-Nov  4 23:11:10 KO1 NetworkManager: <info>  (eth0): deactivating device (reason: 0).
xxxxxx@KO1:~$

---

### Post by mpokrywka on 2009-11-04
From your log it looks that after resume your network card does not work (does not seem to receive packets).
Earlier in log there is information about network driver (NetworkManager: <info> (eth0): new Ethernet device (driver: 'via-rhine'))

Quick look at driver parameters:
modinfo via-rhine
...
parm:           avoid_D3:Avoid power state D3 (work-around for broken BIOSes) (bool)
...

This parameter may fix your problem. (google found me for example [http://linux.derkeiler.com/Mailing-Lists/Fedora/2007-02/msg01577.html](http://linux.derkeiler.com/Mailing-Lists/Fedora/2007-02/msg01577.html) )

You need to edit /etc/modprobe.d/options (sudo gedit /etc/modprobe.d/options) and add following line:
```
options via-rhine avoid_D3=1
```

To be sure also regenerate initramfs (sometimes network drivers are included):
```
sudo update-initramfs -k all
```

Reboot, and try if now suspend works...

---

### Post by wacky.banana on 2009-11-05
MPokrywka,

Have updated the file ...../modprobe.d/options and added the line you suggested. The original file was empty; is that how it should have been in the first place?

Tried sudo update-initramfs -k all
and got this error message:

You must specify at least one of -c, -u, or -d.

Usage: /usr/sbin/update-initramfs [OPTION]...

Options:
 -k [version]    Specify kernel version or 'all'
 -c        Create a new initramfs
 -u        Update an existing initramfs
 -d        Remove an existing initramfs
 -t        Take over a custom initramfs with this one
 -b        Set alternate boot directory
 -v        Be verbose
 -h        This message

Not sure what's wrong with the command as it looks ok to me. Any ideas please?

Thanks

WB

---

### Post by mpokrywka on 2009-11-05
> **wacky.banana said:**
> MPokrywka,

Have updated the file ...../modprobe.d/options and added the line you suggested. The original file was empty; is that how it should have been in the first place?


Yes, file could have been empty - this means no ubuntu specific kernel hacks were present, no problem. Simply add mentioned kernel module option.

> **wacky.banana said:**
> 
Tried sudo update-initramfs -k all
and got this error message:
...



Sorry for this, I made mistake, should be:
**sudo update-initramfs -u -k all**

After regenerating initramfs reboot and try to suspend/resume.

---

### Post by wacky.banana on 2009-11-05
Mpokrywka,

Completed the items as outlined above, rechecked the modprobe file, rebooted the machine and it still does not work. New file output is as below.

What's your view please.

Thanks

WB

_**File Output:**_
terval 5
Nov  5 13:50:48 KO1 NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Nov  5 13:50:48 KO1 dhclient: Listening on LPF/eth0/00:13:8f:db:33:1d
Nov  5 13:50:48 KO1 dhclient: Sending on   LPF/eth0/00:13:8f:db:33:1d
Nov  5 13:50:48 KO1 dhclient: Sending on   Socket/fallback
Nov  5 13:50:49 KO1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Nov  5 13:50:49 KO1 dhclient: DHCPOFFER of 192.168.2.2 from 192.168.2.1
Nov  5 13:50:49 KO1 dhclient: DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
Nov  5 13:50:49 KO1 dhclient: DHCPACK of 192.168.2.2 from 192.168.2.1
Nov  5 13:50:49 KO1 dhclient: bound to 192.168.2.2 -- renewal in 38055 seconds.
Nov  5 13:50:49 KO1 NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Nov  5 13:50:49 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Nov  5 13:50:49 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Nov  5 13:50:49 KO1 NetworkManager: <info>    address 192.168.2.2
Nov  5 13:50:49 KO1 NetworkManager: <info>    prefix 24 (255.255.255.0)
Nov  5 13:50:49 KO1 NetworkManager: <info>    gateway 192.168.2.1
Nov  5 13:50:49 KO1 NetworkManager: <info>    nameserver '192.168.2.1'
Nov  5 13:50:49 KO1 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Nov  5 13:50:49 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Nov  5 13:50:49 KO1 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Nov  5 13:50:49 KO1 avahi-daemon[836]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Nov  5 13:50:49 KO1 avahi-daemon[836]: New relevant interface eth0.IPv4 for mDNS.
Nov  5 13:50:49 KO1 avahi-daemon[836]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Nov  5 13:50:49 KO1 init: apport pre-start process (1111) terminated with status 1
Nov  5 13:50:49 KO1 init: apport post-stop process (1127) terminated with status 1
Nov  5 13:50:50 KO1 acpid: client connected from 1215[107:114]
Nov  5 13:50:50 KO1 NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Nov  5 13:50:50 KO1 NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Nov  5 13:50:50 KO1 NetworkManager: <info>  Activation (eth0) successful, device activated.
Nov  5 13:50:50 KO1 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Nov  5 13:50:50 KO1 NetworkManager: <info>  (eth1): carrier now OFF (device state 7, deferring action for 4 seconds)
Nov  5 13:50:52 KO1 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Nov  5 13:50:52 KO1 gdm-binary[1336]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Nov  5 13:50:52 KO1 gdm-binary[1336]: WARNING: Unable to find users: no seat-id found
Nov  5 13:50:52 KO1 gdm-simple-slave[1425]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Nov  5 13:50:54 KO1 ntpdate[1585]: adjust time server 91.189.94.4 offset -0.486344 sec
Nov  5 13:50:54 KO1 acpid: client connected from 1426[0:0]
Nov  5 13:50:55 KO1 NetworkManager: <info>  (eth1): device state change: 7 -> 2 (reason 40)
Nov  5 13:50:55 KO1 NetworkManager: <info>  (eth1): deactivating device (reason: 40).
Nov  5 13:50:55 KO1 NetworkManager: <info>  (eth1): canceled DHCP transaction, dhcp client pid 923
Nov  5 13:50:55 KO1 NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Nov  5 13:50:55 KO1 acpid: client connected from 1426[0:0]
Nov  5 13:50:57 KO1 console-kit-daemon[841]: WARNING: Couldn't read /proc/834/environ: Failed to open file '/proc/834/environ': No such file or directory
Nov  5 13:52:20 KO1 gdm-session-worker[1804]: pam_sm_authenticate: Called
Nov  5 13:52:20 KO1 gdm-session-worker[1804]: pam_sm_authenticate: username = [wackyb]
Nov  5 14:30:33 KO1 avahi-daemon[1203]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Nov  5 14:30:33 KO1 avahi-daemon[1203]: Successfully dropped root privileges.
Nov  5 14:30:33 KO1 avahi-daemon[1203]: avahi-daemon 0.6.25 starting up.
Nov  5 14:30:33 KO1 avahi-daemon[1203]: Successfully called chroot().
Nov  5 14:30:33 KO1 avahi-daemon[1203]: Successfully dropped remaining capabilities.
Nov  5 14:30:33 KO1 avahi-daemon[1203]: No service file found in /etc/avahi/services.
Nov  5 14:30:33 KO1 avahi-daemon[1203]: Network interface enumeration completed.
Nov  5 14:30:33 KO1 avahi-daemon[1203]: Registering HINFO record with values 'I686'/'LINUX'.
Nov  5 14:30:33 KO1 avahi-daemon[1203]: Server startup complete. Host name is KO1.local. Local service cookie is 3594210154.
Nov  5 14:30:33 KO1 NetworkManager: <info>  starting...
Nov  5 14:30:33 KO1 NetworkManager: <info>  Trying to start the modem-manager...
Nov  5 14:30:33 KO1 modem-manager: Loaded plugin Option
Nov  5 14:30:33 KO1 modem-manager: Loaded plugin Ericsson MBM
Nov  5 14:30:33 KO1 modem-manager: Loaded plugin Gobi
Nov  5 14:30:33 KO1 modem-manager: Loaded plugin MotoC
Nov  5 14:30:33 KO1 modem-manager: Loaded plugin Nokia
Nov  5 14:30:33 KO1 modem-manager: Loaded plugin ZTE
Nov  5 14:30:33 KO1 modem-manager: Loaded plugin Option High-Speed
Nov  5 14:30:33 KO1 modem-manager: Loaded plugin Novatel
Nov  5 14:30:33 KO1 modem-manager: Loaded plugin Generic
Nov  5 14:30:33 KO1 modem-manager: Loaded plugin Huawei
Nov  5 14:30:33 KO1 modem-manager: Loaded plugin Sierra
Nov  5 14:30:34 KO1 NetworkManager:    SCPlugin-Ifupdown: init!
Nov  5 14:30:34 KO1 NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Nov  5 14:30:34 KO1 NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Nov  5 14:30:34 KO1 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0b.0/net/eth1, iface: eth1)
Nov  5 14:30:34 KO1 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0b.0/net/eth1, iface: eth1): no ifupdown configuration found.
Nov  5 14:30:34 KO1 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/net/eth0, iface: eth0)
Nov  5 14:30:34 KO1 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/net/eth0, iface: eth0): no ifupdown configuration found.
Nov  5 14:30:34 KO1 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Nov  5 14:30:34 KO1 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Nov  5 14:30:34 KO1 NetworkManager:    SCPlugin-Ifupdown: end _init.
Nov  5 14:30:34 KO1 NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Nov  5 14:30:34 KO1 NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Nov  5 14:30:34 KO1 NetworkManager: <info>  Wireless now enabled by radio killswitch
Nov  5 14:30:34 KO1 NetworkManager:    SCPlugin-Ifupdown: (146856688) ... get_connections.
Nov  5 14:30:34 KO1 NetworkManager:    SCPlugin-Ifupdown: (146856688) ... get_connections (managed=false): return empty list.
Nov  5 14:30:34 KO1 NetworkManager:    Ifupdown: get unmanaged devices count: 0
Nov  5 14:30:34 KO1 NetworkManager: <info>  (eth1): carrier is OFF
Nov  5 14:30:34 KO1 NetworkManager: <info>  (eth1): new Ethernet device (driver: 'tulip')
Nov  5 14:30:34 KO1 NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Nov  5 14:30:34 KO1 NetworkManager: <info>  (eth1): now managed
Nov  5 14:30:34 KO1 NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
Nov  5 14:30:34 KO1 NetworkManager: <info>  (eth1): bringing up device.
Nov  5 14:30:34 KO1 NetworkManager: <info>  (eth1): preparing device.
Nov  5 14:30:34 KO1 NetworkManager: <info>  (eth1): deactivating device (reason: 2).
Nov  5 14:30:34 KO1 NetworkManager: Added default wired connection 'Auto eth1' for /sys/devices/pci0000:00/0000:00:0b.0/net/eth1
Nov  5 14:30:34 KO1 NetworkManager: <info>  (eth0): carrier is OFF
Nov  5 14:30:34 KO1 NetworkManager: <info>  (eth0): new Ethernet device (driver: 'via-rhine')
Nov  5 14:30:34 KO1 NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Nov  5 14:30:34 KO1 NetworkManager: <info>  (eth0): now managed
Nov  5 14:30:34 KO1 NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Nov  5 14:30:34 KO1 NetworkManager: <info>  (eth0): bringing up device.
Nov  5 14:30:34 KO1 NetworkManager: <info>  (eth0): preparing device.
Nov  5 14:30:34 KO1 NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Nov  5 14:30:34 KO1 NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:12.0/net/eth0
Nov  5 14:30:34 KO1 NetworkManager: <info>  (eth1): carrier now ON (device state 2)
Nov  5 14:30:34 KO1 NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 40)
Nov  5 14:30:34 KO1 NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Nov  5 14:30:34 KO1 NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Nov  5 14:30:34 KO1 NetworkManager: <info>  modem-manager is now available
Nov  5 14:30:34 KO1 NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Nov  5 14:30:34 KO1 NetworkManager: <info>  Trying to start the supplicant...
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth1) starting connection 'Auto eth1'
Nov  5 14:30:34 KO1 NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Nov  5 14:30:34 KO1 NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Nov  5 14:30:34 KO1 NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Nov  5 14:30:34 KO1 NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Nov  5 14:30:34 KO1 NetworkManager: <info>  (eth1): device state change: 5 -> 7 (reason 0)
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction (timeout in 45 seconds)
Nov  5 14:30:34 KO1 NetworkManager: <info>  dhclient started with pid 1347
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) scheduled...
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Nov  5 14:30:34 KO1 NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Nov  5 14:30:34 KO1 NetworkManager: <info>  dhclient started with pid 1361
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Nov  5 14:30:34 KO1 dhclient: Internet Systems Consortium DHCP Client V3.1.2
Nov  5 14:30:34 KO1 dhclient: Copyright 2004-2008 Internet Systems Consortium.
Nov  5 14:30:34 KO1 dhclient: All rights reserved.
Nov  5 14:30:34 KO1 dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Nov  5 14:30:34 KO1 dhclient: 
Nov  5 14:30:34 KO1 dhclient: Internet Systems Consortium DHCP Client V3.1.2
Nov  5 14:30:34 KO1 dhclient: Copyright 2004-2008 Internet Systems Consortium.
Nov  5 14:30:34 KO1 dhclient: All rights reserved.
Nov  5 14:30:34 KO1 dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Nov  5 14:30:34 KO1 dhclient: 
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) started...
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) complete.
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Nov  5 14:30:34 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Nov  5 14:30:35 KO1 NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Nov  5 14:30:35 KO1 dhclient: Listening on LPF/eth1/00:04:5a:7d:5a:e2
Nov  5 14:30:35 KO1 dhclient: Sending on   LPF/eth1/00:04:5a:7d:5a:e2
Nov  5 14:30:35 KO1 dhclient: Sending on   Socket/fallback
Nov  5 14:30:35 KO1 dhclient: Listening on LPF/eth0/00:13:8f:db:33:1d
Nov  5 14:30:35 KO1 dhclient: Sending on   LPF/eth0/00:13:8f:db:33:1d
Nov  5 14:30:35 KO1 dhclient: Sending on   Socket/fallback
Nov  5 14:30:36 KO1 avahi-daemon[1203]: Registering new address record for fe80::204:5aff:fe7d:5ae2 on eth1.*.
Nov  5 14:30:36 KO1 acpid: client connected from 1528[107:114]
Nov  5 14:30:36 KO1 avahi-daemon[1203]: Registering new address record for fe80::213:8fff:fedb:331d on eth0.*.
Nov  5 14:30:37 KO1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Nov  5 14:30:37 KO1 dhclient: DHCPOFFER of 192.168.2.2 from 192.168.2.1
Nov  5 14:30:37 KO1 dhclient: DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
Nov  5 14:30:37 KO1 dhclient: DHCPACK of 192.168.2.2 from 192.168.2.1
Nov  5 14:30:37 KO1 dhclient: bound to 192.168.2.2 -- renewal in 33866 seconds.
Nov  5 14:30:37 KO1 NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Nov  5 14:30:37 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Nov  5 14:30:37 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Nov  5 14:30:37 KO1 NetworkManager: <info>    address 192.168.2.2
Nov  5 14:30:37 KO1 NetworkManager: <info>    prefix 24 (255.255.255.0)
Nov  5 14:30:37 KO1 NetworkManager: <info>    gateway 192.168.2.1
Nov  5 14:30:37 KO1 NetworkManager: <info>    nameserver '192.168.2.1'
Nov  5 14:30:37 KO1 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Nov  5 14:30:37 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Nov  5 14:30:37 KO1 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Nov  5 14:30:37 KO1 avahi-daemon[1203]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Nov  5 14:30:37 KO1 avahi-daemon[1203]: New relevant interface eth0.IPv4 for mDNS.
Nov  5 14:30:37 KO1 avahi-daemon[1203]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Nov  5 14:30:37 KO1 gdm-binary[1485]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Nov  5 14:30:37 KO1 gdm-binary[1485]: WARNING: Unable to find users: no seat-id found
Nov  5 14:30:37 KO1 gdm-simple-slave[1638]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Nov  5 14:30:38 KO1 acpid: client connected from 1643[0:0]
Nov  5 14:30:38 KO1 NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Nov  5 14:30:38 KO1 NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Nov  5 14:30:38 KO1 NetworkManager: <info>  Activation (eth0) successful, device activated.
Nov  5 14:30:38 KO1 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Nov  5 14:30:38 KO1 NetworkManager: <info>  (eth1): carrier now OFF (device state 7, deferring action for 4 seconds)
Nov  5 14:30:39 KO1 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Nov  5 14:30:39 KO1 ntpdate[1736]: adjust time server 91.189.94.4 offset 0.317038 sec
Nov  5 14:30:39 KO1 acpid: client connected from 1643[0:0]
Nov  5 14:30:40 KO1 console-kit-daemon[1222]: WARNING: Couldn't read /proc/1094/environ: Failed to open file '/proc/1094/environ': No such file or directory
Nov  5 14:30:43 KO1 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Nov  5 14:30:43 KO1 NetworkManager: <info>  (eth1): device state change: 7 -> 2 (reason 40)
Nov  5 14:30:43 KO1 NetworkManager: <info>  (eth1): deactivating device (reason: 40).
Nov  5 14:30:43 KO1 NetworkManager: <info>  (eth1): canceled DHCP transaction, dhcp client pid 1347
Nov  5 14:30:43 KO1 NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Nov  5 14:30:50 KO1 gdm-session-worker[1836]: pam_sm_authenticate: Called
Nov  5 14:30:50 KO1 gdm-session-worker[1836]: pam_sm_authenticate: username = [wackyb]
Nov  5 14:31:15 KO1 NetworkManager: <info>  Sleeping...
Nov  5 14:31:15 KO1 NetworkManager: <info>  (eth1): now unmanaged
Nov  5 14:31:15 KO1 NetworkManager: <info>  (eth1): device state change: 2 -> 1 (reason 37)
Nov  5 14:31:15 KO1 NetworkManager: <info>  (eth1): cleaning up...
Nov  5 14:31:15 KO1 NetworkManager: <info>  (eth1): taking down device.
Nov  5 14:31:15 KO1 NetworkManager: <info>  (eth0): now unmanaged
Nov  5 14:31:15 KO1 avahi-daemon[1203]: Withdrawing address record for fe80::204:5aff:fe7d:5ae2 on eth1.
Nov  5 14:31:15 KO1 NetworkManager: <info>  (eth0): device state change: 8 -> 1 (reason 37)
Nov  5 14:31:15 KO1 NetworkManager: <info>  (eth0): deactivating device (reason: 37).
Nov  5 14:31:15 KO1 NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 1361
Nov  5 14:31:15 KO1 NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess#012
Nov  5 14:31:15 KO1 NetworkManager: <info>  (eth0): cleaning up...
Nov  5 14:31:15 KO1 NetworkManager: <info>  (eth0): taking down device.
Nov  5 14:31:15 KO1 avahi-daemon[1203]: Withdrawing address record for 192.168.2.2 on eth0.
Nov  5 14:31:15 KO1 avahi-daemon[1203]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Nov  5 14:31:15 KO1 NetworkManager: <info>  (eth0): carrier now OFF (device state 1)
Nov  5 14:31:15 KO1 avahi-daemon[1203]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov  5 14:31:15 KO1 avahi-daemon[1203]: Withdrawing address record for fe80::213:8fff:fedb:331d on eth0.
Nov  5 14:31:47 KO1 acpid: client 1643[0:0] has disconnected
Nov  5 14:31:47 KO1 acpid: client 1643[0:0] has disconnected
Nov  5 14:31:47 KO1 acpid: client connected from 1643[0:0]
Nov  5 14:31:47 KO1 NetworkManager: <info>  Waking up...
Nov  5 14:31:47 KO1 NetworkManager: <info>  (eth1): now managed
Nov  5 14:31:47 KO1 NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
Nov  5 14:31:47 KO1 NetworkManager: <info>  (eth1): bringing up device.
Nov  5 14:31:47 KO1 NetworkManager: <info>  (eth1): preparing device.
Nov  5 14:31:47 KO1 NetworkManager: <info>  (eth1): deactivating device (reason: 2).
Nov  5 14:31:47 KO1 NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Nov  5 14:31:47 KO1 NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Nov  5 14:31:47 KO1 NetworkManager: <info>  (eth0): now managed
Nov  5 14:31:47 KO1 NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Nov  5 14:31:47 KO1 NetworkManager: <info>  (eth0): bringing up device.
Nov  5 14:31:47 KO1 NetworkManager: <info>  (eth0): preparing device.
Nov  5 14:31:47 KO1 NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Nov  5 14:31:47 KO1 NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Nov  5 14:31:47 KO1 NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Nov  5 14:31:47 KO1 NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Nov  5 14:31:47 KO1 NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Nov  5 14:31:47 KO1 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  5 14:31:47 KO1 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Nov  5 14:31:47 KO1 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Nov  5 14:31:47 KO1 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Nov  5 14:31:47 KO1 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Nov  5 14:31:47 KO1 NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Nov  5 14:31:47 KO1 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Nov  5 14:31:47 KO1 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov  5 14:31:47 KO1 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Nov  5 14:31:47 KO1 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Nov  5 14:31:47 KO1 NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Nov  5 14:31:47 KO1 NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Nov  5 14:31:47 KO1 dhclient: Internet Systems Consortium DHCP Client V3.1.2
Nov  5 14:31:47 KO1 dhclient: Copyright 2004-2008 Internet Systems Consortium.
Nov  5 14:31:47 KO1 dhclient: All rights reserved.
Nov  5 14:31:47 KO1 dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Nov  5 14:31:47 KO1 NetworkManager: <info>  dhclient started with pid 2349
Nov  5 14:31:47 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Nov  5 14:31:47 KO1 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Nov  5 14:31:47 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Nov  5 14:31:47 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Nov  5 14:31:47 KO1 acpid: client connected from 1643[0:0]
Nov  5 14:31:47 KO1 dhclient: 
Nov  5 14:31:48 KO1 NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Nov  5 14:31:48 KO1 dhclient: Listening on LPF/eth0/00:13:8f:db:33:1d
Nov  5 14:31:48 KO1 dhclient: Sending on   LPF/eth0/00:13:8f:db:33:1d
Nov  5 14:31:48 KO1 dhclient: Sending on   Socket/fallback
Nov  5 14:31:49 KO1 avahi-daemon[1203]: Registering new address record for fe80::213:8fff:fedb:331d on eth0.*.
Nov  5 14:31:50 KO1 dhclient: DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
Nov  5 14:31:56 KO1 dhclient: DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
Nov  5 14:32:03 KO1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Nov  5 14:32:07 KO1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Nov  5 14:32:12 KO1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Nov  5 14:32:26 KO1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Nov  5 14:32:33 KO1 NetworkManager: <info>  (eth0): DHCP transaction took too long, stopping it.
Nov  5 14:32:33 KO1 NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 2349
Nov  5 14:32:33 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Nov  5 14:32:33 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
Nov  5 14:32:33 KO1 NetworkManager: <info>  (eth0): device state change: 7 -> 9 (reason 5)
Nov  5 14:32:33 KO1 NetworkManager: <info>  Marking connection 'Auto eth0' invalid.
Nov  5 14:32:33 KO1 NetworkManager: <info>  Activation (eth0) failed.
Nov  5 14:32:33 KO1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Nov  5 14:32:33 KO1 NetworkManager: <info>  (eth0): device state change: 9 -> 3 (reason 0)
Nov  5 14:32:33 KO1 NetworkManager: <info>  (eth0): deactivating device (reason: 0).
Nov  5 14:37:21 KO1 NetworkManager: <info>  Sleeping...
Nov  5 14:37:21 KO1 NetworkManager: <info>  (eth1): now unmanaged
Nov  5 14:37:21 KO1 NetworkManager: <info>  (eth1): device state change: 2 -> 1 (reason 37)
Nov  5 14:37:21 KO1 NetworkManager: <info>  (eth1): cleaning up...
Nov  5 14:37:21 KO1 NetworkManager: <info>  (eth1): taking down device.
Nov  5 14:37:21 KO1 NetworkManager: <info>  (eth0): now unmanaged
Nov  5 14:37:21 KO1 NetworkManager: <info>  (eth0): device state change: 3 -> 1 (reason 37)
Nov  5 14:37:21 KO1 NetworkManager: <info>  (eth0): cleaning up...
Nov  5 14:37:21 KO1 NetworkManager: <info>  (eth0): taking down device.
Nov  5 14:37:21 KO1 NetworkManager: <info>  (eth0): carrier now OFF (device state 1)
Nov  5 14:37:21 KO1 avahi-daemon[1203]: Withdrawing address record for fe80::213:8fff:fedb:331d on eth0.
Nov  5 14:37:25 KO1 NetworkManager: <info>  Waking up...
Nov  5 14:37:25 KO1 NetworkManager: <info>  (eth1): now managed
Nov  5 14:37:25 KO1 NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
Nov  5 14:37:25 KO1 NetworkManager: <info>  (eth1): bringing up device.
Nov  5 14:37:25 KO1 NetworkManager: <info>  (eth1): preparing device.
Nov  5 14:37:25 KO1 NetworkManager: <info>  (eth1): deactivating device (reason: 2).
Nov  5 14:37:25 KO1 NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Nov  5 14:37:25 KO1 NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Nov  5 14:37:25 KO1 NetworkManager: <info>  (eth0): now managed
Nov  5 14:37:25 KO1 NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Nov  5 14:37:25 KO1 NetworkManager: <info>  (eth0): bringing up device.
Nov  5 14:37:25 KO1 NetworkManager: <info>  (eth0): preparing device.
Nov  5 14:37:25 KO1 NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Nov  5 14:37:25 KO1 NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Nov  5 14:37:25 KO1 NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Nov  5 14:37:26 KO1 avahi-daemon[1203]: Registering new address record for fe80::213:8fff:fedb:331d on eth0.*.

---

### Post by mpokrywka on 2009-11-05
Looks like this option doesn't work in your case - after resume no DHCP packets are received...

My last idea:
Reboot to get working network, prepare to suspend - remove *via-rhine* driver:
```
sudo rmmod via-rhine
```

Now suspend your computer, after resume try to load network driver:
```
sudo modprobe via-rhine
```

Wait some time for NetworkManager to spot new network interface and try to connect.

If unloading driver before suspend and loading after resume works, it could be automated, but I will check how to do it later, if it works for you.

---

### Post by wacky.banana on 2009-11-05
Mpokrywka,

Last solution worked perfectly. Network card found almost instantly.

So how doe we automate this so that it works each time ater suspend? If the worse comes to the worse I would be happy to manually run a script file each time; however I am sure all this can be automated.

Really appreciate your help here.

Thanks

WB

---

### Post by mpokrywka on 2009-11-05
Create config file in /etc/pm/config.d with *SUSPEND_MODULES="via-rhine"* line, i.e.
```
sudo sh -c 'echo SUSPEND_MODULES=\"via-rhine\" >> /etc/pm/config.d/01fix_resume_net_failure'
```


Ok, this is only workaround, it would be better if kernel works properly...

If you have some time I advise you to report this problem on [www.kernel.org](www.kernel.org) bugzilla.

Also you can remove this "options" line from /etc/modprobe.d/options

---

### Post by wacky.banana on 2009-11-05
Hello again,

I took some time to do some testing as your solution did not seem to work at first. I then discovered that the auto eth0 option was not enabled (something had switched it off).

With that option enabled the card works every time from suspend which is a great result. I will continue to test over the next day or so to ensure that this is a stable and consistent solution and report back to you. Brilliant result.

Now believe it or not the Hibernate option does not work either. Despite the fact that I have a 5gb swap file in place to cover off physical memory of 2gb in my machine,  resume from Hibernation simply hangs the machine after a while.

The only way out is to physically switch off and reboot, which results in a disk check before I get control of the PC again.

Any ideas on this problem and a solution for it?

Thanks for what you have done so far on the Suspend front which was really, really bugging me.

WB

---

### Post by mpokrywka on 2009-11-05
Most linux problems with suspend/hibernate come from dodgy video drivers.
I won't help you with this problem - I don't know how to diagnose those problems. You can try your luck with passing "quirk" parameters to pm-hibernate:
**sudo pm-hibernate --help**

Pick one or more, for example:
**sudo pm-hibernate --quirk-s3-bios --quirk-s3-mode**
And hope for success...

Most helpful would be posting on list with suspend/hibernate experts:
[http://www.tuxonice.net/lists.html](http://www.tuxonice.net/lists.html)
Someone there would know what quirks are needed for which video hardware...

---

### Post by wacky.banana on 2009-11-05
Mpokrywka,

Thanks for that. Will give it a try later.

Just come out of suspend after an hour away and the machine works fine.

Interesting point you make about dodgy video drivers. I use an Nvidia video card which works fine in Windows. Are you saying that equivalent drivers for Linux are written by 3rd parties and have not been developed properly?

Once again thanks for the Suspend solution. I will report the kernel problem when I have more time.

All the best.

WB

---

