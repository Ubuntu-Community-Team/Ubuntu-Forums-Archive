---
title: "Where is the proper location to have Samba shares?"
date: 2009-03-17
forum: Networking &amp; Wireless
---

### Post by Sootah on 2009-03-17
I have a small server that I'm setting up that will server a few roles, one of which is to act as a fileserver over the network via Samba. Where is best, or "proper" location for me to create the share folders? I'd be creating a folder called "samba" and then making the individual share folders reside within there.

/home/samba?
/samba?
/somewhereelse/samba?

Also, is there any special consideration I should give as to what user owns the folders? Forgive the novice questions, I'm new to Linux.



Thanks in advance,

-Sootah

---

### Post by lykwydchykyn on 2009-03-17
If you want to stick to the [FHS](http://www.pathname.com/fhs/), I believe the proper place would be /srv/samba.

> 
/srv : Data for services provided by this system
Purpose

/srv contains site-specific data which is served by this system.

Tip	Rationale
 	

This main purpose of specifying this is so that users may find the location of the data files for particular service, and so that services which require a single tree for readonly data, writable data and scripts (such as cgi scripts) can be reasonably placed. Data that is only of interest to a specific user should go in that users' home directory.

The methodology used to name subdirectories of /srv is unspecified as there is currently no consensus on how this should be done. One method for structuring data under /srv is by protocol, eg. ftp, rsync, www, and cvs. On large systems it can be useful to structure /srv by administrative context, such as /srv/physics/www, /srv/compsci/cvs, etc. This setup will differ from host to host. Therefore, no program should rely on a specific subdirectory structure of /srv existing or data necessarily being stored in /srv. However /srv should always exist on FHS compliant systems and should be used as the default location for such data.

Distributions must take care not to remove locally placed files in these directories without administrator permission.

Of course, it'll work anywhere.  Before I knew about the FHS, I used to create a directory called /data or /shares, or use /home/shared (so I only had to back up /home).

---

### Post by inobe on 2009-03-17
[https://help.ubuntu.com/8.10/internet/C/networking-shares.html](https://help.ubuntu.com/8.10/internet/C/networking-shares.html)

scroll down and check shared folder via nautilus, samba setup is almost effortless and allows you to point to the folder.

---

