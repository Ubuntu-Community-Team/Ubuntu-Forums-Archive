---
title: "NFS + Samba + XP across Internet"
date: 2011-12-01
forum: Networking &amp; Wireless
---

### Post by chrislynch8 on 2011-12-01
Hi,

I've a central Ubuntu Server 10.04LTS, I have a shared folder on on this called central. I am using NFS to share this folder to all my remote Servers over my VPN.

In remote offices we have Users connecting to their local server using Sambs to connect to local Shares and to this central share.

In Windows when a user accesses the central share I can see using TCPDUMP the NFS traffic coming to my central server the getattr requests & reply - one each per folder. Depending on hte number of folders in the folder they open there may be alot of traffic and the shares where very very very slow.

What I have done so far is break the folders into lots of smaller sub folders, and increase the actimeo option in NFS to hold the cache for longer. So if I access the NFS share via commond line when logged into the server via putty, NFS is much faster now as it is issuing the gettattr for less folder as I cd into them.

But in XP when I roll the mouse over a folder it seems that it want to scan all the subdirectories and files and causes more delays from a users point of view. Does anyone here know if there is a setting in NFS to only scan directories in the folder only when access is requested, or a setting in XP that will not scan all sub, sub-sub, sub-sub-sub directories by default.

Rgds
Chris

---

### Post by praseodym on 2011-12-01
Hi,

in heterogeneous environments NFS doesnt work (properly). Install samba on your server, too.

---

### Post by chrislynch8 on 2011-12-02
I have samab installed also, I have alot of setting on XP now that have improved the performance but this is the actual issue I am see now. Look like its around awhile, anyone know of a fix for this

[http://lists.samba.org/archive/samba-technical/2009-April/064369.html](http://lists.samba.org/archive/samba-technical/2009-April/064369.html)

When I hover over a Folder I am seeing this type of packet over and over again a few hundred times
1416	130.799781	192.168.131.65	192.168.1.240	SMB	258	NT Create AndX Request, Path: \www\service:{4c8cc155-6c1e-11d1-8e41-00c04fb9386d}:$DATA

Any idea what eactly it is looking for?


Rgds
Chris

---

