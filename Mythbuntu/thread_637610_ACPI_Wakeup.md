---
title: "ACPI Wakeup"
date: 2007-12-11
forum: Mythbuntu
---

### Post by Glenhawk on 2007-12-11
I have followed the steps in the guide...
[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)

...and I can get right down to "If it did wake, CONGRATULATIONS! It's all downhill from here..."
Now my computer DID wake but after that I get stuck.
I follow all the instructions to the letter and by the next test "Another Test" where you set the acpi time to "2007-12-12 12:12:12" and then run mythbackend to see if the time is altered. Surprise surprise, it didn't work.
I went back and checked everything (I had mostly copied and pasted so my syntax shouldn't be wrong) and I thought maybe the visudo step wasn't working becasue I didn't seem to be passing a time from mythtv to acpi.
After much research on visudo, I have confirmed that it is doing what it should but I still am not passing any time info from mythtv.

I tried "echo $time > /home/glen/my.log" in place of the wake command and it created an empty log file but I don't even know if that is a valid command (I picked it up from a forum post *and I didn't even know where it had been* ;-))

SO, basically I would like to test whether the $time variable is being set and I am not sure how. 

I have set my time format to "yyyy-MM-dd hh:mm:ss" with no quotes becasue when I "cat /proc/acpi/alarm" that is the format it is in. Why the captial MM when the rest are lower case? should I have quotation marks around the format?

It is also possible that hwclock.sh has been set wrong but I would like to think not becasue I have gotten past that step and tests had worked. My doubt is becasue my hwclock.sh looks different from the one in the guide...

Their final product after adding ONE line:
>             # Updates the Hardware Clock with the System Clock time.
            # This will *override* any changes made to the Hardware Clock.
            #
            # WARNING: If you disable this, any changes to the system
            #          clock will not be carried across reboots.
            #
            if [ "$HWCLOCKACCESS" != no ]; then
                if [ "$GMT" = "-u" ]; then
                    GMT="--utc"
                fi
                /sbin/hwclock --systohc $GMT $HWCLOCKPARS $BADYEAR

               ** echo "$ACPITIME" > /proc/acpi/alarm && sleep 1 && echo "$ACPITIME" > /proc/acpi/alarm**

                fi
            ;;


My final product after adding the same ONE line:
> 	    # Updates the Hardware Clock with the System Clock time.
	    # This will *override* any changes made to the Hardware Clock.
	    #
	    # WARNING: If you disable this, any changes to the system
	    #          clock will not be carried across reboots.
	    #
	    if [ "$HWCLOCKACCESS" != no ]; then
		log_action_msg "Saving the system clock"
		if [ "$GMT" = "-u" ]; then
		    GMT="--utc"
		fi
		if /sbin/hwclock --systohc $GMT $HWCLOCKPARS $BADYEAR; then
		    verbose_log_action_msg "Hardware Clock updated to `date`"
		**echo "$ACPITIME" > /proc/acpi/alarm && sleep 1 && echo "$ACPITIME" > /proc/acpi/alarm**
		fi
	    else
		verbose_log_action_msg "Not saving System Clock"
	    fi
	    ;;
	show)
	    if [ "$HWCLOCKACCESS" != no ]; then
		/sbin/hwclock --show $GMT $HWCLOCKPARS $BADYEAR
	
	    fi
	    ;;


Any helpful comment would be greatly appreciated,
Thanking you,
Glen

---

### Post by tohc1 on 2007-12-11
If you managed to get the computer to boot your most of the way there.

I'm not sure were you're going wrong but its somewhere in configuring mythtv.

Here my notes on the settings that I used to make wakeup work

In myth-setup

startup command: 		""
idle timeout: 			"30" seconds	
Startup before rec. (secs): 	300
wakeup time format: 		"yyyy-MM-ddThh:mm"
Set wakeuptime command: 	"sudo mythshutdown --setwakeup $time"
halt command: 			"sudo mythshutdown --shutdown"
pre-shutdown command: 		"sudo mythshutdown --check"

