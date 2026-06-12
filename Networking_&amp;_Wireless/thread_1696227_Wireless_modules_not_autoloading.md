---
title: "Wireless modules not autoloading"
date: 2011-02-27
forum: Networking &amp; Wireless
---

### Post by phillips321 on 2011-02-27
I'm the lead dev of GnackTrack and we are having a few issues with wireless cards.

We have manually compiled the compat-wireless modules and added a few patches for various things such as monitor mode, packet injection, etc.

Now when a user boots GnackTrack even though their wifi card is shown under lspci (or lsusb) they still have to manually load the module with modprobe.

How can we ensure that when specific hardware is detected the correct driver module is loaded?

I know i can just add all the modules to /etc/modules but then all of the modules will be in memory even if only one wireless card is on the box.

Thanks in advance

---

