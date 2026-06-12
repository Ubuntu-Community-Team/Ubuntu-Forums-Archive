---
title: "Unable to connect to master backend server"
date: 2010-03-13
forum: Mythbuntu
---

### Post by CheapoDepot on 2010-03-13
Linux n00b here. I've been using Mythbuntu 8.10 for about 6 months with no recent problems until now.

Here is my setup. I have a combined frontend/backend server in the basement and xbmc on xbox connecting to server through SMB shares. This has worked great for months without any problems.

All of a sudden, on Wednesday, my xbmc could not find any smb shared folders. I checked the server and using the frontend could not get in. It asked me to select language. The says "No UPnP backends found". The it takes me to Database Configuration page. I keep all the information here the same because that is what was working before. It then gives me this message. "Could not connect to the master backend server -- is it running? Is the IP address set for it in the setup program correct?" Then it keeps repeating.

I checked the /var/log/mythtv/mythbackend.log. The file size has inflated to approx. 600 mb. It keeps repeating the same message over and over.

> Cannot login to database?

Would you like to configure the database connection now? [yes]  
[console is not interactive, using default 'yes']
Database host name: [192.168.1.104]  
[console is not interactive, using default '192.168.1.104']
Should I test connectivity to this host using the ping command? [yes]  
[console is not interactive, using default 'yes']
Database non-default port: [0]  
[console is not interactive, using default '0']
Database name: [mythconverg]  
[console is not interactive, using default 'mythconverg']
Database user name: [mythtv]  
[console is not interactive, using default 'mythtv']
Database password: [C1RFOKlE]  
[console is not interactive, using default 'C1RFOKlE']
Unique identifier for this machine (if empty, the local host name will be used):  
[console is not interactive, using default '']
Would you like to use Wake-On-LAN to retry database connections? [no]  
[console is not interactive, using default 'no']
2010-03-13 12:06:28.017 Unable to connect to database!
2010-03-13 12:06:28.040 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'yoda.local' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-03-13 12:06:28.136 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2010-03-13 12:06:28.187 Cannot login to database?
2010-03-13 12:06:28.188 Cannot login to database?192.168.1.104 is the local IP address of the backend/frontend server.

I looked earlier in the log file from wednesday. This is what it says.

