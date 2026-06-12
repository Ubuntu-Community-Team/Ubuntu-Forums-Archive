---
title: "Ubuntu desktop can't connect to Samba server"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by zoomiest on 2009-08-12
I have a small peer-to-peer network, with two Samba file servers a couple of Windows desktops and a couple of Ubuntu desktops...

My windows (XP) machines see and access the Samba shares just fine... but my Ubuntu desktops can't. I find this weird. Should I be using NFS?

**Background**
Error Messages on Ubuntu Desktop:
"Unable to Mount Location: Failed to retrieve share list from server."

When I use SMB4K, I can see the other computers on the network (network neighborhood), but not the shares...


So, I have kicked this around for a while, and decided I had better ask the community... many thanks, in advance.

---

### Post by superprash2003 on 2009-08-12
try accessing manually via ip like smb://x.x.x.x 
for reference : [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by Iowan on 2009-08-12
See if [this]("http://ubuntuforums.org/showthread.php?t=1169149") helps.  
IIRC, the "Failed to retrieve share list" message relates to firewall.

---

