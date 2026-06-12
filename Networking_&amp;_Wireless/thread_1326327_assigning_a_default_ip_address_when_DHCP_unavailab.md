---
title: "assigning a default ip address when DHCP unavailable"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by robertbub on 2009-11-14
I would like to define an IP address when it cannot be got automatically via a dhcpd server.

It looks like the way to do this is via dhclient.conf.  But, after looking at the man page, and doing some web searches, it is not obvious how this is done.

In particular, the man page doesn't describe when the leases stanza is consulted.  Is it only after the dhcp timeout has been reached?  Or it is always consulted?  If it's always read and parsed, is there a way to make it as generic as possible such that it first tries its best to use the DHCP before giving up and using a static fixed ip address?

Thanks for any clarification.

---

### Post by Iowan on 2009-11-14
I had something similar set up in Network Manager for awhile. I had "Auto eth0" and a "Manual" connection. I don't remember if I just choose the "Manua"l connection when DHCP failed, or if I had both set to "Connect automatically" and Network Manager ran "Manual" only if "Auto eth0" failed.

---

### Post by driftertx on 2009-11-14
Sounds like you got a bigger problem if your DHCP server randomly doesn't reply...Why not just set a static IP for the connection?

---

### Post by robertbub on 2009-12-25
> **driftertx said:**
> Sounds like you got a bigger problem if your DHCP server randomly doesn't reply...It's possible that the DHCP server will not be running.  I would like the machine in question (a mobile one) to work both with and without a DHCP server.> Why not just set a static IP for the connection?Because if DHCP is available, then I don't wanna muck with the router/computer/whatever to figure out what static addresses would work.

---

### Post by capscrew on 2009-12-25
> **robertbub said:**
> It's possible that the DHCP server will not be running.  I would like the machine in question (a mobile one) to work both with and without a DHCP server.Because if DHCP is available, then I don't wanna muck with the router/computer/whatever to figure out what static addresses would work.

That's what AVAHI is for.  I situations where no DHCP server is found, AVAHI should hand out a 169.254.x.x address.  This should give you internet access only.

See [**_[COLOR="DarkSlateGray"]here [/COLOR]_**]("https://help.ubuntu.com/community/HowToZeroconf")for more information.

---

