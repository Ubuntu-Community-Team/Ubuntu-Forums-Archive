---
title: "Myth backend starts before DVB-T initialised"
date: 2009-12-03
forum: Mythbuntu
---

### Post by Sangoma-1701D on 2009-12-03
Hi all,

Since my upgrade to 9.10 (well, upgrade, hosed then reinstall) I have been having issues with mythbackend. At first I thought it was crashed MySQL tables, but having checked this on a regular basis and scripting a fix for the tables at each boot I noticed the issue still occurring.
Investigating the logs further they appear to imply that once mythbackend has started, opened the database and read the location of the configured DVB-T cards it can't open them.

> 2009-12-02 18:28:33.946 mythbackend: Problem with capture cards: Card 1failed init
2009-12-02 18:28:34.037 DVBChan(2:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: No such file or directory (2)
2009-12-02 18:28:34.050 DVBChan(2:/dev/dvb/adapter0/frontend0) Error: Failed to open DVB frontend device due to fatal error or too many attempts.
2009-12-02 18:28:34.099 mythbackend: Problem with capture cards: Card 2failed init
2009-12-02 18:28:34.135 DVBChan(3:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
			eno: No such file or directory (2)
2009-12-02 18:28:34.167 DVBChan(3:/dev/dvb/adapter1/frontend0) Error: Failed to open DVB frontend device due to fatal error or too many attempts.
2009-12-02 18:28:34.196 mythbackend: Problem with capture cards: Card 3failed init
2009-12-02 18:28:34.212 DVBChan(4:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
			eno: No such file or directory (2)
2009-12-02 18:28:34.243 DVBChan(4:/dev/dvb/adapter1/frontend0) Error: Failed to open DVB frontend device due to fatal error or too many attempts.
2009-12-02 18:28:34.260 mythbackend: Problem with capture cards: Card 4failed init
2009-12-02 18:28:34.282 MythBackend, Error: No valid capture cards are defined in the database.

A simple restart of mythbackend fixes the issue.
This leads me to believe that with mythbackend now using Upstart it may be starting before the cards are initialised and therefore can't see the cards.

Looking at the Upstart mythbackend script I was wandering if a simple edit of the 'start on' line might allow mythbackend to wait until the cards are available before starting?

From:

```
start on (local-filesystems and net-device-up IFACE=lo)
```

To:

```
start on (local-filesystems and net-device-up IFACE=lo and -e /dev/dvb/adapter0/frontend0 and -e /dev/dvb/adapter1/frontend0)
```

I've set this now in the mythbackend Upstart script (/etc/init/mythtv-backend.conf) and it appears to be working if I run the command:

```

initctl reload mythtv-backend
sudo stop mythtv-backend
sudo start mythtv-backend
```

Problem is, that mythbackend does not appear now to start on boot. Does anyone have any idea where Upstart logs to (if it does - can't see anything in syslog) or know if there is something wrong with the Upstart code I've changed? Or am I barking up the wrong tree completely here with this issue? :)

Many thanks in advance,

Barny.

---

### Post by Sangoma-1701D on 2009-12-05
Ok, I've now managed to figure out the correct syntax for setting in the Upstart script. Testing over the last few hours appears to have resolved my issue.
Hope this helps someone else if they have the same problem.

Adjust your mythbackend Upstart file (/etc/init/mythtv-backend.conf) to something like:

```
script	
	[COLOR="Red"]#added to ensure that the DVB-T cards are init before myth
	while [ -c !/dev/dvb/adapter0/frontend0 ] || [ -c !/dev/dvb/adapter1/frontend0 ]; do
		date >> /home/mythbox/.mythbackend-init.log
		echo "Mythtv-backend Upstart: DVB-T devices are not yet registered. Waiting 1 second then trying again..." >> /home/mythbox/.mythbackend-init.log
		sleep 1s
	done
	date  >> /home/mythbox/.mythbackend-init.log
	echo  "Mythtv-backend Upstart: DVB-T devices are now registered. Starting mythbackend" >> /home/mythbox/.mythbackend-init.log
        #end of additions - original code below[/COLOR]
	test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
	exec /bin/su -c "/usr/bin/mythbackend $ARGS" $USER
end script
```

Remember to change "/dev/dvb/adapter0/frontend0" & "/dev/dvb/adapter1/frontend0" to reflect the path(s) to your tuner devices and change all instances of "/home/mythbox/.mythbackend-init.log" to a log file name/location of your choice.

I have noticed that because of the above changes (obviously) the mythbackend process can sometimes take quite a while to startup, meaning that mythwelcome/mythfrontend can start before the backend. You can delay the start of mythwelcome/mythfrontend by following the advice here:

[https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/470672]("https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/470672")

Barny.

---

### Post by [S2] on 2009-12-13
> **Sangoma-1701D said:**
> 
```
script	
	[COLOR="Red"]#added to ensure that the DVB-T cards are init before myth
	while [ -c !/dev/dvb/adapter0/frontend0 ] && [ -c !/dev/dvb/adapter1/frontend0 ]; do
		date >> /home/mythbox/.mythbackend-init.log
		echo "Mythtv-backend Upstart: DVB-T devices are not yet registered. Waiting 1 second then trying again..." >> /home/mythbox/.mythbackend-init.log
		sleep 1s
	done
	date  >> /home/mythbox/.mythbackend-init.log
	echo  "Mythtv-backend Upstart: DVB-T devices are now registered. Starting mythbackend" >> /home/mythbox/.mythbackend-init.log
        #end of additions - original code below[/COLOR]
	test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
	exec /bin/su -c "/usr/bin/mythbackend $ARGS" $USER
end script
```


Thanks for your script. I had to adapt it a bit, it did not work exactly like you posted it:

```
script	
	[COLOR="Red"]#added to ensure that the DVB-T cards are init before myth
	while [COLOR="Green"][ ! -c /dev/dvb/adapter0/frontend0 ] || [ ! -c /dev/dvb/adapter1/frontend0 ][/COLOR]; do
		date >> /home/mythbox/.mythbackend-init.log
		echo "Mythtv-backend Upstart: DVB-T devices are not yet registered. Waiting 1 second then trying again..." >> /home/mythbox/.mythbackend-init.log
		sleep 1s
	done
	date  >> /home/mythbox/.mythbackend-init.log
	echo  "Mythtv-backend Upstart: DVB-T devices are now registered. Starting mythbackend" >> /home/mythbox/.mythbackend-init.log
        #end of additions - original code below[/COLOR]
	test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
	exec /bin/su -c "/usr/bin/mythbackend $ARGS" $USER
end script
```

---

### Post by Sangoma-1701D on 2009-12-14
S2,

Glad the code has helped.
The reason I have:

```
[ ! -c /dev/dvb/adapter0/frontend0 ] && [ ! -c /dev/dvb/adapter1/frontend0 ];
```

in the while loop is because I have two tuner cards and need mythbackend to wait until both are available. If you only have one you can change the code to just:

```
[ ! -c /dev/dvb/adapter0/frontend0 ];
```

Thanks,

Barny.

---

### Post by [S2] on 2009-12-14
> **Sangoma-1701D said:**
> S2,

Glad the code has helped.
The reason I have:

```
[ ! -c /dev/dvb/adapter0/frontend0 ] && [ ! -c /dev/dvb/adapter1/frontend0 ];
```

in the while loop is because I have two tuner cards and need mythbackend to wait until both are available. If you only have one you can change the code to just:


Hi Barny,

that's wrong :)
&& means "and". If you need to wait for booth cards, you should use "or", so you loop until both cards exist.

```
[ ! -c /dev/dvb/adapter0/frontend0 ] [COLOR="Red"]||[/COLOR] [ ! -c /dev/dvb/adapter1/frontend0 ];
```

reads "if adapter0 does not exist or adapter1 does not exist continue the loop".

---

### Post by Sangoma-1701D on 2009-12-14
Damn it! You are correct. :D :oops:
If I'd coded the loop to check 'if exists' the && would work.
Coding it to check for 'if not exists' then the || is correct.

I hate not statements, real head screw! ](*,)

Thanks S2.

Barny.

---

### Post by thewbman on 2009-12-14
I was having a similar problem with my Hauppauge PVR-500 card.  I used this script with /dev/video0 and /dev/video1 as the device files and it works great.

Thanks.

---

### Post by silverdulcet on 2010-01-26
Just made the upgrade from 9.04 to 9.10 and this fixed a problem with my HVR-2250. I have an HVR-1600 and and HVR-2250. The HVR-1600 would always be ready when mythtv-backend was started. However sometimes, the firmware for the two tuners on the HVR-2250 would not be loaded prior to mythtv-backend starting. This sovled the problem. Thanks so much for posting a solution!

---

### Post by Sangoma-1701D on 2010-01-28
:D glad it helped.

---

### Post by &lt;mike&gt; on 2010-03-27
> **Sangoma-1701D said:**
> 
Remember to change "/dev/dvb/adapter0/frontend0" & "/dev/dvb/adapter1/frontend0" to reflect the path(s) to your tuner devices and change all instances of "/home/mythbox/.mythbackend-init.log" to a log file name/location of your choice.


Would it be possible to pull these paths out of the database dynamically? If so, how do I do it?

---

### Post by Sangoma-1701D on 2010-03-28
Yep, you can do. I've been testing the following modification on my original script for a few weeks now. Probably not the most concise code; I'm sure someone will be able to tidy it up. :)
First it checks that MySQL is running. Then it grabs the MySQL username & password from your mysql.txt file, runs a simple SQL query to get a list of tuner device paths, then loops until all devices are available.
Works for me but your mileage may vary...

Adjust your mythbackend Upstart file (/etc/init/mythtv-backend.conf) to look like (add the red bits):

```
script	
	[COLOR="Red"]#added to ensure that the DVB-T cards are init before myth
	LOG_FILE='/home/mythbox/.mythbackend-init.log' #log file
	#wait for mysql to start
	while [ ! "$(pidof mysqld)" ]; do
		echo "`date`: Mythtv-backend Upstart; MySQL is not ready. Waiting 1 second..." >> $LOG_FILE
		sleep 1s
	done
	echo "`date`: Mythtv-backend Upstart; MySQL is now ready" >> $LOG_FILE
	#get mysql username & password
	MYSQLLIST="~mythtv/.mythtv/mysql.txt ~/.mythtv/mysql.txt /.mythtv/mysql.txt /usr/local/share/mythtv/mysql.txt /usr/share/mythtv/mysql.txt /etc/mythtv/mysql.txt /usr/local/etc/mythtv/mysql.txt mysql.txt"
	for m in $MYSQLLIST
	do
		[ -f $m ] && . $m && break
	done
	#get the tuner card paths
	TUNERS=`mysql --user=${DBUserName} --password=${DBPassword} --database=${DBName} --skip-column-names --execute='SELECT DISTINCT videodevice FROM capturecard;'`
	echo "`date`: Mythtv-backend Upstart; tuners found in database: ${TUNERS}" >> $LOG_FILE
	for t in $TUNERS
	do
		while [ -c !$t ]; do
			echo "`date`: Mythtv-backend Upstart; tuner device ${t} is not ready. Waiting 1 second..." >> $LOG_FILE
			sleep 1s
		done
		echo "`date`: Mythtv-backend Upstart; tuner device ${t} is now ready" >> $LOG_FILE
	done
	echo  "`date`: Mythtv-backend Upstart: tuner devices are now registered. Starting mythbackend" >> $LOG_FILE
        #end of additions - original code below[/COLOR]
	test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
	exec /bin/su -c "/usr/bin/mythbackend $ARGS" $USER
end script
```

Just change the ```
LOG_FILE='/home/mythbox/.mythbackend-init.log'
``` path to a location that you want your log file.

Barny.

---

### Post by ffp on 2010-05-23
Hi,

I adapted this script for Lucid, as:

```
# MythTV Backend service

description     "MythTV Backend"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE=lo)
stop on starting shutdown

#expect fork
respawn

script
#added to ensure that the DVB-T cards are init before myth
	LOG_FILE='/home/htpc/mythbackend-init.log' #log file
	#wait for mysql to start
	while [ ! "$(pidof mysqld)" ]; do
		echo "`date`: Mythtv-backend Upstart; MySQL is not ready. Waiting 1 second..." >> $LOG_FILE
		sleep 1s
	done
	echo "`date`: Mythtv-backend Upstart; MySQL is now ready" >> $LOG_FILE
	#get mysql username & password
	MYSQLLIST="~/.mythtv/mysql.txt /etc/mythtv/mysql.txt"
	for m in $MYSQLLIST
	do
		[ -f $m ] && . $m && break
	done
	#get the tuner card paths
	TUNERS=`mysql --user=${DBUserName} --password=${DBPassword} --database=${DBName} --skip-column-names --execute='SELECT DISTINCT videodevice FROM capturecard;'`
	echo "`date`: Mythtv-backend Upstart; tuners found in database: ${TUNERS}" >> $LOG_FILE
	for t in $TUNERS
	do
		while [ -c !$t ]; do
			echo "`date`: Mythtv-backend Upstart; tuner device ${t} is not ready. Waiting 1 second..." >> $LOG_FILE
			sleep 1s
		done
		echo "`date`: Mythtv-backend Upstart; tuner device ${t} is now ready" >> $LOG_FILE
	done
	echo  "`date`: Mythtv-backend Upstart: tuner devices are now registered. Starting mythbackend" >> $LOG_FILE
#end of additions - original code below

        [COLOR="Red"]USER=mythtv
        ARGS="--logfile /var/log/mythtv/mythbackend.log --user $USER"
        test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
        sleep 10
        /usr/bin/mythbackend $ARGS[/COLOR]
end script
```

And mythbackend don't start !

A simply 

```
sudo start mythtv-backend
```Solves the problem

Can you help me?

Thanks

---

### Post by Sangoma-1701D on 2010-05-24
First check the log file /home/htpc/mythbackend-init.log and see if that gives you any ideas as to where the code is getting stuck.
Secondly, try my original script; you will have to manually put your tuner or tuners paths in, but the script is less complicated and might work better.

Barny.

---

### Post by ffp on 2010-05-24
Thanks for your reply
Here is my /home/htpc/mythbackend-init.log

> Tue May 25 05:07:19 CEST 2010: Mythtv-backend Upstart; MySQL is not ready. Waiting 1 second...
Tue May 25 05:07:20 CEST 2010: Mythtv-backend Upstart; MySQL is now ready
Tue May 25 05:07:21 CEST 2010: Mythtv-backend Upstart; MySQL is now ready
Tue May 25 05:07:21 CEST 2010: Mythtv-backend Upstart; MySQL is now ready
Tue May 25 05:07:21 CEST 2010: Mythtv-backend Upstart; MySQL is now ready
Tue May 25 05:07:21 CEST 2010: Mythtv-backend Upstart; MySQL is now ready
Tue May 25 05:07:21 CEST 2010: Mythtv-backend Upstart; MySQL is now ready
Tue May 25 05:07:21 CEST 2010: Mythtv-backend Upstart; MySQL is now ready
Tue May 25 05:07:21 CEST 2010: Mythtv-backend Upstart; MySQL is now ready
Tue May 25 05:07:21 CEST 2010: Mythtv-backend Upstart; tuners found in database: /dev/dvb/adapter0/frontend0
Tue May 25 05:07:21 CEST 2010: Mythtv-backend Upstart; tuner device /dev/dvb/adapter0/frontend0 is now ready
Tue May 25 05:07:21 CEST 2010: Mythtv-backend Upstart: tuner devices are now registered. Starting mythbackend
I only have one tuner Hauppauge HVR 1110
If i put your original script, tuner don't load the firmware.
When I used karmic, your initial script worked well.

Regards from Catalonia (Spain)

---

### Post by Sangoma-1701D on 2010-05-25
ffp,

From a quick read of the upstart man pages it appears to suggest that you might need exec to run the mythbackend as was in the 9.10 upstart script. Try changing the last line before **end script** from:

/usr/bin/mythbackend $ARGS

to:

exec /usr/bin/mythbackend $ARGS

See if that makes any difference.

Barny.

---

### Post by ffp on 2010-05-26
Thanks, but don't work
> **Sangoma-1701D said:**
> ffp,

From a quick read of the upstart man pages it appears to suggest that you might need exec to run the mythbackend as was in the 9.10 upstart script. Try changing the last line before **end script** from:

/usr/bin/mythbackend $ARGS

to:

exec /usr/bin/mythbackend $ARGS

See if that makes any difference.

Barny.

---

### Post by Sangoma-1701D on 2010-05-26
ffp,

I'm sorry but I don't know the answer then. :(
It would be worth checking your mythbackend logs if you have not; it could be that the mythbackend is starting up from the upstart script but not loading for some other reason?

Barny.

---

### Post by jgil on 2010-05-29
> **ffp said:**
> Hi,

I adapted this script for Lucid, as:

```
# MythTV Backend service

description     "MythTV Backend"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE=lo)
stop on starting shutdown

#expect fork
respawn

script
#added to ensure that the DVB-T cards are init before myth
	LOG_FILE='/home/htpc/mythbackend-init.log' #log file
	#wait for mysql to start
	while [ ! "$(pidof mysqld)" ]; do
		echo "`date`: Mythtv-backend Upstart; MySQL is not ready. Waiting 1 second..." >> $LOG_FILE
		sleep 1s
	done
	echo "`date`: Mythtv-backend Upstart; MySQL is now ready" >> $LOG_FILE
	#get mysql username & password
	MYSQLLIST="~/.mythtv/mysql.txt /etc/mythtv/mysql.txt"
	for m in $MYSQLLIST
	do
		[ -f $m ] && . $m && break
	done
	#get the tuner card paths
	TUNERS=`mysql --user=${DBUserName} --password=${DBPassword} --database=${DBName} --skip-column-names --execute='SELECT DISTINCT videodevice FROM capturecard;'`
	echo "`date`: Mythtv-backend Upstart; tuners found in database: ${TUNERS}" >> $LOG_FILE
	for t in $TUNERS
	do
		while [ -c !$t ]; do
			echo "`date`: Mythtv-backend Upstart; tuner device ${t} is not ready. Waiting 1 second..." >> $LOG_FILE
			sleep 1s
		done
		echo "`date`: Mythtv-backend Upstart; tuner device ${t} is now ready" >> $LOG_FILE
	done
	echo  "`date`: Mythtv-backend Upstart: tuner devices are now registered. Starting mythbackend" >> $LOG_FILE
#end of additions - original code below

        [COLOR="Red"]USER=mythtv
        ARGS="--logfile /var/log/mythtv/mythbackend.log --user $USER"
        test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
        sleep 10
        /usr/bin/mythbackend $ARGS[/COLOR]
end script
```

And mythbackend don't start !

A simply 

```
sudo start mythtv-backend
```Solves the problem

Can you help me?

Thanks
hi
I am also using Lucid and have tried this script and it inizalised the hvr 2200 tuner card,but the backend fails to start.
any help in where to put the appropriate command would be apreciated.

---

### Post by ffp on 2010-05-30
Well,

If firmware are loaded, and the cards initialized (see dmesg), you can try this script:
```
#!/bin/bash

sleep 20
/usr/bin/mythbackend &
sleep 5
mythfrontend --service ;
exit
```Launch manually, if it works you can put it in the startup applications.

---

### Post by benlyboy on 2010-05-30
Hi all

I have had this problem for a while now and living in the midwest where power outs are not uncommon in the winter months, it can be a pain if you are way. I never know if Things I set to record will in fact be recorded.

I was wandering Who decides what things are fixed in updates.


Shouldn't this problem be exactly the type of thing that should be fixed in a daily update?

---

### Post by jgil on 2010-05-31
> **ffp said:**
> Well,

If firmware are loaded, and the cards initialized (see dmesg), you can try this script:
```
#!/bin/bash

sleep 20
/usr/bin/mythbackend &
sleep 5
mythfrontend --service ;
exit
```Launch manually, if it works you can put it in the startup applications.
hi
thank's the script worked manually,now I will add it to a startup script.

John

---

### Post by jgil on 2010-06-06
Hi
I need help
I have got it working through the startup app,but it must start the back-end before I log in.
can you tell me where I can put the command

---

### Post by ffp on 2010-06-07
Hello
> **jgil said:**
> Hi
I need help
I have got it working through the startup app,but it must start the back-end before I log in.
can you tell me where I can put the command
I've a automatic login & no problem.
In my script, backend should start after login, it is launched by your user. 
Can you use automatic login?

---

### Post by jgil on 2010-06-08
Hi
I have successfully started the back-end after log in,but I need to run the back end only


John

---

### Post by ffp on 2010-06-08
> 
I have successfully started the back-end after log in,but I need to run the back end only Type in a terminal
> /usr/bin/mythbackendAnd only start mythbackend.

---

### Post by wayover13 on 2010-07-04
I've run into the problem of capture cards disappearing as well--this after an upgrade of my system to Lucid. The problem actually only manifests when I introduce the nobootwait option into certain entries in my /etc/fstab (back-up drives that aren't present most of the time, but that, because the system expects them to be present, now cause the machine to pause during boot, awaiting input from me). You can read a more detailed description of my particular issue in the thread at [http://ubuntuforums.org/showthread.php?p=9541325&posted=1#post9541325](http://ubuntuforums.org/showthread.php?p=9541325&posted=1#post9541325) .

I've tried the fixes proposed in this thread but they do not work for me: the backend simply refuses to start once I edit /etc/init/mythbackend.conf as proposed in this thread. Only once I replace the edited version of /etc/init/mythbackend.conf with the original, unedited file, can I finally restart the backend.

I confess to not being especially knowledgeable about what the added bits in /etc/init/mythbackend.conf are supposed to do, so I may have done something wrong in implementing this fix. I did copy and paste the red text (I tried both the original and the later,modified versions) and edit as suggested. But as I said, it simply is not working for me: the edited file causes mythbackend to simply not start.

Can anyone propose a resolution for this problem specifically aimed at Lucid and, preferably, one geared toward someone who doesn't understand very well the programming behind the suggested changes?

Thanks,
James

---

### Post by wayover13 on 2010-07-04
I've managed, with some help, to resolve my problem (whereby, since the new Lucid system is booting so quickly, only one of my two capture cards gets initialized before mythbackend starts). The solution is a simpler one than the one posted about in this thread, and involves introducing a "sleep XX" argument into /etc/init/mythbackend.conf (posted about initially in the thread at [http://ubuntuforums.org/showthread.php?t=1521029](http://ubuntuforums.org/showthread.php?t=1521029) ). This is a better solution, for my purposes, than the more complex one being offered within the current thread. Anyway, see [http://ubuntuforums.org/showthread.php?t=1522827](http://ubuntuforums.org/showthread.php?t=1522827) for further details about the problems I had and the solution I implemented on my system.

James

---

### Post by Chunder on 2010-08-28
Not sure whether it will help anyone else, but I had to make a small amendment to ffp's Lucid version above; I thought it was all working, but realised that mythtv-backend wasn't starting up - but the only things in the mythbackend-init.log were statements that mysql was up and running... nothing to do with tuners being unavailable, etc.

I tracked it down by trying the mysql statement (in the 'TUNERS=' line) at a command line directly (substituting the variables ${user} etc. for the real values) and found that my mythtv user wasn't allowed to connect to localhost, but instead could only connect to the actual backend IP address (even though the two are actually the same thing).

The script needed to pass the '--host=...' parameter, and the variable for this that's defined in the mysql.txt file is DBHostName, therefore the change required is as follows
From this:
```
TUNERS=`mysql --user=${DBUserName} --password=${DBPassword} --database=${DBName} --skip-column-names --execute='SELECT DISTINCT videodevice FROM capturecard;'`
```

To this:
```
TUNERS=`mysql --user=${DBUserName} --password=${DBPassword} [COLOR="Red"]--host=${DBHostName}[/COLOR] --database=${DBName} --skip-column-names --execute='SELECT DISTINCT videodevice FROM capturecard;'`
```

Hope that this helps; big thanks to everyone who's helped out with this thread to get to where we are - I've been tearing my hair out trying to work out why Tuner 1 works but Tuner 2 fails, considering they're both on the same Nova-T card! :)

---