> 2010-03-09 07:24:23.688 Expiring 1113 MBytes for 1011 @ Sat Jan 9 17:30:00 2010 => Unknown
2010-03-09 07:24:23.694 Expiring 1114 MBytes for 1011 @ Sat Jan 9 18:00:00 2010 => Unknown
2010-03-09 07:24:23.696 Expiring 1112 MBytes for 1011 @ Sat Jan 9 18:30:00 2010 => Unknown
2010-03-09 07:24:23.697 Expiring 1113 MBytes for 1011 @ Sat Jan 9 19:00:00 2010 => Unknown
2010-03-09 07:24:23.698 Expiring 1113 MBytes for 1011 @ Sat Jan 9 19:30:00 2010 => Unknown
2010-03-09 07:24:23.698 Expiring 1114 MBytes for 1011 @ Sat Jan 9 20:00:00 2010 => Unknown
2010-03-09 07:24:23.699 Expiring 1113 MBytes for 1011 @ Sat Jan 9 20:30:00 2010 => Unknown
2010-03-09 07:24:23.699 Expiring 1113 MBytes for 1011 @ Sat Jan 9 21:00:00 2010 => Unknown
2010-03-09 07:24:23.702 Expiring 711 MBytes for 1011 @ Sat Jan 9 21:30:00 2010 => Unknown
2010-03-09 07:24:23.706 Expiring 1113 MBytes for 1005 @ Sun Jan 10 19:00:00 2010 => Unknown
2010-03-09 07:24:23.710 Expiring 1114 MBytes for 1005 @ Sun Jan 10 19:30:00 2010 => Unknown
2010-03-09 07:24:23.714 Expiring 1112 MBytes for 1005 @ Sun Jan 10 20:00:00 2010 => Unknown
2010-03-09 07:24:23.718 Expiring 106 MBytes for 1005 @ Sun Jan 10 20:30:00 2010 => Unknown
2010-03-09 07:24:23.696 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/yoda/1011_20100109173000.mpg. File doesn't exist.  Database metadata will not be removed.
2010-03-09 07:24:23.728 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/yoda/1011_20100109180000.mpg. File doesn't exist.  Database metadata will not be removed.
2010-03-09 07:24:23.732 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/yoda/1011_20100109183000.mpg. File doesn't exist.  Database metadata will not be removed.
2010-03-09 07:24:23.736 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/yoda/1011_20100109190000.mpg. File doesn't exist.  Database metadata will not be removed.
2010-03-09 07:24:23.740 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/yoda/1011_20100109193000.mpg. File doesn't exist.  Database metadata will not be removed.
2010-03-09 07:24:23.748 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/yoda/1011_20100109200000.mpg. File doesn't exist.  Database metadata will not be removed.
2010-03-09 07:24:23.756 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/yoda/1011_20100109203000.mpg. File doesn't exist.  Database metadata will not be removed.
2010-03-09 07:24:23.764 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/yoda/1011_20100109210000.mpg. File doesn't exist.  Database metadata will not be removed.
2010-03-09 07:24:23.772 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/yoda/1011_20100109213000.mpg. File doesn't exist.  Database metadata will not be removed.
2010-03-09 07:24:23.780 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/yoda/1005_20100110190000.mpg. File doesn't exist.  Database metadata will not be removed.
2010-03-09 07:24:23.788 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/yoda/1005_20100110193000.mpg. File doesn't exist.  Database metadata will not be removed.
2010-03-09 07:24:23.792 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/yoda/1005_20100110200000.mpg. File doesn't exist.  Database metadata will not be removed.
2010-03-09 07:24:23.796 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/yoda/1005_20100110203000.mpg. File doesn't exist.  Database metadata will not be removed.
2010-03-09 07:26:19.433 UPnpMedia: BuildMediaMap VIDEO scan starting in :/mythtv/yoda232/:
2010-03-09 07:26:20.242 UPnpMedia: BuildMediaMap Done. Found 1892 objects
2010-03-09 07:39:23.743 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-03-09 07:39:23.749 Expiring 1076 MBytes for 1064 @ Tue Sep 22 21:31:01 2009 => Unknown
2010-03-09 07:39:23.752 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/yoda/1064_20090922213101.mpg. File doesn't exist.  Database metadata will not be removed.
2010-03-09 07:39:23.752 Expiring 87 MBytes for 1064 @ Tue Sep 22 22:00:00 2009 => Unknown
2010-03-09 07:39:23.760 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/yoda/1064_20090922220000.mpg. File doesn't exist.  Database metadata will not be removed.
2010-03-09 07:39:23.760 Expiring 1113 MBytes for 1011 @ Sat Jan 9 17:30:00 2010 => Unknown
2010-03-09 07:39:23.768 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/yoda/1011_20100109173000.mpg. File doesn't exist.  Database metadata will not be removed.
2010-03-09 07:39:23.768 Expiring 1114 MBytes for 1011 @ Sat Jan 9 18:00:00 2010 => Unknown
2010-03-09 07:39:23.776 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/yoda/1011_20100109180000.mpg. File doesn't exist.  Database metadata will not be removed.
2010-03-09 07:39:23.776 Expiring 1112 MBytes for 1011 @ Sat Jan 9 18:30:00 2010 => Unknown
2010-03-09 07:39:23.784 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/yoda/1011_20100109183000.mpg. File doesn't exist.  Database metadata will not be removed.That repeats as well. I'm assuming that those .mpg files were recorded shows off of cable that I deleted. The thing is, I deleted those files months ago and havent even used cable on the server since then. I did delete them manually by going into the folder in the UBUNTU OS and SHIFT-DEL. I read somewhere that maybe I should have deleted them within MYTHBUNTU interface?

The last thing I can think of is that I have a partition that is seperate from the Mythbuntu OS where I keep all of my media files. My recorded files that I deleted were on this same partition. Well that partition reached 100% storage on Wednesday. Maybe this triggered all of these problems? I've reached 100% before without error and just deleted a few files and it worked fine.

It's a long winded explanation but I figure the more info, the better.

Any help is appreciated. Thanks.

---

### Post by azmyth on 2010-03-13
I suspect a password/permission issue, a network issue, or BE is not running.

"Access denied for user 'mythtv'@'yoda.local' (using password: YES)"

