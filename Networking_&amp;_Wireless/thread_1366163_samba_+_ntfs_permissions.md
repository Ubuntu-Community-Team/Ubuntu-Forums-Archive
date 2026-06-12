---
title: "samba + ntfs permissions"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by ivago on 2009-12-28
Hi,

I've got a dual boot system with Karmic (x64) and Windows 7
I'm sharing my data on /mnt/data wich is a ntfs partition, I can r/w perfect as user or root, but with samba it's anotehr story.

I have shared a couple dirs from /mnt/data with my music and videos but once I've done that I can't browse my workgroup no more in Windows or from my XBMC/XBOX. Even if I put in smb.conf to make it visible and browseabel it doesn't show up.
When I share only my /tmp folder (ext4) my workgroup is browsabel again.
When I use OSX I can see my samba server and when I put in my ubuntu's l/p I can see the sahares.Also when I connect with my XBMC with this command I can see my shared data
[code]smb://ivago:mypassword@TACO/Downloads/Podcasts[
/code]

So basically how do edit my /etc/fstab so my ntfs partition gets mounted with the right permissions so I can browse my workgroup and easily connect from any client without a l/p?

---

