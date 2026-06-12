---
title: "HDHomeRun not found on reboot"
date: 2008-01-30
forum: Mythbuntu
---

### Post by ttabbal on 2008-01-30
I have a fresh install of MythBuntu 7.10. When I boot up, mythbackend can't find my HDHR tuners. If I do a "/etc/init.d/mythtv-backend restart" from an SSH login, it comes up and finds the HDHR just fine and I can record, watch live TV, etc.. Is there some way to get myth to retry the connection automatically? I tried changing to static IP as I saw a message about the network not being available. That made the unavailable message go away, now it just doesn't find the HDHR. I also tried giving myth the device ID of the HDHR tuner instead of using FFFFFFFFFF, but it still doesn't work properly. 

Any hints? Otherwise, Mythbuntu has been great to set up. I just did a pretty basic install and updated the packages using the software update tool. There were some updates to Myth in there. The updater says I'm up to date now. 

It would be nice if the control panel application offered to setup the HDHR for lirc. I used the HDHR website and a thread I found on the forum here to set it up manually editing the config files. I don't mind doing that, but it would be nice to have the tool help out. Great config tool overall though, it really helped me remember all the setup steps to get things going.

---

### Post by ttabbal on 2008-01-31
I found some code on the HDHomerun forums that seems to get the job done. I added this in the start section of the myth-backend statup script. I also had to change the shell from /bin/sh to /bin/bash for the "let" command to work. 

It just forces mythbackend to wait until the hdhomerun_config utility can see the HDHR on the network before it starts up. It seems to get the job done on my machine, though it wouldn't make any sense for users using other capture devices.  


   ```
     
        let n=1
        while [ "$(hdhomerun_config discover)" = "no devices found" -a $n -lt 30 ]
        do
          echo "hdhomerun not found, retry $n"
          let n=n+1
          sleep 1
        done

```

---

### Post by superm1 on 2008-01-31
> **ttabbal said:**
> I found some code on the HDHomerun forums that seems to get the job done. I added this in the start section of the myth-backend statup script. I also had to change the shell from /bin/sh to /bin/bash for the "let" command to work. 

It just forces mythbackend to wait until the hdhomerun_config utility can see the HDHR on the network before it starts up. It seems to get the job done on my machine, though it wouldn't make any sense for users using other capture devices.  


   ```
     

        let n=1
        while [ "$(hdhomerun_config discover)" = "no devices found" -a $n -lt 30 ]
        do
          echo "hdhomerun not found, retry $n"
          let n=n+1
          sleep 1
        done

```
This should be fixed in 8.04, mythbackend is supposed to start a lot later.  Additionally you should be able to get around it by using /etc/network/interfaces rather than network-manager in 7.10.

---

### Post by ttabbal on 2008-01-31
Thanks for the update. I'm not ready to run 8.04 yet, I'm going to wait for the official release. This gets me by for now. I remember looking in /etc/network/interfaces, I thought I had the config in there the normal way. Perhaps I'm remembering the wrong file.

---

### Post by superm1 on 2008-01-31
> **ttabbal said:**
> Thanks for the update. I'm not ready to run 8.04 yet, I'm going to wait for the official release. This gets me by for now. I remember looking in /etc/network/interfaces, I thought I had the config in there the normal way. Perhaps I'm remembering the wrong file.
If you open up network-admin in 7.10, you can configure it to "not use roaming" and then that will configure it using /etc/network/interfaces.

---

### Post by fusionisthefuture on 2009-04-24
man, i really wish this problem was resolved this easily, as long ago as the last post on this thread.  

ive been dealing with this same problem since 7.04 myself, with a hdhomerun tuner.  ive never once been able to use it to record a show like i would like, unfortunately.  

im now on 9.04, and the problem persists.  ive seen about a dozen different workarounds for this problem, but i have yet to find one that works 100% of the time, save the get-it-from-thepiratebay.org-two-days-later one.  

does anyone know of a way i can fix this yet?

just to be clear, the problem is that myth-backend is never running when i boot, it has to be restarted from the terminal.  ive found atleast one method that seems to make it wait long enough to work about half the time.  

