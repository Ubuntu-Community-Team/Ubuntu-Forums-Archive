---
title: "Nvidia Screen Flash or Flashing or Flashes or Blank"
date: 2008-07-02
forum: Multimedia Software
---

### Post by OracleNix on 2008-07-02
Hi all

This seems to be a real problem especially considering all the hacks that have been tried and forgotten.

Anyway if you require a proper solution then do this:

From a previous thread we have...

System > Preferences > Advanced Desktop Effect Settings > General Options > Display Settings > Set Refresh Rate to 60.

... which on it's own did not work.  It did give a clue though.  So...

$ sudo aptitude install nvidia-settings

... System > Administration > X Server Display Configuration > Alongside to "Resolution" there is a drop down list - set this to 60 Hz.

From a problem screen without reboot this has been running for about an hour without complaint.

Hope this helps
G

---

### Post by OracleNix on 2008-07-03
Ignore this last post, this morning I started up again and the flashing returned :-@

Any neat suggestions??

---

