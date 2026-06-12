---
title: "MythWelcome - Community docs for ACPI wake not working with 7.04"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by mattp52 on 2007-06-03
Hi all,

I followed the Ubuntu Howto docs [here]("https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake") to enable auto wake shutoff on my machine but no matter what I did, MythWelcome does not appear to call the script defined in the nvram wake field of mythwelcome setup.

I can confirm that ACPI wake does work as I have run the wake script manually and turned the machine off and it wakes fine. The path to the script has been added to the sudoers file with visudo.

As a side-note, when the machine is started manually with MythWelcome set to launch on log-in, if i exit the front end MythWelcome is consistently locked up and I am unable to select either the menu or relaunch the frontend.

The tutorial mentions an alt to the file '/usr/share/mythtv/startmythtv.sh' however this doesn't exist in my install. Instead I have added the following lines to .gnomerc in the home directory of the mythtv user...

```

sleep 10
exec mythwelcome

```

The closest I have come to a working workaround is to use the following settings and wakeup script (which ignores the $time parameter passed from the backend completely and retrieves it from the schedule table in the database). Because of this it doesn't allow for the pre-roll setting in the wakeup but otherwise does at least boot and shutdown the machine.

I'd like to use a more elegant solution like that in the tutorial though... can anyone confirm mythwelcome can be made to work correctly with 7.02 and, ideally, update the tute to show how it should be configured..?

Settings below:

**MYTH-SETUP:	**
Wakeup time format	yyyy-MM-ddThh:mm:ss
Set wakeuptime command	sudo /usr/bin/MythWakeSet
Server Halt Command	sudo shutdown -h -P now
Pre Shutdown check-command	mythshutdown --check
	
**MYTHWELCOME --SETUP	**
nvram-wakeup Command	mythshutdown --setwakeup $time
nvram-wakeup Restart	
Command to reboot	


**Wake up script (/usr/bin/MythWakeSet)**

```
#!/bin/bash


/usr/bin/mythbackend --printsched > /home/mythtv/schedtxt.txt


THEDAY=`head -12 /home/mythtv/schedtxt.txt | tail -1 | cut -c 47-49 | tr [:space:] - | cut -c 1-3`
THETIME=`head -12 /home/mythtv/schedtxt.txt | tail -1 | cut -c 50-55`


THEDATE=$(date +%Y-%m)
ALLDATE=$THEDATE${THEDAY}${THETIME}

echo `head -12 /home/mythtv/schedtxt.txt`

stamp_file=/home/mythtv/timestamp

# Use this if not using mythwelcome
#echo $1\ $2 > $stamp_file

# Or this if using mythwelcome...
#echo $1 | sed "s/T/ /" >$stamp_file


echo $ALLDATE > $stamp_file

# Read date in local time format and add the time-zone info to the stamp_file
datum=$(/bin/date -f $stamp_file +%F\ %T\ %z)
echo $datum > $stamp_file

# reinterpret this in utc and write to alarm
utcdatum=$(/bin/date -u -f $stamp_file +%F\ %T)
echo $utcdatum > $stamp_file

rm -f $stamp_file
#echo $utcdatum >/proc/acpi/alarm

#Debug version of previous line...
echo $utcdatum | tee -a /tmp/alarmtimes > /proc/acpi/alarm 
```

 
Really hope someone can help here... the setup docs have otherwise been invaluable.

Thanks!

---

### Post by EmuMannen on 2007-06-26
I have the same problem, bump...

Ps. Looks like a typo in the the docs, under  section "MythWelcome", subsection "Configure MythBackend":
> 
Navigate to Shutdown/Wakeup Options and change the following values: Wakeup time format:: yyy-MM-ddThh:mm:ss


Shouldn't it be "**yyyy**-MM-ddThh:mm:ss" instead of "**yyy**-MM-ddThh:mm:ss"?

I have tried both but none work. I have followed the docs and everything works except the MythWelcome part...

---

### Post by striscio on 2007-06-28
I'm also experiencing problems with mithwelcome (mythfrontend alone honors shutdown and wakeup).
I read your message and I found that maybe you have some errors. From the HOWTO:

**Configure MythWelcome**
Exit the frontend, you will automaticaly get the mythwelcome screen. Press F11 to enter the setup and enter the following values: nvram-wakeup Command: sudo /usr/bin/MythWakeSet
nvram-wakeup Restart Command leave blank!
Command to reboot: sudo shutdown -h -r now leave the rest unchanged.
Configure MythBackend

Navigate to Shutdown/Wakeup Options and change the following values: Wakeup time format:: yyy-MM-ddThh:mm:ss
Set wakeuptime Command: mythshutdown --setwakeup $time
Server halt Command: sudo shutdown -h -P now
Pre Shutdown check-command: mythshutdown --check 


It's seems that your settings are different
Also I found these on mythtv users ml:
complete thread [here]("http://www.gossamer-threads.com/lists/mythtv/users/209085?search_string=mythwelcome%20acpi;#209085")
==========================================================
The time limit within which mythwelcome will not shutdown the system if
a recording is pending is also hard-coded to 15 minutes. So you need to
ensure this is set to 15 minutes in mythtv-setup or things won't work
correctly either. 
==========================================================
Which is something I never heard about. Maybe that's why things aren't working?

---

### Post by El_Matthews on 2007-07-16
Did somebody made this work? If yes could you post how you did and maybe your settings as it seems that we all have the same problems with mythwelcome.

Thanks

---

### Post by roofpig on 2007-08-08
> **El_Matthews said:**
> Did somebody made this work? If yes could you post how you did and maybe your settings as it seems that we all have the same problems with mythwelcome.

