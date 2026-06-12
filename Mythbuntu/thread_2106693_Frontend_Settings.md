---
title: "Frontend Settings"
date: 2013-01-19
forum: Mythbuntu
---

### Post by jlp_engineer on 2013-01-19
I know that the FE settings are stored in the MySQL database on the backend server.  If I change the hostname of my frontend, how can I recover all the settings, or am I just screwed, and have to do them all over again?  :-(

---

### Post by nickrout on 2013-01-21
You can change the hostname quite easily using mysql.

The settings table has 3 fields, value, data and hostname. Something like 

UPDATE settings SET hostname = "newhostname" WHERE hostname = "oldhostname"; 

(That will destroy the oldhostname entries)


Although my mysql-fu is crap - for heavens sake back it up!

Similarly it would be posible to duplicate oldhostname to newhostname if you wanted to keep the oldhostname settings in the db.


Also there are playback settings in displayprofilegroups which are also set by hostname.

---

