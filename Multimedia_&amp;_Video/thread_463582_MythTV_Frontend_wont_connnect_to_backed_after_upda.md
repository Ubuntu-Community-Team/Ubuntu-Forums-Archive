---
title: "MythTV Frontend wont connnect to backed after updates installed"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by djseto on 2007-06-03
I am running a frontend/backend combo machine on Ubuntu 6.10. Everything has been working great for months until I installed some "critical updates" today. I dont remember what was installed, but now the Frontend cant communicate with the backend. I have verified that the backend is running. I can ping 127.0.0.1 and I get responses. When I try to start the backend, it says its already running. When I am in the front end and try to watch live TV, it says the inputs are already in use. When I look at the System Status, it says it can't connect to the Master Backend server and asks me to verify the IP is correct in the setup, which it is. Any ideas?

---

### Post by djseto on 2007-06-03
Fixed it. I had to recompile the drivers for my HD Capture cards. I guess one of the new updates was kernel headers or something..

---

### Post by tha_toadman on 2007-06-09
i'm having the same sort of problem....

I have a 7.04 feisty backend and a 6.10 frontend (which i ran "mythtv-setup" on). Now I can use the frontend but when I click "watch tv" it says the same as yours did - something about can't connect to backend and verify the IP address. I did verify (and i can ssh to it) and I know it's working but the frontend is still lost?

7.04 has built-in support for my PVR-150 card so I didn't have up update anything special like you did for that. Any other ideas?

---

### Post by tgm4883 on 2007-06-09
> **tha_toadman said:**
> i'm having the same sort of problem....

I have a 7.04 feisty backend and a 6.10 frontend (which i ran "mythtv-setup" on). Now I can use the frontend but when I click "watch tv" it says the same as yours did - something about can't connect to backend and verify the IP address. I did verify (and i can ssh to it) and I know it's working but the frontend is still lost?

7.04 has built-in support for my PVR-150 card so I didn't have up update anything special like you did for that. Any other ideas?

Isn't mythtv-setup for backends not frontends?

---

### Post by tha_toadman on 2007-06-10
i discovered my problem...

within **/etc/mysql/mysql.txt** my password for the database didn't match what i had configured in 'phpmyadmin'. i found the conflict there, changed it, and now it's working properly.

---

### Post by superm1 on 2007-06-10
> **tha_toadman said:**
> i discovered my problem...

within **/etc/mysql/mysql.txt** my password for the database didn't match what i had configured in 'phpmyadmin'. i found the conflict there, changed it, and now it's working properly.

This stems from something exclusive to Ubuntu/Debian MythTV packages that you don't necessarily find in other distros' packages.  If you are wanting to update any passwords on your MythTV setup for Ubuntu, its best to do it via dpkg-reconfigure rather than forcefully with phpmyadmin and manually editing ~/.mythtv/mysql.txt or /etc/mythtv/mysql.txt.  The password, username, database, and other information are all stored in the debconf database so that future packages can take advantage of this information directly rather than having to use sed/awk/grep on misc mysql.txt files.

Now, if you want to update the **root password** of your mysql server, this is how you do it:
```
sudo dpkg-reconfigure mysql-server-5.0
```

If you want to update the information MythTV needs for contacting your mysql server (**mysql server ip address, root username, root password**)
```
sudo dpkg-reconfigure mythtv-database
```

If you want to update the information MythTV needs for writing to the mysql database (**mythtv username, mythtv password, mysql server ip address, mysql database to use**)
```
 sudo dpkg-reconfigure mythtv-common
```

You will notice reconfiguring mythtv-database and mythtv-common both setup the ip address of mysql server.  This means that if you move the server somewhere, you will need to rerun both reconfigurations.

---

### Post by tha_toadman on 2007-06-15
thanks superm1, for that info! that will definitely come in handy.

---

