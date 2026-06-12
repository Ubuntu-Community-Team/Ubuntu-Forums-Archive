---
title: "CIFS VFS: cifs_mount failed w/return code = -13"
date: 2010-11-22
forum: Networking &amp; Wireless
---

### Post by Minex on 2010-11-22
I've finally updated from Hardy to Lucid and I'm trying to mount my NAS without success.  The NAS hasn't changed, and has a wide open samba share I was mounting using smbfs.  Trying to use CIFS under Lucid seems different.
I'm still on the same subnet as the NAS, and the normal network things work fine.  Trying to browse the share as guest had trouble at first:

```
user@Server:~$ smbclient //192.168.0.24/share -o guest
Domain=[VOLUME] OS=[Unix] Server=[Samba 3.0.34]
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
tree connect failed: NT_STATUS_ACCESS_DENIED

```However, switching to security none seems to work:

```
user@Server:~$ smbclient //192.168.0.24/share -o sec=none
Domain=[VOLUME] OS=[Unix] Server=[Samba 3.0.34]
smb: \> quit

```This got me in and I was able to read/write to the share as expected.

But trying to mount the share isn't working:

```
user@Server:~$ sudo mount -t cifs -o sec=none //192.168.0.24/share /nas/share
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```And dmesg is singing the same tale:

```
user@Server:~$ dmesg | tail
[1225702.695303]  CIFS VFS: cifs_mount failed w/return code = -13

```

---

### Post by Minex on 2010-11-22
Never mind.  Wonky setup on the NAS.  For those of you with NETGEAR ReadyNAS having the same troubles, it wants the user the same as the share name.

```
sudo mount -t cifs //192.168.0.24/share /nas/share -o pass=,user=share
```

---

