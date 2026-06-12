---
title: "[SOLVED] DWA 130 Wireless on Ubuntu 12.10"
date: 2013-03-12
forum: Networking &amp; Wireless
---

### Post by AveryRe on 2013-03-12
Hello! I am having some issues with my Dlink DWA 130 wireless dongle and Ubuntu 12.10 . I attempted installing the drivers with ndiswrapper but had little to no luck, probably because I am doing so incorrectly or something. I'm not too used to using the command line, previously I had gotten it to work on an older installation using the ndiswrapper gtk, but am unable to do the same procedure on 12.10 properly.

Anyone who could walk me through this, I would greatly appreciate it!

If it helps, here are where the drivers are located: [http://www.dlink.com/ca/en/home-solutions/connect/adapters/dwa-130-wireless-n-usb-adapter](http://www.dlink.com/ca/en/home-solutions/connect/adapters/dwa-130-wireless-n-usb-adapter)

I can provide any information necessary! Thanks!

Avery

---

### Post by AveryRe on 2013-03-13
Fixed it! The solution, just in case someone else has the issue, was to download the tarball for the newest version of ndiswrapper from sourceforge, manually remove the old installation, install the new version and install the drivers as usual.

---