First thing I do is make sure the BE is running with

ps -A | grep mythback

If this looks good, then I'd try to ping the BE server from a different PC on the network.

If this looks good, I'd check your pass hasn't changed.

I'd also check to make sure the BE server IP hasn't changed with ifconfig and make sure the IP is correct in mythtv-setup.

---

### Post by CheapoDepot on 2010-03-13
ps -A | grep mythback
This command shows the following...
> 5260?       00:01:09 mythbackendDoes that mean that the backend is running?


Using a windows pc onthe network and in the command prompt, I entered the following.
> ping 192.168.1.104I did receive a response.


The mythcoverg password is "C1RFOKlE" when logging in.
/etc/mythtv/mysql.txt has the following...
> DBHostName=192.168.1.104

# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
DBHostPing=no

DBUserName=mythtv
DBPassword=C1RFOKlE
DBName=mythconverg
DBType=QMYSQL3
So the password looks the same.
Is there another place to check the password?


In myth-tv setup, 192.168.1.104 is entered.
As shown above, /etc/mythtv/mysql.txt has DBHostName=192.168.1.104.
ifconfig reveals the following... (I don't know how to copy from terminal so I type it here)
> eth0      Link encap:Ethernet
             inet addr:192.168.1.104
lo          Link encap:Local Loopback
            inet addr:127.0.0.1Are there any other places to check the IP address?

---

### Post by CheapoDepot on 2010-03-13
I don't know if this helps but I can access mysql mythconverg as user mythtv by entering the following...
> 
$mysql -u mythtv mythconverg -p
Enter password: C1RFOKlE

Not that I would know what to do after accessing it.

---

### Post by 4dognight on 2010-03-14
Access denied for user 'mythtv'@'yoda.local' (using password: YES)

Is yoda defined in your /etc/hosts file?

---

### Post by CheapoDepot on 2010-03-14
Below is what is in my /etc/hosts file...
> 
127.0.0.1    localhost
127.0.1.1    yoda

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
Does 127.0.1.1 need to be 192.168.1.104?

---

### Post by 4dognight on 2010-03-14
yes. Assuming that is the IP address you configured in mythtv for the backend.

---

### Post by CheapoDepot on 2010-03-16
Ok, I figured out a couple of things in the past few days.

First, I entered the following and it solved my backend server problem while leaving the settings as they were previously.
> 
sudo /etc/init.d/mythtv-backend start
I was then able to use the frontend (same computer as backend) with no problems. The following error then ceased in my log file thus slowing down the log entries and log file size.

Access denied for user 'mythtv'@'yoda.local' (using password: YES)

Second, I still had errors in the log file as shown below. This error was in my first post. The error also kept making log entries, but much slower.
> 
2010-03-09 07:24:23.688 Expiring 1113 MBytes for 1011 @ Sat Jan 9 17:30:00 2010 => Unknown
2010-03-09 07:24:23.696 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/yoda/1011_20100109173000.mpg. File doesn't exist. Database metadata will not be removed.
This error was caused by deleting the recorded files outside of mythtv. It left some metadata or something still in mythtv. Here is how I fixed it.
Opened mythtv and went to "Watch Recordings". Select each individual recorded video that does not exist and delete, delete, delete.

However, not all of my problems are solved. I still cannot connect to my ubuntu samba shares on other computers or xbox. I tried restarting samba with the following command but still can't connect to the shares.
> 
sudo /etc/init.d/samba restart
If anyone has any ideas, please let me know.

I don't get how the server was working fine one day and then all of these issues came up all of a sudden. Things like this shouldn't just happen should they? It seems like I would have had to have done something to cause this to happen.

---

### Post by CheapoDepot on 2010-03-16
All problems are now solved.

Somehow my samba shared folders were removed. It's funny though, that was the first thing I checked when I started having all these problems and it looked fine.

I entered the following command today before checking the samba shared folders. I doubt this is what solved my problem because it's just a tool to be able to share through nautilus. What can I say? I was getting desperate!
> 
sudo apt-get install nautilus-share
I went to Applications>System>Shared Folders. All my SMB shares were gone. I went through and hit Add>Other and selected my folders. Everything works great now!

For anyone who may have the same trouble as me, there are your three quick and easy methods.

Still no idea how it happened...

Thanks to everyone who helped!

---

