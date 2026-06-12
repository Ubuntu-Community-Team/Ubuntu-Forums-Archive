---
title: "Do you need a TV Tuner to run MythTV/Mythbuntu?"
date: 2008-01-07
forum: Mythbuntu
---

### Post by Brind'Amour on 2008-01-07
Sounds like a silly question but there is a reason for it.

I am currently running a Vista MCE machine with a TV Tuner that works perfectly. I have an Ubuntu computer running as a BitTorrent downloader. The files are downloaded onto the Ubuntu machine and served from there or transferred across to the MCE machine. {This system works quite well, so why would I want to change? To try a new OS I 'spose.}

I currently have two reasonable spec machines that I am testing Mythbuntu on, that will eventually go into use as follows:

A; **Backend:** Running as a Gutsy desktop with primary backend, frontend for occassional use, and Azureus running for BitTorrent. Possibly most of the big HDD's will go into this computer. This computer will be on permanently.

B; **Frontend:** Gutsy desktop again, secondary backend, TV Tuner card, primarily acting as a frontend attached to the AV equipment. This PC will not be switched on all the time, only loaded up when viewing media.

I have sucessfully setup Gutsy with Mythbuntu on top on both machines. Neither computer has a TV Tuner in it as that is being used in the current Vista MC.

I cannot get B from above to connect to the mysql server on A. I have confirmed passwords, although I am a little shaky on permissions.

After all that I have two relatively simple questions. Firstly, does the primary backend need a TV Tuner for the mysql database to be populated and, hence secondly, is this setup going to work?

---

### Post by volkswagner on 2008-01-07
Confused on B. frontend.  Yes or no does it have a tv tuner?

If you do not plan on using mythbuntu as a PVR you should not need a tv tuner to populate Mysql.  

You need to be able to access mysql as mythtv user using the correct password.

In a terminal on master backend run

```
mysql -u mythtv -p
```

prompt asks for password, enter pasword and you should be now at a mysql> prompt.

If you get errors possibly you changed your password in myth-setup.  If you did change it you need to tell mysql.

look here [http://www.cyberciti.biz/faq/mysql-change-root-password/]("http://www.cyberciti.biz/faq/mysql-change-root-password/")

once you can access mysql via root and mythtv users you should run the following

```
sudo dpkg-reconfigure mythtv-database
sudo dpkg-reconfigure mythtv-common
```

Run these on both machines.  What has worked best for me, on master backend use localhost for location of mysql, and use ip address of the master machine when specify location for all other machines connecting.

---

### Post by Brind'Amour on 2008-01-07
I realised after I posted that it was not that clear.

B does not have a TV Tuner at the moment whilst I am testing. It will later when these machines are put into use.  But I think you answered my question with your second line.


I ran both those lines on the Master backend no problems. When I tried to run the first command on the secondary backend it stated:

```
/usr/sbin/dpkg-reconfigure: mythtv-database is broken or not fully installed
```

Which I would assume to be correct as there shouldn't be a mysql database running on anything other than the primary backend

After successfully running the second command you gave on the secondary backend, I am still unable to access the mysql database on the primary backend.

---

### Post by volkswagner on 2008-01-07
Sorry for that.  The first command is only for the backend.  

Can you access mysql -u mythtv -p on the backend?

---

### Post by Brind'Amour on 2008-01-07
That's OK.

I can access mysql -u mythtv -p on the backend.

I can access the local mysql databases through the test in the Mythbuntu Control Centre on each PC. However, when I try and access the mysql database on the primary backend from the secondary backend, it always fails.

I have now reversed the roles of the two PCs and it seems to work. Strange, very strange.

---

### Post by badurally on 2008-02-02
I cant access mysql db on my backend.
i tried, sudo mysql -u mythtv - p
then i entered my password and the following error 1045 (28000) appears
it says : Access denied for user 'mythtv'@'localhost' (using password:YES)

how do i solve this issue as i cant connect my front end DB?

---

### Post by volkswagner on 2008-02-03
You may have changed the mythtv user password in mythtv but not in mysql.

Check this file for what you set the password to be  /etc/mythtv/mysql.txt

run
```
tail /etc/mythtv/mysql.txt
```

If this returns the password you are using than you need to actually tell mysql this is the password to use. 

Hope you can access mysql with root account.  If you did set a password during the install run
```
mysql -u root -p
```

If you did not set a password try
```
mysql -u root
```

once you get a mysql> prompt you can set the password for user mysql

[http://www.cyberciti.biz/faq/mysql-change-root-password/]("http://www.cyberciti.biz/faq/mysql-change-root-password/") 

in the link above you can follow these insructions
> Changing MySQL root user password using mysql sql command

You must follow instructions very carefully!  Exactly as shown be sure to correctly change pertinent info ie: user name and password to suit your install

---

### Post by mister_p_1998 on 2008-12-01
I want to run Mythbuntu to stream video and Internet radio over my home network via the WiFi, there will be no TV cards in the system, do I still need to run a back-end? or can I play it all through the Front-end streaming from my server in the loft?

---

### Post by Archmage on 2008-12-01
Keep in mind that you must specife where you can connect to the MSQL-Database. The standard is 127.0.0.1 only. In this case you can't connect from an other PC and need to change it.

To answer your question: Yes, you can run Mythbuntu without a TV-Card. But it would make mure more sence, if the PC that is 24/7 on also have the TV-card. So it can record in the background and you can shut down the other PCs.

---