i know many of you are thinking "why not just leave your computer on?"  well, energy savings for one, noise for another.

---

### Post by ttabbal on 2009-04-25
The real fix is to have Myth keep looking for the tuners. I don't know why it doesn't. Perhaps it's time for me to dust off the old compiler and see if I can submit a patch. 

Have you tried the most recent .21-fixes releases? Or even trunk?

---

### Post by fusionisthefuture on 2009-04-25
im using whatever version of myth comes in the 9.04 repos.  i havent tried anything with it on this release yet.  how to go about getting it to keep looking would be helpful.

---

### Post by whosmatt on 2009-04-25
> **fusionisthefuture said:**
> man, i really wish this problem was resolved this easily, as long ago as the last post on this thread.  

ive been dealing with this same problem since 7.04 myself, with a hdhomerun tuner.  ive never once been able to use it to record a show like i would like, unfortunately.  

im now on 9.04, and the problem persists.  ive seen about a dozen different workarounds for this problem, but i have yet to find one that works 100% of the time, save the get-it-from-thepiratebay.org-two-days-later one.  

does anyone know of a way i can fix this yet?

just to be clear, the problem is that myth-backend is never running when i boot, it has to be restarted from the terminal.  ive found atleast one method that seems to make it wait long enough to work about half the time.  

i know many of you are thinking "why not just leave your computer on?"  well, energy savings for one, noise for another.

I am also having this problem.. Fresh 9.04 install, new HDHomerun.  It works great until I reboot.  to get it working again, I have to go back to the backend setup and just touch the tuner setup; i don't have to delete and re-add... it is enough just to confirm the tuners that are already set up in the database.

---

### Post by whosmatt on 2009-04-25
I think I fixed my problem simply by adding an entry for eth0 to /etc/network/interfaces  

why would it default to not bringing up the NIC until xfce loads?  that seems kind of dumb.

---

### Post by fusionisthefuture on 2009-04-25
what did you add to the interfaces file?

---

### Post by whosmatt on 2009-04-25
> **fusionisthefuture said:**
> what did you add to the interfaces file?

```
auto eth0
iface eth0 inet dhcp
```

for a static ip it would be something like this

```
auto eth0
iface etho inet static
address 192.168.44.204
netmask 255.255.255.0
gateway 192.168.44.1
```

then you would edit resolv.conf and enter your dns server(s) there

---

### Post by superm1 on 2009-04-26
> **whosmatt said:**
> I think I fixed my problem simply by adding an entry for eth0 to /etc/network/interfaces  

why would it default to not bringing up the NIC until xfce loads?  that seems kind of dumb.
Given this type of solution, this can be two possible different bugs that i see:

1) Network Manager isn't configuring system wide connections for ethernet devices.  Check in the gui when xfce gets started up

2) Network Manager is configuring the device too late at startup.  This sounds most likely to me, and short of writing a patch for mythtv to periodically try to connect to a device that it doesn't find on startup, I'm not sure what else can be done about this.

---

### Post by Dewey_Oxberger on 2009-04-26
It's sure looks like NetworkManager bringing up the network much more slowly than just manually configuring it.  The mythbackend logs show "network unreachable".

I have another problem in 9.04 that is kind of related - mysql isn't coming up quickly and it seems related to the network being up.  Mythfrontend is choking up failed db queries and frontend boots into a crippled state.

To get it all working in 9.04 I had to manually configure the network by making the /etc/network/interfaces file:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

Then had to move /etc/rc2.d/S31mythtv-backend to S99z_mythtv_backend to give mysql enough time to come up (It now works after a reboot about 90% of the time).

There are some crazy loose screws in the mysql stuff.  I've seen 100% cpu from mysqld on a few occasions.  All of it looks like it has been bugged but it's to crazy to get a handle on.

---

