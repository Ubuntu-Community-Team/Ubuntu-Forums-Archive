---
title: "Problem changing hostname"
date: 2014-07-02
forum: Mythbuntu
---

### Post by lordviperz on 2014-07-02
I just recently setup a new system and restored the database from my old system. The old system is running Mythbuntu 10.10, the new system is 14.04. The database imported without errors but since I was going to run both systems until I finish the new system and test it, I had to change the hostname in the imported database to the new system's hostname. So when I run the restore script with the hostname argument I get the following output. 

Unable to update hostname in table: displayprofilegroups
Duplicate entry 'High Quality-MythTV-2' for key 'PRIMARY'
Unable to update hostname in table: housekeeping
Duplicate entry 'JobQueueRecover-MythTV-2' for key 'task'
Unable to update hostname in table: jumppoints
Duplicate entry 'Reload Theme-MythTV-2' for key 'PRIMARY'
Unable to update hostname in table: keybindings
Duplicate entry 'TV Frontend-TOGGLERECORD-MythTV-2' for key 'PRIMARY'
Unable to update hostname in table: storagegroup
Duplicate entry 'Banners-MythTV-2-/var/lib/mythtv/banners/' for key 'grouphostdir'


The system seems to function fine for recordings and live tv, but half of the videos I have copied over are missing their coverart and information. When I try to retrieve the info I get an error message saying it couldn't retrieve the details and mentioned the old system's hostname. Anyone have any ideas?

---

### Post by lordviperz on 2014-07-02
This is because I ran both the backend and frontend after importing the database before I updated the hostname. So I fixed it by starting over and updating the hostname before I started things. Live and learn I guess.

---

