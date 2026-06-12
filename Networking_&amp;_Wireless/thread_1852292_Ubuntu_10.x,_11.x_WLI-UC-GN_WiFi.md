---
title: "Ubuntu 10.x, 11.x WLI-UC-GN WiFi"
date: 2011-09-29
forum: Networking &amp; Wireless
---

### Post by dot09 on 2011-09-29
I've been through dozens of forum posts, blogs, etc.  I can't get past any of the items in order to get anything working.  I think this is why, but I do not know how to fix it:

My device, when connected, shows up like this with lsusb:

Bus 001 Device 002: ID 0411:014f MelCo., Inc.

All of the other posts I've seen point to a difference device ID.  In fact, 015d matches the product name, branding, etc of the device I bought.

There is no entry in /etc/udev/rules.d/70-persistent-net.rules for my device.  I considered manually editing the file to add my device but I wasn't sure what to enter for the MAC address without knowing for sure what it is on the device.

I've tried all the blacklisting, lsusb, modinfo, fiddle-faddle, hop-n-scotch.  I can see messages in the syslog when I connect/disconnect the device.  I *never* get any reference to wlan0 or ra0, etc.  the iw* commands do nothing, networking doesn't even show wireless as an option.

I've installed fresh, with the device connected, Ubuntu 10.10, 11.04 and now 11.10 (all of which were 64-bit).  No dice.

I should have noted that the device is working properly in a Windows machine when inserted.  I don't think the system knows what to do with my particular vendor:device ID.

Thoughts?

Regards,

Bill Mote

---

