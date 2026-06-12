---
title: "Cannot connect to database insanity"
date: 2011-01-07
forum: Mythbuntu
---

### Post by Lido on 2011-01-07
I finally decided to update my myth box from 7.10 to 10.10 yesterday. During installation I selected that the backend may be used by other frontends and also that there might be other backends that this machine would use (can't remember exactly how it's worded).

Now, no matter what I try, the frontend cannot connect to the local backend. And...the backend setup can't connect to the database unless I use the root user/pw. I can use mysql client in terminal to login as the mythtv user, but for whatever reason, the setup requires root. I'm also getting the "No UPnP Backends" message in setup when I've got the mythtv user/pw in there instead of the root user/pw.

Now the completely insane thing is that the frontend can't connect to the backend regardless of the db settings (root or mythtv).

my router consistently gives this machine the ip 192.168.1.103, and that was pre-populated in a lot of places when I ran setup the first time. Tuner card, schedules direct and everything else set up ok, but the frontend won't connect.

In the quasi-terminal window that pops up when setup runs I see a "can't connect to database error" and "Driver error was [1/1045]" and "Access denied for user 'mythtv'@'MythTV-Lido' (using password: YES)".

I've checked ~.mythtv/mysql.txt and /etc/mythtv.txt and config.xml too. All have the right ipaddress, port username and pw for the database (192.168.1.103, 3306 and mythtv).

Any idea what to try next? I'd hate to have to reinstall for THIS, though sometimes that seems to be the only way to make some problems go away.

---

### Post by wyliecoyoteuk on 2011-01-07
7.10 to 10.10 may just be too big a step.
I have moved mine from 8.04 to 8.10. to 9.04, to 9.10, to 10.04, without any real issues.

As it is a MYSQL issue, have you tried installing sql-admin to see if you can figure out the permissions?

---

### Post by azmyth on 2011-01-07
I wonder if the computer name changed

cat /etc/hostname

---

### Post by newlinux on 2011-01-07
I'm going to ask a lot of questions (hard to troubleshoot somethings without being there).
I'm assuming you did a clean install of 10.10, correct? Did you restore the DB from your previous installation? If so what version of myth were you running? Also, I want to confirm that this frontend on is on the same machine as your master backend? If not what is your configuration?

Can you show us your frontend logs from when you it can't connect? Can you confirm that your backend is running?

You run the test SQL connection in  mythtbuntu-control-centre what happens?

Also, just a shot in the dark, but if this is a standalone backend/frontend combo, try putting in 127.0.0.1 in mythfrontend for the backend ip.

---

### Post by Lido on 2011-01-08
> **newlinux said:**
> I'm going to ask a lot of questions (hard to troubleshoot somethings without being there).
I'm assuming you did a clean install of 10.10, correct? Did you restore the DB from your previous installation? If so what version of myth were you running? Also, I want to confirm that this frontend on is on the same machine as your master backend? If not what is your configuration?

Can you show us your frontend logs from when you it can't connect? Can you confirm that your backend is running?

You run the test SQL connection in  mythtbuntu-control-centre what happens?

Also, just a shot in the dark, but if this is a standalone backend/frontend combo, try putting in 127.0.0.1 in mythfrontend for the backend ip.

Hi newlinux, your posts actually helped me quite a bit in my first Myth install back in 07 or so on the mythtvtalk forum. Glad to see you're still actively helping people out. Thank you!

It turned out that there was some kind of glitch in the mysql users table. There were three entries for root (host=localhost, MythTV-Lido, and 127.0.0.1), and two for mythtv (host=localhost and host=%, which I guess is a wildcard in mysql). I then ran this:
```
UPDATE user SET Password=PASSWORD('mythtv') WHERE user='mythtv';
```
and it said 2 rows matched, one changed.

Then for whatever reason the root user/pw started working so I plugged in mythtv user/pw and now that's working too. I figured it was something minor like that but couldn't see why it was rejecting both.

By the way, this is a clean 32bit install of 10.10, I didn't try to save any data from the old install. I still have the recordings directory with the files in it, but I don't expect to view them. I keep all my Myth files in a separate partition, which is the only partition that I didn't re-format when I did this clean install so I do still have my video files which I'll re-associate with this setup once it's working (knock on wood).

This is a front/back setup, though I do have another myth fe/be system on the network that I may eventually try to connect to, but for now, I'm happy to have it working standalone.

---

### Post by newlinux on 2011-01-08
that makes sense. Not sure how it got that way, but it makes sense. glad you have it working!

---

### Post by maxpowers43 on 2011-01-10
> **Lido said:**
> Hi newlinux, your posts actually helped me quite a bit in my first Myth install back in 07 or so on the mythtvtalk forum. Glad to see you're still actively helping people out. Thank you!

It turned out that there was some kind of glitch in the mysql users table. There were three entries for root (host=localhost, MythTV-Lido, and 127.0.0.1), and two for mythtv (host=localhost and host=%, which I guess is a wildcard in mysql). I then ran this:
```
UPDATE user SET Password=PASSWORD('mythtv') WHERE user='mythtv';
```and it said 2 rows matched, one changed.

Then for whatever reason the root user/pw started working so I plugged in mythtv user/pw and now that's working too. I figured it was something minor like that but couldn't see why it was rejecting both.

By the way, this is a clean 32bit install of 10.10, I didn't try to save any data from the old install. I still have the recordings directory with the files in it, but I don't expect to view them. I keep all my Myth files in a separate partition, which is the only partition that I didn't re-format when I did this clean install so I do still have my video files which I'll re-associate with this setup once it's working (knock on wood).

