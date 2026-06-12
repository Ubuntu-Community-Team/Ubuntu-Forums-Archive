---
title: "Mythbuntu symbolic links"
date: 2009-04-28
forum: Mythbuntu
---

### Post by Merlin Cosmos on 2009-04-28
Just had a bunpy ride upgrading to mythbuntu 9.04.

I have switched back & forth between Mythbuntu & Knoppmyth a couple of times there are merits to both. 

Having trouble right now deleting shows from the Delete Recordings menu which don't exist on my hard drive anymore. Have done this before using fish in konqueror. It is easier to do in Knoppmyth due to less restrictive permissions.

I could do the same in mythbuntu if I knew where (Which directory) Mythbuntu uses to store its symolic links of Huan readable names. In Knoppmyth its found in the directory MythPretty. If anyone knows the answer to this I would be grateful

---

### Post by dannyboy79 on 2009-04-28
> **Merlin Cosmos said:**
> Just had a bunpy ride upgrading to mythbuntu 9.04.

I have switched back & forth between Mythbuntu & Knoppmyth a couple of times there are merits to both. 

Having trouble right now deleting shows from the Delete Recordings menu which don't exist on my hard drive anymore. Have done this before using fish in konqueror. It is easier to do in Knoppmyth due to less restrictive permissions.

I could do the same in mythbuntu if I knew where (Which directory) Mythbuntu uses to store its symolic links of Huan readable names. In Knoppmyth its found in the directory MythPretty. If anyone knows the answer to this I would be grateful
if you're looking to delete recordings that are showing in the database but are not actually anywhere on a hard drive. you would use this script to fix the database. The script is called myth.find_orphans.pl (see here: [http://www.cuymedia.net/mythtv-trunk/myth_8find__orphans_8pl-source.html](http://www.cuymedia.net/mythtv-trunk/myth_8find__orphans_8pl-source.html)) Instructions on how to use the script are at the begining of the script if you open it with gedit or a text editor.

As far as human readable recordings in mythbuntu, there isn't a location that I aware of. you have to setup root crontab using mythrename.pl. My root crontab looks like this:
0 * * * * /usr/local/bin/mythrename.pl --link /media/300gb/mythtv/readable-recordings
I am still using Mythbuntu Gutsy Gibbon so it's possible that there is a human readable recordings directory setup by default in future releases of Mythbuntu. Here is the script: [http://www.mythtv.org/wiki/Mythrename.pl](http://www.mythtv.org/wiki/Mythrename.pl)

good luck

---

### Post by Merlin Cosmos on 2009-04-29
Thank you for that.

I will give that a try and let you know how it works out

---

### Post by Merlin Cosmos on 2009-04-29
Adjusted myth.find_orphans.pl  to reflect my host, db, user, password,etc/  Get this error message

 Invalid option linkage for "host=s"
Invalid option linkage for "dbhost=s"

Any ideas as to what is wrong

Thank you in advance.

---