Thanks

I found one major issue with the community docs.  Try setting the server halt command (set in mythtv-setup) to

    ```
sudo mythshutdown --shutdown
```

With this change, the shutdown and wakeup cycle works for me, although not 100% reliably.

Sometimes it doesn't want to shut down.  Usually the symptom is that it counts down to 10 seconds but doesn't seem to proceed.  That may be because of the problem someone mentioned earlier (mythwelcome has its own idea that it shouldn't shut down if a recording will happen in less than 15 minutes time) so I've just changed the setting in mythtv-setup to 15 minutes.  If that doesn't solve the problem I guess I'll have to find a way to trace the decisions that mythshutdown and mythwelcome go through. :(

---

### Post by El_Matthews on 2007-08-08
Hello roofpig,


Thanks for the update, keep us informed of the results from you tests.

Greetings

Matthieu

---

### Post by roofpig on 2007-08-10
Well, at this point I suspect that my remaining problem is caused by a bug in idle detectioin  The backend log shows:

```

mythtv@myth:/var/log/mythtv$ tail mythbackend.log
2007-08-10 05:14:43.671 90 secs left to system shutdown!
2007-08-10 05:14:53.863 80 secs left to system shutdown!
2007-08-10 05:15:04.047 70 secs left to system shutdown!
2007-08-10 05:15:13.210 60 secs left to system shutdown!
2007-08-10 05:15:23.398 50 secs left to system shutdown!
2007-08-10 05:15:33.578 40 secs left to system shutdown!
2007-08-10 05:15:43.762 30 secs left to system shutdown!
2007-08-10 05:15:53.953 20 secs left to system shutdown!
2007-08-10 05:16:03.129 10 secs left to system shutdown!
2007-08-10 05:17:33.986 JobQueue: Commercial Flagging Finished, 3 break(s) found.

```

which on the face of it makes no sense: the idle countdown should not have begun if a commercial flagging job was running.  Alternatively (I have not looked at the code yet) the system is supposed to count down and then discover it can't do shutdown, but somehow isn't recovering from that state.   Either way, I don't think the problem is related to configuration.   So:

For the purposes of this thread, I would have to say that ACPI does work, as long as you use "sudo mythshutdown --shutdown" as I mentioned above.

I recalled one more gotcha.  You should test to make sure that "sudo" works without a password.  The instructions for that step weren't working properly for me.  Unfortunately, I can't really recommend my temporary fix (I allow mythtv to run ANY program using sudo without a password).  But it might be worth trying, to see if sudo is part of your problem.

---

### Post by fuchur on 2007-08-11
> **El_Matthews said:**
> Did somebody made this work? If yes could you post how you did and maybe your settings as it seems that we all have the same problems with mythwelcome.

Thanks

I think I had similar problems. I followed the howto in [http://www.mythtv.org/wiki/index.php/ACPI_Wakeup](http://www.mythtv.org/wiki/index.php/ACPI_Wakeup) which is similar to the ubuntu community howto.

If I am correct - which is not necessarily the case as I am not an expert - there is potential source  of errors in both howtos: 

It seems to me that many mythshutdown  versions by default use seconds as output format, not YYYY:MM:DD and so on. So even though the input is in the correct format (as specified in mythtv-setup) the output from myth-setup is not.

That is, it is wrong if you use a script as on the ubuntu-wiki. 
Howver, the script from German mythtv wiki seems to work: 

>  


#!/usr/bin/perl
#
# This script is invoked by mythshutdown to set the wakeup time.
# mythshutdown thinks it's calling nvram-wakeup, and it passes
# "--settime" and a single integer on the command line, which is the
# startup UTC time in seconds since the epoch. We convert it to the form
# understood by the system wakeup script.
#
($sec, $min, $hour, $mday, $mon, $year, $wday, $yday, $isdst) =
localtime ($ARGV[1]);
$year += 1900;
$mon += 1;
$wakeup_time = sprintf "%4.4u-%2.2u-%2.2u %2.2u:%2.2u:%2.2u", $year,
$mon, $mday, $hour, $min, $sec;
`echo "$wakeup_time" >/proc/acpi/alarm`; 

**NOTE: replace localtime with gmtime for UTC system clocks**
soure: [http://www.mythwiki.de/index.php?title=HOWTO_Mythwelcome](http://www.mythwiki.de/index.php?title=HOWTO_Mythwelcome)

This script should replace MythWakeSet from the ubuntu wiki - but as I did not follow that wiki i'm not sure whether additional modifications are needed.


Let me know if anybody else is succesful when replacing the scripts -it works for me, but i am using mythbuntu which presumably uses a newer mythtv. If so, we should probably suggest to mention this to the two english wikis

---

### Post by tsu3000 on 2007-10-09
Hi

Has this issue been resolved? I am keen to start going through the Community wiki tutorial but if it doesn't work properly then I may have to look elsewhere. So is it a case of replacing the MythWakeSet script with the German perl script?

Thanks in advance.

JJ

---

### Post by fuchur on 2007-10-09
> **tsu3000 said:**
> Hi

Has this issue been resolved? I am keen to start going through the Community wiki tutorial but if it doesn't work properly then I may have to look elsewhere. So is it a case of replacing the MythWakeSet script with the German perl script?



I can just tell you that for me, the how-to mentioned in my previous post, which is very similar to the ubuntu how to, did not work initially, but if worked after using the script from the german how-to. 

However, no-one has replied to my earlier post, so I almost assume this did not help too many other people. 

I suggest you just try it with both scripts, and let us know if any of them worked. Try to check intermideate steps (I.e. does it wake up if you manually specify a time, ....) 
For the geman script, don't forget to check wheter u should use localtime or replace it with gmtime ...

On my computer now, acpi wakeup works without any trouble (but it was not easy to set it up)

---

### Post by tsu3000 on 2007-10-10
fuchur

Thanks for your reply. Would you care to share your findings and settings with us?

Anyway I went through the Community tutorial at: [https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake]("https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake")

This is what I found:

I'd like to point out that I am using UTC time for my system.

Everything works as expected up to the point where I configure mythwelcome section. Up to this point the system will wake up at the correct time to do a recording and shutdown as long as the frontend is NOT running, ie scheduling works to a degree. However if I configure the system to start the frontend on bootup then it will wakeup at the correct time and do its recording but the system will never shutdown once its finished because the frontend is still running.

So now the task is to configure mythwelcome. Let the fun begin...

I continued with the tutorial and made the changes to MythWakeSet so that the following code was changed:

```
# store the wake time passed from mythbackend
##echo $1\ $2 > $temp_stamp
tmp=`echo $2 | awk -F: '{print strftime("%Y-%m-%dT%T", $1)}'`
tmp1=`echo $tmp | awk 'BEGIN { FS = "T" } { print $1 }'`
tmp2=`echo $tmp | awk 'BEGIN { FS = "T" } { print $2 }'`
echo $tmp1\ $tmp2 > $temp_stamp
```

I then made the changes to the mythwelcome:

**nvram-wakeup Command:** sudo /usr/bin/MythWakeSet
**nvram-wakeup Restart Command:** left blank
**command to reboot:** sudo shutdown -h -r now

The rest was unchanged.

Then I made the following changes to mythtv-setup under the **Shutdown/Wakeup Options**:

**Wakeup time format:** yyyy-MM-ddThh:mm:ss
**Set wakeuptime Command:** mythshutdown --setwakeup $time
**Server halt Command: **sudo shutdown -h -P now
**Pre Shutdown check-command:** left this blank for my system

With all this in place UTC acpi wakeup did not work! So I am a little lost as what to do next.

I decided to give the "German perl script" a try and replaced the original MythWakeSet script with this:

```
#!/usr/bin/perl
#
# This script is invoked by mythshutdown to set the wakeup time.
# mythshutdown thinks it's calling nvram-wakeup, and it passes
# "--settime" and a single integer on the command line, which is the
# startup UTC time in seconds since the epoch. We convert it to the form
# understood by the system wakeup script.
#
($sec, $min, $hour, $mday, $mon, $year, $wday, $yday, $isdst) =
gmtime ($ARGV[1]);
$year += 1900;
$mon += 1;
$wakeup_time = sprintf "%4.4u-%2.2u-%2.2u %2.2u:%2.2u:%2.2u", $year,
$mon, $mday, $hour, $min, $sec;
`echo "$wakeup_time" >/proc/acpi/alarm`; 
```

But alas that did not wake up the system either...

Any further ideas would be appreciated.

Thanks.

JJ

---

### Post by fuchur on 2007-10-10
Your settings  looked similar to mine, i will look at it more carefully when i have more time. 

Do I understand correctly: Your system, using welcome, shuts down but does not wake up?

The only other thing I could offer currently is that the german howto says that you should somehow run a script like this on startup, to set permission of acpi alarm. It looks a bit hacky, and it is s not in the ubuntu howto, or did I overlook it?

 ```

chown mythtv:root /proc/acpi/alarm
chmod 644 /proc/acpi/alarm
```

In any case, you could of course just try to issue these commands (as root) , than the wakeup should work at least once...

Btw, I now think that the German script does the same as the modified mythwakeset, but I overlooked this modification when I tried to install it mysef

---

### Post by tsu3000 on 2007-10-10
Yes that is correct: my system does shutdown correctly when Mythwelcome is running and the system is idle (and the frontend is NOT running). 

From looking at the translation of the German wiki, I could not work out how the perl script should be run in conjunction with Mythtv. Is it just a case of running it as a separate script? If so how does Myth know what time was set? Also do you know what the section (with the network interfaces) at the beginning is all about?

I am going to try some more tests and see what I find.

Thanks.

JJ

---

### Post by fuchur on 2007-10-10
> **tsu3000 said:**
> Yes that is correct: my system does shutdown correctly when Mythwelcome is running and the system is idle (and the frontend is NOT running). 

From looking at the translation of the German wiki, I could not work out how the perl script should be run in conjunction with Mythtv. Is it just a case of running it as a separate script? If so how does Myth know what time was set? Also do you know what the section (with the network interfaces) at the beginning is all about?

I am going to try some more tests and see what I find.

Thanks.

JJ

i&#314;l look at that later, but the network thing is the stuff from my previous post: they want to set the permissions  of acpi/alarm, and they say ubuntu does not remember them so you have to do it at boot.  and to do it at startup they add it to the network configuration. As that seemed weird to me as well, I suggested you try first if changing permissions helps at all, even if the computer forgets them, it should work once...

---

### Post by fuchur on 2007-10-10
What helped me a lot to troubleshoot is to run 
cat /proc/acpi/alarm
in the few seconds after mythwelcome initiates shutdown (beep) and actual shutdown.
This enables you to find out if no time is set at all, or the wrong time is set.

Anyways. 

Here a quick translation of the german howto, but apart from the 2 differences mentioned above there is really nothing new. It is also very brief.

1.) Test if ACPI works(link 1) and make a script that runs at startup:

crate  a script in   in  /etc/network/if-up.d/ , (and make it executable) with content
```

#!/bin/sh -e
if [ "$IFACE" = "lo" ]; then
        exit 0
fi
chown mythtv:root /proc/acpi/alarm
chmod 644 /proc/acpi/alarm
```

2.) follow link 2

3.)  create the wake-up script (see content above)
4.) configure mythwelcome (enter the path to the wake-up script in " nvram-wakeup command"), for shutdown:" sudo /sbin/shutdown now -h" after allowing the mythtv user to shutdown without password (use sudo visudo)

