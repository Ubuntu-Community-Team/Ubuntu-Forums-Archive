---
title: "Rhythmbox cannot access files on samba-share"
date: 2008-06-15
forum: Multimedia Software
---

### Post by melhor on 2008-06-15
Hi!

Some days ago i bought a NAS-Storage for backing-up my files (zyxel-NSA220). Because i found it very attractive storing all my data on a Raid1-System, i also put my music on that storage.
I mounted the samba-share to the directory /home/peter/Musik/NSA (where /home/peter/Musik is the rhythmbox library path) with the following entry in /etc/fstab:
```
//storage/music /home/peter/Musik/NSA/ smbfs user,defaults,locale=de_AT.UTF-8,credentials=/home/peter/.smbcredentials/.peter 0 1
```
After starting rhythmbox again it started scanning my storage as expected. But it did not add all of my music to the library, but only those songs which did not have any spaces in the filenames or paths.
I tried it with banshee ... and it worked. But i prefer rhythmbox :), despite banshee does not update my library continually and i love that.

Any Ideas?

---

