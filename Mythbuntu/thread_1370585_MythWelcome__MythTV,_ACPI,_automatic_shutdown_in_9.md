---
title: "MythWelcome / MythTV, ACPI, automatic shutdown in 9.10"
date: 2010-01-02
forum: Mythbuntu
---

### Post by ozite on 2010-01-02
Start by reading about _[ACPI wakeup]("http://www.mythtv.org/wiki/ACPI_Wakeup") _at MythTV.org. That page has useful information that is reproduced here. I tried following the _[HOWTO ACPI wakeup on mythbuntu 9.04]("http://ubuntuforums.org/showthread.php?t=1176528")_ and had limited success with MythWakeSet, as it only rebooted and never shut down. I borrowed heavily from that HOWTO and tried to keep the same format. Note the [Mythwelcome ]("http://www.mythtv.org/wiki/Mythwelcome") wiki was out of date, but still has good information, e.g. on MythShutdown. The following is what worked for me, at least based on the incomplete notes that I kept.  There may be some errors that I will attempt to correct.

**Assumptions/Prerequisites: **
- Ubuntu 9.10 (64 bit)
- front end and back end on same machine (MythTV 0.22)
- bios clock using UTC (not local time)
What to expect:
Your system should shutdown after the machine idle for predetermined period. When it is time to do record, the box will automatically restart. Once complete and idle, it will shutdown. The automatic shutdown can be overridden to enable the user uninterrupted viewing.

**Step 1: A few outside settings and checks**
In the BIOS, ensure that in the Power Menu, ensure that alarm wakeup is DISABLED.
System, preferences, power management. (never put computer to sleep)

check kernel to make sure you are more recent than 2.6.22

```
uname -a
```
For me it returned: Linux htpc-desktop 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux

**Step 2: Give mythtv permissions**
From a terminal
```
sudo visudo
```
add the following to the bottom...
```
%mythtv ALL = NOPASSWD: /sbin/shutdown, /bin/sh, /usr/bin/setwakeup.sh
```

