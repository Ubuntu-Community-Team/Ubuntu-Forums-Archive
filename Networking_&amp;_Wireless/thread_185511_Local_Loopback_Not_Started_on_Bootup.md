---
title: "Local Loopback Not Started on Bootup"
date: 2006-05-31
forum: Networking &amp; Wireless
---

### Post by rschlack on 2006-05-31
I can't get my local loopback started automatically when booting up.  This causes extreamly long login times with gnome and some programs will not run.  I often have to switch over to a text session or launch xterm and do a "sudo ifconfig lo up" to get things moving.

Is there any way to fix this?  My /etc/network/interfaces file has "auto lo" in it.

Thanks in advance for the help.

---

### Post by mlitteken on 2007-07-20
I have the same problem, "sudo ifconfig lo up" works to get the local loopback going, but otherwise it isn't there. The "auto lo" in my /etc/network/interfaces file is present.

Does anyone have any thoughts to either make it load properly or to automate running "sudo ifconfig lo up" every time?

I'm running Ubuntu 7.04, and have used ndiswrapper to make my wireless Netgear WPN111 work, which it does. However, and this may be a part of the problem, when I try to view my network settings using System, Administration, Network a window appears, but never fills in, and just hangs.

Here is the result of cat /etc/network/interfaces
[quote=/etc/network/interfaces]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

# iface eth0 inet static

auto wlan0
iface inet dhcp
wireless-essid DILLPICKLE
wireless-mode managed
wireless-channel 9[/quote]


Thanks a bunch for any help.
-Matthaus

---