### Post by dannyboy79 on 2007-07-17
> **superm1 said:**
> This stems from something exclusive to Ubuntu/Debian MythTV packages that you don't necessarily find in other distros' packages.  If you are wanting to update any passwords on your MythTV setup for Ubuntu, its best to do it via dpkg-reconfigure rather than forcefully with phpmyadmin and manually editing ~/.mythtv/mysql.txt or /etc/mythtv/mysql.txt.  The password, username, database, and other information are all stored in the debconf database so that future packages can take advantage of this information directly rather than having to use sed/awk/grep on misc mysql.txt files.

Now, if you want to update the **root password** of your mysql server, this is how you do it:
```
sudo dpkg-reconfigure mysql-server-5.0
```

If you want to update the information MythTV needs for contacting your mysql server (**mysql server ip address, root username, root password**)
```
sudo dpkg-reconfigure mythtv-database
```

If you want to update the information MythTV needs for writing to the mysql database (**mythtv username, mythtv password, mysql server ip address, mysql database to use**)
```
 sudo dpkg-reconfigure mythtv-common
```

You will notice reconfiguring mythtv-database and mythtv-common both setup the ip address of mysql server.  This means that if you move the server somewhere, you will need to rerun both reconfigurations.

OK, I have been talking to you a little here and there about this issue and I am really at my wits end!!!! My main goal is to get xbmcmythtv to work. I can see the Upcoming Scheduled Recordings when I am in the xbmcmythtv but nothing else which leads me to belive that I am connected to the database??? I am using smb://192.168.0.3/media/400gb/mythtv for the Recordings Folder and the Live tv folder within the settings page within xbmcmythtv but they don't work. I have tried to use smb://daniel:<password>@192.168.0.3/blah/blah BUT that doesn't work because my password for connecting to the smb share has symbols in it, like the @ symbol among others. I have even tried to use the ASCI equivalent for @, which was %40 I believe, and also the ASCI equivalent for the other symobls but to no avail. There's a setting within xbmc to set the username and password for the local workgroup which is why I believe that I can view the shares and Mythtv shows just fine thru xbmc but not thru the python script, xbmcmythtv.

When I test the settings, I still get, "unable to connect to database, conn". Someone suggested that I try to connect to the mysql database from another machine, everytime I try, it fails also? I check to make sure that netstat -pant shows port 3306 listening on 0.0.0.0 and it is. This is what I get:
ERROR 1045 (28000): Access denied for user 'mythtv'@'XUBUNTU-FIESTY' (using password: YES)
and when I view the priveleges thru phpmyadmin, I am allowing user mythtv to connect from all (%) hosts but still no avail???