Configure mythwelcome.

```
mythwelcome --setup
```

This presents an interface similar to mythtv-setup. Edit the settings according to your configuration. I had:

nvram-wakeup Command: 			sudo your-path-to-wakeup-script 
nvram-wakeup Restart Command: 		blank
Command to reboot: 			sudo shutdown -h now
Command to shutdown: 			sudo shutdown -h now
Command to run Xterm: 			xterm
Command to run to start the Frontend: 	mythfrontend

Disable the time update on shutdown, it sounds like you've done this successfully. I do mine a bit differently using my own similar wakeup script which saves the system time before setting the wakeup alarm.

edit the sudoers file you'll need to make sure that your shutdown script has sudo access

```
>sudo visudo
```

add to groups section
```
%mythtv ALL = NOPASSWD: /sbin/shutdown,/usr/bin/mythshutdown, your-path-to-wakeup-script
```

here's my wakeup script if it helps:
```

#!/bin/bash

# Script to set wakeup time using acpi alarm
# Called from mythwelcome
# first option passed from mythwelcome is --settime second is time since 1970

# save the system clock to hw clock
# if this is done on shutdown it needs to be disabled as it will not wakeup so do   it here first
hwclock --systohc

#for testing
stamp_file=/home/mythtv/timestamp

#convert from stupid time in seconds since 1970
b=$(date -d "1970-01-01 UTC $2 sec" +%F\ %T)

# write the time to a test file
echo $1\ $2\ $b\ >$stamp_file

#write wakeup time to acpi alarm
echo $b>/proc/acpi/alarm
```

Hope this helps,

---

### Post by Glenhawk on 2007-12-12
do you have to use MythWelcome to have the backend shutdown and wakeup? I don't use a frontend on my backend, I have a frontend installed near my TV connected by the LAN.

In your time format, "yyyy-MM-ddThh:mm" what is the T for? Is it to signify a space?

ANYWAY... I am still plugging at it and so I decided to go back to the vanilla guide and try again. At this point it seems to write the ACPI after some time but I am not sure what is triggering it. I will update as progress continues

---

### Post by Glenhawk on 2007-12-12
I am not sure whether this sounds horribly obvious but it only writes the wakeup time after Mythbackend successfully stops itself.

From the guide I had no idea that this was what I should have been focussing on. I am thinking that I was not successfully getting mythbackend to stop and therefore the time was never sent to the ACPI alarm.

The quest continues, I will update as progress continues

---

### Post by Glenhawk on 2007-12-12
It is all so deliciously stupid the way this is unravelling. After my recent epiphany about the time write after mythbackend stop I revisited the settings and realised that this time I had used &#8220;exit 0&#8221; for my &#8220;Pre Shutdown check-command:&#8221; instead of the recommended &#8220;sudo /usr/bin/MythShutdownCheck&#8221;. The reason I was not getting a written time was because I was still logged in! I was still logged in and so MythShutdownCheck was not letting the backend stop and therefore no wakeup time.

I think I am nearly done :-D

---

### Post by m3s3lf on 2008-01-22
> **Glenhawk said:**
> It is all so deliciously stupid the way this is unravelling. After my recent epiphany about the time write after mythbackend stop I revisited the settings and realised that this time I had used &#8220;exit 0&#8221; for my &#8220;Pre Shutdown check-command:&#8221; instead of the recommended &#8220;sudo /usr/bin/MythShutdownCheck&#8221;. The reason I was not getting a written time was because I was still logged in! I was still logged in and so MythShutdownCheck was not letting the backend stop and therefore no wakeup time.

I think I am nearly done :-D


I don't understand... if you *had* been using "exit 0" in place of using MythShutdownCheck, wouldn't it shutdown whether you were logged in or not?  Maybe you mean you *had not* been using "exit 0"? 

 I ask because I'm having the exact same problem.

Thanks!
Billy

---

