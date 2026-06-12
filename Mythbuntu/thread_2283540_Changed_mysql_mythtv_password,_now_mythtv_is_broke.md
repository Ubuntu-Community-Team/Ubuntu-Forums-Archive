---
title: "Changed mysql mythtv password, now mythtv is broken"
date: 2015-06-22
forum: Mythbuntu
---

### Post by brian_hayward on 2015-06-22
Hello, I was in the process of trying to connect a remote frontend to my current mythtv setup.  I run mythbuntu 14.00.  I found a forum post that instructed people to change the mythtv mysql user to password=mythtv.  i didn't know what the password was for the user mythtv so i thought changing the password would'nt be a bad idea.  now when i open the local myth frontend it gives me an error telling me it cant connect to the backend.  Any help here is greatly appreciated.  I know i haven't provided a lot of information, but i can provide more if somebody asks for it.  Thanks.

Brian.

---

### Post by aelfric55 on 2015-06-22
If you can log into mysql itself 
```
$mysql -u mythtv -p
```
from a terminal using mythtv's new mysql password, then the password change was successful. If the password change was successful, did you also change the password in mythtv's "config.xml" files, which may normally be found in one or more of the ~/.mythtv directories under the /home/[user] directories, in the /etc/mythtv directory and sometimes also under /root/.mythtv ? If by some fluke you still have a leftover active mysql.txt file in one of these directories, it will also need to be corrected, or got rid of in favor of the config.xml file.

---

### Post by brian_hayward on 2015-06-23
> **aelfric55 said:**
> If you can log into mysql itself 
```
$mysql -u mythtv -p
```
from a terminal using mythtv's new mysql password, then the password change was successful. If the password change was successful, did you also change the password in mythtv's "config.xml" files, which may normally be found in one or more of the ~/.mythtv directories under the /home/[user] directories, in the /etc/mythtv directory and sometimes also under /root/.mythtv ? If by some fluke you still have a leftover active mysql.txt file in one of these directories, it will also need to be corrected, or got rid of in favor of the config.xml file.

i was able to log into the database using the username and password of mythtv.   i looked at all the config.xml files under the /etc directory, the mythtv user directory, and my local user home directory.  i even checked under /root/.mythtv, but that config files was linked to the file under the /etc directory.  All of the config files had the correct IP address, username and password.  I could not find any mysql.txt files.  However mythtv still can't connect to the backend, and when i go to the mythweb it throws up errors about incorrect mysql passwords.   

I just realized yesterday that i had a backup of my OS and i keep regular backups of the mysql database, so i did a restore.  I don't have time to troubleshoot this mess, and i don't want to miss out on my stories.  Thank you for the reply thought...i greatly appreciate it.  Please feel free to add more to this post though...maybe somebody else will find it useful.  Thanks again.

---

