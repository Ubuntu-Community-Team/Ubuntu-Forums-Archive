---
title: "mythtv uPnp error"
date: 2009-03-09
forum: Multimedia Software
---

### Post by sephirothsigep on 2009-03-09
alright i have gone through all of the howto's and guides trying to troubleshoot the issues that i have going on with my fresh install of ubuntu 8.10 for mythtv. this is going to be a frontend backend desktop combo. now the reason that i did not use mythbuntu is because of the unique raid configuration that i have going on. I have fakeRaid working in linux. yep thats right.fakeraid. so here are the steps that i have taken so far.

[LIST=1]
[*]using synaptic i installed mythtv (ie mythtv-common, mythtv-frontend, and mythtv-backend)
[*]
i was then presented with the standared screen for setting up mysql and giving it a root password. once done doing that i gave mythtv the needed info for mysql. 
[*]I then ran system> administration > mythtv backend setup. this asks if you want the current user to be added to the mythtv group and i did.
[*]logged out and then backin and ran the mythtv backend setup again. 
[*]I then was having issues and getting the standard uPnP error and "Blue screen of death". so i then ran dpkg-reconfigure mythtv-common, and dpkg-reconfigure mythtv-database.
[*] i then ran through the setup for the backend and everything went fine. i was able to scan for channels and all of my channels where found.
[*] so next i try to run the front end and once again get the "blue screen of death" that asks for a language and says that no uPnP backends found. 
[*] so i enter the database information. hostname, username , password ect. after doing then i click next and finished. 
[*]i am then presented with an error message that i can find little information on that says **"Cannot find (ping) database host on the network."**
[/LIST]
I have also installed phpmyadmin and have looked at the database and it looks as though the mythtv user has everything that he needs. just to make sure that he does i have given him full control with the following two commands
[LIST]
[*]GRANT ALL ON *.* TO 'mythtv'@'localhost' IDENTIFIED BY '<dynamic password>'
[*]GRANT ALL PRIVILEGES ON 'mythconverg.* to 'mythtv'@'localhost'
[/LIST]

i also took a look at the tables in the mythconverg database and the channel information is there so i know that i have access to the database from the backend. now i just need to be able to give the frontend access. so my issues that i have no idea why I am having issues getting access to the front end when i can see that the backend has access to the database. if you need any more information let me know

---

### Post by sephirothsigep on 2009-03-09
well i have solved this issue kinda. i reinstalled my raid config and started over. this time instead of installing all of the needed items for mythtv all at once i installed mysql then phpmyadmin and finally mythtv and along the way made sure that everything was working fine.

---