### Post by AKADAP on 2009-04-28
I had this issue (see this thread: [http://ubuntuforums.org/showthread.php?t=1064519](http://ubuntuforums.org/showthread.php?t=1064519))
Unfortunately, the link to the solution at silicondust is now broken.
I'll attempt to describe the fix here.
The trick is to delay the start of mythbackend until the network is up and the HDHomeRun devices are talking.

In the /etc/rc2.d directory, change the name of S??mythtv-backend to S50mythtv-backend. The ?? was a lower number (I don't have it anymore, so I don't know what that ?? was). This puts the start of mythtv-backend later in the boot process.

In the same directory, create a file named "S49WaitForHDHomeRun" with the following contents:
```
let retries=0
echo -e "Waiting for network to reach HDHomeRun\n"
until hdhomerun_config discover >/dev/null
do
  if [ $retries -gt 15 ]; then
    eerror "Timed out, no HDHomeRun found"
    return 1
  fi
  echo -n "-"
  sleep 1
  let retries=retries+1
done
echo -e "HDHomeRun found\n"

```

This program attempts to contact a HDHomeRun box, and hangs up the boot process until it succeeds or times out. It tries 15 times with a one second delay between each retry.
You will probably have to do a sudo to create this file as root, and sudo to change the name of the S50mythtv-backend file.
Also you will have to do a 

sudo chmod +x S49WaitForHDHomeRun

to make it executable.

I got this from the silicon dust website a few months ago, but it seems to have disappeared from there.

Anyway, I have been using this without problems since I implemented it.

---

### Post by Dewey_Oxberger on 2009-04-28
lol - I wrote that script a year ago and posted it to the SD forum.  It was written for bash.  It kind-of works in sh but not totally.  I'll attach the correct version here.  (It needs a #!/bin/bash at the top).

Oddly enough that script didn't work for me in 9.04 because of the strange behavior in mysql.  I've been writing STATUS queries to see if I can see what mysql is doing but I'm not learning anything worthwhile.  I need to write a script that actually connects and does db queries.  I suspect that mysql does some kind of restart about 5 sec after the network comes up and that is screwing up mythbackend.

I called it S61WaitForSDHomeRun.txt but you can drop the .txt.

---

### Post by AKADAP on 2009-04-29
> **Dewey_Oxberger said:**
> lol - I wrote that script a year ago and posted it to the SD forum.  It was written for bash.  It kind-of works in sh but not totally.  I'll attach the correct version here.  (It needs a #!/bin/bash at the top).

Oddly enough that script didn't work for me in 9.04 because of the strange behavior in mysql.  I've been writing STATUS queries to see if I can see what mysql is doing but I'm not learning anything worthwhile.  I need to write a script that actually connects and does db queries.  I suspect that mysql does some kind of restart about 5 sec after the network comes up and that is screwing up mythbackend.

I called it S61WaitForSDHomeRun.txt but you can drop the .txt.

Well, thank you.
At least for me, this has been working.

---

### Post by AKADAP on 2009-04-30
Damn! Its not working any more!
I added the #!/bin/bash line at the beginning of the file,
change the eerror line to echo -e, and the return 1 to exit 1, and now it doesn't work.

I manually ran the program and it returned 0 when the HDHomeRuns were found, and delayed 15 seconds when HDHomeRuns were not found, so the script works, but now on boot my system does not find any tuners, including the ATI HD Blunder which does not depend on the network at all!

My system hasn't recorded anything since monday (the 27th), so it appears not to be an issue with changing the script.

---

### Post by AKADAP on 2009-05-01
I let my computer power itself up for a 7:00 PM recording. When it was up, it had no tuners, and had deleted all scheduled recordings.

Looking in the mythbackend.log, I found a bunch of errors:
2009-04-30 18:39:00.886 Current Schema Version: 1214
Starting up as the master server.
2009-04-30 18:39:04.288 DB Error (InitializeInputs):
Query was:
SELECT cardinputid,        inputname,   startchan,        tunechan,    externalcommand,        sourceid FROM cardinput WHERE cardid = 1
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

Looking through syslog, I find:
Apr 30 18:38:45 amachine mysqld_safe[3225]: started
Apr 30 18:38:45 amachine mysqld[3228]: 090430 18:38:45 [Warning] option 'net_buffer_length': unsigned value 8388608 adjusted to 1048576
Apr 30 18:38:46 amachine mysqld[3228]: 090430 18:38:46  InnoDB: Started; log sequence number 0 150867
Apr 30 18:38:46 amachine mysqld[3228]: 090430 18:38:46 [Note] /usr/sbin/mysqld: ready for connections.
Apr 30 18:38:46 amachine mysqld[3228]: Version: '5.0.75-0ubuntu10'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
Apr 30 18:38:46 amachine /etc/mysql/debian-start[3339]: Upgrading MySQL tables if necessary.

then:
Apr 30 18:39:03 amachine mysqld_safe[4600]: Number of processes running now: 1
Apr 30 18:39:03 amachine mysqld_safe[4608]: mysqld process hanging, pid 3227 - killed
Apr 30 18:39:03 amachine mysqld_safe[4611]: restarted
Apr 30 18:39:03 amachine mysqld[4614]: 090430 18:39:03 [Warning] option 'net_buffer_length': unsigned value 8388608 adjusted to 1048576
Apr 30 18:39:03 amachine mysqld[4614]: InnoDB: Log scan progressed past the checkpoint lsn 0 150867
Apr 30 18:39:03 amachine mysqld[4614]: 090430 18:39:03  InnoDB: Database was not shut down normally!
Apr 30 18:39:03 amachine mysqld[4614]: InnoDB: Starting crash recovery.
Apr 30 18:39:03 amachine mysqld[4614]: InnoDB: Reading tablespace information from the .ibd files...
Apr 30 18:39:03 amachine mysqld[4614]: InnoDB: Restoring possible half-written data pages from the doublewrite
Apr 30 18:39:03 amachine mysqld[4614]: InnoDB: buffer...
Apr 30 18:39:03 amachine mysqld[4614]: InnoDB: Doing recovery: scanned up to log sequence number 0 150877
Apr 30 18:39:03 amachine mysqld[4614]: 090430 18:39:03  InnoDB: Started; log sequence number 0 150877
Apr 30 18:39:03 amachine mysqld[4614]: 090430 18:39:03 [Note] /usr/sbin/mysqld: ready for connections.
Apr 30 18:39:03 amachine mysqld[4614]: Version: '5.0.75-0ubuntu10'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)

Which means I get the error message in the mythbackend.log just about the same time mysqld gets restarted.

I see two possibilities, 1) Myth does a query at just the wrong time and gets hosed. 2) Myths query causes the database daemon to hang.

