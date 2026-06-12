---
title: "Share FAT Card Over Samba"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by RealG187 on 2009-05-28
I am trying to share my FAT16 formatted card over Samba so I can access it in my Virtual Machine. When I goto the share in the VM I get access denied. I tried both making a symlink to the path where the card is mounted and placing it on my main share (called "Incoming" and located on my desktop on my EXT3 partition) and sharing the card directly.

I might be able to use USB (I think my laptop's card reader is an internal USB device) but there are a few problems with that:
I could only access file on the guest, where sharing it over Samba allows me to access it in multiple VMs and on the host
Making a symlink to the card is the easiest way
In VirtualBox my USB devices menu is empty!

---

### Post by RealG187 on 2009-06-07
bump

---

