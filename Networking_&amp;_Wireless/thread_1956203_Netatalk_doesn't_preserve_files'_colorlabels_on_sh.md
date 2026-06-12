---
title: "Netatalk doesn't preserve files' colorlabels on shared HFSplus drive"
date: 2012-04-10
forum: Networking &amp; Wireless
---

### Post by kaspar128 on 2012-04-10
I have a 1 Tb usb-drive with work on it. It is formatted as hfs+ and used by Mac-osx(10.6)users. Lots of files and folders on it are "color-labeled". 

I want to mount the drive(hfsplus-format) on my ubuntu server(lucid) and share it with netatalk(so that mac-users can have acces to it).
But when I connect to it from my MacbookPro, I don't see any colorlabels.. I can create new ones which are persistent when I reconnect.
When I dismount the drive from the server and remount it on my MacbookPro, I don't see the ones created through the network but the previously ~locally~ created labels re-appear.

I found out that the colorlable information is stored in the hidden ".AppleDouble"-directory.
On the netatalk homepage I read:
> ..AppleDouble file of Mac OS X 10.6 is incompatible to V1 and V2.


So it is likely that colorlabeling won't be possible via netatalk for us.. Is it possible with something else? Samba sharing perhaps?
Or sharing a dmg-volume?

---

