---
title: "How to modeswitch Novatel U679 USB LTE stick 1410:5059"
date: 2012-08-01
forum: Networking &amp; Wireless
---

### Post by jcobban on 2012-08-01
I am trying to get the Novatel U679 USB LTE stick obtained from my network vendor (Bell Canada) working on Linux.

As usual with these devices it initially comes up as a disk drive.  So I need to issue a modeswitch command to it.  I went to /usr/share/usb_modeswitch and extracted the configuration file associated with the vendor and product id.  This looks like:

```
# Novatel Wireless MC545 HSPA

TargetVendor=  0x1410
TargetProduct= 0x7042

MessageContent="5553424312345678000000000000061b000000020000000000000000000000"
NeedResponse=1

```

When I issue "usb_modeswitch -c <above file>" it complains that it cannot find the product, which makes sense since the id is 1410:5059, not 1410:7042.  So not really understanding what is going on I try to make the command happy by adding a default vendor and product id to the config file:

```
# Novatel Wireless U679 HSPA

DefaultVendor=  0x1410
DefaultProduct= 0x5059

TargetVendor=  0x1410
TargetProduct= 0x7042

MessageContent="5553424312345678000000000000061b000000020000000000000000000000"
NeedResponse=1

```

Now when I issue "usb_modeswitch -c <filename>" I get:

```
$ sudo usb_modeswitch -c /etc/usb_modeswitch.d/1410\:5059
[sudo] password for jcobban: 

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 002 on bus 008 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Ambiguous Class/InterfaceClass: 0xef/0x08
Using first interface: 0x00
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

```

At which point the process hangs and I am left with a device which has not associated driver.

I even went to the manufacturer and received what purports to be a Linux driver (in deb format) for the product and installed that.

---

### Post by jcobban on 2012-08-03
The solution to getting this stick working was far from intuitive:

[LIST=1]
[*]Eject the "disk drive" that the stick is pretending to be in order to supply the config software for Windows/Mac!
[*]In the network status display a new "Wired Connection" appears.  Ignore this.  Farther down the list, after any WIFI networks, an entry appears for the 4G/LTE network.  Click on this and the menu for configuring the provider appears.  Complete this and the network connection is up.
[/LIST]

I imagine that somewhere in Ubuntu there is a list of USB product ids for which the system does the "Eject" automatically as soon as it sees them, and the id for this stick just isn't in that list.

---

### Post by ernied on 2012-10-17
> **jcobban said:**
> The solution to getting this stick working was far from intuitive:

[LIST=1]
[*]Eject the "disk drive" that the stick is pretending to be in order to supply the config software for Windows/Mac!
[*]In the network status display a new "Wired Connection" appears.  Ignore this.  Farther down the list, after any WIFI networks, an entry appears for the 4G/LTE network.  Click on this and the menu for configuring the provider appears.  Complete this and the network connection is up.
[/LIST]

I imagine that somewhere in Ubuntu there is a list of USB product ids for which the system does the "Eject" automatically as soon as it sees them, and the id for this stick just isn't in that list.

I've tried this on my laptop running Eeebuntu (based on Ubuntu 9.04) and on my desktop running 12.04. On the desktop, it appears to be trying to use eth0 as the network interface for the stick, but it already has a fixed IP address and other previous settings that force it to use the wired network. On the laptop, it tries to create a second ethernet device but eventually claims that there are no IPv6 routers present and tries to discover DHCP on the network before NetworkManager gives up and deactivates the device.

So I'm a little confused about what you did to make this stick work.

---

