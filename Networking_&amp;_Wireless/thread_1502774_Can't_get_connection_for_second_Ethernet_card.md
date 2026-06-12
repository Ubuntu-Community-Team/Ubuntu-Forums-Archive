---
title: "Can't get connection for second Ethernet card"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by DevilInPgh on 2010-06-06
I'm trying to set up a shared Internet connection that had been broken by a previous update, I believe.  Eth0 is connected to the Internet, whereas eth2 should be the connection going to my Roku set-top box.  Under the nm-applet icon, an entry exists for "Auto eth0" for the first card, but there is nothing under the second card except "disconnected".  How do I make a connection entry under my eth2 card so that I can share my Internet connection with my Roku box?

---

### Post by DevilInPgh on 2010-06-06
Bttt

---

### Post by Iowan on 2010-06-06
The interface (eth2) shows up under **sudo lshw -C network**?  I'm curious what happened to eth1... **ifconfig -a.** probably doesn't show eth2 either.

---

### Post by DevilInPgh on 2010-06-06
Output to lshw -C network is at [http://pastebin.ubuntu.com/445687/](http://pastebin.ubuntu.com/445687/)

Also, somehow the designations are mixed up.  Linksys should be eth0, whereas Accton should be eth2.  I'm not sure how that happened.  Maybe that's part of the problem?

ifconfig -a output is at [http://pastebin.ubuntu.com/445689/](http://pastebin.ubuntu.com/445689/)

---

### Post by Iowan on 2010-06-06
You should be able to create a new interface via Network Manager... although I'm still a bit confused how/why the designations changed. You *might* be able to edit them in */etc/udev/rules.d/70-persistent-net.rules*.

---

### Post by DevilInPgh on 2010-06-06
That didn't help.  Moreover, when I attempted to create a second profile and put the MAC address of the Roku box in the entry, it fails to show up under the nm-applet icon under either card, so there is no way of starting it.  At least I hope I'm right in putting the Roku's MAC address in the connection entry.

---

### Post by wise_crypt on 2010-06-06
type sudo iptables -L and pastebin it please
this link [https://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing) << might also help you to share your connections

---