### Post by m3s3lf on 2008-01-26
My machine is shutting itself down now, but it's setting the wrong wakeup time. :confused:  I can't figure out how it's coming up with time it's coming up with.  My board is on local time, so I don't need an extra script (I believe)... I'm just using the following for my set wakeup time command.
```
sudo sh -c 'echo $time > /proc/acpi/alarm'
```

Did you make any progress Glenhawk?

Thanks,
Billy

---

### Post by volkswagner on 2008-03-25
I am trying to get this set up.  Following this guide also

[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake]("https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake")

I can get my machine to wake if I manually set a wake up time.

I can not get the machine to set a shutdown time.  I am confused with this guide. 

What is the "set wakeup" script or command to be used when the machine uses local time?

Are there any processes that can stop this from working?  I have LCDd proc running for my VFD.  Can this stop the script from working?

I have tried the script posted in this forum.  I have tried to list the following in mythbackend-setup for the setWakeCommand.
[LIST=1]
[*]sudo sh -c 'echo $time > /proc/acpi/alarm'
[*]sudo /usr/bin/MythWakeSet (copied and made executeable from above post)
[*]mythshutdown --setwakeup $time (also with sudo)

[/LIST]

My Mobo is Gigabyte GA-MA69GM-S2H, it is a dual boot with XP and comfirmed to use local not UTC time.  Time/Date format is yyyy-MM-dd hh:mm:ss
I have tried the above settings in date format and also the following
[LIST=1]
[*]yyyy-MM-ddThh:mm:ss
[*]yyyy-MM-dd:hh:mm:ss
[/LIST]

I have not got a far to mess with Mythwelcome, nor NVram.
Nothing in syslog.  Is there another log I should check.

---

### Post by volkswagner on 2008-03-25
I ran
```

sudo /usr/bin/MythWakeSet
```

It did in fact set a new time for wake.  It was six days and twenty-five minutes in the future.  I did not see any signifigance to this time.  The closest scheduled recordings are one day from now and eight days from now.

Again this is the script posted in this thread.  I still do not know why myth wont call this script.

---

### Post by majoridiot on 2008-03-26
> **volkswagner said:**
> I ran
```

sudo /usr/bin/MythWakeSet
```

It did in fact set a new time for wake.  It was six days and twenty-five minutes in the future.  I did not see any signifigance to this time.  The closest scheduled recordings are one day from now and eight days from now.

Again this is the script posted in this thread.  I still do not know why myth wont call this script.

the correct command to set the time in backend setup is:

```
sudo /usr/bin/MythWakeSet $time
```

things to check if MythWakeSet works manually but not from myth-

check permissions of /usr/bin/MythWakeSet to be sure it is owned by root and is readable and executable

check the capitalization of MythWakeSet in backend setup and the filename itself- i wrote i guide and screw it up myself ;)

make sure that MythWakeSet is in the mythtv string of your visudo settings... check capitals and spelling there, too.

---

### Post by volkswagner on 2008-03-26
Thanks for the reply.  I will double check the items you mentioned.

The guide is great.  I am not sure what script to use if the system is on local time not UTC.  It seems I am missing a piece of the puzzle.

If my system is on local time what should be in my *SetWake script?

---

### Post by volkswagner on 2008-03-26
> check permissions of /usr/bin/MythWakeSet to be sure it is owned by root and is readable and executable

Looks good to my newbie eyes.

```
-rwxr-xr-x 1 root root 579 2008-03-25 16:55 MythWakeSet
```

```
sudo /usr/bin/MythWakeSet $time
```
I got the same time set and date set so now it set five days from now and same time 2008-03-31 19:00:01.

I still have the same two recordings scheduled.  3/26@21:00-22:00, 4/2@21:00-22:00
I wonder if the day matters.  It seems possible the day may get ignored.  I will do a mock test as described in the how to and see if it wakes when I manually run the command and shut it down.

---

### Post by majoridiot on 2008-03-26
> **volkswagner said:**
> Thanks for the reply.  I will double check the items you mentioned.

The guide is great.  I am not sure what script to use if the system is on local time not UTC.  It seems I am missing a piece of the puzzle.

