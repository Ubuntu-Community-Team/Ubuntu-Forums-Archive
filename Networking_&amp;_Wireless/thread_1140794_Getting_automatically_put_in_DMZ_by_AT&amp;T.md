---
title: "Getting automatically put in DMZ by AT&amp;T"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by Backharlow on 2009-04-27
I need some speculation everyone.
My Ubuntu has 2 nics. nic 1 connects via dynamic ip to a netgear switch (along with a half-dozen other mixed OS machines). NIC 2 I don't use; it stays "down".

The switch's web interface for administration appears to reside on a cable modem. The setup is AT&T Uverse. This has a feature (variation of DMZ mode?) called DMZplus, in which you can dmz 1 comp from the LAN manually. All standard stuff. However, I do not use DMZ, nor do I want to.

What happens is (once a week?) the admin interface will display a warning message stating that there is a router behind the router, and if I click fix, it will resolve the issue. If I click fix, it dumps my Ubuntu box into DMZ. I do not want Ubuntu dmzed. If I don't click fix, I can't use the rest of the Admin interface, until I do.

Thoughts: Maybe Ubuntu is "advertising" that it is capable of DMZ, or that it would like to be DMZed, because the router is most definitely trying to force Ubuntu into DMZ because of something it detected.

other facts:
I have Apache running on port 80 of Ubuntu.
At one point in time (with a prior router) I forwarded internet from nic 1 to nic 2, but didn't commit any start-up scripts to the OS for that activity, and that was many reboots ago.

Any help would be appreciated.

---