I hope it is the first because if it is, it can be fixed with a 30 second delay during the boot process, so that is what I will attempt.

---

### Post by AKADAP on 2009-05-01
This did not work. This morning, my computer was on and recording, but it had found only one of the five tuners, and there were a bunch of "MySQL server has gone away" errors in the myth log. Unfortunately, the system logs did not go back far enough for me to see if the same error occurred.

---

### Post by Dewey_Oxberger on 2009-05-02
Finally, someone with the same problem as me!  With 9.04 I've been fighting this dragon for weeks.

I got it working: manually config the network.  Shut off NetworkManager.  In rc2.d move S31Mythbackend to S99zMythbackend.

Watch those logs.  I still get a failed query from time to time but it mostly works.

From what I can tell mysql comes up, then about 5 sec later it stops taking connections for a few seconds.  Then it starts working again.  I'd guess the issue has always been there but 9.04 has just the right boot timing to expose the problem.

---

### Post by AKADAP on 2009-05-02
I am still having issues with the mysql_safe daemon thinking that mysqld is hung and killing it.

What I'd like to do is change the S50mythtv-backend link to point to a different script that starts a 3rd script and exits. That third script would wait a minute or two before calling the original mythtv-backend script.

The idea is to have the first script return immediately so that it does not hang up the boot sequence. I'd like to delay the start of mythtv-backend long enough that all of the rest of the booting stuff has completed. I know that it is safe to start mythtv-backend once I have logged in, so in theory this should work.

Problem is, I don't know much about what Linux is doing during the start of all of those daemons. Is each of those daemon starting scripts running as its own thread with nothing waiting for their completion? If not, how do I start a background thread and return such that the system thinks the original calling thread has completed.

I'd also like to be able to add messages to the log file in my script. I see other scripts using "log_daemon_msg" and similar commands, but I don't know where those are documented.

---

