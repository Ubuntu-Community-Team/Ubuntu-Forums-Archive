---
title: "Playing with your MAC"
date: 2010-10-27
forum: Networking &amp; Wireless
---

### Post by Objekt on 2010-10-27
I just tried the following experiment:

-Turned on access control by MAC address on my wireless N/wired gigabit router.  That is, only MAC addresses on a predefined list would be allowed access to the network.  I have this on all the time, although it's of limited usefulness (see below).
-Connected a netbook running Ubuntu 10.04 to my router by both of its NICs, wireless and wired.
-Changed the MAC on the netbook's wired NIC.  Disconnected its wireless NIC temporarily.

As expected, the router cut off the netbook immediately.

What surprised me was that, when I had the netbook connected by both methods, the wired NIC's MAC address was shown for both IPs.  Is that unique to the way Ubuntu handles networking, or to my router?

It is ridiculously easy to change your NIC's MAC with the NetworkManager applet.  No command-line shenanigans are even necessary.  Controlling access by MAC on your wireless router is clearly no guarantee of anything.  That is one reason I also have its wireless side encrypted & locked down with a strong password.

I am not sure whether this shows a weakness in using MAC addresses for access control, or some quirk of how my router detects MACs.  Possibly it's both.

---