---

### Post by tsu3000 on 2007-10-11
OK thanks for the info. I will give this a try once I have a spare moment, and I will post the results of my tests...

Thanks.

JJ

---

### Post by tsu3000 on 2007-10-12
OK here are my results of my tests.

All seems to be working now - just!! But I still need to do some more tweaks to really make sure.

These are my settings:

**Mythwelcome setup:**

**nvram-wakeup Command:** sudo /usr/bin/MythWakeSet
**nvram-wakeup Restart Command:** LEAVE BLANK
**Command to reboot:** sudo shutdown -h -r now
**Command to shutdown:** sudo /sbin/poweroff

Now for mythtv-setup:

**Shutdown/Wakeup Options:**

**Wakeup time format:** yyyy-MM-ddThh:mm
**Set wakeuptime Command:** mythshutdown --setwakeup $time
**Server halt Command:** mythshutdown --shutdown
**mythalarm-command:** BLANK for the time being

The above settings for mythtv-setup are essentially the same as the ones from the mythwelcome wiki at: [http://www.mythtv.org/wiki/index.php/Mythwelcome]("http://www.mythtv.org/wiki/index.php/Mythwelcome")

Next ensure that /sbin/poweroff is put into sudoers file, (you might as well put /sbin/reboot as well):

sudo visudo:

```

%mythtv ALL = NOPASSWD: /sbin/shutdown, /usr/bin/MythWakeSet, /proc/acpi/alarm, /usr/bin/MythShutdownCheck, /etc/init.d/mythtv-backend, /usr/bin/MythShutdown, /sbin/poweroff, /sbin/reboot
```

This is the MythWakeSet script I used (from German mythwelcome wiki):

```

#!/usr/bin/perl
#
# This script is invoked by mythshutdown to set the wakeup time.
# mythshutdown thinks it's calling nvram-wakeup, and it passes
# "--settime" and a single integer on the command line, which is the
# startup UTC time in seconds since the epoch. We convert it to the form
# understood by the system wakeup script.
#
($sec, $min, $hour, $mday, $mon, $year, $wday, $yday, $isdst) =
gmtime ($ARGV[1]);
$year += 1900;
$mon += 1;
$wakeup_time = sprintf "%4.4u-%2.2u-%2.2u %2.2u:%2.2u:%2.2u", $year,
$mon, $mday, $hour, $min, $sec;
`echo "$wakeup_time" >/proc/acpi/alarm`;

```

Note the use of *gmtime *for UTC based system clock.

Put MythWakeSet in /usr/bin with the correct permissions and ownership.

Also according to the German wiki you need to set up a script to change permissions for /proc/acpi/alarm:

Create a file in /etc/network/if-up.d/ and call it whatever, say mythalarm:

```

#!/bin/sh -e
if [ "$IFACE" = "lo" ]; then
        exit 0
fi
chown mythtv:root /proc/acpi/alarm
chmod 644 /proc/acpi/alarm

```

Ensure it has the correct permissions:

```
chmod 755 /etc/network/if-up.d/mythalarm
```

I may, as a test, remove this because I cannot work out how this makes the system  wakeup as it does.

All this seems to make the system wakeup for a recording and shutdown when the backend is 100% idle - as it should. But I found that on some occasions mythwelcome will report that it is recording something when its idle and vice versa !!?? Othertimes mythwelcome will say it will do a countdown to shutdown but then start the countdown again (this is without the Pre-Shutdown check). Perhaps the backend is not 100% idle when it does this eg when it is doing some database maintenance?

Thanks goes to fuchur for helping me resolve some of these problems.

JJ

---

### Post by El_Matthews on 2007-10-12
Hello,

Now that there's activity again in this thread I restarted working on this subject. This time I got further ;)

ACPI start-up time is written correctly and my pc starts on the correct time. But as soon as the pc starts it loads mythwelcome. I have set this in the startup of my mythuser. 

My problem is that mythwelcome starts and loads directly the myth-fronted even after after an acpi start, this means that after finishing the recording the pc doesn't shut down. If i manually exit the frontend, the pc will sut down correctly after the recording.

So, how does mythwelcome get the difference between acpi start or user wake start?

Any ideas?

Greetings
Matthieu

---

### Post by tsu3000 on 2007-10-12
Hi

I'll try and answer your questions first then tell you what I know from the tests I have done.

> But as soon as the pc starts it loads mythwelcome. I have set this in the startup of my mythuser.

This is normal if you have made mythwelcome start on system bootup. In fact its the preferred method. :)

