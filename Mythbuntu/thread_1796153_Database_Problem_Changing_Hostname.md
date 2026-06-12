---
title: "Database Problem Changing Hostname"
date: 2011-07-03
forum: Mythbuntu
---

### Post by fullmoonguru on 2011-07-03
Using instructions from the Mythtv wiki I changed the hostname of the machine & then did this:

                        	 	 	 	pre.cjk { font-family: "DejaVu Sans",monospace; }p { margin-bottom: 0.08in; }  > sudo /usr/share/mythtv/mythconverg_restore.pl --change_hostname &#8211;old_hostname="my_old_name" &#8211;new_hostname="my_new_name"  I got this error:

  	 	 	 	pre.cjk { font-family: "DejaVu Sans",monospace; }p { margin-bottom: 0.08in; }  > The argument you supplied for the database information file is invalid. If you were trying to specify a backup filename, please use the &#8211;directory and --filename arguments. 
ERROR: Invalid database information file, stopped at /usr/share/mythtv/mythconverg_restore.pl line 710. It seems to indicate that I didn't tell it where the database file is, but as far as I know it's in the default location.  I do have my database backups in a different folder, but it doesn't need to access the db backups does it?

---

