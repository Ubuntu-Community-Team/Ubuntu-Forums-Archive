---
title: "mythwelcome, nvram-wakeup issues"
date: 2009-02-13
forum: Mythbuntu
---

### Post by mathog on 2009-02-13
Sigh, more issues.  

Short form:

Mythbuntu 8.10
1.  How to force mythwelcome onto screen 1 instead of screen 0?
2.  Why isn't mythwelcome shutting down?
3.  I think I have nvram-wake configured - what is the shortest command I can run from the command line to tell it "wake up in 5 minutes"?

Long form:

1.  I had mythfrontend starting up nicely and automatically on tv-out (screen 1) by putting in /etc/mythtv/session-settings:

MYTHFRONTEND_OPTS="-display :0.1"

Then in the same file, I uncommented mythwelcome, and did:

mythwelcome -s

and added the -display :0.1 to the end of the line that starts mythfrontend.  

Reboot.

Mythfrontend comes up on screen 1 (tv-out) as desired, but mythwelcome comes up on screen 0.  That isn't going to work very well in DVR use when there is no screen 0!

Is there an option in the /etc/mythtv/session-settings file to place mythwelcome too?  It seems not to have a -display option...

2.  When mythwelcome times out its log file starts doing this:

```
2009-02-12 21:15:40.521 MythWelcome received a SHUTDOWN_NOW event
2009-02-12 21:15:51.932 MythWelcome received a SHUTDOWN_NOW event
2009-02-12 21:16:03.237 MythWelcome received a SHUTDOWN_NOW event
2009-02-12 21:16:14.396 MythWelcome received a SHUTDOWN_NOW event
etc.

```
Yet it doesn't shut down.  The process belongs to user "dvr", and dvr is in groups:

```
adm:x:4:ubuntu,dvr
dialout:x:20:mythtv,ubuntu,dvr
cdrom:x:24:mythtv,ubuntu,dvr
plugdev:x:46:ubuntu,dvr
mythtv:x:108:ubuntu,dvr,root
lpadmin:x:115:dvr
sambashare:x:117:dvr
admin:x:123:dvr
dvr:x:1000:
```


Protection on mythshutdown is:
-rwxr-xr-x 1 root root 87880 2008-10-15 22:43 /usr/bin/mythshutdown

Is it supposed to be something else, perhaps a sticky bit set?

Thanks.

---

### Post by mathog on 2009-02-13
Anybody?

---

### Post by silverdulcet on 2009-02-14
I can't speak to getting mythwelcome to come up on a specific screen. But there are a couple things to check as to why its not shutting down. 

Regarding the machine not shutting down when it times out. Did you edit the /etc/sudoers file so that the user you run mythtv as is able to run/access all the commands and files it needs to as root?

The commands to wake it in 5 minutes is:
```
echo 0 > /sys/class/rtc/rtc0/wakealarm
echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm

```

You need to run this command as root. So make sure to get a root prompt first with:

```
sudo su
```

This thread has some good info about configuring mythwelcome correctly. The most recent posts are more accurate.