Do I need to change the Mysql IP Address to the Static IP of the Main Backend Server? BEcause if so, when I run sudo dpkg-reconfigure mythtv-database, and change it from 127.0.0.1 to the static IP of the main backend server (keep in mind this is all done on the main backend/frontend/desktop), leave "root" and then enter the password for root, this is what it tells me:
Failed to connect to database: Access denied for user 'root'@'UBUNTU.getmyip.com' (using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database

BUT, I can tell you that the root password I am trying is correct because I can connect to the mysql database just fine using mysql -u root -p, then enter the same exact password and it'll work just fine.

But when I run that same command and leave mysql ip address to 127.0.0.1, it works just fine. I don't understand the connection between mysql root user, mysql.txt, mythtv user and the ip addresses? Also, what should mysql.txt look like IF I want to be able to connect from other machines??? I have tried changing that DBHostName to the static ip as well and that doesn't work then either???? 

PLEASE HELP!!!!

---

### Post by MCMcButtah on 2007-07-17
Have you done this?

check this on your backend machine:

# sudo nano /etc/mysql/my.cnf

look for :

bind-address= 127.0.0.1

and comment it out by hashing it:

#bind-address= 127.0.0.1

restart mysql server:

# sudo /etc/init.d/mysql restart

and try to connect from the frontend.

If that is not commented out you will only be able to connect from the localhost. 

BTW: Kinda confused by a bunch of what you posted, but your smb: problems should be unrelated to any mythtv mysql problems. Sorry if I misunderstood what you were saying though.

---

### Post by dannyboy79 on 2007-07-18
I have done that but thanks for trying. What I don't get is the whole mythtv username and password thingy. Is the mysql.txt file for the mythtv user, as far as the password that's in it or is that the root password for the mysql database mythconverg?

I have a frontend/backend/desktop setup, when I do sudo dpkg-reconfigure mythtv-common or mythtv-database, should I be entering the static ip of the backend server or should I be putting 127.0.0.1? Because if I put in the static ip of the backend server, it doesn't work. I do know that within the mthtv-setup, I am suppose to be putting the backend server's static ip instead of 127.0.0.1 and that's done. I had to make a password for the root user for mysql because I am using mythtweb so I don't want anyone to be able to go into phpmyadmin and mess with my databases. 

Do you use xbmcmythtv? That's the only thing I am having problems with, Mythtv on the frontend/backend/desktop is awesome! I can even use mythtweb on my Treo 700p to do scheduling etc etc. It's great. Either I figure out how to get xbmcmythtv to work on my modded xbox or I just build a cheap frontend out of the old hardware I have sitting around. 

So if you can maybe answer the few questions I have asked I would apprecaite it. Thanks again for trying though.

---

### Post by tgm4883 on 2007-07-18
> **dannyboy79 said:**
> I have done that but thanks for trying. What I don't get is the whole mythtv username and password thingy. Is the mysql.txt file for the mythtv user, as far as the password that's in it or is that the root password for the mysql database mythconverg?

I have a frontend/backend/desktop setup, when I do sudo dpkg-reconfigure mythtv-common or mythtv-database, should I be entering the static ip of the backend server or should I be putting 127.0.0.1? Because if I put in the static ip of the backend server, it doesn't work. I do know that within the mthtv-setup, I am suppose to be putting the backend server's static ip instead of 127.0.0.1 and that's done. I had to make a password for the root user for mysql because I am using mythtweb so I don't want anyone to be able to go into phpmyadmin and mess with my databases. 

Do you use xbmcmythtv? That's the only thing I am having problems with, Mythtv on the frontend/backend/desktop is awesome! I can even use mythtweb on my Treo 700p to do scheduling etc etc. It's great. Either I figure out how to get xbmcmythtv to work on my modded xbox or I just build a cheap frontend out of the old hardware I have sitting around. 

So if you can maybe answer the few questions I have asked I would apprecaite it. Thanks again for trying though.

I'm not exactly sure the question on which ip address you need in "sudo dpkg-reconfigure mythtv-common" as I don't know what it is asking.  I did throw xbmcmythtv on my xbox last night, so hopefully I will have it all configured today or tomarrow and I'll have something for you.

:EDIT:

I really think that xbmcmythtv needs to get on the ball though.  I don't really like to install unneeded things on my backend, and Samba is something I was trying to avoid.

---

### Post by edward4130 on 2007-07-19
Well loved that others had the same issues, but now that I have goen through everythig I have totally FUBAR'd my mythtv.  It is a frontend/backend that was running good for about 6 months.  Currently when I startup it goes to a blue mythtv screen and goes through a database setup for passwords and then exits... that's it!  I also did the cron.daily thing and it gave me....
```
edward@mediacenter:~$ sudo /etc/cron.daily/mythtv-backend 
Password:
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open

```

So I hope someone can help me out.  I have limited hours to work on my linux stuff, so this forum has been a real help.  Superm1 has really helped me out of a jam more than once  thanks!  BTW did you move?  I thought you were in Ames IA...?

-Edward4130 , Kansas city Kansas

---

### Post by dannyboy79 on 2007-07-19
I am not sure what you're trying to do by starting it from cron, do you even have the command located there, I know I don't on my machine! 

To stop or start, all you do is this command
sudo /etc/init.d/mythtv-backend restart (or stop or start)


well, this is what I suggest. First, run
sudo dpkg-reconfigure mysql-server-5.0
(enter a password for your root user for the mysql database)
then run
sudo dpkg-reconfigure mythtv-database
(this will ask you which Host the mysql database is running on, I entered 127.0.0.1. then it'll ask who the admin should be for this database, enter root, then enter a password for this account.)
then run sudo dpkg-reconfigure mythtv-common
(this will ask you what user you want to run mythtv with, I used mythtv, then it wanted to know the password for that user, I chose the same exact password that I chose for the root password for mythtv-database.)

That should get you going again, if the database is broken or whatever, there's a command to repair it (mythtconverg database that is), you'll have to gogle for that I forget what it is.

Ensure that you remove the file called mysql.txt from your home dir that get's stored within the hidden .mythtv folder, so that it reads from the global file located within /etc/mythtv/.

Then also, make sure that the password for the mythtv user for the mysql database mythconverg matches what you entered when you did the mythtv-common command above. Again, you'll have to gogle that sorry.

Good luck

---

### Post by edward4130 on 2007-07-20
Thanks guys,  that did the trick, ran dkpg-reconfigure on each one and it was fine after refilling the database and restarting the backend.  

Now that there are newer video cards and even a "abit" motherboard with HDMI ati video card on it I am debating on moving up to HDcards.  If anyone has any input on what ones work well for myth/linux drop me a note off this thread.  You could say I want to build a new one for HD and will go the extra to make it a All-in-One entertainment Center.

-Edward4130 Kansas city Kansas

---

### Post by edward4130 on 2007-07-24
OK spoke far too soon.  I have no schedule information, and when i attempt to even go to the directory that I need to do the fix table i get an authentication, please help I posted on another thread and No reply even with detailed information..

> 
edward@mediacenter:~$ su -l mysql
Password: 
su: Authentication failure
Sorry.
edward@mediacenter:~$ 

now this is really pissing me off!!  What i cant even log into mysql!!! I know the damn password.
> edward@mediacenter:/var/lib/mysql$ ls -la
total 20544
drwxr-xr-x  4 mysql mysql     4096 2007-07-23 22:36 .
drwxr-xr-x 52 root  root      4096 2007-07-14 08:35 ..
-rw-r--r--  1 mysql mysql        0 2007-07-19 22:33 debian-5.0.flag
-rw-rw----  1 mysql mysql 10485760 2007-07-23 08:05 ibdata1
-rw-rw----  1 mysql mysql  5242880 2007-07-23 22:36 ib_logfile0
-rw-rw----  1 mysql mysql  5242880 2007-02-17 17:00 ib_logfile1
drwxr-xr-x  2 mysql mysql     4096 2007-07-23 22:36 mysql
-rw-------  1 mysql mysql        4 2007-02-17 17:00 mysql_upgrade.info
d-wx------  2 mysql mysql     8192 2007-02-20 02:27 mythconverg
edward@mediacenter:/var/lib/mysql$ cd mythconverg/
bash: cd: mythconverg/: Permission denied
edward@mediacenter:/var/lib/mysql$ 

10days without a recording, so mych for the season shows i can't get on DVD later.

-Edward

---

### Post by dannyboy79 on 2007-07-25
> **edward4130 said:**
> OK spoke far too soon.  I have no schedule information, and when i attempt to even go to the directory that I need to do the fix table i get an authentication, please help I posted on another thread and No reply even with detailed information..


now this is really pissing me off!!  What i cant even log into mysql!!! I know the damn password.

10days without a recording, so mych for the season shows i can't get on DVD later.

-Edward
Well I am guessing that you have no lineup because you didn't associate the Source with the capture card. Also, you're aren't hitting Use capture card to scan for channels are you, I tried that and it overwrites all teh data frmo zap2it!

The guy reponded to you about 8 hours ago in the other thread. I see that you posted this 10 hours ago so you should be able to do what he is saying and have it work.

I can't do "su -l mysql" either, I don't think there's a need to anyway. Also, if you think abou it I was unaware that during mythtv setup and also mysql setup that we actually picked a password for the mysql user which is why I am guessing that you can't switch to that user.

As for trying to cd to the /var/lib/mysql/mythconverg directory when you are logged in as yourself, i can't either, and why do you want to? If you really want to (i don't know why) then just switch to the root user by issueing, "sudo -i" and enter YOUR password. This will get you a root prompt temporarily.

---

