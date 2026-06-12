---
title: "Mythmusic files on frontend only"
date: 2009-05-16
forum: Mythbuntu
---

### Post by iitywygms on 2009-05-16
So I have moved from a combined frontend/backend setup to a separate frontend  and backend.  My question is, can mythmusic stream my mp3 files from the backend, or do I need to have those files on the frontend machine I want to play them using mythmusic?
Same question with videos, do they have to be on the frontend machine I want to view them on, or can they be streamed from the backend machine using mythvideo?
If they can, where are the setup directions?  I can't figure out a way in mythmusic setup to point to the directory on my backend machine.
Thanks.

---

### Post by crez79 on 2009-05-17
You need to have the files mounted in the same spot on all frontends to play both music and videos. I believe it sets up the default locations to be shared, but I don't remember as I don't use the default locations.

The easiest way I have found is to have a folder dedicated to shared content, similar to what the default structure is. That way you aren't chasing around a bunch of different folder locations.

---

### Post by iitywygms on 2009-05-18
Fixed.  I did it by creating a nfs share using this guide.
Thanks to all.
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

---

