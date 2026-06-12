---
title: "What Am I Doing Wrong?  Trying to share a mounted drive through NFS."
date: 2011-12-27
forum: Networking &amp; Wireless
---

### Post by marinara on 2011-12-27
I put a couple of old NTFS formatted drives in my ubuntu 10.04 box.

fixed /etc/ftab like this:
/dev/sdb1 /media/oxidation ntfs-3g defaults,user,locale=en_US.utf8 0 0

and mounted the /media directory onto an /exports/share directory 
and connected my client machine to the NFS share.

I see all subdirectories on the client, except for the NTFS drives.
the NTFS drives appear empty, whereas other directories are populated (viewing from the client)


I've noticed that the NTFS drives are mounted with root/root as the owner.  Is this the problem?

---

### Post by marinara on 2011-12-30
I added each filesystem in /media
to my /etc/exports

then restarted nfs and did an exportfs -ra
then unmounted on the client.

and it works now

---