> My problem is that mythwelcome starts and loads directly the myth-fronted even after after an acpi start, this means that after finishing the recording the pc doesn't shut down. If i manually exit the frontend, the pc will sut down correctly after the recording.

This should not happen for a fully automated scheduled wakeup. However this WILL happen if you start the system manually. How is the system started? Is the system waking up to do a recording or are you manually powering up the system?

This is what I know...

Mythwelcome works in one of two ways. The first way is when the system wakes up and does a scheduled recording then mythwelcome shuts down the system once its finished. When mythwelcome starts in this way it should NOT start mythfrontend. As you have seen if the frontend is also running the system will never shutdown.

Now if you manually switched on your system to use Mythtv to watch TV or whatever, then mythwelcome will automatically start mythfrontend as well. Once you have finished with the frontend you exit and mythwelcome takes over to do a shutdown (or you can manually poweroff the system with a configured button on your remote).

I hope all this makes sense.

Thanks.

JJ

---

### Post by El_Matthews on 2007-10-12
thanks for the fast reply.

Mythwelcome starts automatically from gnome session so at least this is correct ;)

Even when the pc starts from an acpi wake-up call it will log-on with user mythtv (auto-log on after 30sec), then starts the mythwelcome and mythwelcome always launches the front-end. 

This is where it goes wrong, it shouldn't launch the front-end in this case. 

