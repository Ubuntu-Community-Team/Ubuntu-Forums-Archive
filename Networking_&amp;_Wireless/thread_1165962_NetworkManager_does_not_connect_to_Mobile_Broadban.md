---
title: "NetworkManager does not connect to Mobile Broadband anymore in Jaunty (Sierra AC880)"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by laenzlinger on 2009-05-21
I have recently installed Ubuntu 9.04 on my lenevo T61. I am using a mobile broadband card (Sierra Wirelss Aircard 880) to connect to the mobile broadband network.

In Ubuntu 8.04 it was working fine by using the NetworkManager. I only had to remove the APN setting in the Advanced Settings of the Connection to get it working. 

Now in Ubuntu 9.04 - in completely fresh installation - I cannot connect anymore to my mobile operator.

In the log files I can now see that the connection is suddenly aborted in the IPCP negotiaten phase. Actually, no IPCP Response is received at all. (See attachment nm-ppp-ubuntu9_04.log). The same actually happend also without the above mentioned fix of the dbus rules.

My knowledge about the PPP Protocol is very limitted so I do not have any idea how to go on from this point. So any help is very much appreciated.

```

========> Insert the sierra 880 PC-Card <=========


NetworkManager: <info>  (ttyUSB0): found serial port (udev:  hal:GSM)
NetworkManager: <info>  (ttyUSB0): ignoring due to lack of probed mobile broadband capabilties
NetworkManager: <info>  (ttyUSB2): found serial port (udev:GSM  hal:)
NetworkManager: <info>  (ttyUSB2): deferring until all ports found
NetworkManager: <info>  Re-checking deferred serial ports
NetworkManager: <info>  (ttyUSB2): new Modem device (driver: 'sierra')
NetworkManager: <info>  (ttyUSB2): exported as /org/freedesktop/Hal/devices/usb_device_1199_6850_noserial_if0_serial_usb_2_4
NetworkManager: <info>  (ttyUSB2): device state change: 1 -> 2
NetworkManager: <info>  (ttyUSB2): deactivating device (reason: 2).
NetworkManager: <info>  Policy set 'Auto blah' (wlan0) as default for routing and DNS.
NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
NetworkManager: <info>  (ttyUSB2): device state change: 2 -> 3


=========> Activate Connection <==========


NetworkManager: <info>  Activation (ttyUSB2) starting connection 'Swisscom'
NetworkManager: <info>  (ttyUSB2): device state change: 3 -> 4
NetworkManager: <info>  Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info>  Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <debug> [1241360812.725471] nm_serial_device_open(): (ttyUSB2) opening device...
NetworkManager: <info>  Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <info>  (ttyUSB2): powering up...
NetworkManager: <info>  Registered on Home network
NetworkManager: <info>  Associated with network: +COPS: 0,0,"Swisscom",0
NetworkManager: <info>  Connected, Woo!
NetworkManager: <info>  Activation (ttyUSB2) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <info>  Activation (ttyUSB2) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <info>  (ttyUSB2): device state change: 4 -> 5
NetworkManager: <info>  Starting pppd connection
NetworkManager: <debug> [1241360813.264504] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute debug user gprs ttyUSB2 noipdefault noauth usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/0 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so
NetworkManager: <debug> [1241360813.266246] nm_ppp_manager_start(): ppp started with pid 17266
NetworkManager: <info>  Activation (ttyUSB2) Stage 2 of 5 (Device Configure) complete.
Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
using channel 8
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB2
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x12345678> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x0 <asyncmap 0x0> <auth chap MD5> <magic 0x12345678> <pcomp> <accomp>]
sent [LCP ConfAck id=0x0 <asyncmap 0x0> <auth chap MD5> <magic 0x12345678> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x12345678> <pcomp> <accomp>]
rcvd [LCP DiscReq id=0x1 magic=0x12345678]
NetworkManager: <info>  (ttyUSB2): device state change: 5 -> 6
rcvd [CHAP Challenge id=0x1 <12345678901234567890123456789012>, name = "UMTS_CHAP_SRVR"]
sent [CHAP Response id=0x1 <12345678901234567890123456789012>, name = "gprs"]
rcvd [CHAP Success id=0x1 ""]
CHAP authentication succeeded
CHAP authentication succeeded
sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
NetworkManager: <info>  (ttyUSB2): device state change: 6 -> 7
rcvd [LCP ProtRej id=0x2 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Modem hangup
Connection terminated.


=======> GSM-Connection disconnected <===========


NetworkManager: <info>  (ttyUSB2): device state change: 7 -> 9
NetworkManager: <debug> [1241360824.469493] nm_serial_device_close(): Closing device 'ttyUSB2'
NetworkManager: <info>  Marking connection 'Swisscom' invalid.
NetworkManager: <info>  Activation (ttyUSB2) failed.
NetworkManager: <info>  (ttyUSB2): device state change: 9 -> 3
NetworkManager: <info>  (ttyUSB2): deactivating device (reason: 0).
NetworkManager: <info>  Policy set 'Auto blah' (wlan0) as default for routing and DNS.
NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
NetworkManager: <info>  (ttyUSB2): now unmanaged
NetworkManager: <info>  (ttyUSB2): device state change: 3 -> 1
NetworkManager: <info>  (ttyUSB2): cleaning up...
NetworkManager: <info>  (ttyUSB2): taking down device.
NetworkManager: <info>  (ttyUSB3): found serial port (udev:  hal:GSM)
NetworkManager: <info>  (ttyUSB3): ignoring due to lack of probed mobile broadband capabilties
NetworkManager: <info>  (ttyUSB5): found serial port (udev:GSM  hal:)
NetworkManager: <info>  (ttyUSB5): deferring until all ports found
NetworkManager: <debug> [1241360826.999325] ensure_killed(): waiting for ppp pid 17266 to exit
NetworkManager: <debug> [1241360826.999522] ensure_killed(): ppp pid 17266 cleaned up
NetworkManager: <info>  Re-checking deferred serial ports
NetworkManager: <info>  (ttyUSB5): new Modem device (driver: 'sierra')
NetworkManager: <info>  (ttyUSB5): exported as /org/freedesktop/Hal/devices/usb_device_1199_6850_noserial_if0_serial_usb_2_5
NetworkManager: <info>  (ttyUSB5): device state change: 1 -> 2
NetworkManager: <info>  (ttyUSB5): deactivating device (reason: 2).




```


BTW: I succeeded connecting to the mobile network by using wvdial. Therfore I am sure it is not a hardware or driver problem. I think it is related to network-manager calling pppd.

---

### Post by justinlawrence on 2009-08-03
I'm getting something similar:

NetworkManager: <info>  (ttyUSB2): ignoring due to lack of mobile broadband capabilties  

I'm using kppp instead at the moment but am keen to get it working nicely in network-manager, if anyone has any suggestions.

---

### Post by kneuzgi on 2010-10-14
Hi

I'm using also a the sierra AC880 with my Lenovo T61 and Swisscom. I can also not connect via NetworkManager or UMTSMON.

I'm using Ubuntu 10.04 LTS

When i'm using wvdial then it's very very solw (ping to internet between 800 and 1200 ms)
so not very interessting to surf in the web :-(

Does anybody have an idea ?

Thx

Regards

Kneuzgi

---

