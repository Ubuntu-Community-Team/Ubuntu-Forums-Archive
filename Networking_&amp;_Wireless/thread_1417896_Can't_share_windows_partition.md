---
title: "Can't share windows partition"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by rocklee on 2010-02-27
Hi folks,

I managed to share local folders in my ubuntu partition using samba with these commands :

 sudo cp /usr/bin/testparm.samba3 /usr/bin/testparm

sudo cp /usr/bin/net.samba3 /usr/bin/net

sudo chmod +x /usr/bin/testparm /usr/bin/net

I can access my windows partition (sda2) which mounts automatically using fstab :

nls=iso8859-1,orwx,umask=002

I do this to share my HTDOCS with my web servers.

The problem that I'm having is that I can share this windows partition via samba, as it gives me a "Could not change the permissions of folder "sda2".

What can I do to make sda2 accessible via my local network?

---

