---
title: "Windbind GIDs maping incorrectly"
date: 2011-08-18
forum: Networking &amp; Wireless
---

### Post by ndberry42 on 2011-08-18
Hi I am dealing with an issue that is somewhat frustrating.  Here is a layout of my environment:

I am using Windows Server 2008 R2 to authenticate using Active Directory putty sessions with winbind for my Ubuntu 10.04 servers.  The problem seems to be that the GID numbers do not map correctly.  When I log in I see this

```

groups: cannot find name for group ID 20009
groups: cannot find name for group ID 20011
groups: cannot find name for group ID 20014
groups: cannot find name for group ID 20016
groups: cannot find name for group ID 20017
groups: cannot find name for group ID 20024
groups: cannot find name for group ID 20027
groups: cannot find name for group ID 20045
```When I use getent group is return this properly:

```
linuxusers:x:20009:[removed list of users]
```but when I run 

```
wbinfo --gid-info=20009
```it is unable to translate the GID to name.  It says:

```
Could not get info for gid 20009

```Some potentially relevant entries from /var/log/samba/log.winbindd

```
winbindd/idmap_tdb.c:623(idmap_tdb_db_init)
  Warning: 'idmap uid' and 'idmap gid' ranges do not agree -- building intersection
```I am thinking that I can fix this by correcting the GIDs in AD and deleting IDMAP's saved settings so it can repopulate with the correct entries.  I am not sure however where that file is located or if that would in fact solve the problem.  If someone could help point me in the right direction it would be appreciated.

---

### Post by luvshines on 2011-08-19
If I understand this correctly, you have Ubuntu server configured to authenticate against Win2008 R2 AD using winbind. Since you say GIDs on AD, you using identity management on 2008 for achieving UID/GID mapping. When you login by ssh using putty you see those error message.
Is my understanding correct ?

If yes, can you share output for following commands```
testparm -s
egrep "winbind" /etc/nsswitch.conf
```

---

