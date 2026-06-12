---
title: "Multiple drives question"
date: 2009-09-29
forum: Mythbuntu
---

### Post by rickyble on 2009-09-29
I had originally 2 drives for my backend.  One was a 30g which had the OS and not much else.  I changed all the workings for myth to point to a 250g drive.  I have filled that drive and added a second 250g for more storage.  My problem is this;  Is there anyway to have mythtv point to both drives as storage for video files.  I grab movies and videos from other sources not capture cards.  I want mythtv to be able to see all stored videos on both drives and play then back from mythtvs interface on the frontend.  thanks

---

### Post by ian dobson on 2009-09-29
Hi,

Maybe you could create a symbolic link from the main video directory that points to the second drive.

For example

/var/videos
/var/videos/drive2

you need to use the ln command to "link" the directory /var/videos/drive2 to /mnt/drive2

Regards
Ian Dobson

---

### Post by tgm4883 on 2009-09-29
Look at this

[http://www.mythtv.org/wiki/Mediashares#Multiple_paths](http://www.mythtv.org/wiki/Mediashares#Multiple_paths)

---

### Post by rickyble on 2009-09-29
thanks I ll try the ":"  Looks like exactly I am looking for.

---

