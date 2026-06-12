---
title: "change backend address without gui?"
date: 2014-02-02
forum: Mythbuntu
---

### Post by pgreenwood on 2014-02-02
New to mythtv. I have mythbuntu 12.04.3 64-bit mythtv 0.25

Somehow I've developed a conflict with the backend ip address. I was trying to change the address from 127.0.0.1 to 192.168.80.1 so to run frontend on a remote computer with the LiveCD.

mythtv-setup complains that it cannot find the backend. [How] can I go into a file(s) somewhere behind the GUI and change the backend ip address to 127.0.0.1? Forgive the oversight if this question has been already answered. I can't find it.

What is the best practice for changing backend ip address to a network-discoverable address? Thank you!

========~$ mythbackend
2014-02-02 10:47:32.630354 C  mythbackend version: fixes/0.25 [v0.25.2-15-g46cab93] [www.mythtv.org](www.mythtv.org)
2014-02-02 10:47:32.630396 C  Qt version: compile: 4.8.1, runtime: 4.8.1
2014-02-02 10:47:32.630408 N  Enabled verbose msgs:  general
2014-02-02 10:47:32.630443 N  Setting Log Level to LOG_INFO
2014-02-02 10:47:32.630536 I  Added logging to the console
2014-02-02 10:47:32.630552 I  Added database logging to table logging
2014-02-02 10:47:32.630664 N  Setting up SIGHUP handler
2014-02-02 10:47:32.640710 N  Using runtime prefix = /usr
2014-02-02 10:47:32.640741 N  Using configuration directory = /home/pat/.mythtv
2014-02-02 10:47:32.643424 I  Assumed character encoding: en_US.UTF-8
2014-02-02 10:47:32.711399 I  Using localhost value of newmyth
2014-02-02 10:47:32.711676 I  Testing network connectivity to 'mythtv'
2014-02-02 10:47:32.714041 I  Starting IO manager (write)
2014-02-02 10:47:32.714154 I  Starting IO manager (read)
2014-02-02 10:47:32.715845 I  Starting process signal handler
2014-02-02 10:47:32.715959 I  Starting process manager

Cannot login to database?

Would you like to configure the database connection now? [no]  2014-02-02 10:47:32.898463 E  Unable to connect to database!
2014-02-02 10:47:32.898501 E  Driver error was [1/2003]:
QMYSQL: Unable to connect
Database error was:
Can't connect to MySQL server on 'mythtv' (111)

2014-02-02 10:47:32.898558 A  Cannot login to database?

2014-02-02 12:49:37.569375 E  Read from stdin failed
2014-02-02 12:49:37.569421 C  Failed to init MythContext.

---

### Post by blm-ubunet on 2014-02-02
The backend error is that it can not connect to mysql DB server.

The mythtv programs use file /home/"user"/.mythtv/config.xml (& other locations as fallback) for DB credentials etc.

A remote FE or BE has to be able to find the databse server (mysql) to then find info to find other FE & BEs.

First make sure you have a database backup stored safely somewhere..

You should attempt to get FE/BE working with real IP address on the same PC before adding an additional remote FE.
I think you are doing just that.

Several things that can go wrong when moving from BE/FE localhost machine to network setup:
- not able to login to mysql
- mysql only listening on 127.0.0.1
- mythconverg DB privileges

& then need mythtv programs to find the mysql server (on the new IP address)

