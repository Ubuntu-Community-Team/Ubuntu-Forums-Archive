---
title: "incredibly slow mythweb on lucid"
date: 2010-05-15
forum: Mythbuntu
---

### Post by jensk on 2010-05-15
I have reinstalled mythbuntu lucid on a new backend. The new sole backend is based on a Shuttle x27D with atom 330 1.6Ghz and 1GB ram. The backend has two disks and two usb tuners. I figured that this should be muscles enough to a backend only machine. Fromtends are on other machines in the house.

I ported the 0.22 database by backup and restore from my earlier backend to the new backend. I have run a db optimize to check and optimize the tables.

I am a bit surprised over the very poor performance of 0.23 on mythweb. Everything from  loading the primary mythweb page takes several minutes. Sometimes the browser times-out before the page is served from the backend.

I have checked the backend and "top" shows plenty of fre CPU ressources. There is a bit of swapping going on but not more than 70MB swap has been used.

Is this a 0.23 issue or is my backend to lame for the new 0.23?

---

### Post by snaef on 2010-09-19
I am having the same issue.  I do not get pages timing out, but queries take at least 3 to 4 times longer than they uses to with previous versions.

Any suggestions?

---

### Post by jensk on 2010-11-03
I have found out what was the cause of this. The cause was that the frontend had a NFS mapping of my NAS drives to the Mythtv recordings directory that the backend used.

Apparently this caused the frontend to be a bit confused about to where to look for the recordings as it could se them both on the nfs mapping and through the mythfs filesystem.

After I removed the frontends NFS mapping from /etc/fstab the delay disappeared.

---

