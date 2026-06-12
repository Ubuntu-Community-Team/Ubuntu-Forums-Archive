---
title: "PPP over serial cable to Windows XP Home"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by ieee488 on 2009-01-01
I have Direct Cable Connection working between Windows XP Home and Windows 2000 PCs so I can move files back and forth.

I wanted to do the same from Ubuntu 8.10 since the Win2k PC also has Ubuntu 8.10. 

Following directions at [http://howto.gumph.org/content/xp-direct-cable-to-linux/]("http://howto.gumph.org/content/xp-direct-cable-to-linux/"), I can get a connection. I can ping the Windows XP Home PC from Ubuntu.

Now I am stuck at how I do I actually move the files.

---

### Post by mpokrywka on 2009-01-01
If you can ping other side, it means network connection is established. If there is network connection then you can use samba. Make network share on Win XP and on Linux open location "smb://this.is.winxp.ip/share_name"

---

### Post by ieee488 on 2009-01-03
Thanks.

I was having problems with samba install and it turns out that there was conflicts with version of samba and that it was trying to use a cached package.

So, Samba is installed and I am ready to give this a try. :D

---