Both these deal with DB privileges etc:
[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)
[http://www.mythtv.org/wiki/Category:MySQL](http://www.mythtv.org/wiki/Category:MySQL)
Note the comments/warnings about changing hostnames (shouldn't be prob here).

You can debug mysql by attempting to connect to mysql & use mythconverg table.
mysql -h192.168.80.1 -u"mythtvuser" -p"mythtvpassword" mythconverg
(quit) to exit..

---

### Post by pgreenwood on 2014-02-02
> **blm-ubunet said:**
> 
You can debug mysql by attempting to connect to mysql & use mythconverg table.
mysql -h 192.168.80.1 -u "mythuser" -p "password" mythconverg
(quit) to exit..

Thank you blm. looking for available databases:
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| test               |
+--------------------+
2 rows in set (0.01 sec)

I'm troubleshooting from a neighboring computer over ssh. I'll go through your suggestions and report back. Thanks for your help!

---

### Post by blm-ubunet on 2014-02-03
Your result (from show databases) suggests that the IP 192.168.80.1 could be another PC with mysql server running but not one that has had a functioning master backend.

Mythtv-setup connects to mysql server using credentials in /home/"user"/.mythtv/config.xml.
Note that the login session user is not necessarily "mythtv".
Mythbackend runs as user "mythtv".

Assuming your mythtv user & passwords are mythtv etc..
From the actual master backend with the mysql server...
```
echo "select * from settings where value=\"MasterServerIP\" " | mysql -h192.168.80.1 -umythtv -pmythtv mythconverg
```
&
```
echo "select * from settings where value=\"MasterServerIP\" " | mysql -h172.0.0.1 -umythtv -pmythtv mythconverg

```
should both work..
or your cmd:
echo "show databases " | mysql -h192.168.80.1 -umythtv -pmythtv

A remote computer should only work with the first line if & only if the mysql server is listening on the correct IP.

Did you change anything in /etc/mysql/my.cnf ?

Mysql does not start correctly (listening on real IP) if networking is not up..The upstart script should be handling that condition.

---

### Post by pgreenwood on 2014-02-08
> **blm-ubunet said:**
> Your result (from show databases) suggests that the IP 192.168.80.1 could be another PC with mysql server running but not one that has had a functioning master backend.

  <snip>

Did you change anything in /etc/mysql/my.cnf ?

Mysql does not start correctly (listening on real IP) if networking is not up..The upstart script should be handling that condition.

I think i will mark this [SOLVED] but I didn't really ever find the answer to the question whether the discoverable IP address is stored anywhere other than in /etc/mysqk/my.cnf or other text files in  /etc or /home directories. I had thought that I might have had a disconnect between these configuration files and something stored in mythconverg, but was never able to dive far enough into mythconverg to find out. 

I may or may not have changed anything in /etc/mysql/my.cnf, I can't recall. I more likely changed the IP address in the backend gui but failed to change it in my.cnf.

I ran mythtv-setup several times in an effort to capture code to paste back here for diagnostics, when, surprisingly, the backend gui came back. Now I think I'm back where I was when I started this thread. As a wise troubleshooter once said, many have chased this phantom!

> **blm-ubunet said:**
> echo "show databases " | mysql -h127.0.0.1 -umythtv -pmythtv

this did return the expected list of databases, but I never got any further than that.

I shall now proceed, cautiously, to see if I can change my backend address from 127.0.0.1 to something remotely discoverable. Thanks for your support!

---

### Post by blm-ubunet on 2014-02-08
All the mythtv programs (& some 3rd party scripts) use the contents of config.xml file to determine hostnames, preferred backend  & IP address of the mysql server.
I believe the original contents of these file(s) are auto-generated from the first time run of "mythtv-setup".
The database contains this info but it does not know which localhostname etc you (might) want to use.
 
It is possible to have the frontend connect to different master backends (good for expts) by having multiple config.xml files & use of an environmental variable.

There are multiple locations that are searched (in a hierarchical order) for config.xml.
~/.mythtv/config.xml
if not found then there 
/etc/mythtv/config.xml

The home folder changes with the "user"...mythtv backend runs as user "mythtv"
so  /home/mythtv/.mythtv/config.xml.

I symlink the "users" home folder locations to the same /etc/mythtv.config.xml file.

Mythtv-setup does not connect to the mythbackend (mythbackend is stopped & must be not running)...
Myth-setup connects to mysql server.

---

### Post by uteck on 2014-02-08
The esiest way to get MythBuntu to allow remote frontends to connect is by using the mythbuntu-control-centre gui which will make the changes for you in the system-roles section.
Otherwise I think you have to edit /etc/mysql/my.cnf on the backend server and change "bind-address  =127.0.0.1" to use the IP.  Then restart MySQL and MythBackend, or reboot.

---

### Post by pgreenwood on 2014-02-10
> **uteck said:**
> The esiest way to get MythBuntu to allow remote frontends to connect is by using the mythbuntu-control-centre gui <snip>

Hey, Uteck! I think I've been following you around since Libranet! Thanks for the input. I'm pleased to have it (and a little gun-shy with my first foray into mythtv). I'll try your suggestions as I know they come with a lot of experience.

Here's a new one on me: In attempting to set a static address for the mythtv NIC, I edited /etc/network/interfaces to specify eth0 as 192.168.0.9. Ok. Nothing seemed to change; it still stayed connected to the internet. But tonight I ran ~$ ip a which returned this:
pat@mythtv:/var/lib/mythtv$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN.
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host.
       valid_lft forever preferred_lft forever
2: eth1: <a wireless card I'm not using>
3: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:13:20:d0:fb:40 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.13/24 brd 192.168.0.255 scope global eth0
    inet 192.168.0.9/24 brd 192.168.0.255 scope global secondary eth0
    inet6 fe80::213:20ff:fed0:fb40/64 scope link.
       valid_lft forever preferred_lft forever

I can ping either 192.168.0.13 OR 192.168.0.9 from another machine on the network or ssh to the
computer over either address. So It looks like I have a static address AND a dynamic address from the DHCP server on the router? I guess I'll run with it until it creates problems.

---

### Post by pgreenwood on 2014-02-11
> **uteck said:**
> The esiest way to get MythBuntu to allow remote frontends to connect is by using the mythbuntu-control-centre gui which will make the changes for you in the system-roles section.
Otherwise I think you have to edit /etc/mysql/my.cnf on the backend server and change "bind-address  =127.0.0.1" to use the IP.  Then restart MySQL and MythBackend, or reboot.

I believe I've changed every instance of 127.0.0.1 in my.cnf files and changed bind address = 192.168.0.9 and rebooted but continue to get the error

    failed to connect to database at 'mythconverg'@'127.0.0.1' for user 'mythtv' with password 'xxxxxxx'.

when attempting to launch a remote frontend. Any suggestions would be appreciated.

Here's what I get when I run ~$ mythbackend
2014-02-11 00:13:48.130985 C  mythbackend version: fixes/0.25 [v0.25.2-15-g46cab93] [www.mythtv.org](www.mythtv.org)
2014-02-11 00:13:48.131026 C  Qt version: compile: 4.8.1, runtime: 4.8.1
2014-02-11 00:13:48.131038 N  Enabled verbose msgs:  general
2014-02-11 00:13:48.131072 N  Setting Log Level to LOG_INFO
2014-02-11 00:13:48.131165 I  Added logging to the console
2014-02-11 00:13:48.131181 I  Added database logging to table logging
2014-02-11 00:13:48.131292 N  Setting up SIGHUP handler
2014-02-11 00:13:48.131383 N  Using runtime prefix = /usr
2014-02-11 00:13:48.131409 N  Using configuration directory = /home/pat/.mythtv
2014-02-11 00:13:48.131583 I  Assumed character encoding: en_US.UTF-8
2014-02-11 00:13:48.132244 E  DBHostName is not set in mysql.txt
2014-02-11 00:13:48.132503 N  Empty LocalHostName.
2014-02-11 00:13:48.132515 I  Using localhost value of mythtv
2014-02-11 00:13:48.132714 I  Testing network connectivity to '192.168.0.9'
2014-02-11 00:13:48.137410 I  Starting IO manager (write)
2014-02-11 00:13:48.137898 I  Starting IO manager (read)
2014-02-11 00:13:48.138937 I  Starting process signal handler
2014-02-11 00:13:48.139510 I  Starting process manager
2014-02-11 00:13:48.312556 N  Setting QT default locale to en_US
2014-02-11 00:13:48.312665 I  Current locale en_US
2014-02-11 00:13:48.312738 N  Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2014-02-11 00:13:48.327832 I  Current MythTV Schema Version (DBSchemaVer): 1299
2014-02-11 00:13:48.328378 I  Loading en_us translation for module mythfrontend
2014-02-11 00:13:48.329423 N  MythBackend: Starting up as the master server.
2014-02-11 00:13:48.442790 E  DTVMux: ParseTuningParams -- Unknown tuner type = 0x2000
2014-02-11 00:13:48.442865 E  DTVChan(192.168.0.18-0): SetChannelByString(6-1): Failed to initialize multiplex options
2014-02-11 00:13:48.565977 E  DTVMux: ParseTuningParams -- Unknown tuner type = 0x2000
2014-02-11 00:13:48.566051 E  DTVChan(192.168.0.18-1): SetChannelByString(6-1): Failed to initialize multiplex options
2014-02-11 00:13:48.673025 E  DTVMux: ParseTuningParams -- Unknown tuner type = 0x2000
2014-02-11 00:13:48.673097 E  DTVChan(192.168.0.18-2): SetChannelByString(6-1): Failed to initialize multiplex options
2014-02-11 00:13:48.679080 W  Scheduler: Listings source '' is defined, but is not attached to a card input.
2014-02-11 00:13:48.680510 I  Found 1 distinct programid authorities
2014-02-11 00:13:48.687422 I  New static DB connectionSchedCon
2014-02-11 00:13:48.692101 E  Failed listening on TCP 127.0.0.1:6544 - Error 8: The bound address is already in use
2014-02-11 00:13:48.692129 E  MediaServer::HttpServer Create Error
2014-02-11 00:13:48.694288 E  Failed listening on TCP 127.0.0.1:6543 - Error 8: The bound address is already in use
2014-02-11 00:13:48.694313 C  Backend exiting, MainServer initialization error.
2014-02-11 00:13:58.687589 I  Running housekeeping thread

If there are other helpful diagnostics, let me know. Thanks.

---

### Post by pgreenwood on 2014-02-11
I had set my computer NIC IP to 192.168.0.9 and also set the backend to 192.168.0.9. I thought that might be the problem, but I reset the NIC IP to 192.168.0.8 leaving the backend at 192.168.0.9 and rebooted -- no change

failed to connect to database at 'mythconverg'@'127.0.0.1' for user 'mythtv' with password 'xxxxxxx'.

===update at 11:32 looking at a deprecated install of linuxmce (which sets the backend ip at 192.168.80.1 by default) on my computer I saw that /etc/mysql/my.cnf had bind=0.0.0.0 so I edited my mythbuntu /etc/mysql/my.cnf accordingly and it seems like it may work, but I'm away from my computer now so I can't tell for sure.

---

### Post by uteck on 2014-02-12
> **pgreenwood said:**
> I had set my computer NIC IP to 192.168.0.9 and also set the backend to 192.168.0.9. I thought that might be the problem, but I reset the NIC IP to 192.168.0.8 leaving the backend at 192.168.0.9 and rebooted -- no change

failed to connect to database at 'mythconverg'@'127.0.0.1' for user 'mythtv' with password 'xxxxxxx'.

===update at 11:32 looking at a deprecated install of linuxmce (which sets the backend ip at 192.168.80.1 by default) on my computer I saw that /etc/mysql/my.cnf had bind=0.0.0.0 so I edited my mythbuntu /etc/mysql/my.cnf accordingly and it seems like it may work, but I'm away from my computer now so I can't tell for sure.
The error you posted says the frontend is looking for the database on itself (127.0.0.1) and not on the backend server IP of 192.168.0.9.
Try rerunnng mythbuntu-control-center on the fronend and in the "System Roles" section and check "No Backend" and "Desktop Frontend"  It should have an option to test the connection.  

If that does not work, check the setting on the backend.
If the backend does not have a monitor attached, you can use "ssh -X 192.168.0.9" to connect with X-windows forwarding, then you can run mythbuntu-control-center and it will display on the machine you are at.  Set the role as Primary Backend.  That should configure everything properly to enable connections.

It's been a few years since I had to change my settings, so I have probably forgotten how to manually do it.

Ah Libranet....that brings back memories. :-)

---

### Post by pgreenwood on 2014-02-13
update at 2/13/14 -- BE and FE seem to work ok together on the Master Backend box (I think that's the correct terminology) but when I run the LiveCD Mythbuntu disk on a remote computer to test a remote frontend I get 

failed to connect to database at 'mythconverg'@'mythtv' for user 'mythtv' with password 'xxxxxxx' 

I need help developing an appropriate troubleshooting path for this problem. I'm SO CLOSE to success! Thank you all!

---

### Post by uteck on 2014-02-14
Master backend is the correct term.  The database on the backend needs to be told to allow remote connections, in the mythbuntu control center, look in the MySQL section and enable it work on the ethernet.  I forgot to mention that step last time.
You can change the security key if you want, but that I think everyone leaves it at 0000.

---

### Post by pgreenwood on 2014-02-14
For context, for others in a similar situation and for myself, next week, when I have to reinstall this beast (which I haven't had to do yet, not counting the LinuxMCE 10.04 install which didn't work with the HDHR3-CC because it was only MythTV 0.24), I have Mythbuntu 12.4.03 64-bit on a tower BE-FE with monitor. Just yesterday with intervention from Cox Omaha, my cable card finally delivered all the content I'm paying for in my subscription, not just the SD and HD ClearQAM channels. She said she unpaired and re-paired the card to accomplish this. She did tell me that the Cox-supplied Motorola Tuning Adapter is really not necessary save for one channel in the lineup--GSN I think. 

I'm using the install disk to test a remote FE on my laptop. The button to "Try Mythbuntu" launches a widget with a button to test the connection. When I "just pushed" that button, the return dialog was failed to connect to database at 'mythconverg'@'127.0.0.1' for user 'mythtv' with password 'xxxxxxx'. I set a new password for user mythbuntu on this test FE and invoked ~$ mythfrontend in a terminal. It complained about the user not being a member of the mythtv group and invited me to add the user to the group, which I did. This required a log-off/on, hence the aforementioned new password (still using the LiveCD). Somewhere along in here there was a complaint that my FE and BE were in different time zones so I had to change the timezone on the test FE. Finally the FE GUI launched. I think the first page displayed the host as "mythtv" with a password different from that on my BE. It finally dawned on me that the "host" had to be the IP address of the BE so I entered that and the password from the BE then, as they say, the magic happened.

I've learned that security key 0000 means any client can access. 

I've also learned that where (what configuration or other file) mysql looks for information can, as I understand from my limited review of postings by Michael T. Dean depend upon the bit of information requested and the version of mythtv involved. In other words it may be difficult to determine exactly where mysql is getting its information and that source may change from version to version.

As far as the LiveCD not automatically recognizing my BE, I suspect that has to do with me setting "Bind=0.0.0.0" in my.cnf. It probably should be the "discoverable" IP address for the Master Backend box. I may fiddle with that. Or I may not. If it ain't broke.... 

Video and Audio -- Video content from the BE displays nicely on the BE and on the FE over Cat5e. Audio from the video works on the FE housed with the BE but does not work on the remote FE. Testing audio with the remote FE setup utility works, so I'll have to figure that out. I'm guessing displays of audio and video on the FE over wireless will not be acceptable unless there's a streaming solution I can figure out.

I'm trying [Torc]("http://trianythingonce.com/blog/torc-for-ios/") on the iPad. It purports to allow you to play recordings on the iPad or just use the iPad as a remote control. The content playback on the iPad isn't workng for me yet. The developer has a link about what other pieces are required to support streaming playback on the iPad. Installation of JW Player, Lame and something else. As I understand his requirements, they include compling the BE with x264 and lame. That sounds to me like I'm supposed to patch the kernel, which I did not do. Again, I may fiddle with this and see where I get. There are innumerable demons to chase behind the curtain of MythTV.

Torc as a remote control/frontend/content selector -- this looks like a solution which may actually make this mythtv-thing work for my wife! I already recorded my first episode of her favorite soap yesterday. 

I'll be looking for a FE solution for our main TV. [Marc Lewis ]("http://www.marclewis.com/tag/mythbuntu/")describes what sounds like a great solution based on Zotac.

---

