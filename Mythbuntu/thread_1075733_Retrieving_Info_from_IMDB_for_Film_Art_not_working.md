---
title: "Retrieving Info from IMDB for Film Art not working"
date: 2009-02-20
forum: Mythbuntu
---

### Post by DigitalDuality on 2009-02-20
d

---

### Post by korgman on 2009-02-20
Check to make sure that the mythtv user has write access to the directory where it copies the movie posters.  Look at the logs in /var/log/mythtv/  when you try to download the art.  I had this problem and I think I saw the failure in either front or backend logs.  It stores the posters in /home/matt/.mythtv/MythVideo on my system.  It may be different on yours.

---

