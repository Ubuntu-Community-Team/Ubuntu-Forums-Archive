---
title: "MythTV ATSC help"
date: 2008-08-17
forum: Multimedia Software
---

### Post by newman on 2008-08-17
There was a setting in previous version of MythTV for "ATSCCheckSignalThreshold" in Settings>>General, but this option is no longer there in the current version. How can I change this setting? The default is 65 and I need to lower it or I can't pick up the weaker signal stations.
thanks

---

### Post by newman on 2008-08-18
shameless bump ^^^

---

### Post by NT4usB on 2008-08-18
If the setting is still valid, edit it directly in the mysql DB.

---

### Post by newman on 2008-08-18
> **NT4usB said:**
> If the setting is still valid, edit it directly in the mysql DB.

How do  I do that?
thanks

---

### Post by NT4usB on 2008-08-19
Use phpmyadmin to edit the tables in Firefox.
Probably the channels table you're after.
Be ware you can wreck something if you're not careful so backup the DB first (and know how to restore it) before you go poking around the tables.

---

### Post by newman on 2008-08-20
Is there a way to go back to the previous version of mythtv?

---

### Post by NT4usB on 2008-08-20
Sure...
But I don't know the steps.

---

### Post by mastermindg on 2009-02-18
Change 50 to whatever you'd like:

MySQL:

```
msyql -u root -p
USE mythconverg
UPDATE settings SET data = 50 WHERE value = 'atscchecksignalthreshold';
```

---

### Post by godsmack97526 on 2009-05-19
I am trying to setup mythtv and having many problems.  I sthere a set of instructions that i could follow to set it up correctly.  I have a Hauppauge 1600 card with a remote and IR blaster.  I am trying to set it up with DirectTV.  Any help would be greatly appreciated.  I am also using Mythbuntu as my OS.
 
Thank You,
Jarred
 
PS if you need any other info just ask and I will give you anything that you need!

---

