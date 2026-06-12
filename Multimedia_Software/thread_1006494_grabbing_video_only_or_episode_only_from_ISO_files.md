---
title: "grabbing video only or episode only from ISO files?"
date: 2008-12-09
forum: Multimedia Software
---

### Post by ukulele_ninja on 2008-12-09
I have a large collection of DVD movies and Television shows on my mythbuntu box, but I was curious if it was possible to use the ISO files to pull out only the movie or only the episodes of television shows? This would greatly reduce the amount of space my ISO files take up and allow me to have a lot of additional ISOS on my box. 

If it cant be done, will mythtv's ripper allow me to choose movie or episode only?

---

### Post by IanW on 2008-12-09
Try OGMRip for this. It's in the repos.

You'll have to mount your ISO first as follows:-
```
sudo mkdir /media/mount                  # <--You'll only need to do this for the first one, others can reuse this directory.
sudo mount foo.iso /media/mount -t udf -o loop # <--Where foo.iso is the name of your disc image, use udf for DVD and iso9600 for CD.

```

Then, start OGMRip, and point it at /media/mount when it asks for a disc to rip.

---

### Post by ukulele_ninja on 2008-12-09
and OGMrip will allow me to seperate out the episodes or main film only?

---

### Post by IanW on 2008-12-09
It will let you choose which tracks of a DVD to rip. You'll have to find out which ones are which by trial & error.

---

### Post by ukulele_ninja on 2008-12-09
ok cool Ill try it thanks!

---

### Post by ukulele_ninja on 2008-12-14
I tried this but its not letting me mount the ISO file intitaially, they are all on my external drive now which is mounted properly and I changed the extension to reflect that but its still not mounting them.

---

