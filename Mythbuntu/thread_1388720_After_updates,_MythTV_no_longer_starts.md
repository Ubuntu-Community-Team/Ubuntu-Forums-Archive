---
title: "After updates, MythTV no longer starts"
date: 2010-01-23
forum: Mythbuntu
---

### Post by Weidbrewer on 2010-01-23
I'm running my backend on a machine with Ubuntu 64 8.10.  I installed some updates last night, and started experiencing problems with a frontend this morning.  

At first, it was working, but throwing errors.  Then, I had left the room for a bit, came back and hit play right as the screen saver was kicking in.  The frontend locked and I had to reboot.  After reboot, MythTV no longer started automatically.  I started it from the dropdown, and again, nothing.  When I started it from terminal, it told me that it could not connect to the backend.  

I tried running Myth from the backend itself, and again, it would not start.  When I tried to go see what was up in the backend manager, it also will not start.  It looks like it's going to start, and then just skips right to the fill database window I normally get when I exit the backend manager.

Since I can't even run the backend manager, I'm at a loss as to how to fix this.  Any ideas?

---

### Post by azmyth on 2010-01-23
Start the processes from a terminal window to see what the output says. It looks like you could have an ip issue. Make sure what you see with ifconfig matches what it says in mythtv-setp.

---

### Post by nickrout on 2010-01-23
> **azmyth said:**
> Start the processes from a terminal window to see what the output says. It looks like you could have an ip issue. Make sure what you see with ifconfig matches what it says in mythtv-setp.

did the update fill the hard drive up?

---

### Post by Weidbrewer on 2010-01-23
Whenever I post on here, I always try to sum up all the obvious things I did, and every time, there turns out to be one I missed... :P


At anywho, yes, it is an IP problem, 100%.  Normally when I've had this happen, I check my router to see if it got changed in there (it hasn't) and then I go to the backend setup to make sure that the value in there hasn't been changed - but the problem is, I can't access the backend at all.  The setup manager won't open.  

In the spirit of completeness, this is the output from running Myth from terminal on the backend server itself:

```
~$ mythtv
2010-01-23 19:01:32.889 Using runtime prefix = /usr
2010-01-23 19:01:32.909 XScreenSaver support enabled
2010-01-23 19:01:32.912 DPMS is active.
2010-01-23 19:01:32.913 Empty LocalHostName.
2010-01-23 19:01:32.913 Using localhost value of *****
2010-01-23 19:01:32.934 New DB connection, total: 1
2010-01-23 19:01:32.942 Connected to database 'mythtv' at host: localhost
2010-01-23 19:01:32.943 Closing DB connection named 'DBManager0'
2010-01-23 19:01:32.945 Primary screen 0.
2010-01-23 19:01:32.946 Connected to database 'mythtv' at host: localhost
2010-01-23 19:01:32.947 Running in a window
2010-01-23 19:01:32.947 Using screen 0, 1280x976 at 0,24
2010-01-23 19:01:32.958 No theme dir: /home/*******/.mythtv/themes/Mythbuntu-8.04
2010-01-23 19:01:32.975 max_width: 1280 max_height: 1024
2010-01-23 19:01:32.977 Primary screen 0.
2010-01-23 19:01:32.978 Running in a window
2010-01-23 19:01:32.978 Using screen 0, 1280x976 at 0,24
2010-01-23 19:01:32.979 No theme dir: /home/*******/.mythtv/themes/Mythbuntu-8.04
2010-01-23 19:01:32.980 Switching to square mode (Mythbuntu-8.04)
2010-01-23 19:01:33.026 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2010-01-23 19:01:33.027 lirc_init failed for mythtv, see preceding messages
2010-01-23 19:01:33.028 JoystickMenuClient Error: Joystick disabled - Failed to read /home/*******/.mythtv/joystickmenurc
2010-01-23 19:01:33.787 New DB connection, total: 2
2010-01-23 19:01:33.788 Connected to database 'mythtv' at host: localhost
2010-01-23 19:01:33.877 Connecting to backend server: 192.168.1.47:6543 (try 1 of 5)
2010-01-23 19:01:33.878 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2010-01-23 19:01:34.743 Connecting to backend server: 192.168.1.47:6543 (try 1 of 5)
2010-01-23 19:01:34.743 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2010-01-23 19:01:36.350 TV Error: Failed to get recording show list

```