**Step 3: Create a script**
Obtained from [http://www.mythtv.org/wiki/ACPI_Wakeup ]("http://www.mythtv.org/wiki/ACPI_Wakeup")

```
sudo gedit /usr/bin/setwakeup.sh
```
add the following, then save the file.
```

#!/bin/sh
#$1 is the first argument to the script. It is the time in seconds since 1970
#this is defined in mythtv-setup with the time_t argument

echo 0 > /sys/class/rtc/rtc0/wakealarm #this clears your alarm.
echo $1 > /sys/class/rtc/rtc0/wakealarm #this writes your alarm

```
Change the permissions of the file so that it can execute

```
sudo chmod +x /usr/bin/setwakeup.sh
```

**Step 4: Disable HWclock updates**
See the _[ACPI Wakeup page]("http://www.mythtv.org/wiki/ACPI_Wakeup")_ for more information

For Debian (and Ubuntu)
Set HWCLOCKACCESS to "no" in /etc/default/rcS
From a terminal
```
sudo cp /etc/default/rcS /etc/default/rcS_backup
```

```
sudo gedit /etc/default/rcS
```
```

#
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.
TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=no
VERBOSE=no
FSCKFIX=no
HWCLOCKACCESS=no
```

after setting the HWCLOCKACCESS=no, save the file

**Step 5: Manually test wakealarm**
From a terminal, run the following to see if ACPI will work
```
cat /proc/driver/rtc
```

Which gave:

rtc_time : 17:53:01
rtc_date : 2009-12-31
alrm_time : 03:**:40
alrm_date : ****-**-**
alarm_IRQ : no
alrm_pending : no
24hr : yes
periodic_IRQ : no
update_IRQ : no
HPET_emulated : yes
DST_enable : no
periodic_freq : 1024
batt_status : okay

Manually test wakealarm, from a terminal, check to see if the PC will startup successfully (outside of MythTV)
```
sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"
sudo sh -c "echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm"
cat /sys/class/rtc/rtc0/wakealarm

```
Now check to see the parameters
```
cat /proc/driver/rtc
```
now shows:
... 
alrm_time : 19:54:57
alrm_date : 2009-12-31
...
Shutdown the PC and wait... Fortunately, the manual shutdown was successful and it successfully restarted in 5 minutes.

**Step 6: MythTV Backend Settings**

```
sudo /etc/init.d/mythtv-backend stop
mythtv-setup
```

Proceed to general>Shutdown/Wakeup Options
startup command: blank
untick Block shutdown before client connected
Set idle shutdown timeout (secs): 120
Set Max. wait for recordings (min): 15
Set Startup before rec (secs): 200
Set Wakeup time format: time_t
Set Command to set Wakeup Time: sudo sh -c "/usr/bin/setwakeup.sh $time"
Set Server Halt command: sudo -H mythshutdown --shutdown
Set pre shutdown check-command: mythshutdown --check

**Step 7: Get Mythwelcome to run a startup**
```
sudo cp /etc/mythtv/session-settings /etc/mythtv/session-settings.old
sudo gedit /etc/mythtv/session-settings
```
modify line from
Code:
#MYTHWELCOME=true
to Code:
MYTHWELCOME=true
save the file, but that didn't seem to do anything. I added a startup command 'mythwelcome' from the System \ Preferences\ Startup Applications menu.

**Step 8: MythWelcome Settings**
From a terminal
```
mythwelcome --setup
```

Mythshutdown/Mythwelcome screen
Command to set wakeup time: sudo sh -c "/usr/bin/setwakeup.sh $time"
wakeup time format: time_t
nvram-wakeup Resart Command: change to blank
Command to reboot: was /sbin/reboot and change to: sudo -H shutdown -h -r now
Command to shutdown: was /sbin/poweroff change to: sudo -H shutdown -h -P now
Command to run Xterm: xterm
Command to run to start the Frontend: /usr/bin/mythfrontend

From a terminal, manually run 
```
mythwelcome
```
Push m, then lock down the settings while working. Push i, then  untick the Automatically start MythFrontend. This also means that you must manually start the Mythfrontend upon startup, or it will shutdown. Return to the menu and remember to unlock.

Hopefully these settings will work. Set a recording for at least 20 minutes in the future. Leave MythWelcome running. It should shut off, then restart for the recording, run the commercial flagging, then shut off until the next recording.

---

### Post by shazbut on 2010-01-04
Thanks for the timely guide, I'm just changing my main backend to 9.10.  I'd followed the 9.04 guide on a test box running 9.10, got it all working perfectly, but forgotten the exact steps.

Only problem I have is this box not liking ACPI wake-on-RTC from power-off.  It works fine from pm-suspend, as per the S3 (Suspend to RAM) section of [this guide]("http://www.mythtv.org/wiki/ACPI_Wakeup#Initiate_manually_2"), but getting the box to reboot after wake from suspend is doing my head in.  There seems to be a problem with the logic of the script they've posted to do this (/etc/init.d/wakeup), in that it looks as if pm-suspend will never get called if there's no scheduled recording, so the machine just endlessly reboots every 2 minutes.

---

### Post by radnor on 2010-01-04
This is the one last thing I would like to get working.  I am using a Dell GX260 for a BE (occasionally as a FE to schedule something - but  have a DESKTOP lockup problem on this system - so that's why it is a BE only).

One thing I noticed on the RTC Alarm on this system is it is either disabled, daily, or (I think) weekdays.  BIOS is at version A05.  A09 is out.  May flash it to make it current.

I can get it to power up (testing before incorporating it into MythWelcome).  Must work on local time VS UTC.  One thing I CANNOT get working is the power off when idle.  I see the countdown from 120 secs to 10, then a restart in the countdown from 120...

A question for someone who is running a BE only....  Will it work?  I would like it to act like my OLD VCR.  Wake up, record, and shutdown (or stay up if in use).  I would like to get away from starting the FE on this system if I can.  Someday, I would like to move it to a remote place in the house.

---

### Post by shazbut on 2010-01-04
Sounds like mythtv doesn't have the permissions to do a shutdown/reboot
Have this running in a terminal:
```
tail -f /var/log/auth
```
When it hits 0 seconds do you get an error in the log?  If so check the sudoers file (see visudo section in the above guide).

---

### Post by radnor on 2010-01-05
```
Jan  5 19:35:24 mythtvbe sudo:   mythtv : TTY=unknown ; PWD=/ ; USER=root ; COMMAND=/bin/sh -c /usr/bin/setwakeup.sh 1262743000

Jan  5 19:35:24 mythtvbe sudo:   mythtv : no tty present and no askpass program specified ; TTY=unknown ; PWD=/ ; USER=root ; COMMAND=/usr/bin/mythshutdown --shutdown

```

---

### Post by AKADAP on 2010-01-05
> **ozite said:**
> 

Proceed to general>Shutdown/Wakeup Options
startup command: blank
untick Block shutdown before client connected
Set idle shutdown timeout (secs): 120
Set Max. wait for recordings (min): 15
Set Startup before rec (secs): 200
Set Wakeup time format: time_t
Set Command to set Wakeup Time: sudo sh -c "/usr/bin/setwakeup.sh $time"
Set Server Halt command: sudo -H mythshutdown --shutdown
Set pre shutdown check-command: mythshutdown --check


Two things to point out:

The "Set Startup before rec" time needs to be longer than it takes for your system to do a disk check if you still have that enabled, otherwise you will miss the beginning of a recording every time your system does a disk check.

I believe that mythshutdown is a leftover (read that as obsolete) from an old method of doing things.
I believe these should work. (I may be wrong since I don't use mythwelcome, but I am certain if you are not using mythwelcome that these will work)
Set Server Halt command: sudo shutdown -h now
Set pre shutdown check-command: (leave blank)

---

### Post by radnor on 2010-01-05
> **AKADAP said:**
> I believe that mythshutdown is a leftover (read that as obsolete) from an old method of doing things

What do you do or use?  I'm on 9.10 and looking for a way to NOT have this thing run when not needed,

Mythwelcome is not a make or break for me.  I'm willing to use whatever will work.

Also, I'm using this as a BE only.  Dont know if that changes things or not.

---

### Post by radnor on 2010-01-06
I'd like to say **THANK YOU** to everyone how posted here.  You helped me alot!

I commented out MythWelcome and rebooted.  Then setup a recording for 0000 (the weather channel - TWC) for 5 minutes.  This morning I started my RFE and did a WOL to the BE.  After BE was up, I watched the 5 minute clip. Great it worked!  Shutdown the RFE, BE shuts down about 2 minutes after that.

Restarted the BE, loaded up the FE set 2 recordings for 1200 and 1800.  Again 5 minute clips of TWC.  BE shutdown 2 minutes after FE closed.  (I LIKE THIS!!!)

I have it wake up 300 seconds before the next scheduled recording, so at 1755, I want to see if it starts up.  I have it at 300 in case if it needs to check the disk at startup.

[COLOR="Red"]I have several questions that follow:[/COLOR]

If I use a PS/3 as a FE, will the BE shutdown while in use?  I do not know what is used to determine the system(s) are connected to the BE.

Anyone know how long the BE will run if you power up and do NOTHING else? 

In the BIOS, I have it set to start daily at 0355 for SD updates at 0400 VIA ROOTs crontab.  When the BE shutsdown due to no activity, is it OVERRIDING the 0355 wakeup for the next scheduled recording???

If the next scheduled recording overrides the BIOS 0355 wakeup call and I power up manually to update SD info (or just surf) will the BE just power down thinking no activity on the BE?  Will it "see" a terminal window is open or firefox is running and postpone the shutdown?

Again, thank you everyone for the help!!!  :popcorn:

---

### Post by AKADAP on 2010-01-06
> **radnor said:**
> What do you do or use?  I'm on 9.10 and looking for a way to NOT have this thing run when not needed,

Mythwelcome is not a make or break for me.  I'm willing to use whatever will work.

Also, I'm using this as a BE only.  Dont know if that changes things or not.

Have a look at the wiki [http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup) and find the "desktop users" section.
This setup allows you to use the computer as a desktop.
The additional script prevents MythTV from shutting down the computer if a user is logged in.
If you use this setup, you must remember to always log out, never shut down your computer. MythTV will shut your computer down for you when it has nothing to do.

---

### Post by AKADAP on 2010-01-06
> **radnor said:**
> I'd like to say **THANK YOU** to everyone how posted here.  You helped me alot!

I commented out MythWelcome and rebooted.  Then setup a recording for 0000 (the weather channel - TWC) for 5 minutes.  This morning I started my RFE and did a WOL to the BE.  After BE was up, I watched the 5 minute clip. Great it worked!  Shutdown the RFE, BE shuts down about 2 minutes after that.

Restarted the BE, loaded up the FE set 2 recordings for 1200 and 1800.  Again 5 minute clips of TWC.  BE shutdown 2 minutes after FE closed.  (I LIKE THIS!!!)

I have it wake up 300 seconds before the next scheduled recording, so at 1755, I want to see if it starts up.  I have it at 300 in case if it needs to check the disk at startup.

[COLOR="Red"]I have several questions that follow:[/COLOR]

If I use a PS/3 as a FE, will the BE shutdown while in use?  I do not know what is used to determine the system(s) are connected to the BE.

Yes, the backend will shut down the computer, only MythTV front ends will keep it from shutting down.
> 

Anyone know how long the BE will run if you power up and do NOTHING else? 


Exactly how long you told it to.
> 
In the BIOS, I have it set to start daily at 0355 for SD updates at 0400 VIA ROOTs crontab.  When the BE shutsdown due to no activity, is it OVERRIDING the 0355 wakeup for the next scheduled recording???

I believe there is only one wake up timer, so yes, whoever writes that timer last determines when it wakes up. This will be a problem until someone writes a generalized solution for waking the computer for scheduled events.
> 

If the next scheduled recording overrides the BIOS 0355 wakeup call and I power up manually to update SD info (or just surf) will the BE just power down thinking no activity on the BE?  Will it "see" a terminal window is open or firefox is running and postpone the shutdown?

Yes, the backend does not care if you are using the computer for something else, it will shut down.
There is a fix for this, See the wiki I linked in my previous post.
> 
Again, thank you everyone for the help!!!  :popcorn:

---

### Post by Stray Wolf on 2010-01-06
You guys seem really knowledgeable so I hope you can help. I'm nearly computer illiterate and by shear dumb luck have made it this far.  I should have known MythTV was beyond me.  The short of it is I downloaded through Gnome, followed the prompts, obviously not accurately, and need to copy some files from my hard drive to an external HDD using the LiveCD.  I'm using the LiveCD because my drive is trashed.  I can see the files I want to copy to my passport but I don't have permission do to so...damn I'm sorry about being convoluded.

---

### Post by JRoque250 on 2010-01-07
Hi and happy new year.

Precede your copy command with 'sudo' and enter your password when prompted. Something like this: 

```
sudo cp from-here to-there
```Back to topic:
Radnor, without fancy scripting so you can use more than one scheduler to set your BIOS, an alternative is to WOL your backend from another PC/device. A router running DD-WRT might be able to do this via a cron job, for example. Or perhaps you can set the backend to record a second or two of a show a couple of minutes before your other job needs to run. Then set the recorded show to expire immediately. 

I use pm-suspend instead of shutdown so the backend starts quicker, among other things. This has worked or not depending on the backend build I run. Right now I can get it to suspend to RAM fine but the backend is not waking up properly and I can't watch (or record) live TV until I reboot. I can play recorded material fine so it's something with the tuners (HVR2250 and HDHomeRun). There's nothing obvious in the logs as they show the suspend/restore steps fine. Anyone else experiencing this problem?

Regards,
JR

---

### Post by JRoque250 on 2010-01-07
UPDATE: My suspend/resume problem is related to the HVR-2250 tuner card driver:

```
DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
 eno: Device or resource busy (16)
```It fails to resume after suspending and drags the backend with it. This seems similar: [https://bugs.launchpad.net/mythbuntu/+bug/495429](https://bugs.launchpad.net/mythbuntu/+bug/495429)

Long live the HDHomeRun!

JR

---

### Post by radnor on 2010-01-07
I may use /usr/bin/checklogin.sh from the link you provided.  I'll have to find the auto login and change it so it does not auto logon.  When I want to use a PS/3, i'll login to the BE.  That will work.

Last night I was tinkering with it.  Used mythshutdown --check.  Did not shut down, but I think it was because I never logged out.  Not sure if it acts like the checklogin.  Will have to find more info out about it today.

I did not look to see if my 0400 crontab job ran this morning.  I'm sure it did not since the next scheduled recording is at 2100.

A way of setting a time to do get updated SD info would be great!  I dont need 14 days worth but it would be nice to have it wake , grab data, and go back to sleep...

---

### Post by SiHa on 2010-01-07
I have a script that does something very similar to what you are after.

I want my backend awake @ 07:00 every day (for the missus!). So I modified the Mythwakeset script thus:

```
Check when the next wakeup is due. 
If next wakeup is before the next 07:00, leave as-is.
Else
Set next wakeup to 07:00.
```
Assuming your backend will go idle and shutdown again after the cronjob, the above could be modified to wake @ 03:55 instead. 

If it will be of any use, I can post it here, when I'm back home.

Edit: The above is on my old 8.04 install (which I have backed up). I haven't set this up with 9.10 yet, I might try the WOL thing from the RFE instead of a daily 07:00 wake. I see you've already done this. One question, does the frontend display a nice 'Waiting for backend' after sending the magic packet?

---

### Post by radnor on 2010-01-07
SiHa,

Sure, that will be fine.  I can change my cron job to 0705.  I give the extra 5 "if" it does a disk check at power up.  The BE should shutdown.  What I am doing in the script is kill the BE then a mythfilldatabase.  I believe the BE will be started after this runs.

Well, when boot my RFE, I do not auto load the FE.  I go to the desktop where I have a script to send the magic packet.  Then I wait to load the FE.  I'm sure I could put it in the RFE when it loads.  Never tried.

---

### Post by SiHa on 2010-01-07
Here's the script:```
#!/bin/bash

# mythwakeset
#
# set mythtv wake-up time with UTC-adjusted time
#

# temp file for working with time
temp_stamp=/home/mythtv/timestamp

# store the wake time passed from mythbackend
echo $1\ $2 > $temp_stamp

#
# Addition to reset MythTV wakeup time to the next 0700hrs - 'tomorrow' 
# if earlier than the next scheduled recording.
# Uses 'date +%s' for calculations. %s = seconds since epoch, much simpler to
# do comparisons with a number.
# SiHa 2008 
#

now=`date +%H`                                 # %H = Hour in 24H clock.
if [[ $now -lt 7 ]] ; then
	tomorrow=`date +%c -d "0700"`          # after midnight, so set to 0700 today
else
	tomorrow=`date +%c -d "+1 day 0700"`   # before midnight set to 0700 tomorrow
fi

nextrectime=`date +%s -f "$temp_stamp"`

# if 0700 tomorrow is earlier than next scheduled recording then change it to 0700
# otherwise leave unchanged

if [[ `date +%s -d "$tomorrow"` -lt $nextrectime ]] ; then
	echo $tomorrow > $temp_stamp
fi

# End of addition.
# Read the date in *locale* time format and tag the time-zone info to the wake time
localeadd=$(/bin/date -f $temp_stamp +%F\ %T\ %z)
echo $localeadd > $temp_stamp

# adjust this to UTC and store the final wake time
utcadj=$(/bin/date -u -f $temp_stamp +%s)

# set the alarm

echo 0 > /sys/class/rtc/rtc0/wakealarm           #this clears your alarm.
echo $utcadj > /sys/class/rtc/rtc0/wakealarm     #this writes your alarm

```

Running to set next 'recording' as 06:55 tomorrow, and 07:05 tomorrow, respectively:

```
mythbox@mythbox-desktop:/usr/bin$ sudo mythwakeset 2010-01-08 06:55
mythbox@mythbox-desktop:/usr/bin$ cat /proc/driver/rtc
rtc_time	: 20:34:08
rtc_date	: 2010-01-07
alrm_time	: 06:55:00
alrm_date	: 2010-01-08
alarm_IRQ	: yes
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: no
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay
mythbox@mythbox-desktop:/usr/bin$ sudo mythwakeset 2010-01-08 07:05
mythbox@mythbox-desktop:/usr/bin$ cat /proc/driver/rtc
rtc_time	: 20:34:34
rtc_date	: 2010-01-07
alrm_time	: 07:00:00
alrm_date	: 2010-01-08
alarm_IRQ	: yes
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: no
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay

```

You will see that the alarm is set to the earlier of the recording time passed to the script, or 07:00. Could just as easily be 04:00.

> 
Well, when boot my RFE, I do not auto load the FE. I go to the desktop where I have a script to send the magic packet. Then I wait to load the FE. I'm sure I could put it in the RFE when it loads. Never tried.

Ah, OK. I thought you were using the functionality in the FE to wake the backend server. Never mind, I'll give it a try myself.

Edit: BTW, all guides I've seen have as the first step, Disable BIOS 'Wake from RTC'. Not sure they work well together.

---

### Post by AKADAP on 2010-01-07
> **radnor said:**
> I may use /usr/bin/checklogin.sh from the link you provided.  I'll have to find the auto login and change it so it does not auto logon.  When I want to use a PS/3, i'll login to the BE.  That will work.

That is exactly how I am using it.

> 
Last night I was tinkering with it.  Used mythshutdown --check.  Did not shut down, but I think it was because I never logged out.  Not sure if it acts like the checklogin.  Will have to find more info out about it today.

I did not look to see if my 0400 crontab job ran this morning.  I'm sure it did not since the next scheduled recording is at 2100.

A way of setting a time to do get updated SD info would be great!  I dont need 14 days worth but it would be nice to have it wake , grab data, and go back to sleep...

Mythshutdown is obsolete and redundant don't use it. Everything it used to do is done by the myth backend.
Besides mythshutdown --check doesn't do a shutdown anyway.

---

### Post by radnor on 2010-01-07
> **SiHa said:**
> 
Ah, OK. I thought you were using the functionality in the FE to wake the backend server. Never mind, I'll give it a try myself.

I added to my RFE the magic packet script.  If starts the BE fine.  One problem I did encounter was, my NFS mounts were not there.  What I was doing was manually sending the WOL and running "sudo mount -a" to connect the NFS mounts.

---

### Post by radnor on 2010-01-07
Well, we'll see how it goes.  

SiHa, put in your script for a 0700 wakeup.  Roots' crontab is set for 0703.  Thank you by the way.

Added the check login script.  It worked great.  Logged in used BE for a while, no shutdown - GOOD.  Logged out and down she goes.  Just killing a few minutes now, have a recording going and want to make sure BE does not fall asleep during it.
[COLOR="Red"]Well I did something, this is not working.  Will play with it later.[/COLOR]

Tomorrow morning I'll be near the BE, so I will see if it wakes up at 0700.

BE did not fall asleep while recording.  I'm very happy with the setup.

The ONLY thing I need to do now is on the RFE send a "sudo mount -a" to reread the fstab and mount the NFS.

Thank you everyone!!!

---

### Post by SiHa on 2010-01-08
> **radnor said:**
> I added to my RFE the magic packet script.  If starts the BE fine.  One problem I did encounter was, my NFS mounts were not there.  What I was doing was manually sending the WOL and running "sudo mount -a" to connect the NFS mounts.

Good point, thanks, hadn't thought of that. It'll be easy enough to script that bit, I think.

---

### Post by Neon Dusk on 2010-01-08
> **AKADAP said:**
> 
Mythshutdown is obsolete and redundant don't use it. Everything it used to do is done by the myth backend.
Besides mythshutdown --check doesn't do a shutdown anyway.

Can you please provide a reference or link that indicates mythshutdown is obsolete and shouldn't be used?

For a dedicated be/fe system configured to automatically start the frontend then, as far as I can see, mythshutdown combined with mythwelcome is the only way to get ACPI wakeup properly configured with the following features :-

[LIST]
[*]The system wont't shutdown if the fe, or a remote fe, is connected.
[*]When starting up for a scheduled recording the frontend won't load, only mythwelcome, therefore it will shutdown after the recording is completed.
[/LIST]

---

### Post by radnor on 2010-01-08
> **SiHa said:**
> Good point, thanks, hadn't thought of that. It'll be easy enough to script that bit, I think.

I think I have the script, just one thing I DO NOT have.  Mount will require the ROOT pw.  How do you pass to (or include with) your script the pw for the ROOT account?  VISUDO?  Other?

---

### Post by SiHa on 2010-01-08
Visudo is the only way, as far as I know. The good news is that in 9.10 the editor defaults to nano instead of vim.```
sudo visudo
``` Add to the %mythtv line (which I assume you already have as you've got this far).```
%mythtv ALL = NOPASSWD: **stuff already here**, /bin/mount
```

And, (as I'm sure you know, but just in case) the script will need the full line, including the sudo.```
sudo mount -a
```

Also, just one thing. It is quite easy to mess up your sudoers file. as I've found out to my cost. Once it's messed you can't 'sudo' to fix it! As a precaution, because I'm paranoid, I always backup first:```
sudo cp /etc/sudoers /etc/sudoers.bak
```Then if it does get screwed, you can drop to a root shell from the grub menu and restore the backup.

---

### Post by AKADAP on 2010-01-09
> **Neon Dusk said:**
> Can you please provide a reference or link that indicates mythshutdown is obsolete and shouldn't be used?

No I can't. Because I could not find any useful information on it when I was attempting to use it last year. What I found was that the most recent version I could find was much older than any other part of MythTV, and it seemed to be duplicating what the mythTV backend already did.
> 

For a dedicated be/fe system configured to automatically start the frontend then, as far as I can see, mythshutdown combined with mythwelcome is the only way to get ACPI wakeup properly configured with the following features :-

[LIST]
[*]The system wont't shutdown if the fe, or a remote fe, is connected.
[*]When starting up for a scheduled recording the frontend won't load, only mythwelcome, therefore it will shutdown after the recording is completed.
[/LIST]

My system is a fe/be system that works fine without mythshutdown or mythwelcome. My system does not autologin. I have it set up such that it will not shut down if someone is logged into the computer, therefore the only think I can't confirm is working without mythshutdown is the remote fe since I do not have a remote fe.
My system is not dedicated solely to MythTV, so Mythwelcome is not appropriate for it.

edit:
I went back and found the relevant thread where I determined that mythshutdown was obsolete:
[http://ubuntuforums.org/showthread.php?t=1069317](http://ubuntuforums.org/showthread.php?t=1069317)
The most important posts are #25, #30, #36, #41, #45, #51 and #52.

---

### Post by Neon Dusk on 2010-01-09
> **AKADAP said:**
> No I can't. Because I could not find any useful information on it when I was attempting to use it last year. What I found was that the most recent version I could find was much older than any other part of MythTV, and it seemed to be duplicating what the mythTV backend already did.


Looking at [http://svn.mythtv.org/trac/log/trunk/mythtv/programs/mythshutdown/main.cpp](http://svn.mythtv.org/trac/log/trunk/mythtv/programs/mythshutdown/main.cpp) mythshutdown it's still in active development

> **AKADAP said:**
> 
My system is a fe/be system that works fine without mythshutdown or mythwelcome. My system does not autologin....
My system is not dedicated solely to MythTV, so Mythwelcome is not appropriate for it.

For a fe/be system that not dedicated to myth then I agree that mythwelcome/mythshutdown is not suitable. However I imagine that quite a few people do have a dedicated system that they would like configured with ACPI wakeup - in these cases I think mythwelcome combined with mythshutdown is the best solution.

Edit:
> **AKADAP said:**
> 
I went back and found the relevant thread where I determined that mythshutdown was obsolete:
[http://ubuntuforums.org/showthread.php?t=1069317](http://ubuntuforums.org/showthread.php?t=1069317)
The most important posts are #25, #30, #36, #41, #45, #51 and #52.

Which is an incorrect assumption on your part. mythshutdown is the helper program for mythwelcome and both are still in development

I think part of your problems on that thread is that mythwelcome/mythshutdown was originally designed to do a nvram-wakeup (different from an ACPI wakeup). However the configuration* on the first post of this 'MythWelcome /MythTV' thread shows how to set-up ACPI wakeup on a mythtv system that uses mythwelcome. 

* This configuration won't allow mythwelcome to detect if the start-up is manual or due to a scheduled recording, which is why the original poster has disabled 'Automatically start MythFrontend' in mythwelcome, a solution can be found [thread=1353286]here[/thread]

I've updated the [MythTV ACPI Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup) to include the Mythwelcome/MythShutdown info.

---

### Post by AKADAP on 2010-01-10
> **Neon Dusk said:**
> Looking at [http://svn.mythtv.org/trac/log/trunk/mythtv/programs/mythshutdown/main.cpp](http://svn.mythtv.org/trac/log/trunk/mythtv/programs/mythshutdown/main.cpp) mythshutdown it's still in active development



For a fe/be system that not dedicated to myth then I agree that mythwelcome/mythshutdown is not suitable. However I imagine that quite a few people do have a dedicated system that they would like configured with ACPI wakeup - in these cases I think mythwelcome combined with mythshutdown is the best solution.

Edit:

Which is an incorrect assumption on your part. mythshutdown is the helper program for mythwelcome and both are still in development

I think part of your problems on that thread is that mythwelcome/mythshutdown was originally designed to do a nvram-wakeup (different from an ACPI wakeup). However the configuration* on the first post of this 'MythWelcome /MythTV' thread shows how to set-up ACPI wakeup on a mythtv system that uses mythwelcome. 

* This configuration won't allow mythwelcome to detect if the start-up is manual or due to a scheduled recording, which is why the original poster has disabled 'Automatically start MythFrontend' in mythwelcome, a solution can be found [thread=1353286]here[/thread]

I've updated the [MythTV ACPI Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup) to include the Mythwelcome/MythShutdown info.

Is mythshutdown still attempting to run a non-existent script? This was the primary reason I assumed it was obsolete.

---

### Post by Neon Dusk on 2010-01-10
mythshutdown --shutdown will run the 'Command to Set Wakeup Time' script configured in mythwelcome --setup (think the default is /usr/bin/nvram-wakeup but this can be changed in the mythwelcome setup)

---

### Post by radnor on 2010-01-17
> **SiHa said:**
> I have a script that does something very similar to what you are after.

I want my backend awake @ 07:00 every day (for the missus!). So I modified the Mythwakeset script thus:

```
Check when the next wakeup is due. 
If next wakeup is before the next 07:00, leave as-is.
Else
Set next wakeup to 07:00.
```

OK, I have a question...

Now LOCAL time is: 00:08
UTC is: 05:08

Computer is set for UTC.
If I create a file, it has a LOCAL time stamp (fine).
Wake up time in the script is adjusted for UTC (OK too).

Computer is set to wake daily to run a cron job at 0700AM LOCAL (1200 UTC).  

The cron job.... Do I set it for 0705 LOCAL or 1205 (UTC)???  The delay of 5 minutes is if the computer needs to scan the disks, etc.  I have it set for 05 12 * * * now.  

Will know in the AM if I was right or not.

---

### Post by SiHa on 2010-01-17
I think you'll find it should have been local. On my system at least, cron's time is local.

---

### Post by radnor on 2010-01-17
Been pulling my hair out all day on this. Could not get it to wake up for recordings. Finally went to the backend log and found this:

```
2010-01-17 18:07:39.749 Unable to connect to database!
2010-01-17 18:07:39.792 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.so
ck' (2)

..........................................................................
2010-01-17 18:07:42.657 UPnPautoconf() - No UPnP backends found
2010-01-17 18:07:42.725 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-01-17 18:07:42.969 Deleting UPnP client...
2010-01-17 18:07:43.551 Failed to init MythContext, exiting.
2010-01-17 18:07:44.233 mythbackend version: branches/release-0-22-fixes [225
94] www.mythtv.org

```

---

### Post by regeya on 2010-01-29
Mine will shut down if I power it up manually and there's no pending recordings, and will power itself back up to do a recording.  I have my machine set to transcode everything, and mythfrontend always reports that MythTV is busy transcoding.  If I start up the frontend when I know it's idle, it will have the last two transcode jobs listed as finished in the System Status screen, but apparently mythwelcome never gets the message that they're finished...

On this same machine I had MythTV 0.22 installed, running, and shutting down and restarting correctly on an Arch install.  Is it 0.23 related?  Anyone other than me have this problem?  Anyone managed to come up with a fix?  I've been bashing my head on the desk over this one...

EDIT:  I see now that I didn't search quite well enough.  Apparently there's a bug that leaves mythtranscode hanging, possibly related to the Delete files slowly option.  There's an ugly hack to work around this on this bug report:  [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/481104]("https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/481104")

---

### Post by Point &amp; Click on 2010-03-03
I originally had a problem with "mythshutdown now" and when I checked MythShutdown it doesn't accept "now" as a parameter, (just run it from the command line, and it lists what does work)

So I changed "Set Server Halt command" to "mythshutdown --safeshutdown", but I'm now where Radnor was:

> **radnor said:**
> ```
Jan  5 19:35:24 mythtvbe sudo:   mythtv : TTY=unknown ; PWD=/ ; USER=root ; COMMAND=/bin/sh -c /usr/bin/setwakeup.sh 1262743000

Jan  5 19:35:24 mythtvbe sudo:   mythtv : no tty present and no askpass program specified ; TTY=unknown ; PWD=/ ; USER=root ; COMMAND=/usr/bin/mythshutdown --shutdown

```


I know it's a month ago - but how do I get past this? ;)

The reason I'm asking is that I'm following this thread to setup a combined FE / BE and my setup won't shutdown and Myth Welcome just keeps looping.

Are you using MythShutdown now, or just sudo shutdown?

Thanks

---

### Post by Neon Dusk on 2010-03-03
Have you tried using the settings in the [MythTV ACPI Wakep wiki](http://www.mythtv.org/wiki/ACPI_Wakeup) -> Integrate Into mythTV -> Mythwelcome users?

---

### Post by Point &amp; Click on 2010-03-04
Yep, that's where I started.... then when that wasn't working quite as well, I found this thread and thought it was more specific to the situation I was looking at...

I've just checked the logs from another PC that's setup to ping my Media (Myth) PC and it looks like I've finally cracked it

I found out by using tail -f /var/log/auth.log and noticing that the  command was being run as root - when I ran the command in the logfile in  terminal, bam!, machine shuts down :p

So, I knew I was on to something.

Basically, due to all the editing of the settings, I'd left "sudo -H" before "mythshutdown --safeshutdown", removing the "sudo -H" cured it.

Much higher WAF now ;)

Plus I'm saving on some money keeping an idle pc running for no reason.

So, thanks all.

---

### Post by Point &amp; Click on 2010-03-04
Just another thought - I've also changed the Frontend settings 

Advanced/Setup -> Setup -> General -> Program Exit settings

And changed the halt command from ```
halt
``` to ```
/usr/bin/mythshutdown --safeshutdown
```- I've yet to test this (as I'm writing this entry on the same machine! ;))

(My exit menu setting is "Show quit, reboot and shutdown")

Not sure if anyone else has any comments on these settings??

Cheers

---

### Post by sbradley07 on 2010-04-29
Sorry to resurrect an old thread, but this seemed to be the best/most recent thread to post my issue.

I have followed all of the guidance in this thread and the ACPI Wakeup wiki page.  My issue is that my PC is not waking up for scheduled recordings.  
The issue is that **alrm_time=****-**-****, which I gotta believe would keep the PC from waking up.

Here are some more details:
- Running Mythbuntu 9.10, 32 bit 
- The manual test to shutdown/wakeup works fine. 
- The PC shuts down fine
- Running combined frontend/backend

I tried manually running setwakeup.sh and was getting similar but slightly different results.  Not sure I am formatting the command line correctly.  For the manual test, I entered:

sudo setwakeup.sh "2010-04-30 10:50:00"

and the output from "cat /proc/driver/rtc" is: 

rtc_time	: 19:15:34
rtc_date	: 2010-04-29
alrm_time	: 19:20:27
alrm_date	: ****-**-29

So slightly different than what I see when Myth shuts itself down, but still not right.  If that's not a valid format to test, can someone post a proper one.  Here's my script:

```
#!/bin/sh
#$1 is the first argument to the script. It is the time in seconds since 1970
#this is defined in mythtv-setup with the time_t argument

echo 0 > /sys/class/rtc/rtc0/wakealarm      #this clears your alarm.
echo $1 > /sys/class/rtc/rtc0/wakealarm     #this writes your alarm
```

Anyone have any idea what I might be doing wrong?

---

### Post by Neon Dusk on 2010-04-29
Is your bios time in localtime or UTC?

You should be able to tell by running
```

cat /proc/driver/rtc

```

setwakeup.sh expects to be passed an epoch time. e.g. Fri, 23 Apr 2010 20:50:16 GMT would be 1272055816

You can add some extra commands to you setwakeup.sh script to see whats going on. Look in /var/log/mythtv/mythbackup.log after the backend has been restarted.

```

#!/bin/sh
#$1 is the first argument to the script. It is the time in seconds since 1970
#this is defined in mythtv-setup with the time_t argument
LOG=/var/log/mythtv/mythbackend.log

echo "Passed time: $1" >> $LOG
echo "Running $0 to set the wakeup time to $SECS" >> $LOG

echo 0 > /sys/class/rtc/rtc0/wakealarm      #this clears your alarm.
echo $1 > /sys/class/rtc/rtc0/wakealarm     #this writes your alarm

```

---

### Post by sbradley07 on 2010-04-29
I was pretty sure my BIOS was UTC time based on the documentation, but I'm not 100%.  I will make the script changes and post the results in a bit.  For now, here is the output from rtc:  

```
rtc_time	: 21:51:57
rtc_date	: 2010-04-29
alrm_time	: 19:20:27
alrm_date	: ****-**-29
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

Here's the section of the log related to the shutdown/wakeup:

> 2010-04-29 18:38:26.678 CheckShutdownServer returned - OK to shutdown
2010-04-29 18:38:26.729 Running the command to set the next scheduled wakeup time :-
						sudo sh -c "/usr/bin/setwakeup.sh 1272624600"
Passed time: 1272624600
Running /usr/bin/setwakeup.sh to set the wakeup time to 
2010-04-29 18:38:26.820 Running the command to shutdown this computer :-
						mythshutdown --shutdown

---

### Post by Neon Dusk on 2010-04-29
It does appear that your bios is using UTC - which should make things easier.

---

### Post by Neon Dusk on 2010-04-30
Sorry, I missed a command and there was a typo in the updated setwakeup.sh script. Can you try
```

#!/bin/sh
#$1 is the first argument to the script. It is the time in seconds since 1970
#this is defined in mythtv-setup with the time_t argument
LOG=/var/log/mythtv/mythbackend.log

echo "Passed time: $1" >> $LOG
echo "Running $0 to set the wakeup time to $1" >> $LOG

echo 0 > /sys/class/rtc/rtc0/wakealarm      #this clears your alarm.
echo $1 > /sys/class/rtc/rtc0/wakealarm     #this writes your alarm
cat /proc/driver/rtc >> $LOG

```

Are you using mythwelcome? I see in your log the shutdown command is 'mythshutdown --shutdown' (you would normally use mythshutdown with mythwelcome).

Can you post your mythbackend Shutdown/Wakeup Options (mythtv-setup) & MythShutdown/MythWelcome Settings (mythwelcome --setup or F11 in mythwelcome)

---

### Post by sbradley07 on 2010-04-30
I made the changes.  Here is what the log shows:
```
2010-04-30 10:41:11.865 CheckShutdownServer returned - OK to shutdown
2010-04-30 10:41:11.907 Running the command to set the next scheduled wakeup time :-
						sudo mythshutdown --setwakeup 2010-05-01T06:50:00
2010-04-30 10:41:12.020 Running the command to shutdown this computer :-
						sudo mythshutdown --shutdown
Passed time: 1272711000
Running /usr/bin/setwakeup.sh to set the wakeup time to 1272711000
rtc_time	: 14:41:12
rtc_date	: 2010-04-30
alrm_time	: 10:50:00
alrm_date	: 2010-05-01
alarm_IRQ	: yes
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: no
DST_enable	: no
periodic_freq	: 1024
batt_status	: dead
```

From that, it looks like the alrm_date is correct.  However, when I booted the machine back up, I see:
```

rtc_time	: 14:58:49
rtc_date	: 2010-04-30
alrm_time	: 10:50:00
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

Is that normal?  I haven't re-tested a wakeup for a recording, because it always looked like the date was wrong.  Maybe it's actually working now.  I will test.

---

### Post by sbradley07 on 2010-04-30
Well, I have to apologize...as it is working now!  I was mislead by the ***-**-** date and assumed that it was wrong.  Somewhere in the various config changes I made, I made the correct ones.  I just ran a test, and the PC woke up properly.

It appears that the date gets saved correctly (as seen in the log I posted upthread), but it gets wiped when the PC wakes up.  Go figure!

Thanks for the help!

---

### Post by JasonEde on 2010-05-08
In 9.10 I tried using the wakeup time period in mythwelcome --setup to make sure the box was on to do its xmltv update during the night. However, with that set then it seems to ignore the program settings and just set the times for the wakeup period.

Is there a way to get it to both have that programmed hour wakeup period and normal program recording periods?

---

### Post by AKADAP on 2010-05-08
> **JasonEde said:**
> In 9.10 I tried using the wakeup time period in mythwelcome --setup to make sure the box was on to do its xmltv update during the night. However, with that set then it seems to ignore the program settings and just set the times for the wakeup period.

Is there a way to get it to both have that programmed hour wakeup period and normal program recording periods?

See this: [http://www.mythtv.org/wiki/Using_ACPI_%26_MythTV_to_run_other_applications](http://www.mythtv.org/wiki/Using_ACPI_%26_MythTV_to_run_other_applications)

This does not work with mythwelcome. It is intended for those who use their system as both a desktop and a mythTV frontend/backened. Its implementation should be a good starting point.

---

### Post by Neon Dusk on 2010-05-08
@JasonEde

Can you post more details of your configuration?

Is mythwelcome set to automatically start

What daily Wakeup/Shutdown periods are set
Can you post your mythbackend Shutdown/Wakeup Options (mythtv-setup) & MythShutdown/MythWelcome Settings (mythwelcome --setup or F11 in mythwelcome)

---

### Post by JasonEde on 2010-05-10
Mythwelcome starts automatically and doesn't start mythfrontend automatically on startup.

I had the Period 1 start time set to 2am and the period 1 end time set to 3am.

On saturday when I was testing this. I had it setup to record Dr Who on bbc1 at 18:00. I'd set it up to start at 17:50 and then I let mythwelcome set the time to bootup and the machine then shutdown with the time set correctly to 17:50.

I then powered the machine back up and set the time periods to those above. When I went back into mythwelcome and left the machine idle it still said the next recording was at 18:00 the same day, but then when it shut itself down the startup time was set to 2am the next morning and not 17:50 that day. Then I turned off the wakeup period and the next time the machine shut itself down the wakeup time was set correctly.

It seems like the periods in mythwelcome override those set in any programmes as opposed to being in addition to.

My EPG normally updates itself between 2am and 3am which is why I want the machine to be on then. Also it won't interfere with any recordings at that time.

Oh the settings I have are those recommended in the 1st page of this thread for backend...

Also is mythfilldatabase run if the frontend isn't running? i.e. as the settings for it are in the frontend is it controlled from there or from the backend? Thats not a huge issue as could always schedule a cron job for when the machine is on in middle of the night.

---

### Post by Neon Dusk on 2010-05-10
That's not the results I get.

The wakeup time is correctly set to either the next scheduled program or the next daily wakeup time (whichever is first). You can see that the logic for this in the shutdown() method of [mythshutdown](http://svn.mythtv.org/trac/browser/branches/release-0-22-fixes/mythtv/programs/mythshutdown/main.cpp)

> 
Oh the settings I have are those recommended in the 1st page of this thread for backend..

These settings are incorrect, the backend will never detect if it's a user or scheduled start with them. I recommend that you use settings in the mythwelcome section of the [ACPI Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup) wiki.

([s]However it still doesn't explain the results you're seeing. You could try the extra logging from the steps I posted [thread=1377610]here[/thread][/s])

Edit: Think this does explain explain the results you're seeing. If you're using Daily wake-up times and are not calling 'mythshutdown --setwakeup $time' you might get those results.

---

### Post by JasonEde on 2010-05-13
I modifed the shutdown to  mythtv wiki and it does seem to have solved the problem thanks. The box is starting up and shutting down as required.

---

### Post by JEStone on 2011-01-28
> **Point & Click said:**
> Yep, that's where I started.... then when that wasn't working quite as well, I found this thread and thought it was more specific to the situation I was looking at...

I've just checked the logs from another PC that's setup to ping my Media (Myth) PC and it looks like I've finally cracked it

I found out by using tail -f /var/log/auth.log and noticing that the  command was being run as root - when I ran the command in the logfile in  terminal, bam!, machine shuts down :p

So, I knew I was on to something.

Basically, due to all the editing of the settings, I'd left "sudo -H" before "mythshutdown --safeshutdown", removing the "sudo -H" cured it.

Much higher WAF now ;)

Plus I'm saving on some money keeping an idle pc running for no reason.

So, thanks all.

Worked for me, removed the "sudo -H". 

The "-H" flag for shutdown is there any reason we should have it? I'm not completely sure what that flag is for. I figure its something to do with halt.

Any rate everything seems to work now.

thanks

---

