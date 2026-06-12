---
title: "Unable to connect with 3G after not using it for 2 months"
date: 2011-06-05
forum: Networking &amp; Wireless
---

### Post by azzid on 2011-06-05
Yesterday I tried to connect using my 3G, it has been working since I installed the computer more than a year ago.

When I try to connect I get the following in the syslog (and daemon.log)
```
Jun  5 10:50:21 ubuntu NetworkManager: <info>  Activation (ttyUSB0) starting connection '3 Bredband'
Jun  5 10:50:21 ubuntu NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 (reason 0)
Jun  5 10:50:21 ubuntu NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  5 10:50:21 ubuntu NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Jun  5 10:50:21 ubuntu NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Jun  5 10:50:21 ubuntu NetworkManager: <WARN>  stage1_prepare_done(): GSM modem connection failed: (32) Sending command failed: device is not enabled
Jun  5 10:50:21 ubuntu NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 9 (reason 1)
Jun  5 10:50:21 ubuntu NetworkManager: <info>  Marking connection '3 Bredband' invalid.
Jun  5 10:50:21 ubuntu NetworkManager: <info>  Activation (ttyUSB0) failed.
Jun  5 10:50:21 ubuntu NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 (reason 0)
Jun  5 10:50:21 ubuntu NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0).
Jun  5 10:50:21 ubuntu modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (connected -> disconnecting)
Jun  5 10:50:21 ubuntu modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (disconnecting -> connected)

```

After alot of swearing ang scratching of the head I've resorted to trying this from i live cd, but with the same results. I know I've been able to connect using livecd before so I'm a bit worried that something might have happened with the hardware.

What I'm hoping for though is some way to determine that it is the sim-card and/or something on the operator side that is bork.

Does anyone know how to further pinpoint the issue? And/or troubleshoot the hardware? I should be able to send AT-commands directly to the modem, does anyone know how and/or the syntax for establishing the data connection?

EDIT: I'm using an Asus eee 901  with builtin 3G modem.

---

### Post by azzid on 2011-06-05
Since the machine was bought in april 2009 I figured I could try connecting using ubuntu 9.04 since that was probably what I first got it working under.

Still no go, but something else in the log:
```
Jun  5 11:28:53 ubuntu NetworkManager: <info>  Activation (ttyUSB0) starting connection '3 (Bredband)' 
Jun  5 11:28:53 ubuntu NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 
Jun  5 11:28:53 ubuntu NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled... 
Jun  5 11:28:53 ubuntu NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started... 
Jun  5 11:28:53 ubuntu NetworkManager: <debug> [1307273333.115739] nm_serial_device_open(): (ttyUSB0) opening device... 
Jun  5 11:28:53 ubuntu NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete. 
Jun  5 11:28:53 ubuntu NetworkManager: <info>  (ttyUSB0): powering up... 
Jun  5 11:28:53 ubuntu NetworkManager: <info>  Registered on Roaming network 
Jun  5 11:28:53 ubuntu NetworkManager: <info>  Associated with network: +COPS: 0,2,"24004",2 
Jun  5 11:28:53 ubuntu NetworkManager: <info>  Connected, Woo! 
Jun  5 11:28:53 ubuntu NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) scheduled... 
Jun  5 11:28:53 ubuntu NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) starting... 
Jun  5 11:28:53 ubuntu NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 5 
Jun  5 11:28:53 ubuntu NetworkManager: <info>  Starting pppd connection 
Jun  5 11:28:53 ubuntu NetworkManager: <debug> [1307273333.549025] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute ttyUSB0 noipdefault noauth usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/2 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so 
Jun  5 11:28:53 ubuntu NetworkManager: <debug> [1307273333.551640] nm_ppp_manager_start(): ppp started with pid 5664 
Jun  5 11:28:53 ubuntu NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) complete. 
Jun  5 11:28:53 ubuntu pppd[5664]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Jun  5 11:28:53 ubuntu pppd[5664]: pppd 2.4.5 started by root, uid 0
Jun  5 11:28:53 ubuntu pppd[5664]: Using interface ppp0
Jun  5 11:28:53 ubuntu pppd[5664]: Connect: ppp0 <--> /dev/ttyUSB0
Jun  5 11:28:53 ubuntu pppd[5664]: Unable to obtain CHAP password for ubuntu on UMTS_CHAP_SRVR from plugin
Jun  5 11:28:53 ubuntu pppd[5664]: No CHAP secret found for authenticating us to UMTS_CHAP_SRVR
Jun  5 11:28:53 ubuntu pppd[5664]: CHAP authentication succeeded
Jun  5 11:28:53 ubuntu pppd[5664]: CHAP authentication succeeded
Jun  5 11:28:55 ubuntu pppd[5664]: Modem hangup
Jun  5 11:28:55 ubuntu pppd[5664]: Connection terminated.
Jun  5 11:28:56 ubuntu pppd[5664]: Exit.
Jun  5 11:28:56 ubuntu NetworkManager: <WARN>  ppp_exit_code(): ppp pid 5664 exited with error: A modem hung up the phone 
Jun  5 11:28:56 ubuntu NetworkManager: <debug> [1307273336.947666] ppp_watch_cb(): ppp pid 5664 cleaned up 
Jun  5 11:28:56 ubuntu NetworkManager: <info>  (ttyUSB0): device state change: 5 -> 9 
Jun  5 11:28:56 ubuntu NetworkManager: <debug> [1307273336.948045] nm_serial_device_close(): Closing device 'ttyUSB0' 
Jun  5 11:28:56 ubuntu NetworkManager: <info>  Marking connection '3 (Bredband)' invalid. 
Jun  5 11:28:56 ubuntu NetworkManager: <info>  Activation (ttyUSB0) failed. 
Jun  5 11:28:56 ubuntu NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 
Jun  5 11:28:56 ubuntu NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0). 
Jun  5 11:28:56 ubuntu NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Jun  5 11:28:56 ubuntu NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed

```

---

### Post by azzid on 2011-06-14
Today I went to my operator and bought a new modem (Huawei E367). I also got a new sim card.

After running:
```
/lib/udev/modem-modeswitch -v 0x12d1 -p 0x1446 -t option-zerocd
```
to have udev recognize the new modem correctly it worked perfectly.

Since the new modem is working I guess something must've happened to the old modem (Huawei E620) but I can't really accept that it is just broken. 

Does anyone know any way to like reset such a device or something?

---

### Post by azzid on 2011-08-27
My provider had done some changes to their network, I needed a new firmware for the modem.

I tried to upgrade but it failed and bricked my hardware.

---

