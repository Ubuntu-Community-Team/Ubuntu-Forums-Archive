---
title: "Can't connect wireless in 11.10"
date: 2011-10-28
forum: Networking &amp; Wireless
---

### Post by graynada on 2011-10-28
I have tried in both Lubuntu and Xubuntu and I get exactly the same results.

I am unable to connect my wireless after installing 11.10. I am using a USB network device (Addon ADD-NWU272Ev2) and I can see available networks, however the connection is never made and every couple of minutes or so I get an authorisation window open up.

If I install ndiswrapper and load the windows driver I can connect my wireless, until I next reboot, then I go back to the situation above.  sudo modprobe ndiswrapper has no effacet.

If I blacklist the alternate driver (from ndiswrapper -l) on reboot no wireless networks are listed and again modprobe ndiswrapper has no affect.

I am assuming that I have a working driver installed at installation as I can see the available networks.  I have been trying to work through this for about 5 days, and I am on my umpteenth re-install.

Any help would be gratefully received, but please be gentle I have fairly limited Linux knowledge.

---

### Post by graynada on 2011-11-28
I get exactly the same results in Fedora 16 and the new LMDE so basically anything with a kernel 3.0 or greater.  Guess it's a kernel issue then.

---

