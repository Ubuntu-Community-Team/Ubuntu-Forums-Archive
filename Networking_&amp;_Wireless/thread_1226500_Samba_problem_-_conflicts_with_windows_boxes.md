---
title: "Samba problem - conflicts with windows boxes"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by elmosim2 on 2009-07-29
Does anyone know of problems that samba can create problems for windows boxes?  We have been getting the "delayed write failed" message (in windows) when users are trying to write to a usb drive sitting on a server.  

The message I received from my boss was as follows:
We need to make sure that none of our Linux boxes are running Samba, because (according to [his colleague]), they force a browser election and can cause problems because they assume control of the network browsing and NetBIOS names. This may be the cause of the “delayed write failed” that [a user] and others are seeing in Outlook from the archive.pst files.

I just wanted to know if there is any truth in this.

Should I go talk to the guys at samba.org?

---

### Post by Iowan on 2009-07-29
I presume they're talking about Samba servers forcing election... The smb.conf file can be configured so the servers don't attempt to enter the master browser election, and they can also be configured to LOSE the election if it does happen. I'll need to look up specifics in my SAMBA UNLEASHED book.

---

