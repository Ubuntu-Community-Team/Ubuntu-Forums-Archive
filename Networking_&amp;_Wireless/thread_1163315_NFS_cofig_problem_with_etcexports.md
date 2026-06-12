---
title: "NFS cofig problem with /etc/exports"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by Jeconti on 2009-05-18
I'm trying to let my Myth frontend laptop be able to play the videos from my backend server. I wrote the final entry and based on the error I get, I think it doesn't like that my external label has spaces on it. I'll post my /etc/export and then the error it gives me when I run exportfs

```
/var/lib/mythtv/recordings    *(ro,async,no_root_squash,no_subtree_check)
/var/lib/mythtv/videos    *(ro,async,no_root_squash,no_subtree_check)
/var/lib/mythtv/music    *(ro,async,no_root_squash,no_subtree_check)
/var/lib/mythtv/pictures    *(ro,async,no_root_squash,no_subtree_check)
/var/lib/mythtv/videos    192.168.0.0/24(ro,async,no_root_squash,no_subtree_check)
/var/lib/mythtv/music    192.168.0.0/24(ro,async,no_root_squash,no_subtree_check)
/var/lib/mythtv/pictures    192.168.0.0/24(ro,async,no_root_squash,no_subtree_check)
#User added
/media/Jesse Media Storage    192.168.0.0/24(ro,async,no_root_squash,no_subtree_check)
```

```
exportfs: No options for /media/Jesse Media: suggest Media(sync) to avoid warning
exportfs: /etc/exports [8]: Neither 'subtree_check' or 'no_subtree_check' specified for export "Media:/media/Jesse".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: No options for /media/Jesse Storage: suggest Storage(sync) to avoid warning
exportfs: /etc/exports [8]: Neither 'subtree_check' or 'no_subtree_check' specified for export "Storage:/media/Jesse".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: Storage has non-inet addr
exportfs: Storage has non-inet addr
exportfs: Warning: /media/Jesse does not exist
exportfs: Warning: /media/Jesse does not exist

```

---

