---
title: "master backend showing as secondary backend in mythbuntu-control-centre"
date: 2014-09-20
forum: Mythbuntu
---

### Post by chicobiker on 2014-09-20
I have a combined frontend/backend that I used a standard ubuntu install for the backend and frontend.  The backend on this machine is acting as my master backend.  I did not install mythtv-backend-master on it.  Now I have two additional front ends all working fine and I wanted to back up the "master" backend/database.  I downloaded mythbuntu-control-centre as I like to use the backup tool and see that my backend is showing up as a secondary backend and won't let me do a backup (has to be done on the master backend).  I am unsure what will happen if I just tell mythbuntu control centre to install master backend.  Can I install master backend without messing up my existing backend setup?  Thanks for any help.

---

### Post by chicobiker on 2014-09-21
Dug around and found more info on the mythtv-backend-master package and learned it is a package to set up all the other resources that mythtv-backend needs to serve remote frontends as a master.  As far as I can figure, since my system is working fine, I must have installed it at one time then perhaps deleted it.  Not really sure.  In any case I just added it back and since I already had everything it provided I don't think it did anything really.  But more importantly I can now do backups with mythbuntu-control-centre.

---

