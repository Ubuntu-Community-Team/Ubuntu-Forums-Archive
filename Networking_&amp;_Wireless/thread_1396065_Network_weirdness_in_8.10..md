---
title: "Network weirdness in 8.10."
date: 2010-02-01
forum: Networking &amp; Wireless
---

### Post by Rastus302 on 2010-02-01
OK,
I have ubuntu 8.10 installed on a Dell Poweredge 1850 server.  The install went fine and it seems to be working OK BUT... the network icon in the upper right hand screen has a yellow triangle with an exclamation point in it.  I figured that this meant that there was a network problem but the internet seems to work OK with dhcp and it downloads system updates fine.  I can surf with firefox fine.

Furthermore, when I click on the network Icon, the dropdown list has the ethernet adaptors grayed out.  One says "Wired Network DELL 82541GI Gigabit Ethernet controller" and below it has "Device unmanaged"  the second has "Wired Network DELL DELL 82541GI Gigabit Ethernet controller" and below it has "Auth Ethernet".

My questions   are
1. Why are they grayed out in the dropdown menu?
2. How, then am I able to connect to the ethernet? and
3. How can I fix it?

Suggestions would be very helpful
Thanks

PS  If I click on the "connection Information" in the dropdown menu, I get a dialog message that says "No Valid Active Connections Found"

OK, more info.

When I edited the /etc/network/interfaces I made a static IP as follows:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
address 192.168.100.29
gateway 192.168.100.10
netmask 255.255.255.0
network 192.168.100.0
broadcast 192.168.100.255


It works fine but the menubar icon still has the exclamation point and the ethernet cards are still grayed out in the menu.

Clearly I am missing something.

---

### Post by Iowan on 2010-02-01
The warning message is Network Manager complaining that there are interfaces it doesn't control. The entry in */etc/network/interfaces* is responsible. Your options (maybe not _all_ of them):
1. Ignore the message and revel in a working network.
2. Configure the static address via Network Manager.
3. Disable Network Manager (or remove it completely).
4. Use DHCP (via NM) and configure static lease in DHCP server.

---

### Post by Rastus302 on 2010-02-02
THanks.
For now I will revel.
As long as I can VNC to the static IP life is good.

---

