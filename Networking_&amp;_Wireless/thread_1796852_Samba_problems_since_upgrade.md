---
title: "Samba problems since upgrade"
date: 2011-07-04
forum: Networking &amp; Wireless
---

### Post by scorpiosun on 2011-07-04
Hi all, first-time post here, I haven't found a solution to this one that actually works.

Basically when I had 9.10 I right-clicked on a directory from Nautilus and shared it, and this installed a bunch of Samba stuff. This then allowed me to add a printer which is connected to my dad's Windows XP machine, using the old favourite "Windows printer via Samba" -> Browse option.

When I installed 10.04, and more recently Ubuntu Studio 11.04, nothing I try will let me access anything on the XP machine. We're in the same workgroup, and I can see the computer itself, but not access anything on it. Nothing on the XP machine has changed, so this is obviously an Ubuntu problem. (To clarify, I did not upgrade my Ubuntu versions from one to the next, I did a clean re-install both times.)

When I type "smbclient -L <computer-name> -N" into the terminal it just says "Error returning browse list: NT_STATUS_OK" and neither Nautilus nor the Add Printer dialog can access anything on it.

I've tried all manner of suggestions like installing winbind, editing smb.conf & nsswitch.conf, but nothing makes the slightest difference. I just can't figure out why something that worked out of the box on one version suddenly won't work at all on another. It's been about 7 years since I dabbled under the hood of Linux so go easy on me!

---

