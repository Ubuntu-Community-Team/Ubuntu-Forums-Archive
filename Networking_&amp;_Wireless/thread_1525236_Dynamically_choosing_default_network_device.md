---
title: "Dynamically choosing default network device"
date: 2010-07-06
forum: Networking &amp; Wireless
---

### Post by nuclear_eclipse on 2010-07-06
I have a desktop machine with a hardwired network connection on a private network (eth0), and a usb-based network device (usb0) that is only plugged in part of the time and connects to a public network.  Is it possible to configure the system so that when usb0 is available, it uses usb0 as the default network device, but can fail back to using eth0 if either usb0 is unavailable or if connecting to an address on the private network?

When I plug in usb0, NetworkManager detects and sets up the connection just fine, but it seems that the system continues to use eth0 as the default outbound connection.  Is there any way to specify a priority on these devices without crippling eth0?

---

