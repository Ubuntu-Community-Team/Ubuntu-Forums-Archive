---
title: "hardy won't ack my teathered phone"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by SaintDanBert on 2009-03-04
When I connect my phone via its data cable, the logs blather about
rndis_host and usbcore and usb 3-1 then no "kernel hookup" happens.
Using lsmod, I find rndis_host so I suspect some event isn't setup
or that some other config isn't present or correct. I have no idea
what or how to proceed. Shouldn't I see some positive indicator
that hardy has a modem after I connect the phone?  

I know that something is going on because network manager drops any network connection that is already in progress ... I presume it expects to swap over to the new interface if that wakes up.  [ASIDE -- what if I want to gateway from mobile broadband to wire or wireless enet...]

Here is a chunk of log file when I connect the phone by USB cable.
-----------------------------
Mar  4 18:56:49 mumbles kernel: usb 2-1: new full speed USB device using uhci_hcd and address 2
Mar  4 18:56:49 mumbles kernel: Device driver usbdev2.2_ep00 lacks bus and class support for being resumed.
Mar  4 18:56:49 mumbles kernel: usb 2-1: configuration #1 chosen from 1 choice
Mar  4 18:56:49 mumbles kernel: Device driver usbdev2.2_ep81 lacks bus and class support for being resumed.
Mar  4 18:56:49 mumbles kernel: Device driver usbdev2.2_ep82 lacks bus and class support for being resumed.
Mar  4 18:56:49 mumbles kernel: Device driver usbdev2.2_ep03 lacks bus and class support for being resumed.
Mar  4 18:56:50 mumbles kernel: usbcore: registered new interface driver cdc_ether
Mar  4 18:56:50 mumbles kernel: Device driver eth1 lacks bus and class support for being resumed.
Mar  4 18:56:50 mumbles kernel: eth1: register 'rndis_host' at usb-0000:00:1a.1-1, RNDIS device, 80:00:60:0f:e8:00
Mar  4 18:56:50 mumbles kernel: usbcore: registered new interface driver rndis_host
Mar  4 18:56:50 mumbles dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
-----------------------------

... here net manager is searching for a connection it never finds ...

This happens at disconnect
-----------------------------
Mar  4 18:57:34 mumbles dhcdbd: Unrequested down ?:3
Mar  4 18:58:04 mumbles kernel: usb 2-1: USB disconnect, address 2
Mar  4 18:58:04 mumbles kernel: eth1: unregister 'rndis_host' usb-0000:00:1a.1-1, RNDIS device
Mar  4 18:58:16 mumbles kernel: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Mar  4 18:58:19 mumbles dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Mar  4 18:58:19 mumbles dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Mar  4 18:58:19 mumbles dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu
-----------------------------

... here net manager finds the connection in use before I connect the phone  ...

Is this telling me that the phone replaces the existing 'wlan0' device?
And then it goes away at disconnect? [ASICE -- How do I give it a unique name  that sticks around from boot to boot and use to use? ]

Can someone shed light on what to do next?
Thanks,
~~~ 0;-D
an olde geek learning new tricks ... slowly

---

