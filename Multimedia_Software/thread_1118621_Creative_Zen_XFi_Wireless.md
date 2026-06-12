---
title: "Creative Zen XFi Wireless"
date: 2009-04-07
forum: Multimedia Software
---

### Post by Matrix09 on 2009-04-07
I notice from the threads on this forum that a number of users have problems with the Zen XFi on Ubuntu 8.10.

I'm running this on my HP Mini-Note, and wanted to use it to manage my new Creative Zen XFi. As an MTP only player there are some issues with it, and I'd much prefer to use UMS. However, it's not available. I don't want to use the hopeless Creative supplied Zen media manager or Windows media player as these both truncate file and track names.

I plugged my Zen into my Mini-Note and had no success with connecting to Gnomad, though mtp-detect detected it OK but specified "device not recognised". Fortunately I do have it running on my Gentoo based laptop with Gnomad and Amarok 2.

I though what was needed for Ubuntu 8.10 was a set of udev rules for udev to hotplug the Zen. On my Gentoo notebook there is a set of rules at:

/etc/udev/rules.d/65-mtp.rules

Which looks like this (not the full file as it stretches to 845 lines):

> 
# UDEV-style hotplug map for libmtp
# Put this file in /etc/udev/rules.d

ACTION!="add", GOTO="libmtp_rules_end"
ATTR{dev}!="?*", GOTO="libmtp_rules_end"
SUBSYSTEM=="usb", GOTO="libmtp_usb_rules"
# The following thing will be deprecated when older kernels are phased out.
SUBSYSTEM=="usb_device", GOTO="libmtp_usb_device_rules"
GOTO="libmtp_rules_end"

LABEL="libmtp_usb_rules"

# Creative ZEN Vision
ATTR{idVendor}=="041e", ATTR{idProduct}=="411f", SYMLINK+="libmtp-%k", MODE="666"
# Creative Portable Media Center
ATTR{idVendor}=="041e", ATTR{idProduct}=="4123", SYMLINK+="libmtp-%k", MODE="666"
# Creative ZEN Xtra (MTP mode)
ATTR{idVendor}=="041e", ATTR{idProduct}=="4128", SYMLINK+="libmtp-%k", MODE="666"
# Dell DJ (2nd generation)
ATTR{idVendor}=="041e", ATTR{idProduct}=="412f", SYMLINK+="libmtp-%k", MODE="666"
# Creative ZEN Micro (MTP mode)
ATTR{idVendor}=="041e", ATTR{idProduct}=="4130", SYMLINK+="libmtp-%k", MODE="666"
# Creative ZEN Touch (MTP mode)
ATTR{idVendor}=="041e", ATTR{idProduct}=="4131", SYMLINK+="libmtp-%k", MODE="666"
# Dell Dell Pocket DJ (MTP mode)
ATTR{idVendor}=="041e", ATTR{idProduct}=="4132", SYMLINK+="libmtp-%k", MODE="666"
# Creative ZEN Sleek (MTP mode)
ATTR{idVendor}=="041e", ATTR{idProduct}=="4137", SYMLINK+="libmtp-%k", MODE="666"
# Creative ZEN MicroPhoto
ATTR{idVendor}=="041e", ATTR{idProduct}=="413c", SYMLINK+="libmtp-%k", MODE="666"
# Creative ZEN Sleek Photo
ATTR{idVendor}=="041e", ATTR{idProduct}=="413d", SYMLINK+="libmtp-%k", MODE="666"
# Creative ZEN Vision:M
ATTR{idVendor}=="041e", ATTR{idProduct}=="413e", SYMLINK+="libmtp-%k", MODE="666"
# Creative ZEN V
ATTR{idVendor}=="041e", ATTR{idProduct}=="4150", SYMLINK+="libmtp-%k", MODE="666"
# Creative ZEN Vision:M (DVP-HD0004)
ATTR{idVendor}=="041e", ATTR{idProduct}=="4151", SYMLINK+="libmtp-%k", MODE="666"
# Creative ZEN V Plus
ATTR{idVendor}=="041e", ATTR{idProduct}=="4152", SYMLINK+="libmtp-%k", MODE="666"
# Creative ZEN Vision W
ATTR{idVendor}=="041e", ATTR{idProduct}=="4153", SYMLINK+="libmtp-%k", MODE="666"
# Creative ZEN
ATTR{idVendor}=="041e", ATTR{idProduct}=="4157", SYMLINK+="libmtp-%k", MODE="666"
# Creative ZEN V 2GB
ATTR{idVendor}=="041e", ATTR{idProduct}=="4158", SYMLINK+="libmtp-%k", MODE="666"
# Creative ZEN Mozaic
ATTR{idVendor}=="041e", ATTR{idProduct}=="4161", SYMLINK+="libmtp-%k", MODE="666"
# Creative ZEN X-Fi
ATTR{idVendor}=="041e", ATTR{idProduct}=="4162", SYMLINK+="libmtp-%k", MODE="666"
# Samsung YP-900
ATTR{idVendor}=="04e8", ATTR{idProduct}=="0409", SYMLINK+="libmtp-%k", MODE="666"

# Rules for another 800 lines or so

GOTO="libmtp_rules_end"

LABEL="libmtp_rules_end"



I copied this file into /etc/udev/rules.d/ on my Mini-Note and hey presto, hotplugging of the Zen! Now it works with Gnomad, and QLix appears to detect it as well.

This may work for you as well. If you want the full rules file send me a PM and I'll e-mail you a copy.

This file may be included in the version of udev in 9.04, which would account for Zen "plug and play" out of the box with 9.04.

---

