---
title: "mysql refusing connection for 'mythtv'@'%'"
date: 2014-05-05
forum: Mythbuntu
---

### Post by dannyboy79 on 2014-05-05
i had my whole system working just fine with mythtbuntu 12.04 and 0.26+fixes (backend) and an xbmc frodo (frontend) and it all worked great. These are physically 2 different machines just to note.

So I upgraded the backend server to xubuntu 14.04 and to mythtv 0.27+fixes (upgraded from 12.04 xubuntu) and my xbmc install to Gotham Beta4 and no matter what I do in phpmyadmin the backend is refusing any connection from IP addresses that are not itself. The backend is working fine, it's accepting connection from itself as seen when I run the mythtv-setup and the backend starts up just fine.

The things I've done;
-my.cnf bind-address is 192.168.0.5 
-master backend ip and backend ip are both 192.168.0.5
-the config.xml located in /home/ubu/.mythtv, /home/mythtv/.mythtv, & /etc/mythtv/ all have the same information for Host, username, password, and database. I noticed i still have mysql.txt files laying around. should I delete those?
-i tried running mysql commands for granting permission of user mythtv using hostnames and IP's but ultimately installed phpmyadmin and when i view the privileges of the mythconverg database it all looks good. GRANT is enabled for mythtv@%

Any other suggestions?

---

### Post by tgm4883 on 2014-05-05
> **dannyboy79 said:**
> i had my whole system working just fine with mythtbuntu 12.04 and 0.26+fixes (backend) and an xbmc frodo (frontend) and it all worked great. These are physically 2 different machines just to note.

So I upgraded the backend server to xubuntu 14.04 and to mythtv 0.27+fixes (upgraded from 12.04 xubuntu) and my xbmc install to Gotham Beta4 and no matter what I do in phpmyadmin the backend is refusing any connection from IP addresses that are not itself. The backend is working fine, it's accepting connection from itself as seen when I run the mythtv-setup and the backend starts up just fine.

The things I've done;
-my.cnf bind-address is 192.168.0.5 
-master backend ip and backend ip are both 192.168.0.5
-the config.xml located in /home/ubu/.mythtv, /home/mythtv/.mythtv, & /etc/mythtv/ all have the same information for Host, username, password, and database. I noticed i still have mysql.txt files laying around. should I delete those?
-i tried running mysql commands for granting permission of user mythtv using hostnames and IP's but ultimately installed phpmyadmin and when i view the privileges of the mythconverg database it all looks good. GRANT is enabled for mythtv@%

Any other suggestions?

Did you restart after making all those changes?

---

### Post by dannyboy79 on 2014-05-05
yes, i restarted the server. i also always used flush privileges; as well. i just don't know how to trouble shoot this. maybe i can install a mythtv frontend on another machine in my LAN and see if that works. Shouldn't the allow all privileges line of 'mythtv@'%' that shows in phpmyadmin be enough? 

i used to get refused connection from 'mythtv'@'crystalbuntu.local' before I added a line to my my.cnf to not skip-name-resolve so that's not the issue because now it refuses connection from the IP. I've triple checked the password used on xbmc mythtv addon, it's the same password in my config.xml files.

I did a restore of the database from my 0.26+fixes mythtv installation so shouldn't the privileges have stayed the same? the IP on the client trying to connect didn't change either. only thing that's new is the OS, the mythtv version and mysql version.

UPDATE: i am so embarased it took me hours upon hours of fiddling with mysql and phpmyadmin but I finally found the issue, the client (XBMC cmyth) had a capital "O" when it was suppose to be a zero "0". as soon as I fixed the password within XBMC the mythtv addon connected immediately to the backend.

---