### Post by Dewey_Oxberger on 2009-05-02
To see what the script is doing you can just use echo and do alt+tab+F8 which shows the boot session.  You'll see the messages there.

---

### Post by AKADAP on 2009-05-03
using ctl-alt-F8, I was able to see that the WaitForHDHomeRun script was finding the HDHomeRun cards on its first attempt, and it is delaying the start of mythbackend by a minute as it should. Unfortunately, I still found this in my syslog file:

May  3 09:39:02 AComputer /USR/SBIN/CRON[4232]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
May  3 09:39:58 AComputer mysqld_safe[4576]: Number of processes running now: 1
May  3 09:39:58 AComputer mysqld_safe[4584]: mysqld process hanging, pid 3206 - killed
May  3 09:39:58 AComputer mysqld_safe[4587]: restarted

From this you can see the 1 minute delay, so it appears that mysqld_safe doesn't detect that mysqld is hung until the mythbackend attempts to access the database. This means a simple delay is unlikely to fix the problem.

Is there a way to do a simple, harmless database access from a script that would trigger the mysqld_safe to restart mysqld? If I could put that in my script before the delay, it might work around the problem.

---

### Post by voipguy on 2009-05-03
Im running 9.04 and have a HDHR also, what was your fix to have the hdhr work after a re-boot?

my current work-around is to exit myth front end, start myth backend, exit, run mythfilldatabase, re-start myth frontend.

Please explain:
I got it working: manually config the network. How?

 Shut off NetworkManager.   How? 

In rc2.d move S31Mythbackend to S99zMythbackend. How?

Thanks!
Chuck

---

### Post by Dewey_Oxberger on 2009-05-03
AKADAP, I'm with you.  We need a script to wait for the database to be up and stable.  Kind of like the WaitForHDHomeRun script.

I have tried using mysql to query the uptime but it isn't much help.

I don't know much about database access.  I'm not sure what can be done from the command line.  It may take perl or python to get it going.

---

### Post by AKADAP on 2009-05-04
> **Dewey_Oxberger said:**
> AKADAP, I'm with you.  We need a script to wait for the database to be up and stable.  Kind of like the WaitForHDHomeRun script.

I have tried using mysql to query the uptime but it isn't much help.

I don't know much about database access.  I'm not sure what can be done from the command line.  It may take perl or python to get it going.

A simple delay won't be enough. I have delayed the start of mythbackend by up to a minute, that also delays the restart of mysqld. It does seem to help a bit in that since fewer things are happening after a 1 minute delay, the restart of mysqld happens faster, and I get fewer errors in the mythbackend log, but it certainly does not solve the problem. This was why I was asking about a simple harmless database query I could do to hopefully trigger the mysqld restart before the delay.

---

### Post by AKADAP on 2009-05-04
> **voipguy said:**
> Im running 9.04 and have a HDHR also, what was your fix to have the hdhr work after a re-boot?

my current work-around is to exit myth front end, start myth backend, exit, run mythfilldatabase, re-start myth frontend.

Please explain:
I got it working: manually config the network. How?

 Shut off NetworkManager.   How? 

In rc2.d move S31Mythbackend to S99zMythbackend. How?

Thanks!
Chuck

Look in your log files, I've seen people complain of at least three different causes of this problem. My system suffers from two of them.

1) myth backend starts before network is up, can't find HDHomeRun.
       Solution: add script to poll for detection of HDHomeRun, delaying start of mythbackend (see a few posts back for scripts for this)

2) mysql_safe thinks mysqld has hung and restarts causing database errors in mythbackend log.
       No solution yet.

