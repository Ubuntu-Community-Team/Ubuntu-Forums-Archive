---
title: "Network drive WITHOUT Samba?"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by ronniestamps on 2010-02-23
How can I make an external USB hard drive accessible (r/w) to my netbook without the use of samba? 

The hard drive is connected to Studio 9.10 and the netbook is running NBR 9.10. I've used samba in the past without any issues with win/lin/mac on the same network. I have all Ubuntu machines now and just need to have my USB hard drive be a network drive for my business.

I've tried just sharing the appropriate folders but samba is needed for that. I can't get samba to work properly for the life of me.

Ubuntu Studio 9.10 (Host w/ usb hard drive)
Ubuntu Netbook Remix 9.10 (Netbook needing to read/write to usb drive on Ubuntu Studio)

Thank you in advance!

---

### Post by johnson.d on 2010-02-23
If you don't want to samba to connect your network drive, you can probably use NFS to share the network drive. The following link can help you setting up NFS server in Ubuntu Studio

[https://help.ubuntu.com/9.10/serverguide/C/network-file-system.html](https://help.ubuntu.com/9.10/serverguide/C/network-file-system.html)

---

