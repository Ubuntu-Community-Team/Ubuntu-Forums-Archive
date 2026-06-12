---
title: "No wired/wireless internet Connectivity | Ubuntu 10.04"
date: 2011-03-06
forum: Networking &amp; Wireless
---

### Post by deceaseddolphin on 2011-03-06
Hi,

I've upgraded Ubuntu today where the upgrade removed my network-manager and now I'm struggling to install a suitable network-manager.

I tried different solutions to fix internet but none suits my problem. Wireless notifications would not appear on the panel. I tried enabling it by right-clicking but no success. Network manager would neither appear in the panel nor in the system -> preferences tabs!

You can see the boot screen errors [here]("http://ideasandbeyond.blogspot.com/2011/03/ubuntu-boot-error.html").

P.S: I do not intend to fill this forum with redundant information but would like to fix this issue ASAP!


I posted a [thread]("http://ubuntuforums.org/showthread.php?t=1701625") in Installations and Upgrades. I'm hopeful of a response here.

Edit:

I included couple of lines in /etc/network/interfaces

auto eth0
iface eth0 inet dhcp


then wired internet started working. then i installed WICD package for handling wireless internet, restarted.... now its working as well!

---

