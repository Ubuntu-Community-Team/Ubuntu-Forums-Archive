---
title: "Trying to restore an old database"
date: 2008-11-11
forum: Mythbuntu
---

### Post by Daminator on 2008-11-11
Hello again all,

I screwed up my beautiful Ubuntu/Mthbuntu set up the other day and installed a fresh version of Ubuntu 8.10. I've added Mythbuntu and all of my recordings and a back up of mythconverge are on a seperate partition.

I found this page which is what I think I've done in the past:
[https://help.ubuntu.com/community/MythTV/Install/Live/Feisty%2B/WhatNext_BE](https://help.ubuntu.com/community/MythTV/Install/Live/Feisty%2B/WhatNext_BE)

The instructions are:

# mysql -u mythtv -p 'drop database mythconverg'                           ### drops your current database!!
# mysql -u mythtv -p 'create database mythconverg'                         ### creates a new empty database
# zcat /var/backups/mythconverg.sql.gz | mysql -u mythtv -p mythconverg    ### fills the new database with your backup

to restore a DB that Mythbuntu has been automatically backing up.

I have a completely clean install of Ubuntu that I have added Mythbuntu frontend and backend packages to it. I also have a file, "mythconverg.sql.gz" waiting to be restored.

When I try to run the above instructions, I fail at the first hurdle:

damian@MythBox:~$ mysql -u mythtv -p 'drop database mythconverg'
Enter password: ERROR 1045 (28000): Access denied for user 'mythtv'@'localhost' (using password: NO)

For the password, I have tried just pressing enter (blank password) and I have tried entering the Mysql password that Mythbuntu told me it was making for mythconverg. neither of them work. I've also tried running the whole thing with 'sudo' before it. Still no joy.

This must be really simple. What am I doing wrong?

Thanks
Damian

---

### Post by ian dobson on 2008-11-11
Hi,

The -u mythtv -p mythconverg  should be your user name for "-u" and password for "-p"

For me it would be:-
mysql -u mythtv -ptTaDaFs 'drop database mythconverg' 

you can find the password in the mysql.txt file.


Regards
Ian Dobson

---

### Post by Daminator on 2008-11-13
Thanks for that.

I ended up using this procedure:
[http://www.uluga.ubuntuforums.org/showpost.php?p=2298778&postcount=4](http://www.uluga.ubuntuforums.org/showpost.php?p=2298778&postcount=4)
and it worked well for me.

All videos seem to be back now. The only problem I've got is that only my user seems to be working. Other users on the same system and other frontends seem to be having trouble connecting and saying that there's no pin number set or something. I'll have to work out what's going on there.

Thanks for replying
Damian

---

### Post by klc5555 on 2008-11-13
> **Daminator said:**
> Thanks for that.

I ended up using this procedure:
[http://www.uluga.ubuntuforums.org/showpost.php?p=2298778&postcount=4](http://www.uluga.ubuntuforums.org/showpost.php?p=2298778&postcount=4)
and it worked well for me.

All videos seem to be back now. The only problem I've got is that only my user seems to be working. Other users on the same system and other frontends seem to be having trouble connecting and saying that there's no pin number set or something. I'll have to work out what's going on there.

Thanks for replying
Damian

All other users on same machine and all remote frontends will need their old mysql passwords updated to the current one from their individual frontend setup screens. Remote slave backends will need the password updated by running mythtv-setup on the remote machines running the slave backends.

Cheers!:)

---

### Post by Daminator on 2008-11-13
Sorted, Thanks for that

---

