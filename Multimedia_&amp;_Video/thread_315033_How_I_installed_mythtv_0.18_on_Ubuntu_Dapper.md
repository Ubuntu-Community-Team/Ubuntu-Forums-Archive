---
title: "How I installed mythtv 0.18 on Ubuntu Dapper"
date: 2006-12-08
forum: Multimedia &amp; Video
---

### Post by nomin on 2006-12-08
After reading an article in maximumpc saying mythtv is for "linux experts only" and seeing how long it took me to figure out how to get mythtv going compared to how few steps are actually involved, I figured I would record everything I did with this installation and put it in a message board to make things easier for both myself and anyone else interested.  I want to keep this as simple as possible and eventually make a step-by-step that anyone can follow.  

1) make sure your cable card is connected correctly by testing it with tvtime or kdetv.  Just open up synaptic then search for and install one of them.  I've found tvtime to be the better of the 2 on ubuntu dapper.  If you can watch tv and hear the sound you will be able to get mythtv going.  

2) Install mysql server 4.1.
     -- select "No Configuration" for postfix when prompted.
     -- select System->Administration->Services from the menu and disabled unwanted daemon tasks such as postfix

3) Install mythtv.
     -- asks for you to set mysql password
     	-- "configuring mythtv-backend" window opens with message in it saying to run mythtv-setup to complete mythtv installation.  There are instructions in it saying, "this program requires an X display, so you must either login to an X session as the 'mythtv' user, or otherwise arrange for that user to have access to your X display." plus some other essential information which I copied and pasted into text editor and saved it.  Then pressed the 'forward' button in the lower right corner of the window.
	-- received error message.  2 errors:  "E: mythtv-database: subprocess post-installation script returned error exit status 1"
"E: mythtv: dependency problems - leaving unconfigured"

4) 'mythtv' was created as a user on your computer.  You will then set a password for that user.  Then grant access rights to the mythtv user by editing the file /etc/group and mythtv to all groups that your original user is in. This will allow him to use sudo, access the cdrom etc.  

ex - admin:x:106:nomin,mythtv

5)logout of your session and log back in as mythtv

6) Now it's time to do some stuff in the terminal.  
Type these commands in this order in a terminal:
sudo mysql < /usr/share/mythtv/sql/mc.sql
mysql -u root mythconverg
grant all on mythconverg.* to mythtv@"%" identified by "mythtv";
flush privileges;
quit

7) Type this into a terminal to see if it lets you log into mysql:
[INDENT][/INDENT]mysql -u mythtv -p
     -if it works than so far so good.

8) change the password in /etc/mythtv/mysql.txt to mythtv

9) open up a terminal and type "mythtv-setup".  Go through each part of the setup in order and read through everything.  What you tell it to do determines whether it works or not.  

10) open terminal and type "mythfilldatabase"

11) sudo /etc/init.d/mythtv-backend start

12) tail -f /var/log/mythtv/mythbackend.log

13) mythfrontend
	---no luck getting channels yet

14) set up account with zap2it.

15) run mythtv-setup again and put in info about zap2it.

16) run "sudo /etc/cron.daily/mythtv-backend" as instructed and it will download from zap2it's database.

17) typed "mythbackend" then "mythfrontend"

-------and voila!  You should be running mythtv now.

P.S. - I'm going to continue to work on this how-to until it's as simple and straightforward as possible so any feedback will be helpful.

---

### Post by superm1 on 2006-12-08
Your living a bit in the past by using .18 on dapper..... .20 has been out for a few months now. I've got packages together for it at my own repository, [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1)

```
sudo gedit /etc/apt/sources.list
```
Add: 
```
         deb http://home.eng.iastate.edu/~superm1 dapper main
```

Add my key: 
```
wget http://home.eng.iastate.edu/~superm1/80DF6D58.gpg -O- | sudo apt-key add -
```

---

### Post by superm1 on 2006-12-08
> **nomin said:**
> 
P.S. - I'm going to continue to work on this how-to until it's as simple and straightforward as possible so any feedback will be helpful.

Also, its much better to add to the ubuntu documentation project for dapper rather then another howto that is missing lots of information.  The edgy version is finished, and the dapper is mostly a copy of it showing a few differences:

[http://help.ubuntu.com/community/MythTV](http://help.ubuntu.com/community/MythTV)

---

### Post by hurtman on 2007-02-12
Thank you!  I have been struggling with Mythtv for a couple of days now (database connection problems).  I've googled and googled to find the answers to my mythtv installation problems.  This is by far the best guide on the net.  Following this procedure installed mythtv flawlessly on my computer.  I used mysql 5.0  instead of 4.1 and installed it on Ubuntu Edgy using these same instructions.  Thanks!

---

