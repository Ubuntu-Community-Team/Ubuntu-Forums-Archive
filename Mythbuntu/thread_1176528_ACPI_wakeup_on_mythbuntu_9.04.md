---
title: "ACPI wakeup on mythbuntu 9.04"
date: 2009-06-02
forum: Mythbuntu
---

### Post by zaprat on 2009-06-02
the acpi wiki's tends to be difficult to follow in places as they cater for multiple scenario's mostly at older versions. Here is my attempt at a HOW-TO for mythbuntu 9.04
 
**Assumptions/Prequisites**
- mythbuntu 9.04
- front end and back end on same machine
- bios clock using UTC (not local time)
 
**What to expect**
At completion of this how-to your system should suspend after the machine idle for predetermined period, it will shutdown. When it is time to do something, the machine will automatically restart and perform the activity required. Once complete and idle once more it will shutdown. The automatic shutdown can be overiden enabling the user uninterupted viewing.
 
**How it works**
Mythbackend is running and monitors activity. If it is idle for predetermined timeframe it will run a command mythshutdown with various switches and parameters.
In summary if idle it runs the following commands.
mythshutdown --check (this checks for activity). If a user is logged in, it will prevent shutdown by returning 1; if OK to shutdown will return a 0 (same as exit 0)
mythshutdown --settime $time (this stores the time for next wakeup, it does not write to bios h/w clock )
mythshutdown --shutdown (this triggers a script that sets time to wakeup in bios h/w clock and then shutdown/power off the computer)
 
When you boot the machine, the mythwelcome screen will be displaye. The mythwelcome program monitors activity and displays status of the backend. If the machine is idle for a preset time (noted by a countdown in mythwelcome, it will automatically shutdown the computer)
 
If whilst mythwecome is running, the user presses select/enter on remote/keyboard, the mythfrontend application will be started enabling the user to watch tv etc. If the mythfrontend is running, the machine will prevented from shutting down. To enable automatic shutdown/wake capability, the user must return to the mythwelcome screen by entering stop/end. THIS IS IMPORTANT!
 
**STEP 1 - check bios clock is UTC**
to check if bios clock is running UTC, start a command line session, then
```

$cat /proc/driver/rtc

```
the rtc_time should be a UTC time
 
**STEP 2 - create MythWakeSet script**
```

$mkdir ~/myscripts
$cd ~/myscripts
sudo apt-get install gedit
gedit MythWakeSet

```
 
The cut and paste following code (taken from acpi wake page [https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake))
 
Note: if you have gedit installed already, there is no need to reinstall it; if you are not sure type gedit to determine if it installed.
 
```

#!/bin/sh
 
# inspired from http://www.mythtv.org/wiki/index.php/ACPI_Wakeup
# and https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake
#
# MythWakeSet
#
# set mythtv wake-up time with UTC-adjusted time
#
# use: MythWakeSet date time      
# ex.: MythWakeSet 2008-11-02 20:15:00
# See also 'man date' for date/time-formats.
 
# TimeZone, use +0100 for GMT+1
#TZ="+0100"
TZ=$(date +%z)
 
LOG=/var/log/mythtv/mythbackend.log
 
DATE=$(date -d "$1 $2 $TZ" "+%F %H:%M:%S" -u)
SECS=$(date -d "$1 $2" "+%s")
 
echo Running $0 to set the wakeup time to $1 $2 >>$LOG
 
if [ -e /sys/class/rtc/rtc0/wakealarm ]; then
  echo 0 > /sys/class/rtc/rtc0/wakealarm
  echo $SECS > /sys/class/rtc/rtc0/wakealarm
  echo "echo 0 > /sys/class/rtc/rtc0/wakealarm" >>$LOG
  echo "echo $SECS > /sys/class/rtc/rtc0/wakealarm" >>$LOG
  cat /proc/driver/rtc  >>$LOG
else
  if [ -e /proc/acpi/alarm ]; then
    echo $DATE > /proc/acpi/alarm
    echo "echo $DATE > /proc/acpi/alarm" >>$LOG
  else
    echo "ERROR, Wakeup not set, no /sys/class/rtc/rtc0/wakealarm and no /proc/acpi/alarm found" >>$LOG
  fi
fi

```
 
save the script
now make the script executable and put it in /usr/bin
 
```

$ chmod +x MythWakeSet
$ sudo cp MythWakeSet /usr/bin

```
 
Brief explanation of script: the scripts takes the time in yyyy-MM-dd hh:mm:ss and converts it secs since 19.. in UTC. It then writes the time to bios hw clock (not sure). This done by echo $SECS > /sys/class/rtc/rtc0/wakealarm command. The /prco/acpi/alarm is legacy and is not used in 9.04.
 
 
**STEP 3 - configure backend to sleep/wake**
Stop the backend and setup
 
```

$ sudo /etc/init.d/mythtv-backend stop
$ mythtv-setup

```
 
Proceed to general>Shutdown/Wakeup Options
untick Block shutdown before client connected
Set idle shutdown timeout (secs): 120
Set Max. wait for recordings (min): 15
Set Startup before rec (secs): 200
Set Wakeup time format: yyyy-MM-dd hh:mm:ss
Set Command to set Wakeup Time: sudo -H mythshutdown --setwakeup "$time"
Set Server Halt command: sudo -H mythshutdown --shutdown
Set pre shutdown check-command: mythshutdown --check
 
Note: if you are using EIT; you need to set the idle time to less that 5 minutes. If set longer, the EIT scan will interupt the idle time and it will never expire and hence the box will not shut down. In have set it to 120 secs here.
 
**STEP 4 - get mythwelcome to run a startup**
 
Now you need to get mythwelcome working
 
```

$sudo cp  /etc/mythtv/session-settings /etc/mythtv/session-settings.old
$sudo gedit /etc/mythtv/session-settings

```
 
modify line from
```

#MYTHWELCOME=true

```
to
```

MYTHWELCOME=true

```
 
save the file
 
**STEP 5 - configure mythwelcome**
 
run setup for mythwelcome
```

$mythwelcome --setup

```
 
update the setup page as follows:
 
set nvram-wakeup Command: sudo -H /usr/bin/MythWakeSet "$time"
set nvram-wakeup Restart Command: leave blank!
set Command to reboot: sudo -H shutdown -h -r now
set Command to shutdown: sudo -H shutdown -h -P now
 
exit mythwelcome setup.
 
**STEP 6 - get everything working**
reboot system by
```

$sudo reboot

```
 
now the system will start with mythwelcome then load mythfrontend. 
 
**STEP 7 - prevent mythfrontend from starting on restart**
To prevent frontend from starting at next reboot, exit mythfrontend and return to mythwelcome.
 
Prior to doing this step. You may need lock the system by selecting "m" on the keyboard and selecting lock shutdown. This will prevent the machine from shutting down whilst you are within mythwelcome. Remember to unlock after you are finished otherwise the machine will _never shutdown._
 
Hit "i" on keyboard and untick Automatically Start Myth Frontend. This will prevent mythfrontend from starting next time you reboot
 
**STEP 8 - TEST**
Now to test
 
reboot as before
 
you should be at the mythwelcome screen
hit select/enter on remote/keyboard to start mythfrontend and schedule a program to record about 30 minutes in the future (not less the 15 minutes).
now return to mythwelcome by pressing stop/Esc button few times
 
the machine should automatically shutdown in approximately 2 minutes (see count down). If mythwelecome indicates that there are jobs in the queue being processed, it will not shutdown until jobs are complete. You will need to perform a retest after the jobs are completed. 
 
Aproximately 2 minutes prior to the time, the machine should restart and start mythwelcome. The machine should record and on completion and idle, it will shutdown. 
 
Note: you can prevent shutdown at any time by starting mythfrontend within 2 minutes of boot from mythwelcome. But to recommence shutdown, you must return to mythwelcome.
 
Hope this helps.
 
This information was taken from a number of sources including 
 
[http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup)
and
[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)
 
a more detailed explanation can be at these sites.
 