3) some other network problem. (I don't have this one, see Dewey_Oxberger post)

All of the files that appear in /etc/rc2.d are actually symbolic links to files in /etc/init.d When he mentions moving Sxxfile to Syyfile, all that really happens is renaming the symbolic link.
This is done by changing to the /etc/rc2.d directory, then running the following command:
sudo mv SxxFile SyyFile

This directory is used during the startup an runlevel 2 to start daemons. the S at the beginning of the file name means that the system should start the daemon, the number indicates the sequence that the start of daemons happens. (From this point on, I'm guessing as to what actually happens) If there are two files SxxFile and SyyFile where xx<yy, SxxFile must complete before SyyFile is allowed to start. I think all files such that xx==yy are run in parallel.

---

### Post by superm1 on 2009-05-07
Regarding the mysql being hung thing, please activate jaunty-proposed, perform all updates (make sure mysql server gets updated) and add feedback to bug 
**326768**

Note, this might actually help the problem with the hdhr too indirectly since mysql is "actually" ready sooner..

Thanks!

---

### Post by AKADAP on 2009-05-07
> **superm1 said:**
> Regarding the mysql being hung thing, please activate jaunty-proposed, perform all updates (make sure mysql server gets updated) and add feedback to bug 
**326768**

Note, this might actually help the problem with the hdhr too indirectly since mysql is "actually" ready sooner..

Thanks!

Tried this, it required a reboot, still got this in my log file
May  7 12:43:01 AComputer mysqld_safe[4938]: Number of processes running now: 1
May  7 12:43:01 AComputer mysqld_safe[4946]: mysqld process hanging, pid 3191 - killed
May  7 12:43:01 AComputer mysqld_safe[4949]: restarted

---

### Post by AKADAP on 2009-05-09
> **AKADAP said:**
> Tried this, it required a reboot, still got this in my log file
May  7 12:43:01 AComputer mysqld_safe[4938]: Number of processes running now: 1
May  7 12:43:01 AComputer mysqld_safe[4946]: mysqld process hanging, pid 3191 - killed
May  7 12:43:01 AComputer mysqld_safe[4949]: restarted

Installed a new update today, Lots of mysqld messages in the log file, none appear to be errors, all appear to occur when mysqld starts, none occurred when mythtv-backend started 3 minutes later. 
Seems the bug may be fixed.

---

### Post by superm1 on 2009-05-09
> **AKADAP said:**
> Installed a new update today, Lots of mysqld messages in the log file, none appear to be errors, all appear to occur when mysqld starts, none occurred when mythtv-backend started 3 minutes later. 
Seems the bug may be fixed.
It's important to specify the version of mysql you are using when posting messsages so we know where your issue is in reference to
apt-cache policy mysql-server-5.0 would do the trick

---

### Post by AKADAP on 2009-05-10
> **superm1 said:**
> It's important to specify the version of mysql you are using when posting messsages so we know where your issue is in reference to
apt-cache policy mysql-server-5.0 would do the trick
```

mysql-server-5.0:
  Installed: 5.1.30really5.0.75-0ubuntu10.1
  Candidate: 5.1.30really5.0.75-0ubuntu10.1
  Version table:
 *** 5.1.30really5.0.75-0ubuntu10.1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/main Packages
        100 /var/lib/dpkg/status
     5.1.30really5.0.75-0ubuntu10 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages

```

---

### Post by AKADAP on 2009-05-11
> **AKADAP said:**
> Installed a new update today, Lots of mysqld messages in the log file, none appear to be errors, all appear to occur when mysqld starts, none occurred when mythtv-backend started 3 minutes later. 
Seems the bug may be fixed.

I spoke too soon. I found missing database errors in mythbackend.log again. syslog reset itself after this error occurred, so I could not see the database error that caused it.

---

### Post by Dewey_Oxberger on 2009-05-12
Are you sure it wasn't from a system reboot or shutdown?

I'm having no trouble with the patch installed.

---

### Post by AKADAP on 2009-05-13
> **Dewey_Oxberger said:**
> Are you sure it wasn't from a system reboot or shutdown?

I'm having no trouble with the patch installed.

I only see that error message on boot, never on shutdown.

Did not see the error on the last two boots.
It appears that the syslog is being restarted every other day. Unfortunately it does so shortly after boot, so when it does, I get no data on the boot process.

---

### Post by storyid on 2009-06-07
I have logged a bug with the mythbuntu team about the issue of the hdhomerun not being found at boot/reboot.  I encourage everyone else that is having this problem to go out and say "this affects me too".  Thank you!

Here is a link to the bug report:

[https://bugs.launchpad.net/mythbuntu/+bug/384556](https://bugs.launchpad.net/mythbuntu/+bug/384556)

Ian

---