If my system is on local time what should be in my *SetWake script?

it should work exactly as it is is in the guide.  the "local time" question came up a few weeks ago for someone who
was GMT timezone and was having problems.  a few changes to the guide were necessary, but once they were
made, everything worked fine.  

using the MythWakeSet provided in the *non-mythwelcome* section of the guide should work for you.

---

### Post by majoridiot on 2008-03-26
> **volkswagner said:**
> I wonder if the day matters.  It seems possible the day may get ignored.  I will do a mock test as described in the how to and see if it wakes when I manually run the command and shut it down.

some motherboards ignore the month... that might throw you off a little in interpreting it.

it is also valuable the check /var/log/mythtv/mythbackend.log to see if you get any errors on shutdown logged there.
many times it will reveal a sudo or typo issue, etc.

if you are testing MyWakeSet by hand, don't forget to provide the date and time arguments or it won't change the setting.

---

### Post by volkswagner on 2008-03-26
Pleas allow me to explain my confusion.

From the guide:
> Scripts and Settings

You will likely need at least one of these scripts for the wake-up/shutdown process:

    *

      a script to adjust and set the wake-up time (if your mobo clock is UTC)
    *

      a Pre-shutdown script (possibly)
    *

      a Server Halt script (if you use poweroff kernel)

Examples of a wake script MythWakeSet, pre-shutdown script MythShutdownCheck and server halt script for poweroff kernel MythShutDown are provided here. If you need to do something special on your system before shutdown, such as special service shutdown scripts, etc., then you are responsible for integrating them into the provided script.
MythWakeSet

If your hardware clock is set to UTC, you need MythWakeSet to adjust between the wake time MythTV will report (local time) with the time the RTC alarm requires (UTC).

To create the wake script, open the editor of your choice and copy and paste the following. Save it as MythWakeSet

> a script to adjust and set the wake-up time (if your mobo clock is UTC)
I am sorry for taking this too literal.  The way I interpret this, "if my MOBO is in local time this script is not need".  I may need a different script, or need to comment out some instructions.

MythWakeSet

If your hardware clock is set to UTC, you need MythWakeSet to adjust between the wake time MythTV will report (local time) with the time the RTC alarm requires (UTC).

> To create the wake script, open the editor of your choice and copy and paste the following. Save it as MythWakeSet: 

Again if you are "majoridiot", I am "presidentidiot".  YOU are WAY smarter than me.  This is how you can write such a guide.  I would still be setting up tuners , rather than perfecting my setup.  Without YOUR help and help from others, I could not be where I am.  So please don't take this as critical.  I am just trying to get through this.  I hope if I explain you may lead me where I need to go.


> 
using the MythWakeSet provided in the non-mythwelcome section of the guide should work for you. 

I know I am thick.  I assume this means the script at the top of the HOW TO.  I will change my script to that one.

To further complicate things, I have a combined BE/FE.  I will need to run mythwelcome.  I did not get that far yet.

---

### Post by majoridiot on 2008-03-26
> **volkswagner said:**
> Pleas allow me to explain my confusion.
From the guide:

I am sorry for taking this too literal.  The way I interpret this, "if my MOBO is in local time this script is not need".  I may need a different script, or need to comment out some instructions.

MythWakeSet

If your hardware clock is set to UTC, you need MythWakeSet to adjust between the wake time MythTV will report (local time) with the time the RTC alarm requires (UTC).

Again if you are "majoridiot", I am "presidentidiot".  YOU are WAY smarter than me.  This is how you can write such a guide.  I would still be setting up tuners , rather than perfecting my setup.  Without YOUR help and help from others, I could not be where I am.  So please don't take this as critical.  I am just trying to get through this.  I hope if I explain you may lead me where I need to go.

I know I am thick.  I assume this means the script at the top of the HOW TO.  I will change my script to that one.

To further complicate things, I have a combined BE/FE.  I will need to run mythwelcome.  I did not get that far yet.

some of the text in the guide is now slightly out of date, and has been edited by others.
so it's hard to keep up with the state of things...

