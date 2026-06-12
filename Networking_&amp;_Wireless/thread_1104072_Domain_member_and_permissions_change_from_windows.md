---
title: "Domain member and permissions change from windows"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by ZefQ on 2009-03-23
Hey so I followed this guide [http://ubuntuforums.org/showthread.php?t=280702](http://ubuntuforums.org/showthread.php?t=280702) to make my ubuntu file server member of my domain. and it all worked fine, i can see user and groups with wbinfo, how ever i cant seem to logon to the box with a AD user don't know why.

Another question and really the one that matters. I want to be able to change the file-permissions on shared files from Windows. And if a understand it correct, it is possible. I just have to add ACL to my fstab. but i cant seem to get it to work.

Otherwise it works like a charm. If i try to access the shard files from a computer that isn't on the domain i get prompt for login. If i try to change permissions with an ordinary domain user i get "Access denied", and if a do it with administrative account i can change permissions but it doesn't stick.

Would be grateful for any help on this.

---

### Post by ZefQ on 2009-03-23
update. got the AD login to work at least. still no luck with changeing permissions from Windows thu

---

