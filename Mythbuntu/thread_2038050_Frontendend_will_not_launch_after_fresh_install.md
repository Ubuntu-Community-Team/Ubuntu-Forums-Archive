---
title: "Frontendend will not launch after fresh install"
date: 2012-08-05
forum: Mythbuntu
---

### Post by jeffc7186 on 2012-08-05
I decided to do a fresh install of my FE and now it will not launch. I did have a working FE and did connect to a working BE and am using same hardware and setup as before. Below is the output from when running from terminal.    Any Ideas on what could be wrong?

jeff@htpc:~$ mythfrontend
QGtkStyle was unable to detect the current GTK+ theme.
2012-08-05 17:05:36.421614 C  mythfrontend version: fixes/0.25 [v0.25] [www.mythtv.org](www.mythtv.org)
2012-08-05 17:05:36.421693 N  Enabled verbose msgs:  general
2012-08-05 17:05:36.421787 N  Setting Log Level to LOG_INFO
2012-08-05 17:05:36.421946 I  Added logging to the console
2012-08-05 17:05:36.422041 I  Added syslogging to facility local7
2012-08-05 17:05:36.422072 I  Added database logging to table logging
2012-08-05 17:05:36.422452 N  Setting up SIGHUP handler
2012-08-05 17:05:36.422798 N  Using runtime prefix = /usr
2012-08-05 17:05:36.422935 N  Using configuration directory = /home/jeff/.mythtv
2012-08-05 17:05:36.423903 I  Assumed character encoding: en_US.UTF-8
2012-08-05 17:05:36.426126 N  Empty LocalHostName.
2012-08-05 17:05:36.426172 I  Using localhost value of htpc
2012-08-05 17:05:36.426924 I  Testing network connectivity to '192.168.1.200'
2012-08-05 17:05:36.428660 I  Starting process signal handler
2012-08-05 17:05:36.428889 I  Starting IO manager (read)
2012-08-05 17:05:36.431763 I  Starting process manager
2012-08-05 17:05:36.432362 I  Starting IO manager (write)

---

### Post by jeffc7186 on 2012-08-06
Please help.    Is there any additional information I can provide to help figure this out?

---

### Post by anonymousdog on 2012-08-06
At that point, FE usually starts interacting with X.

What distro are you running (including 32/64-bit)?
What video driver are you running?
Do you get any GUI output at all?
Have you activated the MB repos and updated since install?

Was this truly a clean build (i.e., no home folder preserved)?

---

### Post by jeffc7186 on 2012-08-06
What distro are you running (including 32/64-bit)?
64 bit 12.04

What video driver are you running?
nvidia

Do you get any GUI output at all?
only after the install where it shows setup for BE ip and such after that nothing.

Have you activated the MB repos and updated since install?
I have not activated the repos. I will try that. I have done full update from update manager. 

Was this truly a clean build (i.e., no home folder preserved)?
Yes,  clean install from pendrive reformatting harddrive.

---

### Post by anonymousdog on 2012-08-06
> **jeffc7186 said:**
> 
What video driver are you running?
nvidia

proprietary, binary driver, right?

Mythbuntu 12.04 x86_64 (or another distro?)

So, at the end of your FE (stderr) output when you have no FE GUI: Does a 'pgrep mythfrontend' shows the process running?

---

### Post by jeffc7186 on 2012-08-06
proprietary, binary driver, right?
Yes 

Mythbuntu 12.04 x86_64 (or another distro?)
Yes Mythbuntu 12.04 64bit

So, at the end of your FE (stderr) output when you have no FE GUI: Does a 'pgrep mythfrontend' shows the process running?
jeff@htpc:~$ pgrep mythfrontend
1603
1637
1745
1756
1768
2096
2107
jeff@htpc:~$

---

### Post by anonymousdog on 2012-08-06
You'll probably have to kill all those PIDs before you have any chance of the FE launching successfully.

Then activate the MB repos and update.

Then try again and post back last 20 lines or so of FE log at /var/log/mythtv/mythfrontend.log if it fails (or the stderr output like you did above).

---

### Post by jeffc7186 on 2012-08-06
no luck, killed the PIDS and updated repos.

