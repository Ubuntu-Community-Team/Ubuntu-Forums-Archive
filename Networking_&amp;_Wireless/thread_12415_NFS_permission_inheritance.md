---
title: "NFS permission inheritance?"
date: 2005-01-24
forum: Networking &amp; Wireless
---

### Post by Ndlovu on 2005-01-24
I have a Linux server (Ubuntu Warty) and am connecting to it with a Linux laptop (also Ubuntu Warty). I've had some trouble with Samba, and am considering using NFS instead. The problem is one of permissions - if I create a file, is there some way to have that file inherit the group permissions of the parent directory? At the moment if I create a file it only enables read permissions. There will be other users accessing the server, and if they have permissions to access the directory, they also need to be able to write to and execute the file.

Another question about NFS: does it play nicely with Samba? The rest of the users have Windows machines and will be connecting through Samba.

Thanks,
Rudi

---

### Post by nocturn on 2005-01-25
[QUOTE=Ndlovu]
Another question about NFS: does it play nicely with Samba? The rest of the users have Windows machines and will be connecting through Samba.

Thanks,
Rudi[/QUOTE]

Yes, it does (used it like that for years).

---

