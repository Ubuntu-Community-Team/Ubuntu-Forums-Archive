---
title: "Wired net not resolving names"
date: 2011-06-06
forum: Networking &amp; Wireless
---

### Post by GScully on 2011-06-06
I'm on 11.04 on VMware 4.1, trying to get name resolution working. I can ping by IP other systems including on the internet. The network manager Icon on top shows a wireless icon, but the 'Wired Network' is grayed out and below that says 'device not managed'. What can I do to fix this? The interfaces file has the auto lo, then below that 
iface eth0 inet static
 stuff...
It doesn't work with or without the auto eth0 entries.

I have the nic set to DHCP and on my dhcp server gave it the mac address of the box to assign it an address, that is working.

This was working until today, I had the system off for about a week.

---

### Post by Iowan on 2011-06-06
Try commenting out the definition for eth0 in */etc/network/interfaces* and restart networking. NM and "interfaces" don't always play nicely together.

---

### Post by GScully on 2011-06-07
That didn't seem to help. When I go to the Ping Tab on the network app ping fails yet ping works from the terminal. I'd guess something about network tools is broken?

---

