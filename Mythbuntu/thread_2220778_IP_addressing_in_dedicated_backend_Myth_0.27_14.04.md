---
title: "IP addressing in dedicated backend Myth 0.27 14.04"
date: 2014-04-29
forum: Mythbuntu
---

### Post by drink1297 on 2014-04-29
I have reinstalled the backend as dedicated now 2x, and I am unable to set the IP address in General Setup on the backend as stated in the quick start guide:

[COLOR=#000000][FONT=Ubuntu]Ensure that both the “Local Backend” IP address and the “Master Backend” IP Address are the same as the static IP address you set in Network Manager. 

[SIZE=2]The 'Local Backend' shows loopback 127.0.0.0, and I can highlight it, but not enter my static IP.

The "Master Backend", I can configure to my static IP just fine.

This is preventing the frontends from connecting...any ideas how to fix it?

This is my 5th install now....I originally had 10.04, until it crashed, then 12.04 last week, and was working great, until I tried to add another capture card, and it crashed, then I tried re-install, and I had the same issue, so I thought I would bump up to 14.04, and still the same????

I also am struggling with the Haupuage 1250, I have 2, only one works, and then a 2250 which on boot I recieve the sa7164 are missing...those are not that big a deal, if I can get the frontends connecting, I will get the HDhomerun and run with it.

I have checked the ports for mysql and they are default 3306, problem is I don't even recieve an error on the frontend, it just runs through the setup, and then when I finish, it returns back to it, and I know from prior installs that loopback address is killing me, I just don't know how to change it outside the GUI....[/SIZE]
[/FONT][/COLOR]

---

### Post by drink1297 on 2014-04-29
Here is the Mythtv-backend.log 

Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

---

### Post by drink1297 on 2014-04-29
mike@MythServer:~$ sudo netstat -tap |grep mysql
tcp        0      0 localhost:mysql         *:*                     LISTEN      6381/mysqld     

That should be 3306.....that is waht the xml file shows???

---

### Post by drink1297 on 2014-04-29
I found in the /etc/mysql/conf.d/mythtv.cnf file that the bind address was set to 0.0.0.0

I have adjusted this, but I am at work and remoting into the box, and actually left it scanning for channels when I left, so I will have to see what happens when I get home....

---

### Post by drink1297 on 2014-04-29
mike@MythServer:/etc/mysql/conf.d$ sudo netstat -tap |grep mysql
tcp        0      0 10.1.1.15:mysql         *:*                     LISTEN      7899/mysqld    

Getting better I think

---

### Post by drink1297 on 2014-04-30
Looks like I have traced the issue down to the server is not installing as a Master backend, and I have no idea why...I did 2 more fresh installs on it, one as a stand alone master backend, and one as a backend/frontend combo, and the 127.0.0.0 still will not let me adjust it to the correct IP.

Now, I was able to hit the config.xml file in /etc/mythtv, as well as /home/<user>/.mythtv and adjust, but when I start the backend it starts as a slave, and then (get this) connects to itself as a master backend, but runs as a slave....

I am unsure where or what file I need to hit to make this the master backend...I even followed the install from the 14.04 website to the letter, and I am unable to change the first IP in the General settings of the backup....but the 1250 Hauppauge (one of them anyway) does work.  

I may tru and drop back to 12.04 with Myth 0.26, get everything set up and working, then upgrade to 0.27, which seemed to work prior to my hosing the system.

Any advice here before my head pops off would be appreciated...or if anyone has had the same issue??

---

### Post by drink1297 on 2014-04-30
Well...the new install didn't get SSH installed, so while at work there is nothing I can do, but I am going to try and add the 0.27 Master Backend into the repositories, and get it downloaded and rerun the set up to see if that will allow me to configure the IP's as needed

---

### Post by drink1297 on 2014-05-02
So I did solve the issue...and here is how...

First I reinstalled 12.04 with myth 0.26, from here I was able to configure both IP address' in the backend set up. (Then I upgraded to 0.27)
Now....it get's tricky, because I was never able to get the frontend to connect to the backend, not even with myth 0.26 as I had prior.

Turns out, I probably could have stayed with 14.04 even though I could not change the 127.0.0.1 IP in the backend GUI...here is why....

The understanding I have of the GUI, the top IP configures the GLOBAL my.cnf (/etc/mysql.my.cnf) file with a bind address of 127.0.0.1, and thinking about it, probably not a big deal, because mythtv.cnf takes priority over that file (that should be the 2nd IP in the GUI)
So after the install, you could change the my.cnf BIND address (which I did...and like a dummy I also changed the user to mythtv from mysql <-----bad move, no write access at all...figured it out quick though)
Then in /etc/mysql/conf.d/mythtv.cnf I also changed the bind address to my static ip.....

Reboot the machine (or restart mysql if your good, which I am not) and you should connect :)

For the newbs in MythTv....

This is your friend.... mysql -u mythtv -p  (run it on the backend, enter your password at the prompt)
You should get the mysql> prompt, type use mythconverge
then type show tables

If you have access you should see a list of the mythconverg tables, so far so good....NOW...

exit mysql by typing exit

then mysql -u mythtv -h <your servers IP address> -p

if you can access the database, your my.cnf and mythtv.cnf bind address' are good, if not, adjust them, restart mysql or reboot the machine, and try the command again.

Assuming it works, login to your front end, and run 

mysql -u mythtv -h <your backends IP address> -p
hopefully, your at a mysql> prompt, if not double check the .cnf files BIND address
if you are, you should be able to connect the frontend to the backend, and off you go to watch TV :)

Thanks to all who post in the forums, I have not often struck out on my own to mess with these files, but over years of using MythTV, and accessing forums, I have learned many commands, locations of many files, and none of this would happen without the support of the community.
If your a newb to myth tv, yes...I agree...there are DAY's that go by when you want to rip your hair out, chuck the whole thing...but remember....the forums will teach you more about Linux, and MythTV than any school ever could, they have the most knowledgable people, and some of the best documentation on the system.  Trust me, your learning more than you think...stick with it, because in the end, it is SOOOO worthwhile....

Thanks again to everyone on the forums.

---

### Post by drink1297 on 2014-05-02
One other note for the newbs...check your logs, if you don't know which ones, or where they are:

at your prompt type: locate *.log
you should get a list mostly of /var/log/some.log

Read through it, check the one that looks right, you'll know it when you see it

---

### Post by QA_manager on 2014-09-17
Did you ever solve the problem of 14.04 installing a slave backend even when you select 'Master Backend' during the install process? I am trying to solve that problem here: [http://ubuntuforums.org/showthread.php?t=2244220&page=2](http://ubuntuforums.org/showthread.php?t=2244220&page=2)

No success yet.

---