jeff@htpc:~$ mythfrontend
QGtkStyle was unable to detect the current GTK+ theme.
2012-08-06 21:42:10.344116 C  mythfrontend version: fixes/0.25 [v0.25] [www.mythtv.org](www.mythtv.org)
2012-08-06 21:42:10.344195 N  Enabled verbose msgs:  general
2012-08-06 21:42:10.344288 N  Setting Log Level to LOG_INFO
2012-08-06 21:42:10.344450 I  Added logging to the console
2012-08-06 21:42:10.344547 I  Added syslogging to facility local7
2012-08-06 21:42:10.344576 I  Added database logging to table logging
2012-08-06 21:42:10.344957 N  Setting up SIGHUP handler
2012-08-06 21:42:10.345265 N  Using runtime prefix = /usr
2012-08-06 21:42:10.345409 N  Using configuration directory = /home/jeff/.mythtv
2012-08-06 21:42:10.346344 I  Assumed character encoding: en_US.UTF-8
2012-08-06 21:42:10.350090 N  Empty LocalHostName.
2012-08-06 21:42:10.350125 I  Using localhost value of htpc
2012-08-06 21:42:10.350735 I  Testing network connectivity to '192.168.1.200'
2012-08-06 21:42:10.352067 I  Starting process manager
2012-08-06 21:42:10.352193 I  Starting process signal handler
2012-08-06 21:42:10.352866 I  Starting IO manager (read)
2012-08-06 21:42:10.352985 I  Starting IO manager (write)
^C
jeff@htpc:~$ 



I appreciate your help with this.

---

### Post by anonymousdog on 2012-08-06
I've never seen this in my logs; so, I'd start looking at that.
```
QGtkStyle was unable to detect the current GTK+ theme.
```

You had this working before on same distro, same hardware, nothing changed but the installation of the OS (on a fresh partition)?  Were there any errors on installation?

Does you /var/log/mythtv/mythfrontend.log have anything more interesting at the end (than the stderr output you provided)?

---

### Post by dangerous_d on 2012-08-08
Have you changed the hostname of the frontend?  Check the settings table in the database on the backend and compare the value(s) in the hostname row to the hostname as reported by the frontend.

Have you tried testing the database connection from within Mythbuntu Control Centre?  Go to the mySQL section in MCC and click the "Test" button.

---

### Post by jeffc7186 on 2012-08-08
I have tested connection to BE in Control center and test is OK.

We may have something here on your other comment, I do enter the host IP during the initial setup, however I do not believe I have changed the "hostname".  What seems unusual is when I went to mythweb clicked settings, mythtv, settings table. The drop down menu for edit setting for: does not list the hostname of my last install.  

I am going to try a fresh install and use the hostname which is in the list to see if that works.  If it does great, however how do I add additional hosts to mythweb (or BE) if i add future FE's?

---

### Post by dangerous_d on 2012-08-08
I've never added a second front end, but I recall the settings are specific for a given hostname so you should be ok as long as the hostname of your front ends is unique.  I had a problem when I changed my front end from "localhost" to its ip address without following the instructions in the wiki.  I was later able to clean it up by modifying the database directly.

---

### Post by jeffc7186 on 2012-08-08
I did a new install again.  Same issue.  It has to be this "QGtkStyle was unable to detect the current GTK+ theme." error.  I have Google searched the issue can't find anything helpful.  Are there other sources of help?

---

### Post by dangerous_d on 2012-08-08
What theme were you using for the front end?  Maybe the front end is trying to load a theme that is not included with a clean install (ie- a downloadable theme).  There might be some settings you need to purge when you do a clean install of a previously-configured front end client.

---

### Post by dangerous_d on 2012-08-08
This is from the mythtv wiki.  Check the database for duplicate entries.

> **Change the hostname of a MythTV frontend or backend **

 Before changing the hostname of a MythTV frontend or backend, make sure you create a good database backup, so that you can get back to a known state if things go wrong. 
When changing the hostname of your system, you must perform the following actions before  you start any MythTV programs.  If you start a MythTV program before  modifying the hostname in the database, the program will create new  entries with the new hostname, meaning that the following procedure is  likely to fail because of duplicate entries. 

