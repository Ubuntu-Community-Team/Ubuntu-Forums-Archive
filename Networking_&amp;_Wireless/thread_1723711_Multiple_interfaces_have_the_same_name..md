---
title: "Multiple interfaces have the same name."
date: 2011-04-07
forum: Networking &amp; Wireless
---

### Post by tom17 on 2011-04-07
Hi,

I have a problem where multiple interfaces in my network manager have the same name. This means that I am unable to have different settings for each interface.

Here is my setup:
Ubuntu 10.04 LTS
uname -a: Linux muon 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:21 UTC 2011 i686 GNU/Linux
Adapter 1: 02:00.0 Ethernet controller: Intel Corporation 82573E Gigabit Ethernet Controller (Copper) (rev 03)
Adapter 2: HTC Desire tethered via USB.

When I start from scratch, with no remembered networks in the network manager, the Ethernet is shown as "Auto Ethernet".

When I then connect the HTC Desire, the new network is shown in the network manager also as "Auto Ethernet".

Previously, when I right clicked on the network manager and selected "Edit Connections", there were multiple "Auto Ethernet" entries under the wired tab.

Now (and I do not know what changed, sorry), I only see one entry. When I edit this entry (say, add a route), then the route is added for both network interfaces.
This used to still work, so I was not worried about the name clash, but now it is causing problems so I need to have a different name for each network interface.

Any idea what's going on here or how to reset the network manager to fix this?

Thanks,

Tom...

---

### Post by tom17 on 2011-04-07
Well, I seemed to fix it.

I hunted all over, finding how to rename devices. I tried changing the device names using a UDEV rule. The device names changed, but I still had the same problem in network manager.

Then I figured that this is a nm issue so I delved into the site for that and found the config.

I ended up editing /etc/NetworkManager/nm-system-settings.conf

and found the line:
```
no-auto-default=<mac>,<mac>,<mac>,<mac>,<mac>,<mac>,<mac>
```
(I edited out the mac addresses)

This looked suspicious to me. I could not find any info on this setting and how it fills up like that. I commented it out and my problem is gone.

I now have 2 network adapters to configure in network manager: Auto eth0 and Auto htc0. yay!

Tom...

---