This is a front/back setup, though I do have another myth fe/be system on the network that I may eventually try to connect to, but for now, I'm happy to have it working standalone.
could you clarify the code? if it's a terminal command i'm messing it up. i have the same exact problem on a new install(2nd time..i to thought a reinstall would clear it up). thanks in advance

---

### Post by Lido on 2011-01-11
> **maxpowers43 said:**
> could you clarify the code? if it's a terminal command i'm messing it up. i have the same exact problem on a new install(2nd time..i to thought a reinstall would clear it up). thanks in advance

There are several things to check that could be the issue. Most of the threads like this one are pretty similar and newlinux (and others) seem to suggest that you check the following:

All the following files should have the same ip address and user/pw:
/etc/mythtv/config.xml
/etc/mythtv/mysql.txt
~/.mythv/config.xml
~/.mythv/mysql.txt

Then, login to mysql:
```
mysql -uroot -p
```
(it will ask for your mysql root pw and you'll need to know it and enter it (this is something you set up during the install).

At the mysql prompt:
```
mysql>GRANT ALL PRIVILEGES ON mythconverg.* TO 'mythtv'@"localhost" identified by "password here" WITH GRANT OPTION;
mysql>GRANT ALL PRIVILEGES ON mythconverg.* TO 'mythtv'@"%" identified by "password here" WITH GRANT OPTION;
mysql>use mysql;
mysql>UPDATE user SET Password=PASSWORD('password here') WHERE user='mythtv';
mysql>FLUSH PRIVILEGES;
mysql>exit

```

Then just make sure your frontend setup has the ip address 127.0.0.1 in it and the correct username and pw for the database and you should be set. If the backend setup can't connect to the db, then it will also ask you to enter that info and you'd enter the same thing there. It used to be that you could use "localhost" instead of the localhost ip address (127.0.0.1), but that didn't work for me (though it might still work for you, who knows).

From my experience, some things on myth work like magic and other things that seem like they would be easy end up being a struggle. A lot of times you end up trying what you think was the same thing several times and it finally ends up working.

My next struggle will be to try to get lirc working. I tried to install the new nvidia driver after downloading straight from their site but it did something to my install so I had to reinstall from scratch. Hopefully I won't have to do that again for a long time. My last install lasted from December 2007 until last week so once it's stable it's usually pretty good until I mess with something.

---

### Post by maxpowers43 on 2011-01-12
mysql>UPDATE user SET Password=PASSWORD('password here') WHERE user='mythtv';

sorry to be a pain but i couldn't get the line above to complete. first i got the error " no database selectedf" but i entered mythconverg.*and all seemed well.
then when entering line above i had a syntax error
tried it several different ways but evidently not the right way. thanks for your help

---

### Post by Lido on 2011-01-12
> **maxpowers43 said:**
> mysql>UPDATE user SET Password=PASSWORD('password here') WHERE user='mythtv';

sorry to be a pain but i couldn't get the line above to complete. first i got the error " no database selectedf" but i entered mythconverg.*and all seemed well.
then when entering line above i had a syntax error
tried it several different ways but evidently not the right way. thanks for your help

Sorry, I forgot one thing (edited the message above to correct it though). I copied all this stuff from another few sites and I'm fairly familiar with mysql so I omitted something. The first two lines grant access to the user 'mysql' on the database 'mythconverge', but you need to select the mysql database to update the user table. Try this line before the one that you're having trouble with:
```
use mysql;
```

---

### Post by maxpowers43 on 2011-01-13
i ended up getting it(i think). i used a gui mysql administration app. i'm now having fun with lirc as well. got the remote half way functioning for an hauppauge wintvpvrusb2. didn't think i'd ever use that old thing again! i have no scan option for channel setup. tried all three cable types for U.S. Can't get my directories for videos, etc setup right. i like all the options in various setup sections but some of the simple stuff like designating a directory to include in database could be way more intuitive. as it it there is no way my mom/sister could set this up. guess i'll have to break down and read the community docs and do it right. thanks a lot for your help.

---

### Post by nhtrader on 2011-01-22
Just installed Mythbuntu 10.10_32

I had the same problem and thanks to Lido's advice, I can connect to my database. I no longer jump into the database configuration setup and no longer see the error message " Myth could not connect to database. Please Verify your database settings below" on the first configuration page.

In addition, I found 6 files not 4 ...
/etc/mythtv/config.xml
/home/mythtv/.mythtv/config.xml
/home/dad/.mythtv/config.xml

/etc/mythtv/mysql.txt
/home/mythtv/.mythtv/mysql.txt
/home/dad/.mythtv/mysql.txt

As you can see, there are two users: mythtv and dad. Perhaps this is why this problem (cannot connect to database) occurs. When I installed MythTV I did a clean install (erased all contents of HDD) and made only a few changes to the defaults:

Change 1:   I selected these services: SSH, Samba, NFS, MythTV  (I added NFS and MythTV)

Change 2:   When the database configuration page appeared initially I changed the hostname to my computer name: kub_home
I changed the username to mt_dad
I changed the password to m0000

After reboot, I discovered that these 6 files cited above didn't match these changes. And I changed these files to match. I used 'localhost' as the hostname rather than the computer name 'kub_home'. Then I used Lido's mysql commands to fix/reset mysql's password

---