How does mythwelcome knowns that it woke-up from acpi or from the user?

Greetings

Matthieu

---

### Post by tsu3000 on 2007-10-12
By default mythwelcome should not launch frontend if mythwelcome is started during an auto scheduled wakeup.

How are you starting mythwelcome during system bootup? 

For example on my system I have this:

cat /home/mythtv/.gnomerc

```
sleep 10 && mythwelcome > /tmp/mythwelcome.log 2>&1 &
```

And in mythwelcome setup I have this:

**Command to run to start frontend:** /usr/bin/mythfrontend

> How does mythwelcome knowns that it woke-up from acpi or from the user?

Good question. Unfortunately I do not know enough about Mythtv to answer that one. Perhaps this mythwelcome wiki may provide some answers: [http://www.mythtv.org/wiki/index.php/Mythwelcome]("http://www.mythtv.org/wiki/index.php/Mythwelcome")

JJ

---

### Post by El_Matthews on 2007-10-13
maybe starting gnome with auto-logon is seen as a wake up by user. I will try to find a guide on how  mythtv shoud be started. 

you have set the command in cat /home/mythtv/.gnomerc? I don't have this file. When is it run?

Greetings

Matthieu

---

### Post by El_Matthews on 2007-10-13
ok found the info on .gnomerc in the following guide: [http://www.mythtv.org/wiki/index.php/Frontend_Auto_Login](http://www.mythtv.org/wiki/index.php/Frontend_Auto_Login). I will try this and let you know the result.

greetings

Matthieu

---

### Post by El_Matthews on 2007-10-13
I found this in the logs of the backend;
2007-10-13 11:21:22.671 scheduler: Scheduled items: Scheduled 2 items in 0.6 = 0.38 match + 0.26 place
2007-10-13 11:21:22.706 Recording starts soon, AUTO-Startup assumed

so it detected that it was an auto-startup but still the front-end was started. strange

---

### Post by tsu3000 on 2007-10-15
> **El_Matthews said:**
> 
you have set the command in cat /home/mythtv/.gnomerc? I don't have this file. When is it run?



You can create this file (/home/mythtv/.gnomerc) if you do not have it then put the following in it:

sleep 10 && mythwelcome > /tmp/mythwelcome.log 2>&1 &

Save the file and reboot the system and observe what happens. If all is working you should have mythwelcome start automatically and the frontend start as well (this is normal for a manual poweron).

The .gnomerc file runs at system startup and can run anything you like.

Then as a second test schedule a recording and when the system wakes see if mythwelcome is running (it should if all the settings are correct).

JJ

---

### Post by El_Matthews on 2007-10-23
does somebody knows how to troubleshoot mythwelcome?

when mythwelcome is started with following command from acpi wake-up
```
sleep 10 && mythwelcome > /tmp/mythwelcome.log 2>&1 &
```

I don't get the mythwelcome screen but only the mythfrontend.

---

### Post by jb5 on 2007-11-03
Bump

OK - I like most people can get my mythTV to wake using the [ACPI](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake) instructions, right up to the point that mythwelcome is introduced.

Mythwelcome of course is the stumbling block.

I have created */etc/network/if-up.d/mythalarm*, 
however after playing about I removed the conditional statement of the original (it didn't seem to want to change the permissions for me other wise) and then went on to give anyone and everyone permissions to write to */proc/acpi/alarm* just in case!

```
#!/bin/sh -e

chown mythtv:root /proc/acpi/alarm
chmod 666 /proc/acpi/alarm
```

so 
```
jb@eric:~$ ls -l /proc/acpi/alarm
-rw-rw-rw- 1 mythtv root 0 2007-11-03 09:35 /proc/acpi/alarm

```

However, after many frustrating days I tried a different tack :-

```

jb@eric:~$ cat /proc/acpi/alarm
2007-11-00 13:11:40

jb@eric:~$ mythshutdown -v important --setwakeup 2007-11-03T23:23:23.000
2007-11-03 10:32:57.632 Mythshutdown: wakeup time given is: 2007-11-03T23:23:23.000
jb@eric:~$ sudo MythWakeSet
jb@eric:~$ cat /proc/acpi/alarm
2007-11-01 00:00:00
jb@eric:~$ 

```

So at least something has been written to alarm!

EDIT

OK - So tried each of the following MythWakeSet Scripts

The modified ACPI bash script
```

#!/bin/bash
#
# MythWakeSet
#
# set mythtv wake-up time with UTC-adjusted time
#

# temp file for working with time
temp_stamp=/home/mythtv/timestamp

# store the wake time passed from mythbackend
##echo $1\ $2 > $temp_stamp
tmp=`echo $2 | awk -F: '{print strftime("%Y-%m-%dT%T", $1)}'`
tmp1=`echo $tmp | awk 'BEGIN { FS = "T" } { print $1 }'`
tmp2=`echo $tmp | awk 'BEGIN { FS = "T" } { print $2 }'`
echo $tmp1\ $tmp2 > $temp_stamp

# Read the date in *locale* time format and tag the time-zone info to the wake time
localeadd=$(/bin/date -f $temp_stamp +%F\ %T\ %z)
echo $localeadd > $temp_stamp

# adjust this to UTC and store the final wake time
utcadj=$(/bin/date -u -f $temp_stamp +%F\ %T)

# set the alarm
echo $utcadj > /proc/acpi/alarm


```
Produced 
```

jb@eric:~$ mythshutdown -v important --setwakeup 2007-11-03T22:22:22
2007-11-03 11:31:37.977 Mythshutdown: wakeup time given is: 2007-11-03T22:22:22
jb@eric:~$ sudo MythWakeSet
jb@eric:~$ cat /proc/acpi/alarm
2007-11-01 00:00:00
jb@eric:~$ 

```

The German perl script
```

#!/usr/bin/perl
#
# This script is invoked by mythshutdown to set the wakeup time.
# mythshutdown thinks it's calling nvram-wakeup, and it passes
# "--settime" and a single integer on the command line, which is the
# startup UTC time in seconds since the epoch. We convert it to the form
# understood by the system wakeup script.
#
($sec, $min, $hour, $mday, $mon, $year, $wday, $yday, $isdst) =
gmtime ($ARGV[1]);
$year += 1900;
$mon += 1;
$wakeup_time = sprintf "%4.4u-%2.2u-%2.2u %2.2u:%2.2u:%2.2u", $year,
$mon, $mday, $hour, $min, $sec;
`echo "$wakeup_time" >/proc/acpi/alarm`;

``` 
produced 
```

jb@eric:~$ mythshutdown -v important --setwakeup 2007-11-03T22:22:22
2007-11-03 11:34:32.199 Mythshutdown: wakeup time given is: 2007-11-03T22:22:22
jb@eric:~$ sudo MythWakeSet
jb@eric:~$ cat /proc/acpi/alarm
2007-11-01 00:00:00

```
and from [here](http://www.mythtv.org/wiki/index.php/ACPI_Wakeup)

```

#!/bin/sh
# $1 is the --settime switch that nvram-wakeup normally expects
# $2 is the date/time in seconds since 1970

DATE=`date -d "1970-01-01 $2 sec" "+%F %H:%M:%S" -u`
SECS=`date -d "1970-01-01 $2 sec" "+%s" -u`

# Save the wakeup time
echo "$*"  > /myth.wakeup.args
echo $DATE > /myth.wakeup.time
echo $SECS > /myth.wakeup.secs

if [ -e /sys/class/rtc/rtc0/wakealarm ]; then
        echo 0 > /sys/class/rtc/rtc0/wakealarm
        echo $SECS > /sys/class/rtc/rtc0/wakealarm
fi
if [ -e /proc/acpi/alarm ]; then
        echo $DATE > /proc/acpi/alarm
fi

```
produced 
```

jb@eric:~$ mythshutdown -v important --setwakeup 2007-11-03T22:22:22
2007-11-03 11:35:52.756 Mythshutdown: wakeup time given is: 2007-11-03T22:22:22
jb@eric:~$ sudo MythWakeSet
jb@eric:~$ cat /proc/acpi/alarm
2007-11-01 00:00:01
jb@eric:~$ 

```
```

#!/bin/bash
stamp_file=/home/mythtv/timestamp
#echo $1\ $2 > $stamp_file
# If using mythwelcome you can try the next line instead on the one above.
echo $1 | sed "s/T/ /" >$stamp_file
# Read the date in the locale time format and add the time-zone info to the stamp_file
datum=$(/bin/date -f $stamp_file +%F\ %T\ %z)
echo $datum > $stamp_file
# reinterpret this in utc and write to alarm
utcdatum=$(/bin/date -u -f $stamp_file +%F\ %T)
echo $utcdatum > $stamp_file
rm -f $stamp_file
echo $utcdatum >/proc/acpi/alarm

```
The above actually changed the day to 03, but the time was left at 00:00:00
```
jb@eric:~$ mythshutdown -v important --setwakeup 2007-11-03T22:22:22
2007-11-03 11:37:09.502 Mythshutdown: wakeup time given is: 2007-11-03T22:22:22
jb@eric:~$ sudo MythWakeSet
jb@eric:~$ cat /proc/acpi/alarm
2007-11-03 00:00:00

```

```

#!/bin/bash
stamp_file=/home/mythtv/timestamp

#just log what we get as command line parameters
echo $1 $2 $3> $stamp_file

#i setted mythtv to output the number of seconds since epoch
#so i calculate the number of hours, minutes and seconds from
#now the computer has to wakeup:
sfn=$(($2 - `date +"%s"`))

#and then send it to /proc/acpi/wakeup in the format we saw above
y=`(echo $(($sfn - 3600))|awk '{print strftime("+00-00-00 %H:%M:%S", $1)}')`

echo "$y">/proc/acpi/alarm
echo "$y">>$stamp_file
echo "executed at `date`" >> $stamp_file
exit

```
The above produced :-
```
jb@eric:~$ mythshutdown -v important --setwakeup 2007-11-03T22:22:22
2007-11-03 10:55:58.966 Mythshutdown: wakeup time given is: 2007-11-03T22:22:22
jb@eric:~$ sudo MythWakeSet
jb@eric:~$ cat /proc/acpi/alarm
2007-11-03 22:59:59
jb@eric:~$ 

```

So the last script appears to set the correct date, and at least alter the wakeup time. Running the script again ten minutes later produces 
```

jb@eric:~$ mythshutdown -v important --setwakeup 2007-11-03T22:22:22
2007-11-03 11:04:01.764 Mythshutdown: wakeup time given is: 2007-11-03T22:22:22
jb@eric:~$ sudo MythWakeSet
jb@eric:~$ cat /proc/acpi/alarm
2007-11-03 22:59:59
jb@eric:~$ 

```

so obviously the time part isn't working properly!

Anybody any bright ideas?

```

jb@eric:~$ mythshutdown -v important --setwakeup 2007-11-03T22:22:22
2007-11-03 11:13:36.713 Mythshutdown: wakeup time given is: 2007-11-03T22:22:22
jb@eric:~$ sudo MythWakeSet
jb@eric:~$ cat /proc/acpi/alarm
2007-11-03 22:59:59
jb@eric:~$ 

```

```

jb@eric:/home/mythtv$ cat timestamp

+00-00-00 11:46:13
executed at Sat Nov  3 11:13:47 GMT 2007
jb@eric:/home/mythtv$ 

```

---

### Post by jb5 on 2007-11-09
OK - I've decided to take another look at this.

First :-
Can someone confirm that trying to test the scripts in this way (from the command line) is valid? 
I hope so as it avoids having to wait half an hour just to be disappointed, yet again!

```
jb@eric:~$ mythshutdown -v important,general -w 2007-11-11T10:10:00
2007-11-09 12:05:07.478 Mythshutdown: --setwakeup
2007-11-09 12:05:07.479 Mythshutdown: wakeup time given is: 2007-11-11T10:10:00
jb@eric:~$ sudo MythWakeSet
JB
, , ,
JB END
jb@eric:~$ cat /proc/acpi/alarm
2007-11-01 00:00:01
jb@eric:~$ 

```

Second:-
Is there a way I can test what mythshutdown passes to MythWakeSet using this method, (assuming it is valid)?
I tried adding echo $1, $2, $3 to the start of MythWakeSet but that didn't display anything, leading to my fear that I'm going to have to test each script the hard way!

Any BASH gurus out there willing to offer their expertise?

---

### Post by jb5 on 2007-11-12
I've come across another approach that seems to work, at least for me! [here :KS](http://www.mythtvtalk.com/forum/viewtopic.php?t=5763&start=0)

Basically, the wakeup time format in Myth BackEnd is 
```
yyyy-MM-dd hh:mm:ss
```
Note - the extra T is _NOT_ there, and Set wakeup command in BE is 
```
echo $time | tee -a /var/log/alarmset > /proc/acpi/alarm
```
Server halt command is
```
mythshutdown --shutdown
```
& server pre-shutdownchek  command is
```
mythshutdown --check
```

Now in Mythwelcome the nvram-wakeup command is set to
```
mythshutdown --setwakeup $time
```
command to reboot
```
/sbin/poweroff
```
command to shutdown
```
sudo shutown -h -P now
```

The rest of the settings for mythwelcome and myth BE are the same as the post linked to above.

Note mythwelcome doesn't appear to be able to differentiate whether it was started manually or via the alarm, so:-
Whilst on the mythwelcome screen press the i key (on-keyboard :)) to enter the "info" screen and disable the "automatically start the frontend....."
Now, I have to manually start the frontend when I power-on the machine, but at least it will wake up and shut-down after recording. It would be nice to get this feature working but I guess that is for another day, & another thread!

Also my sudoers file ```
sudo visudo
``` contains the line

```
%mythtv ALL = NOPASSWD: /sbin/shutdown, /usr/bin/MythWakeSet, /proc/acpi/alarm, /usr/bin/MythShutdownCheck, /etc/init.d/mythtv-backend, /usr/bin/MythShutdown, /usr/bin/mythshutdown, /sbin/poweroff
```

Some of those entries are now obsolete but I don't suppose leaving them in will do any harm!

Hope this helps someone else.

So, onto the next issue! ;)

---

### Post by El_Matthews on 2007-11-12
you can follow following thread for the mythwelcome issue;
[http://www.gossamer-threads.com/lists/mythtv/users/299575](http://www.gossamer-threads.com/lists/mythtv/users/299575).

I let you know as soon as I made it work.

---

### Post by jb5 on 2007-11-13
Thanks. I'll keep checking in to see if it's been resolved.

---

### Post by El_Matthews on 2007-11-16
A small update on what I found out on the mythtv mailinglist:

Mythwelcome detects that it was an auto-startup when;
1. recording starts within 15 minutes
2. value  'MythShutdownWakeupTime' is set in the DB.

I think we all have the same problem, we don't set the value  'MythShutdownWakeupTime'.

To set this value you have to use mythshutdown --setwakeuptime yyyy-MM-ddThh:mm:ss. 

I hope this tip can help you, I will do some further testing if I have time this weekend.

Greetings

Matthieu

---

### Post by jb5 on 2007-11-17
Hi Matthieu, thank you for the update.

Unfortunately I could not get the system to wakeup via mythwelcome using that date/time format - (yyyy-MM-ddThh:mm:ss).

Actually my situation isn't so bad at the moment......

Mythwelcome will now wake and shutdown after a recording. (Biggest hurdle overcome)

When I manually power up the machine, with the mythFE auto start disabled, it will stay at the  mythwelcome screen and the auto-shutdown timer doesn't start. 
So I don't have to push a button within a certain time-frame. After I close MythFE the machine switches back to mythwelcome and the auto-shutdown timer now starts. 

So aside from having to push my remote button an extra time when I power up the system, mythwelcome is actually doing almost everything that I need it to.

I will keep checking the thread to see if there are any more updates / movement on this issue.

Thank you again
JB

---

### Post by El_Matthews on 2007-11-26
Gents,

Everything is working! Finally. I am a happy mythuser ;) I will try to explain how it works, I hope this can help you.

so first; these are the settings recommended by mythtv (see [http://www.mythtv.org/wiki/index.php/Mythwelcome](http://www.mythtv.org/wiki/index.php/Mythwelcome))

1. Set wakeuptime command: mythshutdown --setwakeup $time
2. Server halt command: mythshutdown --shutdown

Now let's see what those commands are doing;

Command 1: checks if a wakeup time should be set, if yes it will write to the mythdb the required wakeup fields and after that it will executes the command mentioned under nvram-wakeup command with the required time parameter in Unix time stamp.If you don't set those time values in the DB, mythwelcome will never be able to know that it was a scheduled wake-up.

In clear, mythshutdown --setwakeup $time executes nvram-wakeup command + UnixTimeStamp.

Command 2: will check in mythwelcome if you have set a daily wakeup and if yes it will check if it has to set this as wakeup time (depending on recordings etc). If it has to set the wakeup time it will use again the nvram wakeup command with the unixtimestamp. After timestamps are set it will execute the command: Command to Shutdown.

In clear, mythshutdown --shutdown executes nvram-wakeup command UnixTimeStamp + Command to shutdown.

If I explained everything correctly you should have found that the key to make everything work is the script you put in nvram-wakeup command.

You can use the  MythWakeSet script mentioned in the wiki for that.

I hope this is clear, if not don't hesitate to let me know I will try again;)


PS: A good tip is to execute both command with the verbose switch. You will set everything the command is trying to do.

Greetings

Matthieu

---

### Post by jb5 on 2007-12-12
Hi - Nice! 
Glad you've got it working OK now.

I might have another look at this.

JB

---

### Post by jb5 on 2008-04-21
Update. 
OK so the Set wakeup time command located in MythBackEnd Setup - ```
echo $time > /proc/acpi/alarm 
```
worked a treat until the clocks went forward. :(
As I'd set up my motherboard (MB) during the winter it was set to GMT. When the clocks went forward Myth correctly adjusted to British Summer Time (BST), but my MB remained on GMT! Consequently the machine was waking 1 hour too late! So I went back to creating a script (MythWakeSet) to account for this, below is the result.

```
#!/bin/bash
# Jb Created 08-04-2008
#   Adjust Alarm to compensate for move to Daylight saving Time
#   ACPI - Alarm format >> 2008-12-31 23:59:59
#   Called from MythBackEnd >> sudo /usr/bin/MythWakeSet $time

vDate=${1} ;
vTime=${2} ;
vWake="/proc/acpi/alarm" ;

# Check if British Summer Time i.e. "BST" If so subtract 1 hour from alarm time
if [ $(date +%Z) = "BST" ] ; then
  # Separate the hour from the rest of of the time parameter 
  vHour=${vTime%%:*} ;
  vMinSec=${vTime#*:} ;
  # Check if alarm set for midnight, if so Set to 23 hour rather than -1 !!
  if [ ${vHour} = "00" ] ; then
    echo ${vDate}" 23:"${vMinSec} > ${vWake} ; 
  # If alarm set for 10 or less pad resulting single digit with extra 0. Required ?
  elif [ ${vHour} -le "10" ] ; then
    echo ${vDate}" 0"$((${vHour}-1))":"${vMinSec} > ${vWake} ; 
  else
    echo ${vDate}" "$((${vHour}-1))":"${vMinSec} > ${vWake} ;  
  fi
else
  # If not on Daylight Saving Time then output as normal
  echo ${vDate}" "${vTime} > ${vWake} ;
fi

exit

```

Paste into text file called MythWakeSet & then - ```

sudo chmod +x MythWakeSet
sudo cp MythWakeSet /usr/bin/MythWakeSet
```

And then in MythBackEnd Setup -  Set wakeup time command becomes - ```
sudo /usr/bin/MythWakeSet $time 
```

Also /usr/bin/MythWakeSet needs to be added to the sudoers file
```
sudo visudo
```
```
%mythtv ALL = NOPASSWD: /sbin/shutdown, /usr/bin/MythWakeSet, /proc/acpi/alarm, /usr/bin/MythShutdownCheck, /etc/init.d/mythtv-backend, /usr/bin/MythShutdown, /usr/bin/mythshutdown, /sbin/poweroff
```


This script is not a one size fits all solution but should be easy enough to adjust for others who have followed this path & are having similar problems.

```
date +%Z
``` will provide the relevant time zone information.
The difference between ```
date
``` & ```
sudo sh -c 'echo "+00-00-00 00:05:00" > /proc/acpi/alarm'
echo /proc/acpi/alarm
``` (which should set an alarm time five minutes hence), will determine which way the correction needs to go.

BTW the clever bit of code to separate out the hour from the rest of the time variable I found on the web.
```
vHour=${vTime%%:*} ;
vMinSec=${vTime#*:} ;
```

EDIT

Changed the first line of the script to end with bash rather than sh, as with #!/bin/sh the script throws out an error when adjusting time from 09 or 08 hours BST. This problem doesn't occur with #!/bin/bash

---

