---
title: "Can mount network drives but can't see files"
date: 2012-02-07
forum: Networking &amp; Wireless
---

### Post by dpsci on 2012-02-07
I'm running Ubuntu 11.10 with all the latest updates.

I have a number of network drives that I would like to mount using nfs.  I added these lines to my /etc/init.d/nis file:

mount -t nfs 192.168.230.201:/home /networkhome
chmod u+s /networkhome

if I use a console and type "df" I can see the hard drive mounted on /networkhome, however I can't see any files in the directory.  I think this is some kind of networking or permissions error, so I came to you guys.  

What am I doing wrong?  Thanks in advance :KS

---

