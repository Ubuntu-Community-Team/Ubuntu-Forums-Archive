---
title: "Wireless Adapter (ipw2200) ate itself"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by seishinbyou on 2006-06-06
Greetings.  I've always had a heck of a time with wireless adapters.  Breezy was fine, but since I upgraded to 6.06, my laptop (NEC Lavie LN500/C) can not find my wireless adapter.

Under Breezy, my wireless was eth0 by default and the built-in ethernet controller was eth1.  Under Dapper, my ethernet adapter became eth0, and my wireless is nowhere to be found.  I am still sure the system is at least partially aware of it, as when I turn it off/on and do a dmesg, the last lines are:

[4298936.969000] usb 3-1: USB disconnect, address 2
[4298937.885000] usb 3-1: new full speed USB device using uhci_hcd and address 3

I have been googling and browsing through these forums and trying to follow instructions on installing the driver and other means to detect my wireless adapter, but nothing seems to work.

I have experience with Linux in general, but I am by no means any sort of expert, so I have to ask for very clear instructions on what I can try.

This is a semi-surviveable catastrophe, as I have some way to connect to the network at the office, but since I am always on the run, not having wireless is a large inconvenience.

Apart from this, and an Intel 855GM problem with Direct Rendering in Dapper (no problem in Breezy), and no sound, everything else is working fine in Dapper, though.

---

