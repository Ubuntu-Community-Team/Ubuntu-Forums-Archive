---
title: "Mythbuntu duplicate files"
date: 2014-09-03
forum: Mythbuntu
---

### Post by mal4 on 2014-09-03
Hi all, apologies if this was already done, I searched and couldn't find anything.
Backing up my mythbuntu files as a safeguard before doing something dangerous to the system, I came across a folder /var/lib/mythtv/banners/show_names that seems to have everything the same as in the 'recordings' folder, only properly named. They seem to be the same size all the way through. Are these actual duplicates? Can the contents of the recoprdings folder be deleted? Will these survive?
Never noticed these before. Cheers

---

### Post by tgm4883 on 2014-09-04
Those are banners, not recordings. Like this [http://thetvdb.com/banners/graphical/80348-g26.jpg](http://thetvdb.com/banners/graphical/80348-g26.jpg)

---

### Post by diyhouse on 2014-09-04
Not sure what you having going on with you banners folder,.. mine on a 14.04 new build system is emtpy!!  Be careful deleting the contents of your recordings folder as there will be database links to these files, and if you delete the contents of the recordings folder you will be left with just the database references, you will then be forced the use a scripts called find_orphans.py to removed any unused files and unused database references.

Once you have a stable system you should be careful about the integrity of your database as this contains your history of viewed progs that you do not want re-recorded, make sure you have backups of it and you do not do things that will confuse it, and mess it up. The dev. boys ( and girls ) do many checks to ensure the myth database is "good",.. and is available through upgrades, we as users should do our best to look after it as well.

---

### Post by mal4 on 2014-09-04
> **tgm4883 said:**
> Those are banners, not recordings. Like this [http://thetvdb.com/banners/graphical/80348-g26.jpg](http://thetvdb.com/banners/graphical/80348-g26.jpg)
They are video files in there, like I said, the same size as the recordings in the 'recordings' folder

---

### Post by tgm4883 on 2014-09-05
> **mal4 said:**
> They are video files in there, like I said, the same size as the recordings in the 'recordings' folder

Ah ok, when you said they were the same size all the way through I thought you meant everything in that folder was the same size. 

That is rather odd, are you sure that folder isn't a symlink to your recordings folder?

---

