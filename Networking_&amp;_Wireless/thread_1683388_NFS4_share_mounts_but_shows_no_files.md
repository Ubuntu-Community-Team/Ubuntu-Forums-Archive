---
title: "NFS4: share mounts but shows no files"
date: 2011-02-07
forum: Networking &amp; Wireless
---

### Post by Rubel on 2011-02-07
Hi folks. I'm using Ubuntu 8.04 to share an nfs directory to some 10.04 clients. My intention is to have everything owned by Ubuntu's "backup" user (which should be the same name and uid on both machines, although the directions I followed have it matching just by names via idmapd).

I followed these directions with the exception of using "mount --bind" -- I just stored my share in the /export directory directly. [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

At first, I saw all the files, but they had a very long number as the user and group names/ids, so I realized I didn't have idmapd running correctly. After I restarted it, everything mounted ('df' shows the share as mounted) but now I don't see anything at all under the mount point.

Is this a bug between the versions of NFS in the different releases of Ubuntu, or should I fall back on NFS3, or is it (hopefully) just my misunderstanding the steps?

---