Note: I had an issue with frontend starting before the backend was ready. For solution see this:
[http://ubuntuforums.org/showthread.php?t=1176303](http://ubuntuforums.org/showthread.php?t=1176303)

---

### Post by ranjo on 2009-06-02
I tried your script and it works perfectly! I never got the ACPI wakeup to work actually.

I used a script before which uses the RTC alarm in the bios. It's configured on a fixed date which the script knows (2008-12-31 23:59:59). When the computer shuts down it calculates the number of seconds before the computer has to wake, it subtracts those seconds of the configured time in the bios. When to computer starts, it restores the old time by adding those subtracted seconds back. It really worked until Jaunty because now all the services are booting at the same time. The time is restored after some services were already started, including mythbackend which thought it was 2008-12-31.

Anyway, i was looking for a solution and this made everything running perfect.

---

### Post by zaprat on 2009-06-03
I noted an error with one of the mythshutdown parameters (missing - for --shutdown). I have corrected it. I have edited/corrected in the original post. I have also added some additional wording to make things flow better.

---

### Post by usererror on 2009-06-12
Oh, this is great! I cannot wait to implement this configuration over the weekend. I am trying to "go green" in my home and try to have only one PC turned on 24/7, which is my web/file server, right now my Mythbuntu box runs 24/7 as well, which is not necessary since I moved all the Video, Pictures, and Music shares off of it.

Thank you VERY much for writing this.

---

### Post by usererror on 2009-06-18
Odd,

I must not be doing something right.  Mine is not doing a count down, ever.

if try to run the first script manually, i can only run it as sudo and i get this error:

```
date: invalid date `  -0400'
```

---

### Post by electrogulp on 2009-07-08
Hi Zaprat, thanks for your tutorial.
I tried your script too but with no success.
When I go out from frontend I can see the Mythwelcome screen, countdown start but, at 10s from the shutdown It restart!! so contdown restart ciclically untill I press "Start Frontend" or exit from the contextual menu.
Can you help me? 
Thanks

---

### Post by Mitch72 on 2009-07-22
> **electrogulp said:**
> Hi Zaprat, thanks for your tutorial.
I tried your script too but with no success.
When I go out from frontend I can see the Mythwelcome screen, countdown start but, at 10s from the shutdown It restart!! so contdown restart ciclically untill I press "Start Frontend" or exit from the contextual menu.
Can you help me? 
Thanks
I'm having the same problem- Mythwelcome counts down, gets to 0, then starts counting again from the start. However, it occasionally works :confused:

Can you run up mythwelcome and mythbackend in terminal, and copy/paste what it says? For me, MythWelcome  says (once it gets to "0", can't copy and paste it 'cos it managed to shut down this time):

```

NOTE: some of the terminal was off the screen- I was using VNC, this is off a screenshot, so some of the commands might be missing at the end- i'll have another look when it boots

CheckShutdownServer returned - OK to shutdown
Running the command to set the next scheduled wakeup time:
sudo -H mythshutdown --setwakeup "2009-07-22 15:26:40"
2009-07-22 15:09:45.670 Running the command to shutdown this computer :
sudo -H mythshutdown --shutdown

date: invalid date '1248247600 +0800'
date: invalid date '1248247600 '

```

MythBackend just gives a "The system will power off now!" message

Any help would be appreciated!

EDIT: Had to manually boot it back up :(

---

### Post by SniperKIng on 2009-07-22
Hey,

Im trying to set this up now too and have come across loads or problems but am pretty close now.

I had the problem with the countdown reaching 0 and then restarting, which for me was cause by mythtv asking for the sudo password in the background and being unable to actually ask for it nothing happened.

To fix it i opened terminal and typed **sudo visudo**

And at the bottom on the file i added 

**%mythtv ALL = NOPASSWD: /usr/bin/MythWakeSet, /sbin/shutdown, /bin/sh, /usr/bin/setwakeup.sh**

And that seems to have worked.

---

### Post by Mitch72 on 2009-07-24
Thanks Sniper, looks like that was the problem I was having, I'll have to look into it

**EDIT:** Yep, it was. Thanks! :D Needed to change it slightly, had to include /usr/bin/mythshutdown (although it might not be needed...) 

Still having problems with the system starting up though :(

**EDIT:** K, I've been able to have the system successfully wake up by using the commands [here]("http://www.mythtv.org/wiki/ACPI_Wakeup#Initiate_manually"). 

By looking at 'cat /proc/driver/rtc/' in the mythtv log, the alrm_date is coming up as ****-07-25, even though the epoch time listed seems correct. From the info in the ACPI Wakeup wiki, i'm guessing that it's being set to a time in the past?

---

### Post by TVtalker on 2009-07-25
Ok, after some changes the shutdown is working. I also added /usr/bin/mythshutdown with **sudo visudo**. Now the system is going down.

Wake up isn´t still working correctly. I have to do some work on it.

Thanks for your script Zaprat

---

### Post by SniperKIng on 2009-07-31
Hey,

Yes ****-07-25 would mean it was set in the past, and was a problem i was having for a while but then i changed the BIOS clock to UCT and it works now.

Also ****-**-25 for example wouldn't always mean it was set in the past as sometimes if i set the alarm shutdown but then manually turned on before the wake up happened, something like that would be shown even though it was in the future.

Hope this helps

---

### Post by dagreatk on 2009-08-03
Great howto system is shutting down automatically but only starting the countdown after i enter frontend atleast one time. I have not tested wakeup yet because i am still trying to figure out why know my program guide is lagging so much now that mythwelcome is starting. now that i am using mythwelcome so i can have the system wake and shutdown on its own there is a huge lag in the program guide while watching live tv

tv playback is fine

any thoughts on why mythwelcome would slow down program guide epg

---

### Post by dagreatk on 2009-08-03
alright i've narrowed down the problem to lirc, my remote and the whole issue with the countdown not starting until i open frontend atleast once is because i didn't untick the option in the general setting that does just that, lock shutdown until a client connects.

as far as the epg is concerned i am using an antec case lirc_imon rm200 remote (pad remote) when i use the keyboard it scrolls perfectly but when i use the remote to scroll it starts fine moving very quickly and slowly slows to a jittery lag

---

### Post by dagreatk on 2009-08-03
i am trying to have the system wake but it is doing nothing. this is what was sent to the log

2009-08-03 17:07:40.798 Running the command to set the next scheduled wakeup time :-
                                                sudo -H mythshutdown --setwakeup "2009-08-03 17:26:40"
2009-08-03 17:07:40.974 Running the command to shutdown this computer :-
                                                sudo -H mythshutdown --shutdown
date: invalid date `1249334800  -0400'
date: invalid date `1249334800 '
Running /usr/bin/MythWakeSet to set the wakeup time to 1249334800
echo 0 > /sys/class/rtc/rtc0/wakealarm
echo  > /sys/class/rtc/rtc0/wakealarm
rtc_time        : 21:07:41
rtc_date        : 2009-08-03
alrm_time       : 21:12:41
alrm_date       : ****-08-03
alarm_IRQ       : no
alrm_pending    : no
24hr            : yes
periodic_IRQ    : no
update_IRQ      : no
HPET_emulated   : yes
DST_enable      : no
periodic_freq   : 1024
batt_status     : okay

---

### Post by dagreatk on 2009-08-03
If anybody was having the same problem as me with a similar output, the solution for it is:

ounce at the mythwelcome --setup step the default value for me at the wakeup time format was time_t,
this is incorrect it should be yyyy-MM-dd hh:mm:ss once i changed this the right values were sent to MythWakeSet and my system powered on at the correct time.

the log now changed to:

Running /usr/bin/MythWakeSet to set the wakeup time to 2009-08-03 19:56:40
echo 0 > /sys/class/rtc/rtc0/wakealarm
echo 1249343800 > /sys/class/rtc/rtc0/wakealarm
rtc_time        : 23:24:27
rtc_date        : 2009-08-03
alrm_time       : 23:56:40
alrm_date       : 2009-08-03
alarm_IRQ       : yes
alrm_pending    : no
24hr            : yes
periodic_IRQ    : no
update_IRQ      : no
HPET_emulated   : yes
DST_enable      : no
periodic_freq   : 1024
batt_status     : okay

This is the correct output

---

### Post by oilsbloke on 2009-08-16
For those that are interested, there are some boards that will only wake up using /sys/class/rtc/rtc0/wakealarm (as we know) but some of those boards will also only take the number of seconds in the future that it should wake up.  

So, if you want the computer to wake up in 1 hour from shutdown time, you need to put  "+3600" (the number of seconds in an hour) to the alarm time.

So, to do this, in MythWakeSet, I replaced the portion of code:
```
DATE=$(date -d "$1 $2 $TZ" "+%F %H:%M:%S" -u)
SECS=$(date -d "$1 $2" "+%s")
 
echo Running $0 to set the wakeup time to $1 $2 >>$LOG
 
if [ -e /sys/class/rtc/rtc0/wakealarm ]; then
  echo 0 > /sys/class/rtc/rtc0/wakealarm
  echo $SECS > /sys/class/rtc/rtc0/wakealarm
  echo "echo 0 > /sys/class/rtc/rtc0/wakealarm" >>$LOG
  echo "echo $SECS > /sys/class/rtc/rtc0/wakealarm" >>$LOG
  cat /proc/driver/rtc  >>$LOG
else
```

with:

```
DATE=$(date -d "$1 $2 $TZ" "+%F %H:%M:%S" -u)
SECS=$(date -d "$1 $2" "+%s")
NOWSECS=$(date -d now "+%s")
NUMSECS=$(($SECS-$NOWSECS))
 
echo Running $0 to set the wakeup time to $1 $2 >>$LOG
echo Running set the wakeup time to secs $NUMSECS >>$LOG
if [ -e /sys/class/rtc/rtc0/wakealarm ]; then
  echo 0 > /sys/class/rtc/rtc0/wakealarm
  echo +$NUMSECS > /sys/class/rtc/rtc0/wakealarm
  echo "echo 0 > /sys/class/rtc/rtc0/wakealarm" >>$LOG
  echo "echo +$NUMSECS > /sys/class/rtc/rtc0/wakealarm" >>$LOG
  cat /proc/driver/rtc  >>$LOG
else
```

and it worked fine.

I hope this helps someone.

---

### Post by kaanchan on 2009-08-17
Thank you very much. Your post helped me immensely. I am running Karmic (9.10) on Sony Vaio VGN-N320E, and it does respond to the +seconds command.

I have a better understanding of /sys/class/rtc/rtc0/wakealarm as well from your post. It seems you cannot see contents of the file, only send commands to it (right?).

Does anyone know how to query if wakealarm has anything set?

---

### Post by oilsbloke on 2009-08-17
```
cat /proc/driver/rtc  >>$LOG

```...in the script segment above queries the wakealarm and give you plenty of information in the logs

from a command line...```
cat /proc/driver/rtc

```...should do the trick

---

### Post by roundhay on 2009-08-20
I have tried to set up this script but it does not appear to be working. I have added /usr/bin/mythshutdown with sudo visudo as indicated by Mitch72 but the system does not shutdown when idle; when the counter gets to 10 seconds it then goes back to 120 seconds?

I have set a recording and when this has finished the system shutdown but if I set subsequent recording, maybe 5 hours in the future, no shutdown?

I have a ASUS P5K Deluxe MB I have not seen this mentioned in any of the ACPI hardware lists I have found, dose anyone know of this board will work with this script?

when I run 
```
$cat /proc/driver/rtc
```
the output is
```
rtc_time	: 23:12:32
rtc_date	: 2009-08-20
alrm_time	: **:**:**
alrm_date	: ****-**-**
alarm_IRQ	: no
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: yes
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay

``` 

Does anyone know how I might get this to work?

---

### Post by roundhay on 2009-08-21
Some more info to add to my previous post.

If there is nothing scheduled the machine shuts down, if I schedule a recording, even 5 or 10 days in the future the machine does not shutdown and once the counter reaches 0 it goes back to 120 seconds.

When I run powersave -S the output is:

```
$ powersave -S
ACPI
```

At 17:05 this evening the out put from cat /proc/driver/rtc was

```
$cat /proc/driver/rtc

htpc@htpc-desktop:~$ cat /proc/driver/rtc
rtc_time	: 17:04:50
rtc_date	: 2009-08-21
alrm_time	: 23:35:15
alrm_date	: ****-**-**
alarm_IRQ	: no
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: yes
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay
```

I'm not sure if the next piece of info is relevant but when  I SSH into my myth box the login displays the following:

```
 $ ssh htpc
Linux ******-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
```

What does the "SMP Fri Apr 17 01:57:59 UTC" mean at the start? It appears to be a date and time but it does not match the system time?

I have read a few other threads and forums and can't see an obvious way to solve this?

---

### Post by jb5 on 2009-08-22
Jumping in at the end here, & haven't re-read the entire thread, but.....
 
I found that if the counter just cycles continually, there was a problem with the shutdown script itself. (At least that was the problem for me)!

First steps would be to check whether the script is listed in your sudoers file, as it will need to be run as root. 
(Also check the spelling of the script you are expecting to run against that in your soders file).

Next I would cd to the directory where the script is stored and try running form there as root, then I would try again by running the full shutdown script as it is listed in the shutdown line for your back-end or MythWelcome etc...

HTH

EDIT -- I've just noticed that it **will** shutdown if there are **NO** scheduled recordings set. The above wont hurt, but maybe not all that useful either! Sorry.

---

### Post by roundhay on 2009-08-25
I have changed a few bios settings and checked all of the code / scripts from the how-to and I still can't get this to work.

The system shutsdown when thre are scheduled records but the counter just cycles when there is a scheduled recording.

I have also noticed that when you esc out of the front end the shutdown option does not work if their is a scheduled recording but the reboot optino does work.

If I have not posted enough informatino can some one let me know if there are any logs I can check to see what is happening?

---

### Post by roundhay on 2009-08-28
I have managed to get this working, the posted script work perfectly I just needed to get the bios setting correct.

I have noticed that the records seem to start a little late and on many programs the beginning is missed.

Is there anyway to get myth to strat records a bit earlier?

---

### Post by jensk on 2009-08-29
Thank you for this very usefull article.

I have a setup with separate back- and frontends - actually several frontends. I problem is how to get the frontends to automatically wake up the backend.

I have a dd-wrt router that can wake the backend at specific times but how do i get the frontends to send the magic packets to the backend when they need to stream recorded videos.

Any creative ideas?
/JK

---

### Post by ktmom on 2009-08-29
> **roundhay said:**
> I have managed to get this working, the posted script work perfectly I just needed to get the bios setting correct.

I have noticed that the records seem to start a little late and on many programs the beginning is missed.

Is there anyway to get myth to strat records a bit earlier?

Is the late start due to the time it takes for your machine to start, or is the recording always late even when the machine is on?  

The first case, increase the "start up before rec" entry in the backend setup.  General > page 5 

The second case, there is a entry for "time to record before the start of show".  It's found under Utilities/Setup > setup > TV settings > general > page 4

> **jensk said:**
> 
I have a dd-wrt router that can wake the backend at specific times but how do i get the frontends to send the magic packets to the backend when they need to stream recorded videos.

Any creative ideas?
/JK

Have you seen this wiki entry? [http://www.mythtv.org/wiki/Wake-on-LAN]("http://www.mythtv.org/wiki/Wake-on-LAN")

or this thread for a diskless front-end [http://ubuntuforums.org/showthread.php?t=908043]("http://ubuntuforums.org/showthread.php?t=908043")

---

### Post by jonnybignote on 2009-10-16
Does anyone know how I'd do this with standby (S3) instead of shutdown?
Thanks

---

### Post by prupert on 2009-10-19
AWESOME POST, it worked for me, with some minor changes. 

I have written up the changes I needed to make to get it to work for the D945GCLF2 here on the MythBuntu how to post: [http://ubuntuforums.org/showpost.php?p=8128247&postcount=60](http://ubuntuforums.org/showpost.php?p=8128247&postcount=60)

---

### Post by Mrazek on 2009-10-26
Absolutely excellent work!!! I tested auto wakeup and shutdown over about a year(!) with no success but using this tutorial it works without no problem for me even on an old MOBO Jetway with P4&1.7.
 
I have only several small but very important additions for other testers:
 
1. If you are starting to test this feature, go first to [http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup) but don't use "Integrate into mythtv" section, try only command line testing.
 
2. If you had success with command line waking up go to this zaprat's tutorial because above mentioned link says nothing about Mythwelcome(!).
 
3. Very important note: **if your sheduled recorting starts in less than 15 minutes no shutdown will be done (try to run mythshutdown -x with verbose switch). In this case the countdown in mythwelcome starts counting again and again.**
 
4. Important note 2: **If automatic shutdown was proceed and any recording was scheduled (more than 15 minutes in future) and you then turned on PC, mythwelcome will report idle with NO countdown (and with no automatic shutdown). It will shutdown for example after running mythfrontend and exiting it.**

---

### Post by bytebidder on 2009-10-26
Confirmed working on socket AM2 Abit A-N78HD motherboard with Mythbuntu 9.04, 9.10, 10.04 LTS and 10.10. 

I had to - 

1. in the motherboard BIOS disable "Wake On Alarm (and other wake)" function and also disable "HPET Support" 

2. follow the instruction steps presented at the beginning of this forum thread

3. add the following 2 lines to /etc/sudoers - to do this execute the following command

linuxuser@home:~$sudo visudo

Defaults visiblepw

%mythtv ALL=NOPASSWD: /usr/bin/MythWakeSet, /sbin/shutdown, /bin/sh, /usr/bin/mythshutdown

4. check that the user who was created on install to run the backend was in fact added to the mythtv and sudo groups. I did this through the GUI application in the desktop menu.

5. In the program settings of Mythwelcome, change "wakeup time format" from "time_t" to "yyyy-MM-dd hh:mm:ss"

I have so far recorded successfully 88 movies whilst working nighshift. So I can confirm that it works well. The only problem I encountered with the hardware was that the BIOS continued to lose about 1 minute of time every 2 months. So I had to install a wireless card and set NTP to update the time automatically on each boot.

If you are still having problems with your install, don't forget to try to diagnose it by looking at the logs in /var/logs/mythtv, particularly the backend log file. What stuffed me up was that I didn't have "Defaults visiblepw" added in the /etc/sudoers file, which I needed because I had SSH and VNC services running on the backend that I had casually ticked to be activated. I had a cryptic "tty" error in the logs that prevented the shutdown script from working. After googling I found the solution. I still only half understand it, but importantly it works. The lesson is to read the logs.


Thanks everyone here!

---

### Post by jMon54 on 2009-11-05
> **usererror said:**
> Odd,

I must not be doing something right.  Mine is not doing a count down, ever.

if try to run the first script manually, i can only run it as sudo and i get this error:

```
date: invalid date `  -0400'
```

I am having this same issue.  Help...!

---

### Post by prupert on 2009-11-05
> **jMon54 said:**
> I am having this same issue.  Help...!
Sounds like you aren't passing the correct date to your systems BIOS. You need to work out what correct date format works with your BIOS first, before setting up all the scripts. Run through the first part of the tutorial first, to find which command works for your BIOS, by running the first script that is mentioned, and then checking the ACPI wake-up date.

---

### Post by jMon54 on 2009-11-05
> **prupert said:**
> Sounds like you aren't passing the correct date to your systems BIOS. You need to work out what correct date format works with your BIOS first, before setting up all the scripts. Run through the first part of the tutorial first, to find which command works for your BIOS, by running the first script that is mentioned, and then checking the ACPI wake-up date.

I have this issue with two different machines: one is an AMD64 the other an Intel P4.

Does this indicate how I need to format that date field?

jmon@jmythtv-desktop:~/myscripts$ cat /proc/driver/rtc
rtc_time	: 18:52:08
rtc_date	: 2009-11-05
alrm_time	: 18:54:41
alrm_date	: ****-**-05
alarm_IRQ	: no
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: yes
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay

---

### Post by prupert on 2009-11-06
> **jMon54 said:**
> I have this issue with two different machines: one is an AMD64 the other an Intel P4.

Does this indicate how I need to format that date field?

jmon@jmythtv-desktop:~/myscripts$ cat /proc/driver/rtc
rtc_time	: 18:52:08
rtc_date	: 2009-11-05
alrm_time	: 18:54:41
alrm_date	: ****-**-05
alarm_IRQ	: no
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: yes
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay

Yes, it definately does. The fact that alrm_date is ***-**-05 means that the date hasn't been passed to the BIOS correctly and it can't understand it (I think it means that the date it was given was in the past).

You thus need to mess around with the different ways of formatting the date to find the one that works with your BIOS. Also, it doesn't matter if it is an AMD64 of P4 processor, it is the Motherboard and hence the BIOS on that Motherboard that is the issue, since that is what you are passing the Date to.

Take a look at this page from the MythTV wiki:

[http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup)

specifically the section:

**Initiate manually **

the different examples here, as far as I know, list the different ways you might need to format the date to get it to work. In my case, I had to use the example give under the "Setting alarm when bios clock is in localtime " section, so the command I needed to use was:

```
SECS=$(date -d "$1 $2" "+%s")
```

Therefore my MythWakeSet looks like this:

```
#!/bin/sh
 
# inspired from http://www.mythtv.org/wiki/index.php/ACPI_Wakeup
# and https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake
#
# MythWakeSet
#
# set mythtv wake-up time with UTC-adjusted time
#
# use: MythWakeSet date time      
# ex.: MythWakeSet 2008-11-02 20:15:00
# See also 'man date' for date/time-formats.
 
LOG=/var/log/mythtv/mythbackend.log

SECS=$(date -d "$1 $2" "+%s")
 
echo Running $0 to set the wakeup time to $1 $2 >>$LOG
 
echo 0 > /sys/class/rtc/rtc0/wakealarm
echo $SECS > /sys/class/rtc/rtc0/wakealarm
echo "echo 0 > /sys/class/rtc/rtc0/wakealarm" >>$LOG
echo "echo $SECS > /sys/class/rtc/rtc0/wakealarm" >>$LOG
cat /proc/driver/rtc  >>$LOG


```

Note I have removed a lot of useless garbage from the MythWakeSet script, since it tried to deal with old boards that didn't use /sys/class/rtc/rtc0/wakealarm, mine does, and it appears that yours does to, so cool.

The important thing to get right is the SECS= command, since that formats the date for your board. As I said, read the section from the MythTV wiki page I mentioned and you can try out different methods to see which one works for you. 

You will know when it is working when cat /proc/driver/rtc returns a valid alrm_date and not one with lots of *s in it.

After that, follow the rest of the tutorial, but also make sure you put the MythTV user in your sudoers file, (see my earlier posts and posts previous to mine about that).

---

### Post by jMon54 on 2009-11-06
Prupert,

Thanks so much for taking the time to reply with such detail.  Unfortunately, nothing seems to work for me.  But I will keep trying and report back when I find a solution.  Thanks again, it's people like you that make the Linux world great!

---

### Post by prupert on 2009-11-06
No probs, I am still learning too, and its sharing our experiences that helps everyone to learn.

I will try to help more, but with this one, I think it's a case of trying it all out first and seeing what works and what doesn't.

Good luck with it all.

---

### Post by schelf on 2009-11-12
Thanks for this how-to =D> !
Finally got ACPI wake-up working thanks to your post.

Mythwelcome doesn't come up automatic on boot but working on that.
BTW: I'm using Mythbuntu 9.10 on a Gigabyte E7AUMDS2H board, with alarm en hpet enabled in the bios.

---

### Post by jMon54 on 2009-11-12
No matter what I try I get this in my log:

echo 0 > /sys/class/rtc/rtc0/wakealarm
echo 1229942700 > /sys/class/rtc/rtc0/wakealarm
rtc_time	: 16:20:17
rtc_date	: 2009-11-12
alrm_time	: 16:25:17
alrm_date	: ****-**-12

Would users who have this working mind posting their MythWakeSet for me to see if I am able to make the modification I need to get this to work?  

Note: I can do the test where it wakes up in 5 minutes just fine.

---

### Post by prupert on 2009-11-12
Mine is the same as the one posted, except I use:

SECS=$(date -u --date "$1 $2" "+%s")

And in mythwelcome i use yyyy-MM-dd hh:mm:ss instead of time_t. - check my post here:
[http://ubuntuforums.org/showpost.php?p=8128247&postcount=60](http://ubuntuforums.org/showpost.php?p=8128247&postcount=60)

---

### Post by jMon54 on 2009-11-12
> **prupert said:**
> Mine is the same as the one posted, except I use:

SECS=$(date -u --date "$1 $2" "+%s")

And in mythwelcome i use yyyy-MM-dd hh:mm:ss instead of time_t. - check my post here:
[http://ubuntuforums.org/showpost.php?p=8128247&postcount=60](http://ubuntuforums.org/showpost.php?p=8128247&postcount=60)

Thanks Prupert - using yours however for me results in:

date: invalid date `  -0500'

---

### Post by jMon54 on 2009-11-12
> **prupert said:**
> Mine is the same as the one posted, except I use:

SECS=$(date -u --date "$1 $2" "+%s")

And in mythwelcome i use yyyy-MM-dd hh:mm:ss instead of time_t. - check my post here:
[http://ubuntuforums.org/showpost.php?p=8128247&postcount=60](http://ubuntuforums.org/showpost.php?p=8128247&postcount=60)

I just noticed this is a little different form your previous post.  I'll have to give it a try.  I just wish I could find a guide to how to interpret the date format.  I have looked and looked but even the man page is not very helpful.

---

### Post by jMon54 on 2009-11-15
I am making progress, I think.  But I am stumped by where the script pulls the values for "$1" and $2" in the DATE and SECS arguments.  Can someone please explain this to me?  Also I onder hat settings you should use in the /etc/default/rcS file for utc when BIOS is in local time.  Thanks.

---

### Post by volkswagner on 2009-11-15
My BIOS is not using UTC time.  Can you offer settings for BIOS with real time vs. UTC?  What can I modify in the script?

I did not see any settings in BIOS for UTC.  If I change the BIOS clock to reflect UTC, what changes to the OS will I need to make so my clock is accurate?

---

### Post by prupert on 2009-11-15
> **jMon54 said:**
> I am making progress, I think.  But I am stumped by where the script pulls the values for "$1" and $2" in the DATE and SECS arguments.  Can someone please explain this to me?  Also I onder hat settings you should use in the /etc/default/rcS file for utc when BIOS is in local time.  Thanks.


$1 and $2 comes from the from mythwakeset script, which is called my mythwelcome. mythwelcome queires your database and finds out when the next recording is, it then uses that info to set the time to wake up the box.

The reason it is TWO variables ($1 AND 4!), not just one ($1) (even though it is just one date/time) is the way the date and time is passed to mythwakeset, since there is a space between the date and the time, the variable passed to mythwakeset appears as two variables, hence $1 and $2, but really it is just dd-mm-yy hh:mm.

---

### Post by prupert on 2009-11-15
> **volkswagner said:**
> My BIOS is not using UTC time.  Can you offer settings for BIOS with real time vs. UTC?  What can I modify in the script?

I did not see any settings in BIOS for UTC.  If I change the BIOS clock to reflect UTC, what changes to the OS will I need to make so my clock is accurate?

There is a whole section about this in the mythtv acpi wiki page:

[http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup)

---

### Post by volkswagner on 2009-11-15
Thanks for the reply prupert.

From your link:

> 

Setting alarm when BIOS clock is in localtime

The BIOS clock is in localtime, however wakealarm must be given a UTC time.

To get a UTC time in seconds since epoch for a local time that we want mythTV to wake up we do the following. We pass the local time that we want to wake up as --date "2008-12-22 10:45:00", we indicate we want it reported as UTC time with -u, and we indicate we want it reported as seconds since epoch with +%s.

date -u --date "2008-12-22 10:45:00" +%s

So to set the alarm we can do the following.

SECS=`date -u --date "2008-12-22 10:45:00" +%s`
echo 0 > /sys/class/rtc/rtc0/wakealarm
echo $SECS > /sys/class/rtc/rtc0/wakealarm

Then we can confirm that the alarm is set with the following.

cat /proc/driver/rtc

If the alarm is set then you should see something like this. If so then shutdown and see if it wakes up at the alarm date/time.

rtc_time	: 13:40:26
rtc_date	: 2008-12-21
alrm_time	: 10:45:00
alrm_date	: 2008-12-22
alarm_IRQ	: yes
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: no
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay

If you see the alarm date similar to ****-12-21 then the alarm is set to a time in the past and it won't wake up.

rtc_time	: 13:42:01
rtc_date	: 2008-12-21
alrm_time	: 13:46:59
alrm_date	: ****-12-21
alarm_IRQ	: no
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: no
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay


It is not clear to me what this means.  

I edited the script from this thread.....I commented out the time zone information.  This writes the correct time for wake, but I still don't get a wakeup.  I am not sure what my issue is.  I originally had 7.10 installed and upgraded to 8.04.  I am trying the other script, that works with old acpi and new rtc alarm, from [https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake) .

I can get my machine to wake with 

```
sudo sh -c 'echo "+00-00-00 00:05:00" > /proc/acpi/alarm'
```

So possibly I need to use the old method.  I am just not sure when wake broke.  I had it working.....I think adding mythwelcome or changes I made implementing mythwelcome broke it.

---

### Post by volkswagner on 2009-11-15
Well, I just got the machine to wake.

I am using the script mentioned above.  I also did a couple mods to hwclock.sh from the ubuntu docs.  And to /etc/default/rcS as per mythtv wiki.

My guess it was the alternate MythWakeSet scrip to use /proc/acpi/alarm.

EDIT: I also commented out the mention of time zone in the above script since my BIOS is set to local time.

---

### Post by prupert on 2009-11-16
Glad you got it working ;)

---

### Post by jMon54 on 2009-11-16
> **volkswagner said:**
> Well, I just got the machine to wake.

I am using the script mentioned above.  I also did a couple mods to hwclock.sh from the ubuntu docs.  And to /etc/default/rcS as per mythtv wiki.

My guess it was the alternate MythWakeSet scrip to use /proc/acpi/alarm.

EDIT: I also commented out the mention of time zone in the above script since my BIOS is set to local time.

May I ask you to post the mods you made to hwclock.sh?  I was about to post my success but it was premature.  I finally got the machine to wake up when it was supposed to but now am having it hang when it should turn itself off.  Didn't have that problem before.  The backend log is showing "SetWakeUptime Command failed, shutdown aborted". The mythwelcome log shows "mythshutdown --startup returned: 1".

---

### Post by AKADAP on 2009-11-16
The instructions in the first post should be added to the wiki. (it is a wiki, you are able to edit it, that is what it is for.)

I would point out that the existing instructions should not be deleted. There are several sets of instructions for several different purposes there. The instructions in the first post of this thread are for a dedicated frontend&backend system whose sole purpose is running MythTV. In the wiki, there are instructions for a dedicated MythTV backend only system, and for a combined frontend & backend system that is also used as a desktop system.

The existing wiki page should probably be reorganized & split into separate pages depending on the purpose of the set of instructions. Unfortunately, this is beyond my understanding of how to edit a wiki.

---

### Post by jMon54 on 2009-11-20
So, the good news is I finally got Mythwelcome working!  It worked great - shutting down as needed, starting up before recording... just great!  I will post the specifics in a future post.

Now here's the problem...  the recordings themselves were so bad they were unwatchable.  I was getting tons of errors in my logs, the kind one sees when the signal is bad and after a few minutes the recording stops.  But when actually watching as they were being recorded or when not using Mythwelcome they were just fine.  Troubleshooting has led me to wondering if my using VDPAU is part of the problem.  I am unsure but suspect the frontend has to be running when VDPAU is doing its thing. Someone in another post said he thought X11 had to be running for VDPAU but I thought it'd be running at the Mythwelcome screen...?  I did try having Mythwelcome start the frontend for me but the problem persists.  So for now I am stumped.  Having the computer turn on and off as needed is useless if the recordings themselves are no good.

Is anyone who has got Mythwelcome running also using VDPAU?

---

### Post by ktmom on 2009-11-22
I'm running Mythwelcome using Myth version 0.21.20080304-1 2228-openglvdpau2 and my recordings work fine.  I have recently developed a crackle in the sound, but not at all what you are describing. 

I'm using a HAUPPAUGE PVR-500 tuner card.

---

### Post by bergqvistjl on 2009-11-23
how do you modify the setings for a bios that DOESNT use UTC? also, whenever i try and set the time manually, using: ```
sudo -H /usr/bin/MythWakeSet "$time"
```, i get: ```
invalid date `  +0000'
``` help please! lol

Edit: well it appears that the wakeup time is set correctly, but the date isn't, according to the /cat/proc/rtc file, which would explain the above error message, i suspect it has something to do with my bios not supporting UTC. These are my wakeup time values for both mythwelcome and mythbackend: yyyy-MM-dd hh:mm:ss
I'm using Karmic 64bit with a bios that DOES NOT support UTC.

What am i doing wrong? :D

---

### Post by kja999 on 2009-11-23
> **ktmom said:**
> I'm running Mythwelcome using Myth version 0.21.20080304-1 2228-openglvdpau2 and my recordings work fine.  I have recently developed a crackle in the sound, but not at all what you are describing. 

I'm using a HAUPPAUGE PVR-500 tuner card.

ktmom, Is the crackle anything like described here : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/266927](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/266927) ?

---

### Post by jMon54 on 2009-11-23
> **bergqvistjl said:**
> how do you modify the setings for a bios that DOESNT use UTC? also, whenever i try and set the time manually, using: ```
sudo -H /usr/bin/MythWakeSet "$time"
```, i get: ```
invalid date `  +0000'
``` help please! lol

Edit: well it appears that the wakeup time is set correctly, but the date isn't, according to the /cat/proc/rtc file, which would explain the above error message, i suspect it has something to do with my bios not supporting UTC. These are my wakeup time values for both mythwelcome and mythbackend: yyyy-MM-dd hh:mm:ss
I'm using Karmic 64bit with a bios that DOES NOT support UTC.

What am i doing wrong? :D

If you are not using UTC, then remove the references to "TZ" in the MythWakeSet file.  That's what worked for me.

---

### Post by bergqvistjl on 2009-11-23
right-o, what value should I put for the wakeup time format, both for mythbackend and mythwelcome?

---

### Post by jMon54 on 2009-11-23
> **bergqvistjl said:**
> right-o, what value should I put for the wakeup time format, both for mythbackend and mythwelcome?


I'm pretty sure that for me it took "yyyy-MM-dd hh:mm:ss" in both places (mythtv-setup and mythwelcome --setup) in order to make it work.  I plan on posting my solution specifics in a future post for anyone that's interested.  I did get this to work, however, my issue is that I had to turn off ACPI in my BIOS for the alarm function to work and in so doing created another problem where my recordings were unviewable due to too many buffering errors.  So for now, I am not using Mythwelcome.

---

### Post by Xerin on 2009-11-23
I'm having a trouble with the computer waking up.
It appears to set the alarm correctly, however the only difference is batt_status is 'dead'.

rtc_time              : 10:23:23
rtc_date              : 2009-11-23
alrm_time           : 10:23:44
alrm_date           : 2009-11-23
alarm_IRQ          : yes
alrm_pending      : no
24hr                   : yes
periodic_IRQ       : no
update_IRQ        : no
HPET_emulated   : yes
DST enable         : no
periodic_freq       : 1024
batt_status          : dead

I've followed the instructions on: [http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup) but can't seem to find a solution.

---

### Post by bergqvistjl on 2009-11-23
> **jMon54 said:**
> If you are not using UTC, then remove the references to "TZ" in the MythWakeSet file.  That's what worked for me.
Thanks, that got rid of the invalid date error, but its still doing it im afraid, even after putting the yyy:mm etc. value in both the backend and mythwelcome setup. The time seems to be set ok, but the date is all ***'s. Ive attached screenshots of both my settings pages, could you tell me if something is wrong? thanks. i tried the bit on the wiki page where you manually set the timer to 5 mins and it should wake up after that, and that worked fine. 

Mythbackend settings:
[IMG]http://img410.imageshack.us/img410/2545/backend.png[/IMG]
Mythwelcome Settings:
[IMG]http://img205.imageshack.us/img205/6301/welcomex.png[/IMG]

---

### Post by jMon54 on 2009-11-23
Here's my MythWakeSet. (Notice how I got rid of the reference to the time zone.):

LOG=/var/log/mythtv/mythbackend.log

#  TZ=$(date +%z)

DATE=$(date -d "$1 $2" "+%F %H:%M:%S" -u)
SECS=$(date -u --date "$1 $2" +%s)
 
echo Running $0 to set the wakeup time to $1 $2 >>$LOG
 
echo 0 > /sys/class/rtc/rtc0/wakealarm
echo $SECS > /sys/class/rtc/rtc0/wakealarm
echo "echo 0 > /sys/class/rtc/rtc0/wakealarm" >>$LOG
echo "echo $SECS > /sys/class/rtc/rtc0/wakealarm" >>$LOG
cat /proc/driver/rtc  >>$LOG

---

### Post by bergqvistjl on 2009-11-24
cheers, ill try that today, do you notice anything wrong with my backend + mythwelcome settings?

---

### Post by bergqvistjl on 2009-11-24
> **jMon54 said:**
> Here's my MythWakeSet. (Notice how I got rid of the reference to the time zone.):

LOG=/var/log/mythtv/mythbackend.log

#  TZ=$(date +%z)

DATE=$(date -d "$1 $2" "+%F %H:%M:%S" -u)
SECS=$(date -u --date "$1 $2" +%s)
 
echo Running $0 to set the wakeup time to $1 $2 >>$LOG
 
echo 0 > /sys/class/rtc/rtc0/wakealarm
echo $SECS > /sys/class/rtc/rtc0/wakealarm
echo "echo 0 > /sys/class/rtc/rtc0/wakealarm" >>$LOG
echo "echo $SECS > /sys/class/rtc/rtc0/wakealarm" >>$LOG
cat /proc/driver/rtc  >>$LOG

i did that, but the time is correct, but the date still isnt:

```
rtc_time	: 12:33:33
rtc_date	: 2009-11-24
alrm_time	: 13:23:40
alrm_date	: ****-**-**
alarm_IRQ	: no
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: no
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay

```
of course it could be displaying the **'s because ive manually woken it up BEFORE the alarm? ill do a proper test and see.

---

### Post by jMon54 on 2009-11-24
Another tip, based on my experience with getting this to work for me, it did not matter if the alarm time looked incorrect when I did "cat /proc/driver/rtc".  In other words, I could not test it this way.  For me, I had to set MythTV to record a program in the future and then wait and see if it worked.  This was slow and cumbersome but it was the only way.  One thing, if the test wake up (the one where you have your system wake up in 5 minutes) doesn't work, you have to fix that first.  The code for that is:

sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"
sudo sh -c "echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm"
cat /sys/class/rtc/rtc0/wakealarm

---

### Post by AKADAP on 2009-11-24
> **jMon54 said:**
> So, the good news is I finally got Mythwelcome working!  It worked great - shutting down as needed, starting up before recording... just great!  I will post the specifics in a future post.

Now here's the problem...  the recordings themselves were so bad they were unwatchable.  I was getting tons of errors in my logs, the kind one sees when the signal is bad and after a few minutes the recording stops.  But when actually watching as they were being recorded or when not using Mythwelcome they were just fine.  Troubleshooting has led me to wondering if my using VDPAU is part of the problem.  I am unsure but suspect the frontend has to be running when VDPAU is doing its thing. Someone in another post said he thought X11 had to be running for VDPAU but I thought it'd be running at the Mythwelcome screen...?  I did try having Mythwelcome start the frontend for me but the problem persists.  So for now I am stumped.  Having the computer turn on and off as needed is useless if the recordings themselves are no good.

Is anyone who has got Mythwelcome running also using VDPAU?

Bad recordings are something else entirely. If you are recording digital broadcasts (clear QAM or ATSC) all the backend needs to do is extract the data from the stream and copy it to disk. No image processing involved, so neither X11 nor VDPAU is involved in the process.

Now you said that you were watching the shows as they were recorded, but you did not say what you were using to watch with. If you were using a different receiver (say your television with its own built in tuner), I'd say look at the signal strength getting to the tuner used by MythTV. If you were using the MythTV live TV vewer, it means you have more than one tuner, and you were watching with a different tuner than was recording. How are they connected? When watching live TV, you can switch tuners (use the 'm' key to bring up a menu), do all tuners work well with the channel that failed to record?

---

### Post by jMon54 on 2009-11-24
I was mistaken when I earlier posted my problem was with VDPAU and or X11.  I believe my issue is with ACPI.  When I have it turned off in the BIOS, I can wake the computer up using Mythwelcome but my recordings suffer with numerous buffer errors unless I am watching while they are being recorded using the one and only tuner I have installed.  Puzzling, right?

---

### Post by bergqvistjl on 2009-11-25
> **jMon54 said:**
> Another tip, based on my experience with getting this to work for me, it did not matter if the alarm time looked incorrect when I did "cat /proc/driver/rtc".  In other words, I could not test it this way.  For me, I had to set MythTV to record a program in the future and then wait and see if it worked.  This was slow and cumbersome but it was the only way.  One thing, if the test wake up (the one where you have your system wake up in 5 minutes) doesn't work, you have to fix that first.  The code for that is:

sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"
sudo sh -c "echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm"
cat /sys/class/rtc/rtc0/wakealarm

well despite the alarm date being incorrect, it woke up on time! :p The only problem now, is that the box still shuts down if the machines idle, even when ive locked it using mythwelcome. Could it be because i need to put mythshutdown --check in the pre-shutdown check command in mythbackend setup, ive currently set it to exit 0. what i want it to do is shutdown the system (and set the next wakeup time etc.) even if my user is logged in with open programs etc, but ONLY if shutdown has been unlocked in mythwelcome.

EDIT: i tried mythshutdown --check, and it worked! thanks for all your help guys!. p.s we should make a couple of stickys, one for setting up mythtv + acpi for those who HAVE a utc mobo, and another one for those who dont.

---

### Post by GuiGuy on 2009-11-28
Thanks for everyone's effort. I struggled with it for a couple of weeks but can't past the bad date format

> 
rtc_time	: 22:39:33
rtc_date	: 2009-11-28
alrm_time	: 22:53:40
alrm_date	: ****-**-28
alarm_IRQ	: no
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: yes
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay


Whilst the machine shuts down ok it  immediately re-boots when the UTC day is earlier than the local day date (I'm in Australia). By example the above shows the 28th when it's actually the 29th here.

Anyway, I think it's time to give up. Somethings in linux are just too hard for ordinary folks. 

Cheers

---

### Post by GuiGuy on 2009-11-28
> **dagreatk said:**
> i didn't untick the option in the general setting that does just that, lock shutdown until a client connects.

I'm having the same issue but don't see the general setting you mention. Or maybe I've been spending too much time on this :D

EDIT: Nevrmind, found it. It's in the backend, right? :)

TIA

---

### Post by ktmom on 2009-11-29
> **kja999 said:**
> ktmom, Is the crackle anything like described here : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/266927](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/266927) ?

No, all my channels have the static and it seems to be related to the recording.  Something has changed and I haven't had time to chase it down.

---

### Post by Senkoboy on 2009-11-29
I am running Unbuntu 8.10 Intrepid, with Myth 0.21, frontend and backend on the same box.

I have on my (myth backend setup) Server Halt Command:  sudo /sbin/halt -p

I am not Mythbuntu so I didn't change the command to /usr/bin/mythshutdown like is shown in some of the threads.

Do I need to change the command to something like: sudo shutdown -h

I ran this test and it worked:

[I]Simple test to wake the machine 5 minutes from now

sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"
sudo sh -c "echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm"
cat /sys/class/rtc/rtc0/wakealarm

Check

cat /proc/driver/rtc

This should return a list of parameters. Check the "alrm_time" is 5 minutes into the future and the "alrm_date" is today.


Shutdown your computer and see if it comes back up in ~5 min.

sudo shutdown -h now
[/I]

 With my current setup (sudo /sbin/halt -p) my computer will shut down when idle, but not restart on time.  I guess it is not getting the time written to the bios.  It could be another problem, but I wanted to start looking here.

Thanks, Mike (AKA Senkoboy)

---

### Post by gwagchunks on 2009-12-04
Hi Everyone

Thanks for this post. I have followed it through and it looks like it's working for me. The machine shuts down when idle. At first I thought that it wouldn't startup because when it shut down and I went into the bios, the bios wakeup time was showing a time that I typed in manually some days ago, and not the time of the next programme to record. Don't be mislead/tricked by this. I started my machine, set a programme to record in the future, the machine shut down when idle, it then booted up at the correct time! Awesome! Thanks again!:D

---

### Post by GuiGuy on 2009-12-04
> **gwagchunks said:**
> Hi Everyone

Thanks for this post. I have followed it through and it looks like it's working for me. The machine shuts down when idle. At first I thought that it wouldn't startup because when it shut down and I went into the bios, the bios wakeup time was showing a time that I typed in manually some days ago, and not the time of the next programme to record. Don't be mislead/tricked by this. I started my machine, set a programme to record in the future, the machine shut down when idle, it then booted up at the correct time! Awesome! Thanks again!:D

This has never worked for me but not for the lack of trying and hundreds of dollars spent on replacing hardware that was recommended. 

It's enough to drive one to that other OS, especially as it does it "out of the box", so to speak. 

Cheers

---

### Post by SiHa on 2009-12-05
Thought I'd add my experience as well.

I just started playing with this, and my BE (which shutdown/woke up perfectly with 8.04) wouldn't wake up. I found something about an HPET conflict in the MythTV ACPI page: [[COLOR="Blue"]_here_[/COLOR]](http://www.mythtv.org/wiki/ACPI_Wakeup#HPET_conflict).
The fix is to add the option **hpet=disable** to the grub menu entry.

9.10 uses GRUB2, so it's not quite as simple as editing menu.lst any more. The config file for GRUB2 is **/boot/grub/grub.cfg**, but **this file should not be edited.** Instead, you edit **/etc/default/grub**.
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
.
.
.

```
And add hpet=disable to the default options```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash hpet=disable"
```
Then update grub, as indicated in the file.```
sudo update-grub
```

For some reason, GRUB complained that it couldn't find a GRUB partition (or something) on /dev/sdc1, when updating. This panicked me a bit because that's the boot drive, but it still seems to boot OK, so I guess it's just a quirk.

In order for APCI wakeup to function, I just needed to reboot once, to diable HPET, now the standard +5mins wakeup test works fine!

---

### Post by jMon54 on 2009-12-06
Thanks SiHa!  That "hpet" trick did the job for me!  I had been struggling with this MythWelcome thing and had just about given up and now it works as it should.

---

### Post by SiHa on 2009-12-06
> **jMon54 said:**
> Thanks SiHa!  That "hpet" trick did the job for me!  I had been struggling with this MythWelcome thing and had just about given up and now it works as it should.

Yeah, it was one of those 'Eureka' moments when I ssh'ed into the  BE (in the loft) when it was due to wake up, and on the third attempt got a password prompt!

---

### Post by GuiGuy on 2009-12-06
> **SiHa said:**
> T

In order for APCI wakeup to function, I just needed to reboot once, to diable HPET, now the standard +5mins wakeup test works fine!

Thanks, but for me it's same old, same old. At the shutdown it goes straight to reboot > countdown 120secs > reboot ad infinitum.

I'm going to give up now I think. Time to think about the alternative. 

Cheers

---

### Post by SiHa on 2009-12-06
[QUOTE=GuiGuy]I'm going to give up now I think. Time to think about the alternative.[/QUOTE]You're using Mythwelcome? Must admit I didn't do that myself.

I want to have the server running from 0700 - 2300, so I just modified the Mythwakeset script to set the wakeup time to 0700, if the next recording is later. Having the frontend running blocks the shutdown, and a cron job shuts down the frontend @ 2300, allowing the backend to go idle and shutdown. I can post the modified wakeset script if it'll help.

---

### Post by GuiGuy on 2009-12-06
> **SiHa said:**
> You're using Mythwelcome? Must admit I didn't do that myself.

I want to have the server running from 0700 - 2300, so I just modified the Mythwakeset script to set the wakeup time to 0700, if the next recording is later. Having the frontend running blocks the shutdown, and a cron job shuts down the frontend @ 2300, allowing the backend to go idle and shutdown. I can post the modified wakeset script if it'll help.

Yea, I have everything as right as I can make it. the frontend does not start automatically, the countdown works, machine shuts down but reboots immediately. 

I suspect it's to do with the date formatting in the script because the date returns a bunch of *** *** etc. However, to construct the right format is beyond my meagre knowledge of these things, even if I knew where to get some insight. 

Cheers

---

### Post by GuiGuy on 2009-12-27
> **zaprat said:**
> 
**STEP 5 - configure mythwelcome**
 
run setup for mythwelcome
```

$mythwelcome --setup

```
 
update the setup page as follows:
 
set nvram-wakeup Command: sudo -H /usr/bin/MythWakeSet "$time"


My ongoing stupidity knows no bounds as I let Linux/Ubuntu/Mythbuntu drive me to the insane asylum :biggrin:

Anyway, I'm trying again. So, I don't see a "nvram-wakeup Command" option in the Mythwelcome configuration. Using MythBuntu Karmic.

TIA

---

### Post by thor999 on 2010-01-02
Well, I am new here (and to Linux as well) and running mythbuntu 9.04, and cannot find a hwclock.sw anywhere on my system, yet, in a terminal, I can "hwclock --" and produce output "Sat 02 Jan 2010 02:52:59 AM CST -0.378141 seconds". I am pretty much stuck 'til I can edit hwclock.sh, which does not exist on my system. Any ideas? Is it something new? Also, sorry to revitalize an old thread, but I need help, I want to record programs w/out wasting electricity, and I have learned Linux STRICTLY for MythTv and have somehow gotten far enough so that this is the only problem left unsolved! Also, I can use the wake command in terminal and it works just fine, FWIW yet cannot obtain success w/ the Mythwelcome portion of this tut. 
 Conicidentally, my hardware clock is in local time, as is my system clock, regardless of what changes I make w/ the hwclock command, anyone have an idea on that one? Being as how I am new to this, I notice that when people threaten to return to windoze out of frustration, they get prompt help; is this a requirement, or a shameful action, worthy of flamage?

---

### Post by jlanza on 2010-02-15
I have 9.10 and suddendly it has stop working the reboot.

when I run:
cat /sys/class/rtc/rtc0/wakealarm

I dont' get any value. Anybody knows why? Any help... I'm desperate of trying many things (hpet, grub, hwclock-save.conf, everything).

TA

---

### Post by AKADAP on 2010-02-15
> **jlanza said:**
> I have 9.10 and suddendly it has stop working the reboot.

when I run:
cat /sys/class/rtc/rtc0/wakealarm

I dont' get any value. Anybody knows why? Any help... I'm desperate of trying many things (hpet, grub, hwclock-save.conf, everything).

TA

You need to tell us a lot more about your setup than "it does not work anymore!".

How is your system set up? Are you using a combined frontend/backend system? Are you running mythwelcome? What does your mythbackend log file have to say?

Can you still manually set the wakealarm?

---

### Post by jlanza on 2010-02-16
> **AKADAP said:**
> You need to tell us a lot more about your setup than "it does not work anymore!".

How is your system set up? Are you using a combined frontend/backend system? Are you running mythwelcome? What does your mythbackend log file have to say?

Can you still manually set the wakealarm?

Hi,

I finally reinstalled and it seems that now it is working again.

The issue was that I couldn't even set the wakealarm manually. As I said the return of /sys/class/rtc/rtc0/wakealarm was no value. And /proc/driver/rtc returns that the alarmIRQ was to no.

Strange... now I cross fingers everything keeps as it is after a brand new installation.

---

### Post by Glenhawk on 2010-07-03
FYI from my MythTV-Users Mailing List Post

> My Google-Fu has failed me 
I am setting up a new Myth Server (combined FE/BE) and I am having trouble with the ACPI settings
I have set this up on many servers but this is the first time on 10.04

I always start here...
[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)

...get some tips from here...
[http://www.mythtv.org/wiki/ACPI_Wakeup#HPET_conflict](http://www.mythtv.org/wiki/ACPI_Wakeup#HPET_conflict)

...and then confirm my settings here...
[http://ubuntuforums.org/showthread.php?t=1176528](http://ubuntuforums.org/showthread.php?t=1176528)

...and I have had plenty of success.

Through many trials and tribulations I have come to the conclusion that the new 10.04 box does everything except execute the MythWakeSet script.
My reasons are from the mythbackend.log file.
Here is an excerpt from my personal server running 9.10...

[QUOTE]2010-07-03 11:51:22.806 CheckShutdownServer returned - OK to shutdown
                2010-07-03 11:51:22.813 Running the command to set the next scheduled wakeup time :-
                sudo -H mythshutdown --setwakeup "2010-07-03 22:17:00"
                2010-07-03 11:51:24.386 Running the command to shutdown this computer :-
                sudo -H mythshutdown --shutdown
                Running /usr/bin/MythWakeSet to set the wakeup time to 2010-07-03 22:17:00
                echo 0 > /sys/class/rtc/rtc0/wakealarm
                echo 1278159420 > /sys/class/rtc/rtc0/wakealarm
                rtc_time : 01:51:25
                rtc_date : 2010-07-03
                alrm_time : 12:17:00
                alrm_date : 2010-07-03
                alarm_IRQ : yes
                alrm_pending : no
                24hr : yes
                periodic_IRQ : no
                update_IRQ : no
                HPET_emulated : yes
                DST_enable : no
                periodic_freq : 1024
                batt_status : okay
                
                ...now compare this with the log from the 10.04...

> 2010-07-03 11:51:22.806 CheckShutdownServer returned - OK to shutdown
                2010-07-03 11:51:22.813 Running the command to set the next scheduled wakeup time :-
                                                                sudo -H mythshutdown --setwakeup "2010-07-03 22:17:00"
                2010-07-03 11:51:24.386 Running the command to shutdown this computer :-
                                                                sudo -H mythshutdown --shutdown
                sh: /usr/bin/nvram-wakeup: not found
                
                Now, I found this page...
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1407793](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1407793)
...and the only suggestion was to make sure there was nothing in the field "nvram-wakeup Restart Command:"
I HAVE NOTHING IN THAT FIELD! 
(I even tried putting the MythWakeSet command in that box just for testing and it still didn't work)

As far as I can see the setup in this 10.04 box is identical to my personal machine running 9.10
Can anyone help me?

PS: I have enabled the mythbuntu Auto Builds and the system has been fully updated at the time of this email.[/QUOTE]

The reply I got and the solution I found...
> On Sat, 2010-07-03 at 17:47 +0100, Douglas Mackay wrote: 
On 3 July 2010 13:47, Glen Hawksworth <glenhawk@optusnet.com.au> wrote:
> >
> > My Google-Fu has failed me
> > I am setting up a new Myth Server (combined FE/BE) and I am having trouble with the ACPI settings
> > I have set this up on many servers but this is the first time on 10.04
> >
> > I always start here...
> > [https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)
> >
> > ...get some tips from here...
> > [http://www.mythtv.org/wiki/ACPI_Wakeup#HPET_conflict](http://www.mythtv.org/wiki/ACPI_Wakeup#HPET_conflict)
> >
> > ...and then confirm my settings here...
> > [http://ubuntuforums.org/showthread.php?t=1176528](http://ubuntuforums.org/showthread.php?t=1176528)
> >
> ...
> 
> I would recommend that you try the settings in the Mythwelcome part of
> the ACPI wakeup wiki [http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup). People
> using old Ubuntu guides have had issues on 10.04 e.g. see here
> [http://ubuntuforums.org/showthread.php?t=1483962](http://ubuntuforums.org/showthread.php?t=1483962)
> _______________________________________________
> 
Douglas I could kiss you! (but I won't, my wife says the stubble grown during my time wrestling with this problem is too scratchy) 
You knocked over the first domino for me and the rest fell in turn.
All the info was right there in front of me but that forum post pointed it out...

...it was the "sudo -H" that I was using. That is the second time it has tripped me up, the first being when for some reason you had to add it 

I removed the -H from the MythWelcome settings and I got the exact same result as your forum post link.
Then I went into the backend settings and removed the -H and the sudo (since you can run mythshutdown without sudo apparently) and bingo it worked.
1000 times thank you,
Glen


---

### Post by zagor on 2010-07-13
Hi,

let me add my issue to this post, for all the other solutions seem not to work for me.
I have a fresh install of mythbuntu 10.04 64bit on a pundit P1-AH2.
Mythwelcome/shutdown/wakeup worked smoothly on this same machine till my previous installation (mythbuntu 9.04 64bit).

I have followed strictly the ACPI wakeup wiki.
It goes smoothly till the mythtv integration (i.e. also the manual test wakes up the box 5min later).
When adding the mythwelcome bit with the settings in the wiki, I have this behaviour:
a) if no recording is set, the box shuts down correctly
b) if a recording is set, the mythwelcome will cycle in the countdown and never shut down.

I've added "sudo" in front of all "mythshutdown" instances (without -H) and now it shuts down, but immediately reboots.

After one of those reboots I've checked cat /proc/driver/rtc
and it gives the ****** in the alrm_time and alrm_date settings.

Same behaviour with yyyy-MM-dd hh:mm:ss instead of time_t.
(btw: in the wiki it's noted as yyyy-MM-ddThh:mm:ss. What's that "T" instead of the space? it's not working either, anyway)

I'll try to use the MythWakeSet as in [http://ubuntuforums.org/showpost.php?p=7388254&postcount=1](http://ubuntuforums.org/showpost.php?p=7388254&postcount=1) instead of setwakup.sh as in the wiki, but any other suggestion would be welcome... 

thanks

---

### Post by alien878 on 2010-07-14
> **zagor said:**
> a) if no recording is set, the box shuts down correctly
b) if a recording is set, the mythwelcome will cycle in the countdown and never shut down.This behaviour indicates that the backend's call to mythshutdown --setwakeup is failing.  Check the backend log and you will probably see an error message.  Last time this happened to me it was because it was looking at an old mysql.txt file for the DB passwords. (why do we have to have so many mysql.txt files scattered all over the place?) 
> **zagor said:**
> Same behaviour with yyyy-MM-dd hh:mm:ss instead of time_t.
(btw: in the wiki it's noted as yyyy-MM-ddThh:mm:ss. What's that "T" instead of the space? it's not working either, anyway)Definitely needs the "T" in 0.23.  This isn't the cause of the countdown cycling above, but without the "T" it will shutdown and only wake up at the next daily wakeup if you have one.

---

### Post by regiss on 2012-03-03
Hi there I'am running mythbuntu 11.10 and trying to wakeup FE/BE.
when I run cat /proc/driver/rtc I get:

rtc_time: 02:00:21
rtc_date: 2012-03-04
alrm_time: 02:05:31
alrm_date: 2012-03-04 
alarm_IRQ: no => I think here is the problem

I have manually tried to put wake up date in bios and it worked. However somehow alarm which is set in mythbuntu is not getting into bios.

Any thought would be greatly appreciated.

Cheers regiss

---

