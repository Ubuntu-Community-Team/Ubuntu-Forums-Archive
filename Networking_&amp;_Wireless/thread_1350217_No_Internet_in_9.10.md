---
title: "No Internet in 9.10"
date: 2009-12-09
forum: Networking &amp; Wireless
---

### Post by pepsifx357 on 2009-12-09
I seem to be having great difficulties getting the Internet to function in 9.10.  This was a clean install of the 64 bit version.

I have a linksys wireless card in the bottom PCI slot, lspci seems to show it as broadcom 54G, but it will not connect to my static wireless network.

/network/interfaces gives me an autolo loopback and nothing else.

So, since I don't have a wired network, I used my macbook pro to share my internet connection with my Ubuntu.  I used the onboard ethernet, turned it on from the BIOS and booted up.  Same thing.  The IP and DNS are all set correctly and I can look at all of my files on my Macbook pro, but still no internet.  lspci shows the ethernet device.  But /network/interfaces still shows auto lo loopback.  Nothing else.

What do I do?  I'm stuck.

---

### Post by Iowan on 2009-12-09
Unless you specifically edited */etc/network/interfaces*, it will contain only those two lines... that's normal for a Network Manager controlled machine. Under Neetwork Manager, you should have the option (under IPv4 settings) to configure static address.

---

