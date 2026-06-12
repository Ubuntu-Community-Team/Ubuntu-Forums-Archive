---
title: "gigolo sftp applies /etc/group to remote server view"
date: 2012-07-11
forum: Networking &amp; Wireless
---

### Post by Travisher on 2012-07-11
Using Xubuntu 12.04.
Set up bookmarks for sftp to a remote server.

I can navigate the remote volume, I can write a new file into a directory on the remote volume. I can delete files owned by another user in the same server based group.

I can't do anything to any file previously placed on the remote volume using gigolo from within gigolo.

When I right click on a file I placed on the server yesterday, and look at the permissions as displayed in gigolo, they are greyed out. 

I notice that the owner is identified by name. A name that does not exist on the remote server, nor does the local computer have the ability to extract that information. What seems to be happening is that gigolo or something connected with it is looking in the local /etc/group and picking the nearest userID/name to the userID number reported by sftp.

e.g. the local /etc/group has the user 'Ann' with the userID 1000 and another  'backuppc' with a userID 1001. Gigolo seems to be interpreting ID 10010 on the server as 'backuppc'.

What else can I tell you... backuppc is an account that has no local login and is only used by backuppc to rsync from a backup server. But I suspect that is irrelevant. What seems to be relevant is that gigolo is applying local /etc/group to remote volumes - which it should not do. Under Unity/ubuntu 12.04 the same bookmarked volume correctly reports  the files as owner 10010 group 1001.

I checked that other folks running Xubuntu are seeing the same thing and indeed they are.
Any workaround or ideas gratefully received.

---

