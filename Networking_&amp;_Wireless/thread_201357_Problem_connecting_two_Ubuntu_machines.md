---
title: "Problem connecting two Ubuntu machines"
date: 2006-06-21
forum: Networking &amp; Wireless
---

### Post by cakeinablender on 2006-06-21
I'm not that much of a newbie but try as I might, I fail at networking.  I'm using a D-Link DI-524 router and cannot connect two Ubuntu systems even with ethernet cables.  When one of the systems was running Windows I had a shared folder which I accessed through Samba.  Now that they are both Ubuntu, I cannot use Samba and have no idea how to use NFS.  Can someone tell me how to make Samba work, or perhaps how to use NFS?  Any help is very much appreciated.

---

### Post by aarbear26 on 2006-06-21
I can't say that this will help much, but i have had a similar problem.  I found that ubuntu can read shares very well but it has this thing with not opening any shares when it's in it's basic form.  If you go to system > administration > shared folders, and then choose a share for each one of your systems, it should detect it between the two computers.  Then just go to places > network servers, and find the shares by computer name, and then share name.  Hope that helps!

---

### Post by cakeinablender on 2006-06-21
I appreciate you responding, but unfortunately that's my issue.  I cannot get my systems to recognize the other's shared folder, even throught Samba.  Unless you're saying that I need to have a shared folder for both at the same time?  I'll actually try that and see if it works.

EDIT: Still didn't work! This is really frustrating!

---

### Post by aarbear26 on 2006-06-30
just in case you haven't gotten it yet, I've been playing around and found out that if you enable folder browsing and make sure your on the same workgroup, it works fine, mine is up and running

---

