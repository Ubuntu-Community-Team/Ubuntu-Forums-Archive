---
title: "DB fixes after reinstall"
date: 2011-07-01
forum: Mythbuntu
---

### Post by extasy on 2011-07-01
My backend died!

So I got a new computer and made a reinstall, I had the db from the old system backed up, and also I was able to save most of my recordings, however not all. So when Putting it in the new system I have alot of recordings that is either missing or do not have a thumbnail.

Does anyone know of a script that can correct these problems, check the storrage groups for files and remove the empty entries in the db and fix thumbnails for missing files?

Kind regards

---

### Post by klc5555 on 2011-07-01
Depends on what version of myth you're running. Up to about 0.23 you should be able to fix much of this with myth.find_orphans.pl in the /contrib directory. This has been removed in 0.24 and replaced with find_orphans.py, about which you can read here: [http://www.mythtv.org/wiki/Find_orphans.py](http://www.mythtv.org/wiki/Find_orphans.py) 

I've not personally ever used this latter script and can't vouch for it. According to its description it does seem to include some of the functionality of the earlier script.

---

