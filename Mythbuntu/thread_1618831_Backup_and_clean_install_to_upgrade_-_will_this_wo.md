---
title: "Backup and clean install to upgrade - will this work?"
date: 2010-11-11
forum: Mythbuntu
---

### Post by marek_online on 2010-11-11
Hi,

I've a Mythbuntu 8.10 machine which has run fine, but I think at this point really wants some upgrading. It's a dedicated machine, so it doesn't get used for much else other than Myth. I know I won't get to to the new 0.24 release, but I figure from 0.21-fixes to 0.23.1 and Mythbuntu 10.10 would be a good step forward.

Googling the issue, it looks like the [clean install instructions here]("http://www.mythbuntu.org/upgrading") (reproduced below to avoid you having to click through) might suit me best.

I just wanted to check with people who might know -

- is this a stupid idea?
- will this mess up the recordings I already have?
- will the database upgrade okay?

The following are all on separate partitions:
/boot
/
/home
/var/lib/
/var/lib/mythtv/store (a 160GB second hard drive I keep music/photos etc. on)


Be grateful for any advice.

M

============

[LIST]
[*] Execute backup script:
[/LIST]
[COLOR=#292929][FONT=Arial][COLOR=#000000][FONT=Verdana]/usr/share/mythtv/mythconverg_backup.pl[/FONT][/COLOR][/FONT][/COLOR]Note: if your system doesn't have the necessary scripts, they may be obtained from SVN.
[http://svn.mythtv.org/trac/browser/trunk/mythtv/programs/scripts/database/mythconverg_backup.pl?format=txt](http://svn.mythtv.org/trac/browser/trunk/mythtv/programs/scripts/database/mythconverg_backup.pl?format=txt)
[http://svn.mythtv.org/trac/browser/trunk/mythtv/programs/scripts/database/mythconverg_restore.pl?format=txt](http://svn.mythtv.org/trac/browser/trunk/mythtv/programs/scripts/database/mythconverg_restore.pl?format=txt)

[LIST]
[*]Save a copy of the resulting backup (which is usually the most recent file in **/var/lib/mythtv/db_backups/**)  someplace that will survive reinstalls and/or disk failures.
[*]Perform Mythbuntu install or upgrade
[*]Stop the backend:
[/LIST]
sudo stop mythtv-backend


[LIST]
[*]Obtain the mythtv password from here:
[/LIST]
grep DBPassword /etc/mythtv/config.xml

[LIST]
[*]Delete old database and create a base new one:
[/LIST]

mysql -u mythtv -p -e "DROP DATABASE IF EXISTS mythconverg;"
mysql -u mythtv -p -e "CREATE DATABASE mythconverg;"


[LIST]
[*]Copy the previously saved database to **/var/lib/mythtv/db_backups/** and then execute the restore command:  
Note: this restore can take a number of minutes for even average sized databases.
[/LIST]
/usr/share/mythtv/mythconverg_restore.pl --directory /var/lib/mythtv/db_backups --filename FILENAME

[LIST]
[*]Start the backend again:
[/LIST]
sudo start mythtv-backend

---