i recommend using the first MythWakeSet from the guide, as i know for certain it
worked the last time i dug into it to help someone.  if you can get it to write the time-
even if the time needs some offset adjustment, that can be done *after* you get it to write
anything at all.

i am running a combined FE/BE and do not use mythwelcome... and everything works
like clockwork.  instead, i have the auto-logon disabled so i can log in manually and if needed
the power button on my remote launches the frontend.

---

### Post by volkswagner on 2008-03-26
I changed the script to the one in the guide. 

I corrected a typo in backend setup for the MythShutdownCheck script.

I was surprised to see it shutdown even at the desktop.  I closed mythfrontend.  I did not log out of the system yet it shutdown.  I am pretty sure the shutdown check is working because it wont shutdown if frontend is open.  It will not shutdown if I have an open ssh session. 

I will need to edit the wakeup script.  It is converting to UTC.  My wakeup time was set four hours ahead.  I assume this is my -5GMT and +1 for DST.

What shall I do to the script?

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
echo $1\ $2 > $temp_stamp

# Read the date in *locale* time format and tag the time-zone info to the wake time
localeadd=$(/bin/date -f $temp_stamp +%F\ %T\ %z)
echo $localeadd > $temp_stamp

# adjust this to UTC and store the final wake time
utcadj=$(/bin/date -u -f $temp_stamp +%F\ %T)

# set the alarm
echo $utcadj > /proc/acpi/alarm
```

> 
i am running a combined FE/BE and do not use mythwelcome... and everything works
like clockwork. instead, i have the auto-logon disabled so i can log in manually and if needed
the power button on my remote launches the frontend.

How do you handle mythfilldatabase.  Does your system wake for this?  Does it just run the next time it wakes?

---

### Post by majoridiot on 2008-03-26
> **volkswagner said:**
> I changed the script to the one in the guide. 

I corrected a typo in backend setup for the MythShutdownCheck script.

I was surprised to see it shutdown even at the desktop.  I closed mythfrontend.  I did not log out of the system yet it shutdown.  I am pretty sure the shutdown check is working because it wont shutdown if frontend is open.  It will not shutdown if I have an open ssh session. 


good.

> **volkswagner said:**
>  I will need to edit the wakeup script.  It is converting to UTC.  My wakeup time was set four hours ahead.  I assume this is my -5GMT and +1 for DST.

What shall I do to the script?

just use this- it's a stripped down version that does no conversion, just a straight echo.

```
#!/bin/bash
#
# MythWakeSet

# temp file for working with time
temp_stamp=/home/mythtv/timestamp

# store the wake time passed from mythbackend
echo $1\ $2 > $temp_stamp

# set the alarm
echo $1\ $2 > /proc/acpi/alarm
exit 0
```

> **volkswagner said:**
> How do you handle mythfilldatabase.  Does your system wake for this?  Does it just run the next time it wakes?

my backend gets regular use and usually fills on a daily basis.  if your backend will be
off more than it is on, i'd suggest unchecking the setting to run mythfilldatabase at the 
time suggested by the grabber- or you may run short of data.

---

### Post by volkswagner on 2008-03-27
Thanks for the help.  majoridiot YOU THE MAN! 

I am not sure why I get this error.  I copied your script.

```
 sudo /usr/bin/MythWakeSet $time
/usr/bin/MythWakeSet: line 12: echo: write error: Invalid argument
```

Is this because I did not set the date argument?  I am not really sure how to do that.

It works!  It set the correct time!  It shutdown after idle!  It woke for my scheduled recording!

This is my first success.  I am not sure why mythfrontend did not load.  I have not disabled autologin.  I only disabled timed login yet.  This may be a one time glitch.  Is this because I did not manually wake the machine?

Now I need to research how to wake the master from my slave BE/FE  machine.  Most viewing will be from the slave.  Most recording is performed on master.

---

### Post by majoridiot on 2008-03-27
> **volkswagner said:**
> I am not sure why I get this error.  I copied your script.

```
 sudo /usr/bin/MythWakeSet $time
