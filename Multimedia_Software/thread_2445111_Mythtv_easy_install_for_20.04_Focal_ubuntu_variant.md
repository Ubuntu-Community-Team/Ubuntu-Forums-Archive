---
title: "Mythtv easy install for 20.04 Focal ubuntu variants."
date: 2020-06-09
forum: Multimedia Software
---

### Post by vidtek on 2020-06-09
I did an easy install for 18.04 and I struggled with focal for a while.   Here are my notes on how I got it all working.

Mythtv uses mysql 8.00 which has a different set of commands  [I]Why oh why do they have to change something that works well and we all know how to use?
[/I]

**mythtv 0.31 install on Focal 20.04**

Before you start do a dist-upgrade and ensure you can get tv reception from your tv source.  I install kaffeine to test, quick and dirty.  I usually install leafpad too but now that's

no longer in the repositories so use mousepad instead, not as good but it's getting there.  So your hardware works, tv and sound let's get started.

1) D/L package from here: [https://www.ubuntuupdates.org/package/core/focal/multiverse/base/mythtv]("https://www.ubuntuupdates.org/package/core/focal/multiverse/base/mythtv")   select: **all arch .deb packages** and download

2)move d/l file to convenient install location I use ~/test

3) run file it will open Qapt installer.

4) answer options as they arise --other computers run mythtv?     # other computers running mythtv on your network?

5) When Qapt is finished the "Close" box at bottom right will be highlighted.

6) Add mythtv/root/your-user to groups mythtv, audio, video.eg.# ```
Add mythtv/root/your-user to groups mythtv, audio, video.eg.# sudo adduser mythtv mythtv, adduser mythtv video, adduser mythtv audio, adduser (YOURUSERNAME) mythtv, adduser (YOURUSERNAME) video, adduser (YOURUSERNAME) audio
```. then re-logon or reboot

7) run sudo visudo and enter the permissions for mythtv especially if you want auto-wake and shutdown

   mine is like this:   ```
%mythtv ALL=NOPASSWD: /usr/sbin/setwakeup.sh, /usr/sbin/mythshutdowncheck.sh, /usr/sbin/checklogin.sh, /bin/systemctl poweroff
```

8) reboot

9) in konsole run:```
 mythtv-setup -w
```   #I use the -w to put it in a window, makes it easier if it hangs

10) Change the default password in mysql.  There are new commands for myqsl 8.0 
	New commands for later mysql versions
  ```
sudo mysql mythconverg

 	         ALTER USER 'mythtv' IDENTIFIED BY 'mythtv';          

           # or
   	 
  	#CREATE USER 'mythtv'@'localhost' IDENTIFIED BY 'mythtv'; 
	 
	FLUSH PRIVILIGES;

        quit  or cntl+d
```

  Ensure all config.xml files are identical.  Locations;-  /etc/mythtv...... ~/.mythtv.......... /home/mythtv/.mythtv......./root/mythtv/.mythtv 
	
	There is a possibility with some instances there may be one in /usr/share/mythtv
   
 If you are using an ip address instead of the default localhost you need to make the following changes.
   in   /etc/mysql/mysql.conf.d/                change the bind address to your own IP address.
    
Also change /etc/mysql/conf.d/mythtv.cnf. 
	[mysqld]
	bind-address=0.0.0.0
	any release of a new version on updates it won't get overwritten.

I will update this as changes happen.   Happy Mythtv-ing all 

I will post a new how-to for the systemd udev system of handling infra-red remotes with Focal. [https://ubuntuforums.org/showthread.php?t=2446164&p=13968094#post13968094](https://ubuntuforums.org/showthread.php?t=2446164&p=13968094#post13968094)

Tony.

---

