---
title: "gnome-keyring-d / nm-applet &quot;Message: secret service operation failed&quot;"
date: 2013-07-20
forum: Networking &amp; Wireless
---

### Post by anocide on 2013-07-20
Hello,

I am having this problem with a 3G dongle that network manager refuses to remember password for. It has been running fine for years and started causing problems today.

Running nm-applet from a terminal gives -

** Message: secret service operation failed: Message did not receive a reply (timeout by message bus)

Seahorse keyring gives the same in a terminal, and "couldn't communicate with keyring daemon" in app window.

The syslog is full of events of this format -

Process: kernel
 [   71.420992] gnome-keyring-d[1973]: segfault at b6112000 ip b7455496 sp bfaa7c04 error 4 in libc-2.11.1.so[b733f000+159000]


Manually killing and restart network manager and gnome-keyring-d do nothing.

This is Lucid 2.6.32-49-generic-pae gnome 2.30.2
gnome-keyring 2.92.92.is.2.30.3-0ubuntu1.1
network-manager 0.8-0ubuntu3.3

There were no system updates that coincided with this, nor any other software added. I am lost - all similar fixes I've seen online do nothing.

---

### Post by mörgæs on 2013-07-20
10.04 is out of support. Better to begin with a fresh install of one of the supported releases.

---