/usr/bin/MythWakeSet: line 12: echo: write error: Invalid argument
```

i dashed that out late last night... remove the \ between arguments in line 12 so it looks like this and it shouldn't error:

```
echo $1 $2 > /proc/acpi/alarm
```

> **volkswagner said:**
> Is this because I did not set the date argument?  I am not really sure how to do that.

you can set the format for the date on the wakeup page of mythtv-setup. you probably want
some variation of yyyy-MM-dd hh:mm:ss

> **volkswagner said:**
> Now I need to research how to wake the master from my slave BE/FE  machine.  Most viewing will be from the slave.  Most recording is performed on master.

this thread should get you going...

[http://ubuntuforums.org/showthread.php?t=360901](http://ubuntuforums.org/showthread.php?t=360901)

---

### Post by volkswagner on 2008-03-27
Wow another great how to.  I have WOL working on my master backend.  Unfortunately my slave machine will be more stubborn.  It is a Dell Dimension 4600 with onboard lan.  I have read some folks have had problems with many different dimension boards.  Some say it just may not work.  The BIOS does not even mention it.  How lame.

I am not sure having a slave limits some custimization.  I was considering setting up ACPI wake on this machine.  The backend setup is for the master on most fields.  Can a slave have a working ACPIwake.

I figured I could just shut the machine down manually.  I configured the exit to give me choices (exit, shutdown, restart).  I put in the shutdown and reboot commands, but they don't work.  

I tried both of the following entries but no luck.

```
sudo shutdown -h -P now
sudo /sbin/shutdown -h -P
```

I thought I could configure the slave to wake the master and wait for it to boot, then log into the backend with the following settings.

 "allow this frontend to wake the master database".  I thought I could check the box, set the wait time to 60sec(max), retry=1, and command=wakeonlan macaddressformaster.  After reading further I don't think this is the intentions for this setup.  

I think my solution is both machines will have autolaunch mythtv disabled.  I will then like shortcuts on the desktop for things like, launch Mythfrontend, wake master.

I did create a launcher for the wakeonlan.  It is so small in the start menu.  In Gnome I can create a launcher on the desktop.  Not sure how to do it with XFCE.

All in all I am on my way to saving energy and my daughters planet.   :)

---

### Post by majoridiot on 2008-03-27
> **volkswagner said:**
> Wow another great how to.  I have WOL working on my master backend.  Unfortunately my slave machine will be more stubborn.  It is a Dell Dimension 4600 with onboard lan.  I have read some folks have had problems with many different dimension boards.  Some say it just may not work.  The BIOS does not even mention it.  How lame.

I am not sure having a slave limits some custimization.  I was considering setting up ACPI wake on this machine.  The backend setup is for the master on most fields.  Can a slave have a working ACPIwake.

I figured I could just shut the machine down manually.  I configured the exit to give me choices (exit, shutdown, restart).  I put in the shutdown and reboot commands, but they don't work.  

I tried both of the following entries but no luck.

```
sudo shutdown -h -P now
sudo /sbin/shutdown -h -P
```

I thought I could configure the slave to wake the master and wait for it to boot, then log into the backend with the following settings.

 "allow this frontend to wake the master database".  I thought I could check the box, set the wait time to 60sec(max), retry=1, and command=wakeonlan macaddressformaster.  After reading further I don't think this is the intentions for this setup.  

I think my solution is both machines will have autolaunch mythtv disabled.  I will then like shortcuts on the desktop for things like, launch Mythfrontend, wake master.

I did create a launcher for the wakeonlan.  It is so small in the start menu.  In Gnome I can create a launcher on the desktop.  Not sure how to do it with XFCE.

All in all I am on my way to saving energy and my daughters planet.   :)

i don't know why a slave couldn't have ACPI wake... as long as you set it up like you have and the mobo complies.  then the frontend
could wake the backend using WOL and wait paitently for it to come to life.

glad you got it working this far, tho! :D

---