Also, when run from here, a Myth window will open, but I get the standard "Cannot connect, etc, is your IP correct, etc" message.  Furthermore, if you notice in the above readout, it says Mythbuntu 8.04, but the machine itself is running 8.10 (Verified in case I'm a total idiot and forgot what OS I was running.)

Also, if it matters, when I go into Mythbuntu Control Center and test the MYSQL connection, it says that the test passed.


Finally, I am unfamiliar with ifconfig, so I don't know what I'm looking for there:

```
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:54:d7:07:5e  
          inet addr:192.168.1.47  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:54ff:fed7:75e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13407 errors:0 dropped:391462365870 overruns:0 frame:0
          TX packets:2979 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1597647 (1.5 MB)  TX bytes:442580 (442.5 KB)
          Interrupt:253 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10680 (10.6 KB)  TX bytes:10680 (10.6 KB)

```

---

### Post by Weidbrewer on 2010-01-23
> **nickrout said:**
> did the update fill the hard drive up?


In answer to your question:  No - I still have 6.8 GB free.

---

### Post by azmyth on 2010-01-23
> Finally, I am unfamiliar with ifconfig, so I don't know what I'm looking for there:

inet addr:192.168.1.47

What you're looking for is to make sure the inet addr is matching your mythtv settings.

Check to make sure the backend is running.

ps -A | grep mythbackend

If this takes you back to the prompt then your backend isn't running. If this is running, then stop the backend and from a command prompt type

mythtv-setup

Under General make sure _both_ the local backend and master backend says

192.168.1.47

Then try again

---

### Post by Weidbrewer on 2010-01-23
It was not running, and took me to a prompt.
Ran setup from terminal and got the same reaction as running it from the drop-down:  It asks to cancel any running backend processes, then skips to the fill DB screen without starting the setup manager.  Terminal text:

```
~$ mythtv-setup
 * Stopping MythTV server: mythbackend                                          No /usr/bin/mythbackend found running; none killed.
                                                                         [ OK ]
 * Restarting MythTV server: mythbackend                                        No /usr/bin/mythbackend found running; none killed.
            
```

---

### Post by nickrout on 2010-01-23
Your messages are very confusing and you seem to be mistaken about a couple of things:

1. it is not entirely clear whether the backend and the frontend are running on the same machine? 

2. run mythfrontend NOT mythtv. 

3. check whether mysql is running on the backend machine

ps ax|grep mysqld

if not then sudo /etc/init.d/mysql start

4. check whether the backend is running

ps ax|grep backend

if not then sudo /etc/init.d/mythtv-backend start

If all appears well at that point then run mythfrontend

---

### Post by Weidbrewer on 2010-01-23
I'm sorry that you are finding these confusing.  I am attempting to be as clear as possible.

The problem first manifested on a remote frontend, but the results are the same running the frontend on the server containing the backend.  From the desktop shortcuts and from terminal, I cannot run mythtv, mythfrontend or mythtv-setup.  So far as I can tell, MYSQL is running, but I will check again when I get home.

Also, since I cannot even get the Backend setup manager to run, I cannot confirm that the IP address is set correctly like I would normally do.  

Hopefully, this will help clear things up.

---

### Post by azmyth on 2010-01-23
I think his terminology is a bit confusing. You should state mythbackend, mythfrontend (GUI), mythtv-setup. Anyhow, no worries I understand.

I assume you're not doing a ssh into your mythtv computer since you need x windows to run mythfrontend and mythtv-setup. Open a terminal and just type at a prompt

mythbackend

then post the resulting output here.

---

### Post by azmyth on 2010-01-23
I'm also confused at why you're just typing

mythtv

to start the frontend.

---

### Post by Weidbrewer on 2010-01-23
Okay - here is the output of requested commands:

```
~$ ps ax|grep mysqld
 5333 ?        S      0:00 /bin/sh /usr/bin/mysqld_safe
 5375 ?        Sl     0:30 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
 5377 ?        S      0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
15583 pts/0    S+     0:00 grep mysqld 

```

```
~$ ps ax|grep backend
 6141 ?        Ss     0:00 /usr/bin/system-tools-backends
15590 pts/0    S+     0:00 grep backend

```

```
~$ mythbackend
2010-01-23 22:10:24.644 Using runtime prefix = /usr
2010-01-23 22:10:24.645 Empty LocalHostName.
2010-01-23 22:10:24.646 Using localhost value of deus-ex
2010-01-23 22:10:24.659 New DB connection, total: 1
2010-01-23 22:10:24.666 Connected to database 'mythtv' at host: localhost
2010-01-23 22:10:24.667 Closing DB connection named 'DBManager0'
2010-01-23 22:10:24.668 Connected to database 'mythtv' at host: localhost
2010-01-23 22:10:24.670 New DB connection, total: 2
2010-01-23 22:10:24.671 Connected to database 'mythtv' at host: localhost
2010-01-23 22:10:24.673 The schema version of your existing database is newer than this version of MythTV understands. Please ensure that you have selected the proper database server or upgrade this and all other frontends and backends to the same MythTV version and revision.

```

This last one surprises me - I know that 9.04/10 uses a new DB format, which is part of the reason I haven't upgraded Ubuntu.  I haven't knowingly upgrade my DB schema either.

---

### Post by Weidbrewer on 2010-01-23
> **azmyth said:**
> I'm also confused at why you're just typing

mythtv

to start the frontend.

I don't, generally...usually I hit the launcher or, most often, have it auto-start at boot.  I next to never start it from terminal at all, as this does not lend itself well to an entertainment center.

"Mythtv," again, is just *one* of the commands I had tried (along with mythfrontend, etc.) It is simply the only one that I got any sort of "reaction" to all (That being the screen that first told me that it could not connect to the backend mentioned above.)

---

### Post by azmyth on 2010-01-23
At some point your mythtv was upgraded which in turn upgraded your database now it appears you're using an older version of mythtv thus it's complaining about having a newer db. Your choice is to upgrade myth to match the db upgrade or downgrade the db to work with your rev of mythtv. Usually a backup is aut generated when a schema is upgraded so it's probably in your backup folder.

---

### Post by Weidbrewer on 2010-01-24
Seeing as how I have 4 remote frontends on this system, mostly using old hardware that requires me to stick with 8.10 or earlier, I think that the best option is to downgrade the DB.  Assuming that there is a backup, what is the easiest way to restore it?

Also, since this upgrade happened without me being aware of doing it, how can I prevent it from happening again.

---

### Post by Weidbrewer on 2010-01-24
I have a backup utility I use (not often enough, it appears) that I was able to restore a copy of my DB through.  It did the trick.  Thanks for the pointer.  I guess now all I'd like to know is how to assure that this won't happen again.

---

### Post by azmyth on 2010-01-24
Anytime you do an upgrade you risk messing your system up. If you stay away from upgrades, your system should work.

---

### Post by Weidbrewer on 2010-01-24
That would be the problem - I didn't upgrade. This happened after just doing normal *updates*.  As I stated above, I have very intentionally *not* upgraded the machines on this system, as I had them working just how I wanted them to.  This is why I was surprised when I saw that terminal read-out that said my DB had been upgraded.  I'm guessing that it must have been snuck in with some update this week.

---

### Post by azmyth on 2010-01-25
I should've said upgrades and/or updates. I've pooched my system as well by doing this. You just never know what could happen.

---

