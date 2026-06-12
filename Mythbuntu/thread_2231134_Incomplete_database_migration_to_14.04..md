---
title: "Incomplete database migration to 14.04."
date: 2014-06-23
forum: Mythbuntu
---

### Post by khPWXxF on 2014-06-23
I recently set up a Mythbuntu 14.04 system (0.27 Mythtv), set up the tuners, got mythwelcome working and changed a keybinding (main menu escape).   I did limited testing then imported a 0.25 database backup into it.
 
```
#!/bin/bash
/usr/share/mythtv/mythconverg_restore.pl\
      --drop_database --create_database\
    --directory /home/phil/work\
      --filename mythconverg-1299-20140527000845.sql.gz
 
```
I then ran the backend setup to convert it from 0.25 to 0.27.   All the recordings and the recording schedule were imported and the timezone tables were created (or retained).
 
Tuner settings, mythwelcome settings and keybindings (eg sticky keys and main menu escape) were all lost though.  In my migration 0.21 -> 0.22 -> 0.25 back in 2012 these parameters were copied over.
 
Why might these settings have been lost this time?   Is it only a migration issue or would a 0.27 backup suffer the same fate?   Is this a bug, a user error or just a limitation of the migration code?
 
Phil

---

### Post by blm-ubunet on 2014-06-23
Different hostname or localhostname?
The localhostname (if non-blank) is used to name/label the "setup" profile.

Something like this (untested) should list all hostname profiles:
(need to replace the password & don't need "[-h<mbe>]" if run on MBE)
```
[FONT=Verdana][SIZE=2][COLOR=black][FONT=Verdana][SIZE=2][COLOR=black][FONT=Verdana][SIZE=2][COLOR=black][FONT=Verdana][SIZE=2][COLOR=black]echo "SELECT hostname FROM settings WHERE hostname IS NOT NULL ;" | mysql [-h<mbe>] -umythtv -pmythtv[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
```

I haven't lost any dB settings in last 4yrs (running master).

---

### Post by khPWXxF on 2014-06-24
Many thanks - yes, indeed that was the problem.  Old was 'myth', new was 'Mythtv'.
Edits to /etc/hostname, to /etc/hosts, reboot, re-import backup, run backend setup and bingo, all settings imported.

Now then
a) How do I mark this thread as solved?
b) Why did the xfce task bar across top of screen re-appear after the reboot I wonder?

Thanks again
Phil

---