It is also critical to ensure you do not change the name of a  host to the name of another already-existing host in the database--doing  so will cause duplicate entries.  Instead, if necessary, run the  command below multiple times, using a temporary "placeholder" hostname  to ensure the different hosts are not improperly merged. 

Note that changing the hostname is performed on an existing  database and does not restore a database.  Therefore, to change a  hostname, ensure that the database exists (restore an old database, as  above, if necessary) and execute the following command, replacing "XXXX"  and "YYYY" with appropriate values for the old and new hostnames,  respectively: 

 mythconverg_restore.pl --change_hostname --old_hostname="XXXX" --new_hostname="YYYY"   

---

### Post by tgm4883 on 2012-08-08
Maybe some more logging will shed some light on it.

```
mythfrontend -v all
```

---

### Post by jeffc7186 on 2012-08-08
jeff@htpc1:~$ mythfrontend -v all
QGtkStyle was unable to detect the current GTK+ theme.
2012-08-08 22:25:59.693514 C  mythfrontend version: fixes/0.25 [v0.25] [www.mythtv.org](www.mythtv.org)
2012-08-08 22:25:59.693593 N  Enabled verbose msgs: all
2012-08-08 22:25:59.693688 N  Setting Log Level to LOG_INFO
2012-08-08 22:25:59.693849 I  Added logging to the console
2012-08-08 22:25:59.693945 I  Added syslogging to facility local7
2012-08-08 22:25:59.693974 I  Added database logging to table logging
2012-08-08 22:25:59.694349 N  Setting up SIGHUP handler
2012-08-08 22:25:59.694938 N  Using runtime prefix = /usr
2012-08-08 22:25:59.695096 N  Using configuration directory = /home/jeff/.mythtv
2012-08-08 22:25:59.695723 E  (old)Settings::ReadSettings(settings.txt) - No such file settings.txt
2012-08-08 22:25:59.696109 I  Assumed character encoding: en_US.UTF-8
2012-08-08 22:25:59.696739 E  (old)Settings::ReadSettings(settings.txt) - No such file settings.txt
2012-08-08 22:25:59.696950 E  (old)Settings::ReadSettings(settings.txt) - No such file settings.txt
2012-08-08 22:25:59.697064 E  (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - No such file /usr/share/mythtv/mysql.txt
2012-08-08 22:25:59.697148 E  (old)Settings::ReadSettings(/usr/etc/mythtv/mysql.txt) - No such file /usr/etc/mythtv/mysql.txt
2012-08-08 22:25:59.697884 E  (old)Settings::ReadSettings(./mysql.txt) - No such file ./mysql.txt
2012-08-08 22:25:59.698098 N  Empty LocalHostName.
2012-08-08 22:25:59.698139 I  Using localhost value of htpc1
2012-08-08 22:25:59.698203 I  Clearing Settings Cache.
2012-08-08 22:25:59.698542 I  DefaultUPnP() - No default UPnP backend
2012-08-08 22:25:59.698609 I  Testing network connectivity to '192.168.1.200'
2012-08-08 22:25:59.704608 I  Starting process manager
2012-08-08 22:25:59.704840 I  Starting process signal handler
2012-08-08 22:25:59.709163 I  Starting IO manager (write)
2012-08-08 22:25:59.710831 I  Managed child (PID: 1796) has started! * command=ping -t 3 -c 1  192.168.1.200  >/dev/null 2>&1, timeout=0
2012-08-08 22:25:59.711223 I  Starting IO manager (read)
2012-08-08 22:25:59.804939 I  Managed child (PID: 1796) has exited! command=ping -t 3 -c 1  192.168.1.200  >/dev/null 2>&1, status=0, result=0
2012-08-08 22:25:59.805325 I  Clearing Settings Cache.
2012-08-08 22:25:59.857676 I  Database connection created: DBManager0
2012-08-08 22:25:59.857797 I  New DB connection, total: 1
^C
jeff@htpc1:~$

Hope this helps.  Thanks!!!!

---

### Post by jeffc7186 on 2012-08-08
x

---

### Post by jeffc7186 on 2012-08-18
Bumb

---

### Post by nickrout on 2012-08-21
> **jeffc7186 said:**
> jeff@htpc1:~$ mythfrontend -v all
QGtkStyle was unable to detect the current GTK+ theme.
2012-08-08 22:25:59.693514 C  mythfrontend version: fixes/0.25 [v0.25] [www.mythtv.org](www.mythtv.org)
2012-08-08 22:25:59.693593 N  Enabled verbose msgs: all
2012-08-08 22:25:59.693688 N  Setting Log Level to LOG_INFO
2012-08-08 22:25:59.693849 I  Added logging to the console
2012-08-08 22:25:59.693945 I  Added syslogging to facility local7
2012-08-08 22:25:59.693974 I  Added database logging to table logging
2012-08-08 22:25:59.694349 N  Setting up SIGHUP handler
2012-08-08 22:25:59.694938 N  Using runtime prefix = /usr
2012-08-08 22:25:59.695096 N  Using configuration directory = /home/jeff/.mythtv
2012-08-08 22:25:59.695723 E  (old)Settings::ReadSettings(settings.txt) - No such file settings.txt
2012-08-08 22:25:59.696109 I  Assumed character encoding: en_US.UTF-8
2012-08-08 22:25:59.696739 E  (old)Settings::ReadSettings(settings.txt) - No such file settings.txt
2012-08-08 22:25:59.696950 E  (old)Settings::ReadSettings(settings.txt) - No such file settings.txt
2012-08-08 22:25:59.697064 E  (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - No such file /usr/share/mythtv/mysql.txt
2012-08-08 22:25:59.697148 E  (old)Settings::ReadSettings(/usr/etc/mythtv/mysql.txt) - No such file /usr/etc/mythtv/mysql.txt
2012-08-08 22:25:59.697884 E  (old)Settings::ReadSettings(./mysql.txt) - No such file ./mysql.txt
2012-08-08 22:25:59.698098 N  Empty LocalHostName.
2012-08-08 22:25:59.698139 I  Using localhost value of htpc1
2012-08-08 22:25:59.698203 I  Clearing Settings Cache.
2012-08-08 22:25:59.698542 I  DefaultUPnP() - No default UPnP backend
2012-08-08 22:25:59.698609 I  Testing network connectivity to '192.168.1.200'
2012-08-08 22:25:59.704608 I  Starting process manager
2012-08-08 22:25:59.704840 I  Starting process signal handler
2012-08-08 22:25:59.709163 I  Starting IO manager (write)
2012-08-08 22:25:59.710831 I  Managed child (PID: 1796) has started! * command=ping -t 3 -c 1  192.168.1.200  >/dev/null 2>&1, timeout=0
2012-08-08 22:25:59.711223 I  Starting IO manager (read)
2012-08-08 22:25:59.804939 I  Managed child (PID: 1796) has exited! command=ping -t 3 -c 1  192.168.1.200  >/dev/null 2>&1, status=0, result=0
2012-08-08 22:25:59.805325 I  Clearing Settings Cache.
2012-08-08 22:25:59.857676 I  Database connection created: DBManager0
2012-08-08 22:25:59.857797 I  New DB connection, total: 1
^C
jeff@htpc1:~$

Hope this helps.  Thanks!!!!

^c killed the process, no wonder it dodn't start!

Have you tried with a different themepainter.```
mythfrontend -O ThemePainter=qt
``` or opengl

---

### Post by Lester_Burnham on 2012-08-21
I haven't read the whole thread, but it looks like it can't find a mysql.txt

Lester

---

### Post by jeffc7186 on 2012-08-21
> **nickrout said:**
> ^c killed the process, no wonder it dodn't start!

Have you tried with a different themepainter.```
mythfrontend -O ThemePainter=qt
``` or opengl

Tried that this is from terminal

jeff@htpc:~$ mythfrontend -O ThemePainter=qt
QGtkStyle was unable to detect the current GTK+ theme.
2012-08-21 21:28:59.649231 C  mythfrontend version: fixes/0.25 [v0.25] [www.mythtv.org](www.mythtv.org)
2012-08-21 21:28:59.649310 N  Enabled verbose msgs:  general
2012-08-21 21:28:59.649402 N  Setting Log Level to LOG_INFO
2012-08-21 21:28:59.649566 I  Added logging to the console
2012-08-21 21:28:59.649659 I  Added syslogging to facility local7
2012-08-21 21:28:59.649685 I  Added database logging to table logging
2012-08-21 21:28:59.650143 N  Setting up SIGHUP handler
2012-08-21 21:28:59.651031 N  Using runtime prefix = /usr
2012-08-21 21:28:59.651548 N  Using configuration directory = /home/jeff/.mythtv
2012-08-21 21:28:59.652386 I  Assumed character encoding: en_US.UTF-8
2012-08-21 21:28:59.654007 N  Empty LocalHostName.
2012-08-21 21:28:59.654058 I  Using localhost value of htpc
2012-08-21 21:28:59.654456 I  Testing network connectivity to '192.168.1.200'
2012-08-21 21:28:59.656814 I  Starting process manager
2012-08-21 21:28:59.656968 I  Starting process signal handler
2012-08-21 21:28:59.661905 I  Starting IO manager (write)
2012-08-21 21:28:59.662149 I  Starting IO manager (read)
^C
jeff@htpc:~$ ^C
jeff@htpc:~$

---

### Post by jeffc7186 on 2012-08-21
> **Lester_Burnham said:**
> I haven't read the whole thread, but it looks like it can't find a mysql.txt

Lester

Can you help me troubleshoot this?

---

### Post by nickrout on 2012-08-22
> **jeffc7186 said:**
> Tried that this is from terminal

jeff@htpc:~$ mythfrontend -O ThemePainter=qt
QGtkStyle was unable to detect the current GTK+ theme.
2012-08-21 21:28:59.649231 C  mythfrontend version: fixes/0.25 [v0.25] [www.mythtv.org](www.mythtv.org)
2012-08-21 21:28:59.649310 N  Enabled verbose msgs:  general
2012-08-21 21:28:59.649402 N  Setting Log Level to LOG_INFO
2012-08-21 21:28:59.649566 I  Added logging to the console
2012-08-21 21:28:59.649659 I  Added syslogging to facility local7
2012-08-21 21:28:59.649685 I  Added database logging to table logging
2012-08-21 21:28:59.650143 N  Setting up SIGHUP handler
2012-08-21 21:28:59.651031 N  Using runtime prefix = /usr
2012-08-21 21:28:59.651548 N  Using configuration directory = /home/jeff/.mythtv
2012-08-21 21:28:59.652386 I  Assumed character encoding: en_US.UTF-8
2012-08-21 21:28:59.654007 N  Empty LocalHostName.
2012-08-21 21:28:59.654058 I  Using localhost value of htpc
2012-08-21 21:28:59.654456 I  Testing network connectivity to '192.168.1.200'
2012-08-21 21:28:59.656814 I  Starting process manager
2012-08-21 21:28:59.656968 I  Starting process signal handler
2012-08-21 21:28:59.661905 I  Starting IO manager (write)
2012-08-21 21:28:59.662149 I  Starting IO manager (read)
^C
jeff@htpc:~$ ^C
jeff@htpc:~$

have you tried opengl?

---

### Post by Lester_Burnham on 2012-08-22
> **jeffc7186 said:**
> Can you help me troubleshoot this?

Not really, the guys you got on it already know 100 times more than me about mythtv :)
Are you running the standard mythbuntu desktop?

Lester

---

### Post by jeffc7186 on 2012-08-22
> **nickrout said:**
> have you tried opengl?

I am not sure.  Where or how do I select it or turn it on or off?  Thank you

---

### Post by jeffc7186 on 2012-08-22
> **Lester_Burnham said:**
> Not really, the guys you got on it already know 100 times more than me about mythtv :)
Are you running the standard mythbuntu desktop?

