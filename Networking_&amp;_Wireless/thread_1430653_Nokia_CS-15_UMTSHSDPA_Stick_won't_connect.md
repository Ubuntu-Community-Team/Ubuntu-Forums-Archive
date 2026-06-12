---
title: "Nokia CS-15 UMTS/HSDPA Stick won't connect"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by untanne on 2010-03-15
Hi all,

I've got a NOKIA CS-15 UMTS/HSDPA stick and I'm running Ubuntu 9.10. So I have installed the buggy zero-cd tool provided by NOKIA. The stick will be recognised as NOKIA DATA CARD and I'm able to config an entry in the network manager (NM).  Obviously the NM can load the driver, because the blue LED is blinking. That means an UMTS network is available. I enter the pin, but I can not connect and I don't known what should I do. Could you give me some hint pls?

The NM-log say:
============
NetworkManager: <info>  (ttyACM1): new GSM device (driver: 'cdc_acm')
NetworkManager: <info>  (ttyACM1): exported as /org/freedesktop/NetworkManager/Devices/2
NetworkManager: <info>  (ttyACM1): now managed
NetworkManager: <info>  (ttyACM1): device state change: 1 -> 2 (reason 2)
NetworkManager: <info>  (ttyACM1): deactivating device (reason: 2).
NetworkManager: flush_routes: assertion `iface_idx >= 0' failed
NetworkManager: flush_addresses: assertion `iface_idx >= 0' failed
NetworkManager: <info>  (ttyACM1): device state change: 2 -> 3 (reason 0)
NetworkManager: Tried to set deprecated property gsm/band
NetworkManager: <info>  Activation (ttyACM1) starting connection 'o2 Pay-by-MB 1'
NetworkManager: <info>  (ttyACM1): device state change: 3 -> 4 (reason 0)
NetworkManager: <info>  Activation (ttyACM1) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info>  Activation (ttyACM1) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <info>  Activation (ttyACM1) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <info>  (ttyACM1): device state change: 4 -> 6 (reason 0)
NetworkManager: Tried to set deprecated property gsm/band
NetworkManager: <info>  Activation (ttyACM1) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info>  Activation (ttyACM1) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <info>  (ttyACM1): device state change: 6 -> 4 (reason 0)
NetworkManager: <info>  Activation (ttyACM1) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: Tried to set deprecated property gsm/band
NetworkManager: Tried to set deprecated property gsm/band
NetworkManager: <info>  Activation (ttyACM1) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <info>  Activation (ttyACM1) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <info>  (ttyACM1): device state change: 4 -> 5 (reason 0)
NetworkManager: <info>  Activation (ttyACM1) Stage 2 of 5 (Device Configure) successful.
NetworkManager: <info>  Activation (ttyACM1) Stage 3 of 5 (IP Configure Start) scheduled.
NetworkManager: <info>  Activation (ttyACM1) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <info>  Activation (ttyACM1) Stage 3 of 5 (IP Configure Start) started...
NetworkManager: <info>  (ttyACM1): device state change: 5 -> 7 (reason 0)
NetworkManager: <info>  Starting pppd connection
NetworkManager: <debug> [1268685663.075443] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute ttyACM1 noipdefault noauth usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/0 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so
NetworkManager: <debug> [1268685663.090193] nm_ppp_manager_start(): ppp started with pid 2480
NetworkManager: <info>  Activation (ttyACM1) Stage 4 of 5 (IP6 Configure Get) scheduled...
NetworkManager: <info>  Activation (ttyACM1) Stage 3 of 5 (IP Configure Start) complete.
NetworkManager: <info>  Activation (ttyACM1) Stage 4 of 5 (IP6 Configure Get) started...
NetworkManager: <info>  Activation (ttyACM1) Stage 4 of 5 (IP6 Configure Get) complete.
Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
** Message: nm-ppp-plugin: (plugin_init): initializing
** Message: nm-ppp-plugin: (nm_phasechange): status 3 / phase 'serial connection'
Using interface ppp0
Connect: ppp0 <--> /dev/ttyACM1
** Message: nm-ppp-plugin: (nm_phasechange): status 5 / phase 'establish'
NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
** Message: nm-ppp-plugin: (nm_phasechange): status 6 / phase 'authenticate'
** Message: nm-ppp-plugin: (get_credentials): passwd-hook, requesting credentials...
** Message: nm-ppp-plugin: (get_credentials): got credentials from NetworkManager
Remote message: TTP Com PPP - Password Verified OK
PAP authentication succeeded
** Message: nm-ppp-plugin: (nm_phasechange): status 8 / phase 'network'
Received bad configure-nak:  02 06 00 2d 0f 01 81 06 00 00 00 00 83 06 00 00 00 00
Received bad configure-nak:  02 06 00 2d 0f 01 81 06 00 00 00 00 83 06 00 00 00 00
Received bad configure-nak:  02 06 00 2d 0f 01 81 06 00 00 00 00 83 06 00 00 00 00
Received bad configure-nak:  02 06 00 2d 0f 01 81 06 00 00 00 00 83 06 00 00 00 00
Received bad configure-nak:  02 06 00 2d 0f 01 81 06 00 00 00 00 83 06 00 00 00 00
NetworkManager: <WARN>  pppd_timed_out(): Looks like pppd didn't initialize our dbus module
NetworkManager: <info>  (ttyACM1): device state change: 7 -> 9 (reason 14)
Terminating on signal 15
** Message: nm-ppp-plugin: (nm_phasechange): status 10 / phase 'terminate'
** Message: nm-ppp-plugin: (nm_phasechange): status 5 / phase 'establish'
NetworkManager: <info>  Marking connection 'o2 Pay-by-MB 1' invalid.
NetworkManager: <info>  Activation (ttyACM1) failed.
NetworkManager: <info>  (ttyACM1): device state change: 9 -> 3 (reason 0)
NetworkManager: <info>  (ttyACM1): deactivating device (reason: 0).
NetworkManager: flush_routes: assertion `iface_idx >= 0' failed
NetworkManager: flush_addresses: assertion `iface_idx >= 0' failed
** Message: nm-ppp-plugin: (nm_phasechange): status 11 / phase 'disconnect'
Connection terminated.
NetworkManager: <info>  Policy set 'M4R' (wlan0) as default for routing and DNS.
NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
** Message: nm-ppp-plugin: (nm_phasechange): status 1 / phase 'dead'
** Message: nm-ppp-plugin: (nm_exit_notify): cleaning up
NetworkManager: <debug> [1268685685.001799] ensure_killed(): waiting for ppp pid 2480 to exit
NetworkManager: <debug> [1268685685.001917] ensure_killed(): ppp pid 2480 cleaned up
NetworkManager: <info>  (ttyACM1): now unmanaged
NetworkManager: <info>  (ttyACM1): device state change: 3 -> 1 (reason 36)
NetworkManager: <info>  (ttyACM1): cleaning up...
NetworkManager: <info>  (ttyACM1): taking down device.

Many thx, Untanne

---

### Post by vtired on 2010-12-26
Please did you manage to connect? Mine won't work on ubuntu 10.04 but on debian squeeze and fedora 14 you plugin and the network manager immediately recognises it. On fedora 13 needed wvdialconf but worked. I thought these things work on ubuntu before anywhere else.

---

### Post by skeptical4life on 2011-04-02
I've got a Nokia cs-18 and am having the same problem. drivers are loaded (blue light is flashing) and it appears that ubuntu is attempting to connect (indicator is spinning) but alas, no connection is ever established. Oh yeah, I forgot to mention that the Nokia software 'Connect to the Internet' button is highlighted and appears to be ready to eecute, but it does nothing when clicked on.

---

