---
title: "locked folder after copying from DVD"
date: 2008-10-22
forum: Multimedia Software
---

### Post by adept_king on 2008-10-22
Every other time I drag a folder of, say, mp3's from a DVD to my Linux installation, the folder arrives locked and i don't have the permission to alter or delete that folder or any of the files within.

this must relate to the fact that a DVD is not usually writeable, and therefore files copied verbatim from the disc will carry the same permissions.  It is a shame that linux does not distinguish between files being copied from read only media to the desktop.

is there a simple script that could be added to Ubuntu to prevent this from ever happening again?  is there a way for Ubuntu to know the difference between an .iso and a hard drive?  

I tried chowning and chmodding but accidentally screwed the permissions for my whole machine due to an error in my code.  Things like this wouldnt happen if a few lines of code were there to prevent files dropped from a cd from arriving locked, and if linux asked if you "really want to alter all your permissions" before you accidentally sudo chmod sudo itself. or before you delete your hard drive while it was in use... stupid stuff like that.

how hard would it be to fix this kind of annoying and obvious stuff?

---