Lester

Running latest version of mythtv and mythbuntu.  Fresh install of FE trying to connect to a working BE.

---

### Post by anonymousdog on 2012-08-22
> **jeffc7186 said:**
> I am not sure.  Where or how do I select it or turn it on or off?  Thank you

mythfrontend -O ThemePainter=opengl

---

### Post by jeffc7186 on 2012-08-22
> **anonymousdog said:**
> mythfrontend -O ThemePainter=opengl

Tried this and same result.  Any other ideas?

---

### Post by jeffc7186 on 2012-08-22
Here is my latest


jeff@htpc:~$ mythfrontend -v all
QGtkStyle was unable to detect the current GTK+ theme.
2012-08-22 20:07:25.448330 C  mythfrontend version: fixes/0.25 [v0.25.2-15-g46cab93] [www.mythtv.org](www.mythtv.org)
2012-08-22 20:07:25.448416 C  Qt version: compile: 4.8.1, runtime: 4.8.1
2012-08-22 20:07:25.448433 N  Enabled verbose msgs: all
2012-08-22 20:07:25.448525 N  Setting Log Level to LOG_INFO
2012-08-22 20:07:25.448695 I  Added logging to the console
2012-08-22 20:07:25.448809 I  Added syslogging to facility local7
2012-08-22 20:07:25.448840 I  Added database logging to table logging
2012-08-22 20:07:25.449217 N  Setting up SIGHUP handler
2012-08-22 20:07:25.449620 N  Using runtime prefix = /usr
2012-08-22 20:07:25.449743 N  Using configuration directory = /home/jeff/.mythtv
2012-08-22 20:07:25.450217 E  (old)Settings::ReadSettings(settings.txt) - No such file settings.txt
2012-08-22 20:07:25.450777 I  Assumed character encoding: en_US.UTF-8
2012-08-22 20:07:25.452100 E  (old)Settings::ReadSettings(settings.txt) - No such file settings.txt
2012-08-22 20:07:25.452298 E  (old)Settings::ReadSettings(settings.txt) - No such file settings.txt
2012-08-22 20:07:25.452403 E  (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - No such file /usr/share/mythtv/mysql.txt
2012-08-22 20:07:25.452481 E  (old)Settings::ReadSettings(/usr/etc/mythtv/mysql.txt) - No such file /usr/etc/mythtv/mysql.txt
2012-08-22 20:07:25.453188 E  (old)Settings::ReadSettings(./mysql.txt) - No such file ./mysql.txt
2012-08-22 20:07:25.453418 N  Empty LocalHostName.
2012-08-22 20:07:25.453461 I  Using localhost value of htpc
2012-08-22 20:07:25.453516 I  Clearing Settings Cache.
2012-08-22 20:07:25.454393 I  DefaultUPnP() - No default UPnP backend
2012-08-22 20:07:25.454478 I  Testing network connectivity to '192.168.1.200'
2012-08-22 20:07:25.469473 I  Managed child (PID: 2763) has started! * command=ping -t 3 -c 1  192.168.1.200  >/dev/null 2>&1, timeout=0
2012-08-22 20:07:25.469862 I  Starting process signal handler
2012-08-22 20:07:25.470708 I  Starting IO manager (write)
2012-08-22 20:07:25.470851 I  Starting IO manager (read)
2012-08-22 20:07:25.471292 I  Starting process manager
2012-08-22 20:07:25.571598 I  Managed child (PID: 2763) has exited! command=ping -t 3 -c 1  192.168.1.200  >/dev/null 2>&1, status=0, result=0
2012-08-22 20:07:25.620616 I  Clearing Settings Cache.
2012-08-22 20:07:25.679580 I  Database connection created: DBManager0
2012-08-22 20:07:25.679704 I  New DB connection, total: 1

---

### Post by JackCorbae on 2012-09-08
I just found this thread and I am in exactly the same boat as the original poster. Same errors, same output ... no Mythfrontend on ONE PC in the house.

All PCs running Ubuntu 12.04 (I think? Did I upgrade the backend? Better check ... it might still be 11.10)

But the PC and laptop are both 12.04 64b and up to date.

Laptop works fine, PC doesn't. Have tried removing and purging Myth from the PC, removed the .mythbuntu and .mythtv folder from /home ... nothing. Can't get it working on my desktop any more. Can't even remember exactly what changed when it stopped working.

---

### Post by TheKiteGuy on 2012-10-07
FYI, I too was suffering from exactly the same issue.

I renamed the .mythtv folder in the home directory and then everything worked fine the next time I attempted to start the front end.

---