[http://ubuntuforums.org/showthread.php?t=702310]("http://ubuntuforums.org/showthread.php?t=702310")

---

### Post by mathog on 2009-02-14
Some progress.

1.  To start mythwelcome and mythfrontend on screen 1 I did the following.

```
cd ~/.config/autostart
rm mythtv
cat >/usr/local/bin/mymythtv.sh <<EOD
#!/bin/sh
export DISPLAY=:0.1
while [ 1 ]; do
  mythwelcome --logfile /var/log/mythtv/mythwelcome.log
done
EOD
sudo chmod 755 /usr/local/bin/mymythtv.sh
cat >mythtv <<EOD
[Desktop Entry]
Name=mythtv startup
Comment=my hack to start mythtv on screen 1
Version=0.9.4
Exec=/usr/local/bin/mymythtv.sh
Type=Application
Encoding=UTF-8
Icon=/usr/share/mythtv/themes/blue/myth_tv_logo.png
StartupNotify=false
Terminal=false
Hidden=false
EOD
```

The loop in the one script is to restart things if for some reason mythwelcome crashes.

2.  This is very old school, but since this is a single user system sudoers is a bit of overkill. It is sufficient to do this to enable shutdown:

sudo chmod 4755 `which reboot`

It is not necessary to change anything related to mythshutdown, at least for the shutdown part of its function.

WARNING.  If the shutdown time in the "shutdown/wakeup options" page of mythtv-setup is set shorter than the time it takes mythwelcome to start mythfrontend, then the system will come up part way and immediately shut down.  I set that time to 60 seconds, which seems to be adequate.

3.  Still stuck here.  There seems to be a disconnect between the settings in mythtv-setup and mythwelcome.  In the former on the
"shutdown/wakeup options" there is:

```
wakeup time format: yyyy-MM dd:hh:mm
command to set wakeuptime:  mythshutdown --setwakeup $time
```

whereas 'mythwelcome --setup' has:

```
command to set wakeup time: /usr/bin/nvram-wakeup  --settime $time --configfile /etc/default/nvram.conf
wake time format:  time_t
(the only other option is yyyy-MM-dd hh:mm:ss

```

This looks like a mix of old and new methods to me.  The wiki for mythwelcome indicates that mythwelcome and the backend use the same time storage location, and this is a bit of a mess since it specifies what seems to be two different time formats.

Shouldn't mythwelcome also be using mythshutdown?
Does mythshutdown use time_t?

Can I please see a command line example for "have mythshutdown set wakeup in 5 minutes and then shutdown"?

Thanks

---

### Post by silverdulcet on 2009-02-15
Please see this post for examples of mythtv-setup and mythwelcome --setup configuration. 
[http://ubuntuforums.org/showpost.php?p=6374963&postcount=130]("http://ubuntuforums.org/showpost.php?p=6374963&postcount=130")

In short mythshutdown saves the startup time for the next recording in the format below. 
```
wakeup time format: yyyy-MM dd:hh:mm
command to set wakeuptime:  mythshutdown --setwakeup $time
```

MythWelcome just starts MythFrontend after it starts itself. When you exit out of MythFrontend you are left with the MythWelcome menu. Once the configurable timeout that you configured in MythWelcome --setup expires it calls the $time variable set with mythshutdown command and runs the script you created to set the /sys/class/rtc/rtc0/wakealarm and uses the time_t or epoch time format instead of the one that is passed by mythshutdown.

So basically the mythshutdown --setwakeup stores the variable in one format, and when mythwelcome actually sets the wakeup time it converts it to epoch time. Thats why you specify one format for mythsetup and a different one for mythwelcome --setup. 

Your "command to set wakeup time" in Mythwelcome --setup should call a script you created. 

```
command to set wakeup time: sudo -H /usr/bin/MythWakeSet "$time"
```

/usr/bin/MythWakeSet
```
#
# MythWakeSet
#
# set mythtv wake-up time with UTC-adjusted time
#
# set the alarm
sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm" # clear it
sudo sh -c "echo $1 > /sys/class/rtc/rtc0/wakealarm" # write the waketime
```

I think the nvram-wakeup command you have specified in Mythwelcome --setup is deprecated IIRC.

---

### Post by mathog on 2009-02-16
> **silverdulcet said:**
> 
[http://ubuntuforums.org/showpost.php?p=6374963&postcount=130]("http://ubuntuforums.org/showpost.php?p=6374963&postcount=130")


Well, I followed that.  But so far no joy.  It is doing a couple of things wrong:

1.  Exit from mythfrontend and mythwelcome comes up.  If nothing is scheduled, or scheduled far enough out it counts down from 60 and shuts down.  If there is something programmed fairly soon (15 minutes) it keeps restarting the count at 60.  At first I thought it was due to the loop in my startup script restarting mythfrontend, but I put a longish sleep command in there, as well as a debugging logger command, and that showed it wasn't mythwelcome restarting, just the count.  I don't understand the restart - there is a 5 minute "maxwait"
and 180 seconds "start", so 8 minutes, yet the count restarts seems to happen unless the recording is scheduled at least 20 minutes out.

2.  When it finally does shut down it reboots immediately.  So I put a
a debugging statement in my MythWakeSet.sh script.  After one of these instant reboots:

```
dvr@:/var/log$ date -u +%s
1234842995
dvr@:/var/log$ grep WakeSet messages
Feb 16 19:53:40 media logger: MythWakeSet called with 1234843920

```

Seems like it just did "reboot" instead of "shutdown".  The MythWakeSet.sh script worked when I tested it with a "shutdown".

---

### Post by silverdulcet on 2009-02-17
> **mathog said:**
> Well, I followed that.  But so far no joy.  It is doing a couple of things wrong:

1.  Exit from mythfrontend and mythwelcome comes up.  If nothing is scheduled, or scheduled far enough out it counts down from 60 and shuts down.  If there is something programmed fairly soon (15 minutes) it keeps restarting the count at 60.  At first I thought it was due to the loop in my startup script restarting mythfrontend, but I put a longish sleep command in there, as well as a debugging logger command, and that showed it wasn't mythwelcome restarting, just the count.  I don't understand the restart - there is a 5 minute "maxwait"
and 180 seconds "start", so 8 minutes, yet the count restarts seems to happen unless the recording is scheduled at least 20 minutes out.

2.  When it finally does shut down it reboots immediately.  So I put a
a debugging statement in my MythWakeSet.sh script.  After one of these instant reboots:

```
dvr@:/var/log$ date -u +%s
1234842995
dvr@:/var/log$ grep WakeSet messages
Feb 16 19:53:40 media logger: MythWakeSet called with 1234843920

```

Seems like it just did "reboot" instead of "shutdown".  The MythWakeSet.sh script worked when I tested it with a "shutdown".

Can you post screenshots of your Mythwelcome --setup screen as well as the Mythtv config screen that has the config options for startup/shutdown? Also, can you post your MythWakeSet script if it differs from the one I posted above? As for the resetting the count, I have read that having EIT updates enabled (schedule updates from the EIT guide data) on your tuners can sometimes reset the timeout for myth-backend. I haven't experienced this, but its something to look into.

---

### Post by mathog on 2009-02-18
> **silverdulcet said:**
> Can you post screenshots of your Mythwelcome --setup screen as well as the Mythtv config screen that has the config options for startup/shutdown? Also, can you post your MythWakeSet script if it differs from the one I posted above? As for the resetting the count, I have read that having EIT updates enabled (schedule updates from the EIT guide data) on your tuners can sometimes reset the timeout for myth-backend. I haven't experienced this, but its something to look into.

MythWakeSet
```
#!/bin/sh
logger "MythWakeSet called with $1"
echo  0 > /sys/class/rtc/rtc0/wakealarm  # clear it
echo $1 > /sys/class/rtc/rtc0/wakealarm  # write the waketime

```

File protections set to 4755:

```
-rwsr-xr-x 1 root root 42704 2008-09-29 16:52 /sbin/reboot
-rwsr-xr-x 1 root root 87880 2008-10-15 22:43 /usr/bin/mythshutdown
-rwsr-xr-x 1 root root 432 2009-02-16 16:06 /usr/local/bin/MythWakeSet

```

This sequence shut down the machine, but did not result in a wake.  Possibly because machine is using local time and mythtv is using UTC?
(This was local time in UTC format +2 minutes.)
```
mythshutdown --setwakeup 2009-02-17T06:15:00
mythshutdown -q
```

Note that this does work, it sets the restart for 2 minutes
in the future, shuts down, and restarts at the appointed time:
 
```
MythWakeSet `date -u '+%s' -d '+ 2 minutes'`
poweroff

```

thanks.

---

### Post by mathog on 2009-02-18
> 
This sequence shut down the machine, but did not result in a wake.  Possibly because machine is using local time and mythtv is using UTC?
(This was local time in UTC format +2 minutes.)
```
mythshutdown --setwakeup 2009-02-17T06:15:00
mythshutdown -q
```


Nope, it was a typo, the date was supposed to be 18, not 17. 

Here is the interesting part.  When the date is set in the past "mythshutdown -q" causes the machine to actually shut down, but of course, it doesn't wake up.  If the time is really set +2 minutes in the future, or even +15, what happens instead is that it immediately reboots at "mythshutdown -q".  It does this whether or not mythwelcome and mythfrontend are running at the same time.  This was tested by filling in this command line, but not hitting ENTER:

```
mythshutdown --setwakeup 2009-02-17T07:15:00 ; \
mythshutdown -q
```

and then killing first the script that starts mythwelcome, then mythwelcome, and then exiting from mythfrontend, and then immediately executing the queued command line.  Done that way, or with mythwelcome & mythfrontend still running, both cases, it immediately reboots.  Note that the front end is just sitting there in the top menu, and there is no transcoding etc. going on.

---

### Post by silverdulcet on 2009-02-18
> This sequence shut down the machine, but did not result in a wake. Possibly because machine is using local time and mythtv is using UTC?
(This was local time in UTC format +2 minutes.)

Unless you have a multi-boot system (with windows) your system clock should default to UTC. That is unless upon install you selected not to set it to UTC. Your system time is then found using the timezone you select to determine local time. 

Is there a reason you have MythShutdown/MythWelcome Settings with:
```
nvram-wakeup Restart Command: /sbin/grub/set-default-1
```

Unless you have a multiboot system where linux isn't the default operating system I don't think this is required at all. If you aren't sure you need this setting I would remove it. 

I forgot to mention, can you also post your /etc/sudoers file? Please note, that the screenshots in the linked post above by Stevi are using these for settings in MythShutdown/MythWelcome Settings:

```
Command to reboot: sudo -H shutdown -h -r now
Command to shutdown: sudo -H shutdown -h -P now
```

You'll notice he added /sbin/shutdown to his /etc/sudoers file. I'm not saying that you can't use /sbin/reboot and /sbin/poweroff instead, but it is not how I have it configured. You could try adding those two to your /etc/sudoers file and see if it works. 

> This sequence shut down the machine, but did not result in a wake. Possibly because machine is using local time and mythtv is using UTC?
(This was local time in UTC format +2 minutes.)

```
mythshutdown --setwakeup 2009-02-17T06:15:00
mythshutdown -q
```

Note that this does work, it sets the restart for 2 minutes
in the future, shuts down, and restarts at the appointed time:

```
MythWakeSet `date -u '+%s' -d '+ 2 minutes'`
poweroff

```


My understanding is that mythshutdown --setwakeup just passes the wake time for the next scheduled program to mythshutdown. It does not actually write that time to the RTC wakeup clock. So just using that, then running mythshutdown -q isn't supposed to work. Where the RTC wakeup clock is set is with your MythWakeSet script.

I'm not able to post them at the moment. But later today I'll post my:
Shutdown Wakeup Options
MythShutdown/MythWelcome Settings
/etc/sudoers file

They are very similar to the post by Stevi I linked a few posts back. Though the screenshots of the settings won't be in german. ;) It is encouraging that it wakes up just fine with using your MythWakeSet script from the command line. There must be some little thing that is configured incorrectly with permissions, /etc/sudoers, MythWelcome Settings/Mythtv Shutdown/Wakeup options. You are almost there.

---

### Post by mathog on 2009-02-18
One other oddness I noticed last night just before shutting down.  When mythtv-setup was running, then as expected:

```
mythshutdown -s
echo $?
255

```
and when mythfrontend was running, but just sitting in the top menu this returned 0.  However, when mythfrontend was actively watching a show it also returned 0.  I would have thought that "watching TV" should have returned an 8.  Or does watching a live show not count as "recording", even though while it is going on the system is spooling a video stream to disk?

I don't think there is a protection problem with mythshutdown, it can clearly do both shutdown and reboot.  The strange thing is that it seems to choose the latter whenever there is wake event set.  I'm beginning to think that there may be a minimum wake period buried somewhere and that my tests are all less than that, so that some piece of code sees "shutdown" but then changes it to "reboot" because "we need to be up in less than MIN_SLEEP seconds".

---

### Post by silverdulcet on 2009-02-18
> **mathog said:**
> One other oddness I noticed last night just before shutting down.  When mythtv-setup was running, then as expected:

```
mythshutdown -s
echo $?
255

```
and when mythfrontend was running, but just sitting in the top menu this returned 0.  However, when mythfrontend was actively watching a show it also returned 0.  I would have thought that "watching TV" should have returned an 8.  Or does watching a live show not count as "recording", even though while it is going on the system is spooling a video stream to disk?

I don't think there is a protection problem with mythshutdown, it can clearly do both shutdown and reboot.  The strange thing is that it seems to choose the latter whenever there is wake event set.  I'm beginning to think that there may be a minimum wake period buried somewhere and that my tests are all less than that, so that some piece of code sees "shutdown" but then changes it to "reboot" because "we need to be up in less than MIN_SLEEP seconds".

The only relevant settings I know of are:
Max. wait for recording (min):5
Startup before recording (secs):180

This means that if a recording isn't starting within 5 minutes then it will shutdown and the wakeup time will be set to 180 seconds before the next program is scheduled to record. I've never had my system reboot at all, so I'm not sure what it uses that command for anyhow. 

As far as mythfrontend, as long as its running your system will not shutdown at all, whether you are watching a video or not.

The relevant line from my /etc/sudoers file.
```
%mythtv ALL = NOPASSWD: /sbin/shutdown, /usr/bin/setwakeup.sh, /sys/class/rtc/rtc0/wakealarm, /usr/bin/MythShutdownCheck, /etc/init.d/mythtv-backend, /usr/bin/mythshutdown
```

You'll notice that I used setwakeup.sh instead of MythWakeSet as the name for the script that sets the rtc alarm. This is just what I happened to name it rather then MythWakeSet. It is very similar to yours.
/usr/bin/setwakeup.sh
```
#!/bin/sh
#$1 is the first argument to the script. It is the time in seconds since 1970
#this is defined in mythtv-setup with the time_t argument

sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"      #this clears your alarm
sudo sh -c "echo $1 > /sys/class/rtc/rtc0/wakealarm"    #this writes your alarm

```

---

### Post by mathog on 2009-02-19
Well, I never could get it to work using that example, but in the end it was beaten into submission, mostly by leaving out as much as possible of mythshutdown.  Here is my final solution:

```

% cat ~/.config/autostart/mythtv_startup.desktop
[Desktop Entry]
Name=mythtv startup
Comment=my hack to start mythtv on screen 1
Version=0.9.4
Exec=/usr/local/bin/mymythtv.sh
Type=Application
Encoding=UTF-8
Icon=/usr/share/mythtv/themes/blue/myth_tv_logo.png
StartupNotify=false
Terminal=false
Hidden=false

% cat /usr/local/bin/mymythtv.sh
#!/bin/sh
#
#  David, this script sets the display and then starts mythfrontend
#  The while script is to restart mythwelcome if it should crash or exit
#  for some reason.
#
export DISPLAY=:0.1
while [ 1 ]; do
  logger "starting mythwelcome at `date`"
  mythwelcome --logfile /var/log/mythtv/mythwelcome.log
  sleep 30 #give it time to shut down if that is why it exited
done

% cat /usr/local/bin/MythWakeSet
#!/bin/sh
# This must be called with a UTC time (time_t format)
# This must run as root.  Set ownership to root:root
#   and chmod 4755 or use sudoers
logger "MythWakeSet called with $1"
echo  0 > /sys/class/rtc/rtc0/wakealarm  # clear it
echo $1 > /sys/class/rtc/rtc0/wakealarm  # write the waketime


```

The mythwelcome and mythtv-setup configurations are in the attachments below.

Basically the way this works is that once it is idle, the backend sets the reboot time itself, and it also does the shutdown itself.  The function of mythwelcome is reduced to offering a way to start the front end (on a normal boot), restart the front end (if one accidentally exits from it or it crashes), and to give some status information once the front end has been closed on purpose.

---

### Post by mathog on 2009-03-05
> **mathog said:**
> Well, I never could get it to work using that example, but in the end it was beaten into submission, mostly by leaving out as much as possible of mythshutdown.  Here is my final solution:


Well, almost final.  I simplified a bit by writing a little program to set the wakealarm (attached, strip the .txt and build it with
```

  gcc -Wall -o setwake setwake.c
  sudo mv setwake /usr/local/bin
  sudo chown root:root /usr/local/bin/setwake
  sudo chmod 4755 /usr/local/bin/setwake
  ./setwake       #show help
  ./setwake ""    #show current wake settings without sudo
  ./setwake $TIME #set wake time without sudo

```


The modified MythWakeSet (active lines only) is:

```

#!/bin/sh
logger "MythWakeSet called with $1"
setwake $1 >/dev/null #it will echo the parameter to stdout

```

There is one problem though, which I guess can be thought of as the "one automatic shutdown only" limitation.  Consider this sequence:
normal boot, mythwelcome starts, it starts mythfrontend, user schedules one recording and then exits mythfrontend.  After 60 seconds the backend shuts down and the computer restarts at the appropriate time and records the show.  However, at the restart mythwelcome ALSO restarts, and it starts mythfrontend.  There may be nobody there to exit from mythfrontend, and consequently the computer will stay on forever.   How does one work around this?

---

### Post by mathog on 2009-03-06
> **mathog said:**
> 
There is one problem though, which I guess can be thought of as the "one automatic shutdown only" limitation.  Consider this sequence:
normal boot, mythwelcome starts, it starts mythfrontend, user schedules one recording and then exits mythfrontend.  After 60 seconds the backend shuts down and the computer restarts at the appropriate time and records the show.  However, at the restart mythwelcome ALSO restarts, and it starts mythfrontend.  There may be nobody there to exit from mythfrontend, and consequently the computer will stay on forever.   How does one work around this?

Figured it out.  On looking back through my notes I had configured Mythwelcome to autostart Mythfrontend because lirc was not working with Mythwelcome, so there was no way to push the button to start the frontend otherwise.  Copied the lirc file "mythtv" to one named "mythwelcome", made a global change in it of mythtv -> mythwelcome, restarted everything and then the remote worked with mythwelcome.   Turning off the autostart option was a bit odd, since starting mythwelcome automatically started the frontend (immediately) there was no time to get into the "i" menu.  Luckily on exiting from the frontend there were 60 seconds to get into Mythwelcome and change this before the system shut itself down.  If the delay to shutdown time were set too short I don't see how one would have time to enter the "i" screen of Mythwelcome and make changes.

Anyway, all good now.

---

