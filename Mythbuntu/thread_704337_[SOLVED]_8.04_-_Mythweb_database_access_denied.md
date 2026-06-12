---
title: "[SOLVED] 8.04 - Mythweb database access denied"
date: 2008-02-22
forum: Mythbuntu
---

### Post by wombo on 2008-02-22
Hello all I have setup a new 8.04 Mythbuntu system and I am having some troubles with mythweb.

I have read through the INSTALL file and googled alot and tested a few different ideas out to no avail and have at last decided to post.

does anybody have any ideas of where to start?


Thanks

---

### Post by foxbuntu on 2008-02-22
Does everything with myth work for you other than Mythweb?

---

### Post by ed3120 on 2008-02-22
I had the same issue before I applied all of the updates.  Be sure to go into the Update Manager, do a check, and then install all updates.

---

### Post by wombo on 2008-02-22
ah thats it. I just installed all the updates and its now working.

Thanks

---

### Post by p$y on 2008-03-26
same problem here 

> Database Access Denied

You are most likely receiving this message because you
have failed to configure mythweb's database login info.

Please see INSTALL for instructions.


Because I changed in the mcc to password protection.
I have purged mythweb & apache2 & apache2.2-common, if I would select php* to, it would remove mythtv etc. too. Would my recording rules etc. stored in the database than be deleted?

After reinstalling mythweb the problem is still there.

All updates installed.

---

### Post by nickblame on 2008-04-27
hell this is a nasty bug. why is there an option to secure mythweb when all it does is break stuff??? the alpha 2 version was ok on that. how is that solved???

---

### Post by nickblame on 2008-04-27
SOLVED
apt-get install phpmyadmin

then on /phpmyadmin of the mythbuntu login as root null password
in priviledges go and set no password for user mythtv%localhost

this bug sucks btw... it should have been working right.

---

### Post by declanh on 2008-04-27
I too am getting 

"Database Access Denied

You are most likely receiving this message because you
have failed to configure mythweb's database login info.

Please see INSTALL for instructions.
"

mysql and /usr/share/mythtv/mythweb/mythweb.conf.apache
both have the same password for the DB. I have tried logging into mysql from the commandline ok but mythweb is still broken. I think this worked ok for me on 8.04RC
        #   setenv db_server        "localhost"
            setenv db_server        "192.168.1.xxx"
            setenv db_name          "mythconverg"
            setenv db_login         "mythtv"
            setenv db_password      "<pwd>"

any ideas what else to try ?
Ive changed this install to run with static IP - that should not make any diff should it ?

D

---

### Post by zukakog on 2008-04-30
I've created a bug at [https://bugs.launchpad.net/ubuntu/+source/mythweb/+bug/224530](https://bugs.launchpad.net/ubuntu/+source/mythweb/+bug/224530)

I tried blanking out the password as suggested above, but it did not work for me.

Either way, put your problems and solutions in the bug tracker listed above, so that maybe it'll be fixed in an update.

---

### Post by Wombiroller on 2008-05-06
All - while this bug gets sorted, this worked for me (no database editing or phpmyadmin req):

1. Edit the mythweb.conf file in apache2 (e.g. ***sudo vim /etc/apache2/sites-enabled/mythweb.conf***)
2. find the ***setenv_db_password*** value and update this (the bit between the double quotes) to the database password listed in the Database Configuration screen of Mythtv Setup GUI (in Setup -> General)
3. Save the file and reboot (not sure why you have to reboot but I did)

Should be fixed now, however for me every time I update the password or username for mythweb this setenv_db_password value gets over-ridden again. 

Cheers,
WR.

---

### Post by justbill6942 on 2008-05-06
You don't need to do a full reboot.  

**sudo /etc/init.d/apache2 restart**

That solved it for me.

---

