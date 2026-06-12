---
title: "Permission problem with smb mount"
date: 2009-03-16
forum: Networking &amp; Wireless
---

### Post by rmessier on 2009-03-16
Hi folks,

I'm trying to mount a remote smb share on a local machine with permissions to rwx------ (700), as seen by local file system. The mount itself succeeds without obvious error, but it won't set the required access (always falls back to 777 instead of 700).

Adding a umask=700 parameter to the corresponding line in /etc/fstab doesn't work:

//192.168.0.20/postgres /mnt/postgres smbfs credentials=/etc/.credentials,uid=postgres,umask=700 0 0

I am missing something about how smb mounts work?

If anyhow relevant, my final goal is to set up a PostgreSQL server on the local machine (sbm client) intended to access a remote database hosted on a NAS (the smb share). PostgreSQL's server requires that the data folder's permissions be 700.

Thanks in advance for any hints,

Raphaël

---

