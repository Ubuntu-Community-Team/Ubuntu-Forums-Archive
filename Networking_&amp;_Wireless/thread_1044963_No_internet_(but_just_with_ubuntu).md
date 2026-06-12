---
title: "No internet (but just with ubuntu)"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by luckygerbils on 2009-01-19
I can't seem to get internet via either the wired or wireless network from Ubuntu.  The strange thing is that both windows and the live cd work perfectly.  
I'm getting an ip address, but after that the router's log shows no requests for any pages. I can't even connect to the router from ubuntu.

The only thing i can think might be affecting me is that I installed dhcp3-server in attempting to connect with a palm device a few days ago.  But in the interim period (including a few restarts) my internet worked fine.  I removed that in an attempt to fix the problem, but there was no effect.

Any ideas what could be the problem or how to just reset my network configuration to what it was at the install?

Thanks!

---

### Post by gotsanity on 2009-01-20
I am having the same exact issue... Im diggin in the forums for it currently but if anyone has any insight please pass it along. It seems that after my fresh install the network manager takes all of my configuration information but doesnt actually apply it to the network card. I can set it to manual and I still dont get any response from my router.

---

### Post by Iowan on 2009-01-20
Post results of **ifconfig**, **iwconfig**, and contents of /etc/network/interfaces.

---

