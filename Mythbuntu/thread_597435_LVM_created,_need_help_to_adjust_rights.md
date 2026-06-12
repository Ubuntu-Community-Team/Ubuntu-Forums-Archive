---
title: "LVM created, need help to adjust rights"
date: 2007-10-30
forum: Mythbuntu
---

### Post by tringwelski on 2007-10-30
Just successfully create my LVM for my MYTHStorage, I have mythtv pointing to /storage/recordings, /storage/videos, /storage/music, /storage/mytharchive.  I can successfully copy files as sudo -i, but when i login as my mythuser, i get permission denied.  

so my mythbackend can not write files either which cause a startup problem.

Thx in advance for your help!

Ringo

---

### Post by superm1 on 2007-10-30
> **tringwelski said:**
> Just successfully create my LVM for my MYTHStorage, I have mythtv pointing to /storage/recordings, /storage/videos, /storage/music, /storage/mytharchive.  I can successfully copy files as sudo -i, but when i login as my mythuser, i get permission denied.  

so my mythbackend can not write files either which cause a startup problem.

Thx in advance for your help!

Ringo
Chown it to mythtv:mythtv (the user allows the user mythbackend runs as to write to the directory) (the group allows your user to read it since its in the mythtv group)

I would also recommend that you made the normal directories in /var/lib to be symlinks to your alternate directories.  Samba, NFS, and mythweb are dependent on using the original directory locations and you would have to manually update.

---

