---
title: "Mythweb Videos not shown"
date: 2010-06-02
forum: Mythbuntu
---

### Post by skytte on 2010-06-02
Videos in mythweb are not showed but i can see the directory tree. 
Tried to change permissions to 777 on files , checked that the video startup directory is set correct. Rescanning from frontend and mythweb no lucky change.

---

### Post by goffa72 on 2010-06-04
I had a similar problem with Mythtv 0.23 that was solved by creating storage group for my videos, coverart etc from the backend setup and deleting the paths to videos, coverart etc in the frontend setup. I think I read somewhere that mythweb is only compatible with storage groups now.

---

