---
title: "Lost video metadata after upgrade"
date: 2014-09-22
forum: Mythbuntu
---

### Post by Adam_Jacobs on 2014-09-22
I have just upgraded my elderly Mythbuntu 10.04 system to a newer version. I did this first by upgrading from MythTV 0.23 to MythTV 0.24 on the old system, then I restored my mythconveg database onto a brand new system with Ubuntu 14.04 and MythTV 0.27. I got reassuring messages about upgrading the database at expected places, and certainly details of my TV recordings were all still there as expected.

However, I appear to have lost all my metadata for my videos. None is visible from the front end, and if I look inside the database at the videometadata table, I find it is completely empty.

One thing I've noticed that I suppose could be related is that I've changed the locations of the folders where things are stored. If I look in the upnpmedia table of the database, it has all my videos there, but with the locations of the files in the places they used to be, not where they are now.

Any ideas how I might be able to get my metadata back? I guess one possible workaround would be to download it all again, but I have over 100 videos, and that would be a bit of a faff.

Thanks
Adam

---

