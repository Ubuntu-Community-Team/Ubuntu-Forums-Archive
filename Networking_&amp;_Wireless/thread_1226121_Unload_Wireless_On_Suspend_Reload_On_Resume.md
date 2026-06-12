---
title: "Unload Wireless On Suspend Reload On Resume"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by redilyn on 2009-07-29
Hi,

When I put my eeepc to sleep and then resume I can not connect to the wireless network.

After resume, I can unload then reload the ath_pci driver and wireless works again.

What I would like to do is setup a script to unload and reload the driver  on resume.

so far I have been able to unload the driver on resume but I can't seem to get it to reload.

I have added "modprobe -r ath_pci" to 72-acpi-pain.sh which unloads the module.

How can i get it to reload once the desktop has loaded?

---

