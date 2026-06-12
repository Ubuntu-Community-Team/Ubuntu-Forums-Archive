---
title: "Howto use Ndiswrapper instead of Prism54"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by annaeus on 2006-06-04
Hi,

had some problems with my Prism54 based Chipset.
Took me a while to figure out how to disable loading of Prism54, because i wanted to use ndiswrapper instead.

Here is what i did:

open /etc/modprobe.d/blacklist with the Editor of your choice an then insert these Lines:

> 
blacklist prism54
 blacklist islsm_usb
 blacklist islsm_pci
 blacklist islsm_device
 blacklist islsm_pci


I also disabled these, by adding them to the same file, perhaps this isn`t necessary.
> 
blacklist ieee80211softmac
 blacklist ieee80211
 blacklist ieee80221_crypt


After that i added ndiswrapper to /etc/modules  and rebootet.

So i was able to use my Wireless again.

Maybe this helpes someone.

Good Luck

---

### Post by az on 2006-06-04
If this is not on this page, someone should add it there:

[https://wiki.ubuntu.com/WifiDocs](https://wiki.ubuntu.com/WifiDocs)


Anyone can edit the wiki.  That's what its for.  Read the wikiguide for editing ([https://wiki.ubuntu.com/WikiGuide](https://wiki.ubuntu.com/WikiGuide))

---

### Post by jml on 2006-06-04
Here is another good reference.

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

Hope it helps.  If anyone is "listening", this should also be pinned to the top of this sub-forum as well.

Joe

---

### Post by awaldram on 2006-06-05
actually a good quick fix for which is my case is caused by a dodgy kernel.

prism54 on 2.6.16 works fine with my v1 3com card, so your ndis wrapper is a god send and works a treat for dapper

---

