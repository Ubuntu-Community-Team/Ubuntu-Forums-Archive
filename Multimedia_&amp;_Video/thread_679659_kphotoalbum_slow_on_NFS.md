---
title: "kphotoalbum slow on NFS"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by ocwo92 on 2008-01-27
I want to use kphotoalbum to catalog our photo albums that are accessible from our home server via NFS.

However, when I start kphotoalbum and tell it to use the server's photo album directory, kphotoalbum is incredibly slow. The speed of the NFS share isn't otherwise slow, and kphotoalbum is fast enough when I specify a local directory.

Playing around a bit, it turns out that only the top-level directory, where kphotoalbum stores its database, must be local for full-speed operation. A symbolic link to the NFS share from within the local top-level directory causes kphotoalbum to index those images at a high speed.

I could probably do with this solution, but unfortunately this means that each user must maintain his/her own top-level directory and hence his/her own database. I'd prefer to use the same database across our home, and if only kphotoalbum allows multiple simultaneous users, the only thing that seems to prevent it is kphotoalbum's slowness when I specify an NFS shared directory as the top-level database directory.

Can anyone help me work around this problem?

---

