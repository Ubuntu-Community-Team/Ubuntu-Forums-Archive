---
title: "no eth0, or anything else there"
date: 2009-10-12
forum: Networking &amp; Wireless
---

### Post by Snake707 on 2009-10-12
Ok,

hi ... I think my problem could prove as difficult. Since I do not really know if it is a real kubuntu. Problem: I got interested in LXDE, since KDE 4.3 was very bugy.  So I tried it and was surprised. So I tried to install LXNM the LXDE Network Manager. In order to do this, synaptic removed gnome-network-manager, network-manager and some other packages I don't remember. The result of it: I have no network. Everything despite lo is killed. But I have the ubuntu CD and use it as a Live CD, where I have a network connection. I also tried to add it to my sources. But network-manager and gnome-network-manager aren't available there. So I assume it has nothing to do with them. So I think I need help to get my System working again.

System: I started with XUbuntu 8.04 and installed KUbuntu 9.04, but I think most of the XUbuntu packages are still there.

sincerely

Snake707

---

### Post by Iowan on 2009-10-12
What direction would you like to go? There's [masonux]("http://sites.google.com/site/masonux/") that claims to use standard NM with LXDE.

---

### Post by Snake707 on 2009-10-12
Hi,

I stepped back. So I manually removed lxnm and manually reinstalled the deb packages of dhcdbd, libdbus-1-2, libnm-util1, network-manager and network-manager-gnome with dpkg.

I do not think, this was a good solution, since I never got lxnm working (ok besides that, the lxmn's man page is horribly useless).

I will mark this thread as solved.

Thank you anyways :)

---

