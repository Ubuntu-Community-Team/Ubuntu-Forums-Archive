---
title: "Need some help setting up Linksys adapter."
date: 2005-12-20
forum: Networking &amp; Wireless
---

### Post by Dural on 2005-12-20
I reconnected a Linksys WUSB11 v 2.5 adapter to a computer that I built over the summer. It is currently running Kubuntu 5.10. I copied the Linksys Linux drivers to the hard drive using Kubuntu, but I am not sure how to install the drivers so while the computer recognizes an adapter connected to the computer, I can not connect to the Internet. What is the easiest way to set up these drivers?

Update: I switched the adapter back to the WUSB11 v 2.8 and when I used lusb, Kubuntu could no longer recognize a device on the computer. After searching through some threads, it seems that to use this adapter with Kubuntu, the atmel wlan firmware has to be installed. However, when I went into Adapt to install this package, the package was not there. I can't figure out whether the repositories are enabled or not, so how can one get the proper firmware for a Linksys WUSB11 v 2.8 network adapter? Any suggestions would be appreciated because I really want to continue using Kubuntu but this will not be possible if I can not connect to the wireless network.

---

### Post by Lambert on 2005-12-20
The driver is in breezy but you need the firmware to make it work which is in the multiverse repos

[http://packages.ubuntu.com/breezy/net/atmel-firmware]("http://packages.ubuntu.com/breezy/net/atmel-firmware")

Make sure your /etc/apt/sources.list has these lines enabled.

deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy universe multiverse

You're going to want to make sure this is an atmel chipset. They switched back and forth with the prism chipset [2.5 prism] [2.6 atmel] [3.0 prism] (not sure about 2.8)

You may want to consider using ndiswrapper and the windows drivers also.

---

### Post by az on 2005-12-20
When you plug in your device, there is a listing in the /var/log/messages that says what module is loaded.  You can tell what chipset you have.

It it is the prism, install the linux-wlan-ng package (it is on the cd.)  It is supposed to work out-of-the-box from that point on (set it up with the networking tool)

If it does not work, join in the bug report:
[http://bugzilla.ubuntu.com/show_bug.cgi?id=15346](http://bugzilla.ubuntu.com/show_bug.cgi?id=15346)

See this to get it working:
[http://ubuntuforums.org/showthread.php?t=102791&highlight=wlanctl-ng](http://ubuntuforums.org/showthread.php?t=102791&highlight=wlanctl-ng)

---

