---
title: "Troubles while building alsa-driver on UbuntuStudio 12.10..."
date: 2013-04-22
forum: Multimedia Software
---

### Post by Tahiro Hashizume on 2013-04-22
Hi,


I've been trying to self-build the alsa-driver with support for CMI8787-HG2PCI.
The device is built around a CMI8787 chip, but it has the PCI ID of 13f6:ffff - and since this is not listed in "oxygen.c", the device simply isn't recognized by the kernel module. So far, I have figured out that the easiest way out of this is to add a line to the source-code of the installed version, yet the process somehow fails while make-ing. (Screen output is to be posted later.)
Another way out I found is that the latest version of alsa-driver includes the official support for the card - but this too, no luck so far.

It may simply be that I'm not following the standard procedure for updating the alsa-driver (e.g. package-dependency matters), so I'd like to know what I should have ready in the system and what I should do. I have so far installed build-essentials and linux-headers-lowlatency aside from the alsa-driver package.

Thanks.

---

### Post by Yellow Pasque on 2013-04-22
Try a newer kernel....

---

