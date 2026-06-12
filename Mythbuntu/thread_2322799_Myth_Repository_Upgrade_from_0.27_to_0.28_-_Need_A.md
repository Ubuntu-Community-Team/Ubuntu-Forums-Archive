---
title: "Myth Repository Upgrade from 0.27 to 0.28 - Need Assistance - Nothing working now"
date: 2016-04-30
forum: Mythbuntu
---

### Post by griggs2 on 2016-04-30
Trying to move from 0.27 to 0.28. Running Mythbuntu 14.04 LTS. 


I backed up my Mythtv db, switched the repositories and updated the BackEnd. It appeared that the backend restarted and updated correctly, so I went ahead with the FrontEnd updates. The FrontEnd restarted and when trying to select a recorded show, MythFrontEnd crashes.


So, I'm running a separate BackEnd and FrontEnd. Neither are working correctly at this point. 


Back at the Backend, mythtv-setup hangs at the setup terminal window.


I've tried restoring the databases a couple times and haven't gotten anywhere with that. I've tried making that the user ID is the same ("mtvbe"), and that hasn't fixed anything. And I've tried running with sudo - which failed as well.


I'm not quite sure what direction I need to turn at this moment. I guess the first thing to do is to get the BackEnd back working - and I hate to go have to rebuild the whole OS, just for this.

Myth BackEnd Log File from Backup prior to Upgrade to now:
[https://www.dropbox.com/s/fbwxv1wdxdelbwv/mythbackend-pruned-20160430.log?dl=0](https://www.dropbox.com/s/fbwxv1wdxdelbwv/mythbackend-pruned-20160430.log?dl=0)

Please let me know if you need any other information or files to provide assistance. I figure I'll work on the back end first, and then figure out the frontend.

Thanks in advance!

./g

---

### Post by blm-ubunet on 2016-04-30
On the MBE:
I would confirm the mysql login credentials in MBEs config.xml allow you to connect to mysql server.
Check mysql log files in /var/log/mysql/

Check something has not changed /etc/mysql/my.cnf.. you need external IP listening so should look something like this:
# skip-networking 
bind-address = <real.static.IP.address-of-mysql-server>

Believe "bind-address = 0.0.0.0" is okay.

You can check mysql connection from remote FE with:
```
mysql -umythtv -pmythtv -h10.0.0.70 mythconverg
select hostname from settings group by hostname;
quit
```

Then stop all FEs & then BE service:
sudo initctl stop mythtv-backend
if that fails then 
killall mythbackend

that might not be correct for mythbuntu as it renames/wraps the actual executable (mythbackend.real) with a script.

run mythtv-setup from terminal with:
mythtv-setup -O ThemePainter=qt -v all

Maybe you need to do this with the original backup database file & let mythtv-setup do the dB upgrade.
People seem to be having upgrade problems with mythmusic schema.

Were you using mythmusic?
Were you using storage groups?

---

### Post by griggs2 on 2016-04-30
Thanks for your assistance.

Two Log Files for mysql.
One from 05:34am this morning.
```

160430  5:34:03 [Note] /usr/sbin/mysqld: Normal shutdown
160430  5:34:03 [Note] Event Scheduler: Purging the queue. 0 events
160430  5:34:05 [Warning] /usr/sbin/mysqld: Forcing close of thread 855  user: 'mythtv'
160430  5:34:05 [Warning] /usr/sbin/mysqld: Forcing close of thread 851  user: 'mythtv'
160430  5:34:05 [Warning] /usr/sbin/mysqld: Forcing close of thread 850  user: 'mythtv'
160430  5:34:05 [Warning] /usr/sbin/mysqld: Forcing close of thread 849  user: 'mythtv'
160430  5:34:05 [Warning] /usr/sbin/mysqld: Forcing close of thread 848  user: 'mythtv'
160430  5:34:05 [Warning] /usr/sbin/mysqld: Forcing close of thread 842  user: 'mythtv'
160430  5:34:05  InnoDB: Starting shutdown...
160430  5:34:06  InnoDB: Shutdown completed; log sequence number 289271784
160430  5:34:06 [Note] /usr/sbin/mysqld: Shutdown complete
160430  5:34:28 [Warning] Using unique option prefix myisam-recover instead of myisam-recover-options is deprecated and will be removed in a future release. Please use the full name instead.
160430  5:34:28 [Note] Plugin 'FEDERATED' is disabled.
160430  5:34:28 InnoDB: The InnoDB memory heap is disabled
160430  5:34:28 InnoDB: Mutexes and rw_locks use GCC atomic builtins
160430  5:34:28 InnoDB: Compressed tables use zlib 1.2.8
160430  5:34:28 InnoDB: Using Linux native AIO
160430  5:34:28 InnoDB: Initializing buffer pool, size = 128.0M
160430  5:34:28 InnoDB: Completed initialization of buffer pool
160430  5:34:28 InnoDB: highest supported file format is Barracuda.
160430  5:34:28  InnoDB: Waiting for the background threads to start
160430  5:34:29 InnoDB: 5.5.49 started; log sequence number 289271784
160430  5:34:29 [Note] Server hostname (bind-address): '::'; port: 3306
160430  5:34:29 [Note]   - '::' resolves to '::';
160430  5:34:29 [Note] Server socket created on IP: '::'.
160430  5:34:29 [Note] Event Scheduler: Loaded 0 events
160430  5:34:29 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.5.49-0ubuntu0.14.04.1'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)

```

and one from 7:07am this morning:
```

160430  7:06:36 [Note] /usr/sbin/mysqld: Normal shutdown
160430  7:06:36 [Note] Event Scheduler: Purging the queue. 0 events
160430  7:06:38 [Warning] /usr/sbin/mysqld: Forcing close of thread 422  user: 'mythtv'
160430  7:06:38 [Warning] /usr/sbin/mysqld: Forcing close of thread 420  user: 'mythtv'
160430  7:06:38 [Warning] /usr/sbin/mysqld: Forcing close of thread 414  user: 'mythtv'
160430  7:06:38 [Warning] /usr/sbin/mysqld: Forcing close of thread 383  user: 'mythtv'
160430  7:06:38 [Warning] /usr/sbin/mysqld: Forcing close of thread 161  user: 'mythtv'
160430  7:06:38 [Warning] /usr/sbin/mysqld: Forcing close of thread 154  user: 'mythtv'
160430  7:06:38 [Warning] /usr/sbin/mysqld: Forcing close of thread 153  user: 'mythtv'
160430  7:06:38 [Warning] /usr/sbin/mysqld: Forcing close of thread 152  user: 'mythtv'
160430  7:06:38 [Warning] /usr/sbin/mysqld: Forcing close of thread 151  user: 'mythtv'
160430  7:06:38 [Warning] /usr/sbin/mysqld: Forcing close of thread 150  user: 'mythtv'
160430  7:06:38  InnoDB: Starting shutdown...
160430  7:06:39  InnoDB: Shutdown completed; log sequence number 290393900
160430  7:06:39 [Note] /usr/sbin/mysqld: Shutdown complete
160430  7:07:06 [Warning] Using unique option prefix myisam-recover instead of myisam-recover-options is deprecated and will be removed in a future release. Please use the full name instead.
160430  7:07:06 [Note] Plugin 'FEDERATED' is disabled.
160430  7:07:06 InnoDB: The InnoDB memory heap is disabled
160430  7:07:06 InnoDB: Mutexes and rw_locks use GCC atomic builtins
160430  7:07:06 InnoDB: Compressed tables use zlib 1.2.8
160430  7:07:06 InnoDB: Using Linux native AIO
160430  7:07:06 InnoDB: Initializing buffer pool, size = 128.0M
160430  7:07:06 InnoDB: Completed initialization of buffer pool
160430  7:07:06 InnoDB: highest supported file format is Barracuda.
160430  7:07:06  InnoDB: Waiting for the background threads to start
160430  7:07:07 InnoDB: 5.5.49 started; log sequence number 290393900
160430  7:07:07 [Note] Server hostname (bind-address): '::'; port: 3306
160430  7:07:07 [Note]   - '::' resolves to '::';
160430  7:07:07 [Note] Server socket created on IP: '::'.
160430  7:07:07 [Note] Event Scheduler: Loaded 0 events
160430  7:07:07 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.5.49-0ubuntu0.14.04.1'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)

```

Nothing looks unusual in either of those.

in my.conf
bind-address is listed as 127.0.0.1.

additionally, the mythtv.conf file in the /etc/mysql/conf.d/ folder says, ```

[mysqld]
bind-address=::
max_connections=100

```

Checking mysql connection from FrontEnd returns this (all looks good):
```

mythtvfe-lr@mythtvfe-lr:~$ mysql -umythtv -p[redacted] -h10.0.0.70 mythconverg
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 322
Server version: 5.5.49-0ubuntu0.14.04.1 (Ubuntu)

Copyright (c) 2000, 2016, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> ^CCtrl-C -- exit!

```

And finally, running "mythtv-setup -O ThemePainter=qt -v all" nets this:
```


mtvbe@mtvbe:~$ sudo initctl stop mythtv-backend
[sudo] password for mtvbe: 
mythtv-backend stop/waiting
mtvbe@mtvbe:~$ mythtv-setup -O ThemePainter=qt -v all
ERROR 1046 (3D000) at line 1: No database selected

```

And >  Were you using mythmusic?
Were you using storage groups?
No and no.

Thanks again.

---

### Post by blm-ubunet on 2016-04-30
That mythtv-setup error is very strange.. Is it the user?

When you run mythtv-setup (or mythbackend.real) from a terminal as the user "mtvbe" these programs do not run as the correct user. This could be bad.
IIUC mythbackend should run as user "mythtv".

Check "mtvbe" is a member of "mythtv" group (if you have one).
[https://help.ubuntu.com/community/MythTV/Install/Server/Backend](https://help.ubuntu.com/community/MythTV/Install/Server/Backend)

Look for /home/mtvbe/.mythtv/config.xml for wrong dB credentials/details.

You have to have at least a default SG setup.

"bind-address = ::" means bind to any IPv4 IPv6 (I didn't know that)
"bind-address = 0.0.0.0" bind to any IPv4
I would avoid the IPv6 complication.

---

### Post by griggs2 on 2016-05-01
blm-ubunet (and others watching from afar),

Thanks again for your help.

> 
That mythtv-setup error is very strange.. Is it the user?

When you run mythtv-setup (or mythbackend.real) from a terminal as the  user "mtvbe" these programs do not run as the correct user. This could  be bad. 

IIUC mythbackend should run as user "mythtv".

Check "mtvbe" is a member of "mythtv" group (if you have one).
[https://help.ubuntu.com/community/My...Server/Backend]("https://help.ubuntu.com/community/MythTV/Install/Server/Backend")


I can't believe so - It's always worked with this user (v0.26 and 0.27) - "mtvbe" is the only user in the mythtv group - and on this backend, it's the only user besides root.

> 
Look for /home/mtvbe/.mythtv/config.xml for wrong dB credentials/details.


/home/mtvbe/.mythtv/config.xml contents:
```

<Configuration>
  <LocalHostName>my-unique-identifier-goes-here</LocalHostName>
  <Database>
    <PingHost>1</PingHost>
    <Host>localhost</Host>
    <UserName>mythtv</UserName>
    <Password>[redacted]</Password>
    <DatabaseName>mythconverg</DatabaseName>
    <Port>3306</Port>
  </Database>
  <WakeOnLAN>
    <Enabled>0</Enabled>
    <SQLReconnectWaitTime>0</SQLReconnectWaitTime>
    <SQLConnectRetry>5</SQLConnectRetry>
    <Command>echo 'WOLsqlServerCommand not set'</Command>
  </WakeOnLAN>
</Configuration>

```

See above - The user listed in config.xml file is "mythtv" - I assume that's the user listed for the mysql db, which connected correctly when I previously did the test from a terminal screen on the FrontEnd (using mythtv and the matching passw).

> 
You have to have at least a default SG setup.


Sorry, not quite sure what you mean - I guess I'll have to fall back on "it worked before." (classic, yeah, I know. heh. sorry!)

> 
"bind-address = ::" means bind to any IPv4 IPv6 (I didn't know that)
"bind-address = 0.0.0.0" bind to any IPv4
I would avoid the IPv6 complication.


Done.

Per MythTV BackEnd install instructions, I commented out "bind-address = 127.0.0.1" in the my.cnf file and per your instructions, changed the bind-address in the /etc/mysql/conf.d/mythtv.cnf file.

Still no change. Just the MythTV Setup Terminal is displayed.

Thanks!

./g

---

### Post by blm-ubunet on 2016-05-01
<> Host>localhost</Host>

localhost needs to changed to a static IP or resolvable hostname (via local /etc/hosts files) to the static IP the mysql server is listening on.
I do **not** think link local 127.0.0.1 is okay.

The remote FE uses its own copy of the config.xml file.

start mythtv-setup on MBE with
```
mythtv-setup -O ThemePainter=qt -v upnp --loglevel=debug
```
might need to change "upnp" to "all" or to "upnp,http"
and/or change "debug" to "notice" or "warning"

---

### Post by griggs2 on 2016-05-02
Fixed localhost reference (tho from terminal that properly resolves to 127.0.0.1) - I've tried the machines hostname (mtvbe) and it's static ip address (10.0.0.70) in the appropriate fields.

I've tried setting the log options and forcing themepainter to qt, but it still hangs with the error that it can't connect to the db. Consequently, since that's the first order of operation, nothing is getting logged. 

I loaded phpmyadmin and was able to successfully connect to the local mysql db (converg) with the uid of "mythtv" and the associated passw. So that part seems fine. 

I'm a little flummoxed by this. None of it makes sense. I'd consider rolling backwards, but at this point, I'm not sure what's entailed in that project.


Thanks again.

./g

---

### Post by griggs2 on 2016-05-03
Does anyone know if MythTV is using /etc/mythtv and/or /home/[user]/.mythtv/??

Seems like I have two locations with copies of config.xml and mythtv.txt... (technically, the mythtv.txt file is a link to the /etc/mythtv version.)

The files all seems mostly similar, but the one in /.mythtv under the user has other current subdirectories (like cache)...


Is there anyway to force a rerun of the db upgrade in 0.28? (like when 0.28 was first run.)
I restored my db from 0.27, and I'm wondering if there a marker somewhere that isn't allowing the db upgrade to occur again.

Thanks!

./g

---

### Post by blm-ubunet on 2016-05-06
Your (earlier) dB error (1046) sounds like missing database schema or wrong name or bad spelling.
Maybe username/password or database tables may be wrong in /etc/mythtv/mysql.txt.

Please try:
```
mysql -umythtv -pmythtv -h10.0.0.70 mythconverg
select hostname from settings group by hostname;
quit
```
on the backend.. do NOT change the host/address.
Check "mtvbe" resolves to 10.0.0.70 or better don't use the name... 
Do not use localhost or 127.0.0.1 anywhere.

Check there is no spelling mistakes with "mythconverg" schema anyway..

The mythtv.txt file is deprecated/unused.

MythTV searches for config.xml is sequence of locations. First found is the winner.
First:  /home/"user"/.mythtv/config.xml
2nd:  /etc/mythtv/config.xml

If running FE & BE on the same box..good idea is to symlink possible FE users to the one file in "mythtv" home folder.

A "user" should normally be "mythtv" for the BE.

A MythTV system must have one MBE & both IP addresses (listed in mythtv-setup run on the MBE) must be the same & be IP addresses not hostnames.
There is only one mysql server used by a mythtv cluster.

Are you sure the mysql password for the "mythtv" user is right/works & matches everywhere ?
Other "users" might not be able to access MythTV's schema by default.. have to grant access rights to other users/IP-ranges.

---

### Post by jammastercd on 2016-05-09
I too am having the same type of issue.  I upgraded MythTV from 0.27 to 0.28 on 14.04 LTS.  I have a single backend with multiple Kodi frontends.  Upon completing the upgrade, none of my FE's can connect.  However, I can see the backend is running and recording shows via Mythweb.  When I try to run mythtv-setup, I get an error message stating:

"ERROR 1046 (3D000) at line 1: No database selected"

I've gone through the two config files listed in the thread ([COLOR=#000000]/home/mythtv/.mythtv/config.xml and [/COLOR][COLOR=#000000]/etc/mythtv/config.xml[/COLOR]) and have confirmed they contain the correct information, which is as follows:
Host=192.168.1.40
Username=mythtv
Password=[redacted]
DatabaseName=mythconverg
Port=3306

In the /etc/mysql/my.cnf file, I've changed the bind address to 0.0.0.0 and commented out the line skip-external-locking.

In the /etc/mysql/conf.d/mythtv.cnf file, I've changed the bind address to 0.0.0.0.

I've confirmed I can log into mysql using the following text:
mysql -umythtv -p[redacted] -h192.168.1.40 mythconverg

With all of these changes and tests, I continue to receive the ERROR 1046 message when I try to run mythtv-setup.  Thoughts?:confused:

---

### Post by griggs2 on 2016-05-10
Not glad you're also having the same problem, but happy it's not just me... :)

./s4z

---

### Post by griggs2 on 2016-05-11
blm-ubunet:

Here's a [syslog from just before starting mythtv-setup]("http://pastebin.com/RPxjHnKX").

During start up it looks like a segfault (see line 11).

Are there other log files I should be looking at? Mythtv-setup.log hasn't been written to since before the upgrade.

./griggs

---

### Post by griggs2 on 2016-05-13
Now that the FrontEnd issues have been resolved (see [this thread]("http://ubuntuforums.org/showthread.php?t=2324100") if you care). Back to the BackEnd...

It appears that the mythbackend is running (recording, playing back, etc.) as expected at this moment. The problem of myth-setup still crashing persists.

In the next day or so, I'll post some new log files, and we'll see if we can work thru this.

./g2

---

### Post by blm-ubunet on 2016-05-14
If mythtv-setup is started as a different "user" then a different config.xml path/file could be used..

Could try start mythtv-setup with debugger "gdb". Would need to install the debugging symbols package.
Could try start with themepainter override:-
```
mythtv-setup -O ThemePainter=qt
```

Starting it from terminal means the logging goes to stdout/stderr & does not go to (r)syslog unless you make it do so..

FE auto-discovery...
Your BE could have UPNP disabled so is not listening on UDP address/port.

---

### Post by griggs2 on 2016-05-14
Problem solved with mythtv-setup on the BackEnd. All is working now.

The clue to the mystery was in doing a little research on the SegFault error listed in the syslog that I posted earlier in this thread (May 11 18:03:18 mtvbe kernel: [437962.121230] mythtv-setup.re[3184]:  segfault at 18 ip 00007f6c5e63f7e2 sp 00007ffd9ed05bd0 error 4 in  libqxcb.so[7f6c5e610000+a7000]).

Weird combination of factors here - I moved my display from the BackEnd, as it shares closet space with my FreeNAS, and the display was needed on that... So essentially the BackEnd had been running headless and I've been using VNC to manage the BackEnd.

I'm not sure if the cause was that it was now headless or that I was using VNC, or a combination thereof. I recall being able to use myth-setup over vnc in the past, but I don't remember if the display was connected and powered on at the time or not.

Reconnecting the display and fully power cycling the BackEnd allowed myth-setup to run without segfaulting on the library from Qt.

As nice as the menuing is for the BackEnd using Qt - in my pea sized brain it seems to make more sense to not use Qt if doing so causes these kinds of errors - It might be better to write an actual windowing set-up application that functions on the desktop and would work on a headless system.

Thanks for everyone's patience and assistance with this. Hopefully it helps a couple others who might run into this sort of thing in the future.

./g2

---

### Post by blm-ubunet on 2016-05-15
You never mentioned running the BE headless...
It does work fine over ssh:-
ssh -C -X mythtv@mtvbe
then
mythtv-setup --geometry XXXxYYY

---

