---
title: "Why does this not work as a simple shutdown???"
date: 2010-06-20
forum: Mythbuntu
---

### Post by BigGeoff on 2010-06-20
Afternoon folks
I have a Shuttle PC on which runs Mythbuntu 9.10. As I don't want to leave this on 24/7 I looked into shutting down after the last recording of the night. I didn't want to get too heavily involved in ACPI wakeup/shutdown, BIOS stuff etc. but I did try this: 

Set user Job #4 to /usr/share/mythtv/myth-halt.sh

which is the same command used when you shut the frontend down and shutdown the computer afterwards (and that works just fine) yet I have tried using this as a user job run after recording (with no other post processing - flagging or transcodeing requested) and it doesn't do anything. I tried setting up a recording with user job 4 after it then closing down the frontend. and that didn't work either. I checked in system info and it gets queued as a job but that's all and I can't see anything in the logs that even remotely seems connected to it.

After trawling though various posts here I also tried:-

setting user job 4 to sudo  /usr/share/mythtv/myth-halt.sh

Setting user Job 4 to sudo shutdown -P +2 (and with -P now options too)

Neither of which worked. I have tried running both in a terminal window and the myth-halt.sh works fine but the shutdown complains about the time format which I dont understand as I took this straight from the help pages.

I cannot for the life of me work out why using the original myth-halt method doesn't work - maybe someone can enlighten me before I go mad......

If anyone could possibly help I would be eternally grateful

Geoff

---

### Post by ozite on 2010-06-20
I'm not sure where the problem is, so I can't help.  I struggled at first with the ACPI wakeup/shut down but managed to get it to work in [_this thread on MythWelcome_]("http://ubuntuforums.org/showthread.php?t=1370585").  Maybe it is something helpful.

---

### Post by Neon Dusk on 2010-06-20
However the settings in the first post of that thread do not work with 'automatically start frontend' or the daily wakeup/shutdown periods.

If do want to set-up ACPI Wakeup / MythWelcome try the settings in the MythWelcome section of the [ACPI Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup) wiki

---

### Post by BigGeoff on 2010-06-20
I suppose the short question should have been if these two commands work just fine in a terminal (I seem to have gotten over the time format problem with Shutdown), why don't they work when you make them a user job? even using sudo doesn't  cure it. Does anyone have success with user jobs or is it just me?

Geoff

---

### Post by superm1 on 2010-06-20
> **BigGeoff said:**
> Afternoon folks
I have a Shuttle PC on which runs Mythbuntu 9.10. As I don't want to leave this on 24/7 I looked into shutting down after the last recording of the night. I didn't want to get too heavily involved in ACPI wakeup/shutdown, BIOS stuff etc. but I did try this: 

Set user Job #4 to /usr/share/mythtv/myth-halt.sh

which is the same command used when you shut the frontend down and shutdown the computer afterwards (and that works just fine) yet I have tried using this as a user job run after recording (with no other post processing - flagging or transcodeing requested) and it doesn't do anything. I tried setting up a recording with user job 4 after it then closing down the frontend. and that didn't work either. I checked in system info and it gets queued as a job but that's all and I can't see anything in the logs that even remotely seems connected to it.

After trawling though various posts here I also tried:-

setting user job 4 to sudo  /usr/share/mythtv/myth-halt.sh

Setting user Job 4 to sudo shutdown -P +2 (and with -P now options too)

Neither of which worked. I have tried running both in a terminal window and the myth-halt.sh works fine but the shutdown complains about the time format which I dont understand as I took this straight from the help pages.

I cannot for the life of me work out why using the original myth-halt method doesn't work - maybe someone can enlighten me before I go mad......

If anyone could possibly help I would be eternally grateful

Geoff

My guess would be the environment from which the command is being ran is missing some variables that are set otherwise when ran as an (interactive) user.

---

### Post by azmyth on 2010-06-20
You may also need to add the commands in the sudoers file for the given user. For example, I tied a remote key to sudo reboot and I had to add my user with the reboot command to the sudoers file otherwise when it was executed it would look for the sudo password and since it got nothing it just wouldn't execute.

You'll probably have to add the commands in the myth-halt script to the sudoers file to get it to work.

---

### Post by BigGeoff on 2010-06-21
Thanks for your input guys.

I edited the sudoers file with visudo to include permissions for mythtv as [Here]("http://ubuntuforums.org/showthread.php?t=1370585") and this hasn't made any difference.

superm1 - could you hazard a guess as to what variables and how I might set them, I am very much feeling my way here.

Geoff

---

### Post by BigGeoff on 2010-06-26
I still have no idea where to go from here guys

---

### Post by azmyth on 2010-06-26
I'd add the user you log in as to the visudo file with the shutdown command and then test it via the command line then test through myth. Visudo is picky about the location of the commands and it won't work if it's out of order. I'd start out with the shutdown command first then work to get myth-halt.sh to work.

---

### Post by PhilWig on 2010-07-01
I run 9.04 and had a problem with user jobs.  They need to be 'ticked' in both front end and backend.

I also found that if you do this, then want to subsequently disable it you will need to put a null job in until all forthcoming recordings have been run, otherwise the jobs fail to complete.  I concluded that it stores a marker in the database when you schedule a recording.
Hope this helps.

Phil

---

### Post by BigGeoff on 2010-07-02
Thanks Phil - I was just wondering how much of this weekend to dedicate to this problem - day job getting in the way again :p

---

### Post by ibuclaw on 2010-07-02
Perhaps if the shutdown script was:
```

dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Shutdown

```
It would work then ? 


Old habit from Openbox days... how to shutdown without root privileges. :)

---

### Post by BigGeoff on 2010-07-03
Just looked at your post again and not sure what you mean PhilWig, when you set up a recording you check whichever user jobs are required but in the backend there appears to be no way to 'tick' user jobs, only to define and name them in backend setup.:confused:

Have I missed something? I must admit to losing track of where various things are in Mythtv due to it's complexity.

I also neglected to mention that although my main box is running 9.04, the Myth box is on 9.10 if that makes a difference?

Geoff

---

### Post by PhilWig on 2010-07-03
Hi BigGeoff,

   just risked having me head torn off - interrupting Wimbledon!

To clarify; I'm running 9.04 on a combined frontend/backend, and yes the two sets of tick boxes are well hidden and I doubted myself for a while.

In Frontend:  Utilities > Setup > TV Settings (not obvious) > General > page 3.

In backend:   General > page 7.

Is your problem that the user job is not being run at all, or that it is running but the shutdown is not being respected?
Substituting with a touch or a date>>somefile.log might tell you?

Have you allowed the myth user to run shutdown as another subscriber has suggested?  See towards the end of this useful article:

[http://www.mythtv.org/wiki/Mythwelcome](http://www.mythtv.org/wiki/Mythwelcome)

On my system I think it's that which allows me to issue "sudo shutdown -h now" from an Xterm without needing a password.

Incidentally, welcome works well on my system apart from the lack of regular housekeeping - does that option not work if you have separate FE and BE?

Hope this helps.
Phil

---

### Post by BigGeoff on 2010-07-04
OK Philwig

Thanks you got it - I had done all of what you suggested already but missed the backend page, in fact page 8 on my system but it is over the right hand side with things on the left to take your attention away (that's my excuse anyway). Set those boxes and hey presto - job runs and system shuts down and powers off.

However, now when I turn it on again, it shuts itself down as soon as it has auto-started the frontend. If I am on the ball and can manage to quickly quit the frontend (only about 50% of the time) then the system stays up and re-starting the frontend doesn't seem to trigger a further shutdown.

Even more confused now.

Geoff

---

### Post by PhilWig on 2010-07-05
Hi Geoff,

I have a whacky hunch with no absolutely evidence to support it.  What if the normal sequence is that user job #4 starts, does it's required work and then exits.  Mythtv then notes in the database that it has completed job#4 and does not need to start it ever again.   Unfortunately, your shutdown prevents that database update, so it starts job#4 again on reload.

If this is the case, then what if instead your user job were to spawn a background job which slept for a few minutes before the sudo shutdown?  that would allow myth to update the database.

ie user job #4 says:    /somepath/myjob4.sh&

and /somepath/myjob4.sh is:
#!/bin/bash
sleep 120
sudo shutdown ...
exit

Phil

---

### Post by BigGeoff on 2010-07-05
Interesting, I was perusing my situation at work today and considered the very thing myself but I have such poor understanding of the way these jobs work that I couldn't decide whether I was using joined up thinking or not. The problem is this is rather academic at present because I don't seem to be able to stop the cycle this evening. I recorded a film last night and used the shutdown job thinking I could spend 5 minutes trying to interupt this constant shutting down with the idea that sooner or later I could stop it and all would be ok but nothing is working. I try ctrl-alt-bkspc to get out of the session, ctrl D, escape but nothing works. Good job I transcode and shift all my recordings off of that machine and onto my NAS cos I may end up wiping it, although it would be a shame if I had to now I have most things set up how I like them and that does seem like giving up.

Any suggestions here would definitely be gratefully received.

Geoff

---

### Post by PhilWig on 2010-07-07
When you start up is there a GRUB safe mode?
Phil

---

### Post by BigGeoff on 2010-07-07
There is and I could get in there without any probs but hadn't a clue what to do when I had :confused:

---

### Post by PhilWig on 2010-07-08
Sorry Geoff things are very fraught here with house moves etc. so this must be off the cuff.
If you could run the backend setup program from the safe mode system then you could turn the shutdown into a null command eg ls>/dev/null

That would restore sanity and allow you to put in a safer script at leisure:

if marker file does not exist, exit
rm marker file
spawn shutdown stuff as previously discussed.

you get the idea - create a marker file to allow it to shutdown ONCE.

Sorry again.
Phil

---

### Post by PhilWig on 2010-07-15
Geoff,
     So you've been able to load a 'safe' mode.
The file:     /etc/init.d/mythtv-backend
is called by the system to start and stop myth backend.

If you were to edit it - look for the line with
start)
and then insert after it a line
   exit 0

then you should be able to load up a normal version of Linux without backend starting and it closing down every time on you.  Frontend might complain, but never mind.

Then you can run setup to swap your offending shutdown for something more benign like just a #.

Re-edit 
     /etc/init.d/mythtv-backend
to take out your exit 0, reboot and you should be back to normal.

Don't know when I'll be online again after the move so good luck.
Phil

---

### Post by BigGeoff on 2010-07-17
Hi Phil

Sorry to take up your time while you are in such a stressful situation, one I can completely sympathise with as we are doing just that at work and will soon be moving house as well, so when you get back on line, here's what's been going on..........

I took a look at /etc/init.d/mythtv-backend and it didn't contain the line you quoted, lots of references to upstart but no line started 'start)'.. I figured that if I removed that file (in fact a link) to another place then it just wouldn't try to start the backend – same effect as what you suggested, or so I thought. Well on reboot it just shut down again. Also tried starting X from the recovery shell then running the backend setup from there but although root was in the mythtv group I kept falling over with database errors – failure to open this that or the other etc. My mythbox has been down for a month now and I think it is time to bite the bullet and reinstall.

Thanks for your all your help – I learned a number of things that I can file away and use somewhere else later even though I couldn't fix this problem.

Geoff

---

### Post by alien878 on 2010-07-20
BigGeoff,

I would suggest you start in safe mode and edit myth-halt.sh to add an "exit 0" at the top so that it doesn't shutdown the system.  Then you can remove it from user job 4 to recover.

I don't have myth-halt.sh on my system.  Apparently, it was remove due to problems (see second last post [http://www.gossamer-threads.com/lists/mythtv/users/441726](http://www.gossamer-threads.com/lists/mythtv/users/441726) )

I suspect that shutting down the system from a user job is always going to be problematic.  (Problems such as what PhilWig suggested where the backend marks a job is run *after* it has run.... but if the job shuts down the computer, it will never be marked as run)

Any reason why you aren't looking at mythwelcome to do this?  It really isn't that difficult.

---

### Post by PhilWig on 2010-07-20
Geoff,
     It looks as if the start/stop mechanisms changed between 9.04 and 9.10 in favour of upstart, hence you not finding the start) 
line.  I'd agree that mythwelcome works well, once you've fathomed out how to set it.
Phil

---

### Post by BigGeoff on 2010-07-20
Hi guys

I did look briefly at Mythwelcome which oddly I only came across recently, however it looked a bit too much like hard work (and this wasn't......) and I had trouble even working out how to invoke it so I kind of gave up. Now, of course, it looks a bit more promising so as I have reinstalled 9.10 I think I will be looking at this next, although there appear to be many forum threads (here and other places) where mythwelcome has thrown up problems.

Cross fingers and watch this space

Geoff

---

### Post by alien878 on 2010-07-21
I'm sure you'll find a lot of scripts googling.  I've attached my scripts below which work on 9.10.

1. Put them somewhere and make them executable.

2. Run sudo mythwelcome-test-wakeup.sh to see if your ACPI works (it will shutdown computer and if it wakes up in 4 mins, it is working... don't forget to run with sudo)

3. Read the top of mythwelcome-set-alarm.sh for instructions on setup.

4. Enable mythwelcome in the mcp (This should then start up mythwelcome instead of mythfrontend... I can't remember for sure.  If it doesn't, then replace mythfrontend with mythwelcome in the startup manager)

mythwelcome-test-wakeup.sh```
#!/bin/sh

echo 0 > /sys/class/rtc/rtc0/wakealarm
echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm
cat /proc/driver/rtc
cat /proc/driver/rtc > /tmp/alarm
echo "Your computer is set to start up in 4 minutes using ACPI."
echo -n "Do you want to shutdown the computer now? (y/n): "
read shutdown
if [ "$shutdown" == "y" ]; then
    echo "\nShutting down now..."
    /sbin/poweroff
    
else
    echo "\nTo shutdown execute the following:"
    echo "sudo /sbin/poweroff"
fi
```

mythwelcome-set-alarm.sh:```
#!/bin/sh

# Instructions (replace /myth/bin/mythwelcome-set-alarm.sh with the full
# path of this file)

# Configure mythwelcome --setup page:
# Command to Set Wakeup Time:     sudo /myth/bin/mythwelcome-set-alarm.sh $time
# Wakeup Time Format:             time_t
# nvram-wakeup Restart Command:   Leave this blank
# Command to reboot:              sudo /sbin/reboot
# Command to shutdown:            sudo /sbin/poweroff
# Command to run Xterm:           xterm
# Command to start the Frontend:  /usr/bin/mythfrontend -l /var/log/mythtv/mythfrontend.log

# Configure mythtv-setup Shutdown/Wakeup Options page:
# Idletimeout (secs):             any value greater that 0
# Wakeup time format:             yyyy-MM-ddThh:mm:ss
# Set wakeup time command:        /usr/bin/mythshutdown --setwakeup $time
# Server Halt command:            /usr/bin/mythshutdown --shutdown
# Pre shutdown check command:     /usr/bin/mythshutdown --check 

# Configure /etc/sudoers by adding the following line without the #:
# mythtv ALL= NOPASSWD: /myth/bin/mythwelcome-set-alarm.sh, /sbin/reboot, /sbin/poweroff

echo 0 > /sys/class/rtc/rtc0/wakealarm      #this clears your alarm
echo $1 > /sys/class/rtc/rtc0/wakealarm     #this writes your alarm
cat /proc/driver/rtc > /var/log/wake_alarm
```

---

### Post by BigGeoff on 2010-07-22
Thanks alien878. I have entered both scripts, saved them and used the test script successfully and I have enabled Mythwelcome at startup instead of the FE. I have tried a few sample recordings, some of which have worked but others not so I will have to go over the steps and settings again (I copied and pasted the scripts). Hopefully I will get time for this over the weekend. 

I also can't seem to find a way of exiting mythwelcome once invoked.

Geoff

---

### Post by alien878 on 2010-07-23
FYI:  You generally never exit from mythwelcome.  To shutdown, you just exit from the frontend to the mythwelcome window.  If nothing is recording/transcoding/etc., the mythwelcome will show a countdown (the idle timeout you configured).  When it gets to zero, it will shutdown the computer.  If something is recording/transcoding/etc., it will display why it isn't shutting down.

You might want to take a look at at least the introduction part of [http://www.mythtv.org/wiki/Mythwelcome](http://www.mythtv.org/wiki/Mythwelcome) (the setup info in the wiki is a bit out of date, but the intro explains how it all works)

---

### Post by BigGeoff on 2010-07-24
I wanted to check some stuff in BE setup etc. so wanted to get back to the desktop but as I have set the startup programs to include mythwelcome........ Guess I will have to go in via the safe boot mode and startx again to remove mythwelcome from the startup programs.

I set up a string of 6 recordings with gaps of 30-60 minutes between the end of one and start of the next and none of them recorded. I also note that when I start it up manually, it goes to mythwelcome then a box flicks on the screen stating it can't connect to the backend, then the system starts the FE on it's own so wondering if there is a clue to whats going on there? I also seem to be experiencing some problem with the program guide. Start it up then go along a channel with the arrow keys and it's fine but try to go up or down to another channel and it hangs for about 20-30 seconds every time.

Geoff

---

### Post by alien878 on 2010-07-26
Going into the backend setup:

No need to boot in safe mode.  Just ALT-F2, enter "xterm" to start an xterm, then run mythtv-setup.  Also, ALT-TAB will cycle through windows and bring eventually bring up the gnome menu at the top.

Programs not recording:

Did the computer shutdown after the mythwelcome countdown?  This is important.  If you shutdown the computer any other way, it will not set the wakeup.  If it did shutdown correctly, check the backend logs.  Error messages on setting the wakeup appear in there.

Warning about not connecting to the backend:

This is common, but it isn't a problem.  Improvements in the ubuntu boot process have caused the backend to start later then mythwelcome.  Once the backend starts, the error goes away.

Frontend starting automatically:

That's how it's supposed to work if you started the computer manually.

Slow program guide:

I noticed this in 0.22, but it improved significantly in 0.23.  Not sure what is going on.

---

### Post by BigGeoff on 2010-07-26
OK I forgot about Alt-F2 which works ok.

Although it has shutdown correctly on some occasions it wont do it now. When you exit the FE:-
1. Slight delay then Mythwelcome screen appears.
2. display says Mythtv is idle and will 'shutdown in 15 seconds'.
3. After 10 seconds it changes to 'shutdown in 5 seconds'
4. After a further 7-8 seconds it just goes back to step 2 again and that's where it sticks.

Here is some of my log:

```
2010-07-26 19:48:25.394 Running the command to set the next scheduled wakeup time :-
						/usr/bin/mythshutdown --setwakeup 2010-07-27T20:55
2010-07-26 19:48:25.501 Running the command to shutdown this computer :-
						/usr/bin/mythshutdown --shutdown
/home/geoff/mythwelcome-set-alarm.sh: 25: cannot create /sys/class/rtc/rtc0/wakealarm: Permission denied
/home/geoff/mythwelcome-set-alarm.sh: 26: cannot create /sys/class/rtc/rtc0/wakealarm: Permission denied
/home/geoff/mythwelcome-set-alarm.sh: 27: cannot create /var/log/wake_alarm: Permission denied
2010-07-26 19:48:25.908 ServerHaltCommand failed, shutdown aborted
2010-07-26 19:48:27.935 I'm idle now... shutdown will occur in 15 seconds.
2010-07-26 19:48:42.698 MainServer::ANN Monitor
2010-07-26 19:48:42.715 adding: geoff-shuttle as a client (events: 0)
2010-07-26 19:48:42.733 MainServer::ANN Monitor
2010-07-26 19:48:42.765 adding: geoff-shuttle as a client (events: 1)
2010-07-26 19:48:42.810 CheckShutdownServer returned - OK to shutdown
2010-07-26 19:48:42.841 Running the command to set the next scheduled wakeup time :-
						/usr/bin/mythshutdown --setwakeup 2010-07-27T20:55
2010-07-26 19:48:42.923 Running the command to shutdown this computer :-
						/usr/bin/mythshutdown --shutdown
/home/geoff/mythwelcome-set-alarm.sh: 25: cannot create /sys/class/rtc/rtc0/wakealarm: Permission denied
/home/geoff/mythwelcome-set-alarm.sh: 26: cannot create /sys/class/rtc/rtc0/wakealarm: Permission denied
/home/geoff/mythwelcome-set-alarm.sh: 27: cannot create /var/log/wake_alarm: Permission denied
2010-07-26 19:48:43.272 ServerHaltCommand failed, shutdown aborted
2010-07-26 19:48:45.307 I'm idle now... shutdown will occur in 15 seconds.
2010-07-26 19:48:59.445 MainServer::ANN Monitor
2010-07-26 19:48:59.480 adding: geoff-shuttle as a client (events: 0)
2010-07-26 19:48:59.498 MainServer::ANN Monitor
2010-07-26 19:48:59.531 adding: geoff-shuttle as a client (events: 1)
2010-07-26 19:48:59.577 CheckShutdownServer returned - OK to shutdown
2010-07-26 19:48:59.606 Running the command to set the next scheduled wakeup time :-
						/usr/bin/mythshutdown --setwakeup 2010-07-27T20:55
2010-07-26 19:48:59.689 Running the command to shutdown this computer :-
						/usr/bin/mythshutdown --shutdown
/home/geoff/mythwelcome-set-alarm.sh: 25: cannot create /sys/class/rtc/rtc0/wakealarm: Permission denied
/home/geoff/mythwelcome-set-alarm.sh: 26: cannot create /sys/class/rtc/rtc0/wakealarm: Permission denied
/home/geoff/mythwelcome-set-alarm.sh: 27: cannot create /var/log/wake_alarm: Permission denied
2010-07-26 19:49:00.201 ServerHaltCommand failed, shutdown aborted
2010-07-26 19:49:02.255 I'm idle now... shutdown will occur in 15 seconds.
```

---

### Post by alien878 on 2010-07-27
Ooops, my bad.  I cleaned up the comments on the script before I submitted it and forgot a sudo in the mythwelcome setup section.  mythwelcome-set-alarm.sh has to be run with sudo in the "Command to Set Wakeup Time".

I've updated the code in my original post.

---

### Post by BigGeoff on 2010-07-28
Due to an administrative error, there will be a short delay while I re-install and set up mythtv.

Whoops........

---

### Post by BigGeoff on 2010-07-29
Managed to screw up sudoers big time and in the process managed to prevent myself from editing it. You live and learn.....

Re-installed Mythtv and set everything back up including the setup items and modified script last night but no time to test it. However, it did shutdown when idle which is a good start!

Have set up some recordings so will see what is what when I get home from work.

Geoff

---

### Post by alien878 on 2010-07-29
> **BigGeoff said:**
> Managed to screw up sudoers big time and in the process managed to prevent myself from editing it. You live and learn.....Ouch...

In the future, you can fix things like this by booting from CD, mounting the drive and then fixing the file.  I keep a parted magic CD handy for cases like this.

Hope your recording works...

---

### Post by BigGeoff on 2010-07-29
Hmmmm bad news - doesn't want to wake up. Checked the mythwelcome setup page and I swear I had set this up according to the instructions in the script but some entries had changed back - the nvram-wakeup Restart command was filled in and I know I cleared that and the Command to set wakeup time was wrong. I changed them, went into and out of the frontend and shutdown and restarted a couple of times and it seems to have stuck but the machine wont wakeup. Logs don't really tell you anything as they are restarted on bootup.

Recording just started so further probing not practical now until tomorrow. At least it will shutdown OK.

Geoff

---

### Post by alien878 on 2010-07-30
The backend logs shouldn't clean up on re-boot.  Have you done something add a cleanup?  The backend logs really help when it comes to setting up mythwelcome.

The scripts also write the wakeup time in /var/log/wake_alarm.  You might want to look here to see if the time was set correctly.

Finally, the Wake Time Format *must* be "yyyy-MMTdd:hh:mm" (Note the "T").  This changed recently and a lot of the howto's out there are wrong.

---

### Post by BigGeoff on 2010-07-31
I was using the log grabber - better look at the individual files.

Didn't you mean the time format is yyyy-MM-ddThh:mm ?

Geoff

---

### Post by BigGeoff on 2010-07-31
Interesting, the check is being done, the wakeup seems to be being set correctly and shutdown  occurs aall without error but no wakeup????

```
2010-07-31 18:48:20.848 adding: geoff-shuttle as a client (events: 1)
2010-07-31 18:48:20.895 CheckShutdownServer returned - OK to shutdown
2010-07-31 18:48:20.927 Running the command to set the next scheduled wakeup time :-
						/usr/bin/mythshutdown --setwakeup 2010-07-31T19:55
2010-07-31 18:48:21.041 Running the command to shutdown this computer :-
						/usr/bin/mythshutdown --shutdown
2010-07-31 20:12:09.954 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-07-31 20:12:10.046 Using runtime prefix = /usr
```

This was set to start up again at 19:55 yet just sat there.

Geoff

---

### Post by alien878 on 2010-08-01
Yes, the format is yyyy-MM-ddThh:mm.

What is in /var/log/wake_alarm?  The script dumps the bios wakeup settings here for debugging.

---

### Post by BigGeoff on 2010-08-01
There is no file 'wake-alarm' in /var/log/

while searching through things yet again last night I realised that in my backend setup, shutdown/wakeup page the first entry 'Startup command' is empty- should there be something in there?

---

### Post by PhilWig on 2010-08-01
Yes, my startup command is blank too: but it's version 9.04.
To summarise my settings:

1. mythwelcome --setup:

   Command to set wakeup       sudo sh -c "/usr/bin/setwakeup.sh $time"
   Wakeup time format          time_t
   nvram -wakeup restart       <blank>
   Command to reboot           <blank>
   Command to shutdown         sudo shutdown -h now
   Command to run xterm        xterm
   Command to start frontend   /usr/bin/mythfrontend
           or:  /usr/bin/mythfrontend --service for logging to /var/log/mythtv/mythfrontend.log


2. backend control centre > general >>>>> shutdown/Wakeup:

   Startup command                <blank>
   Block shutdown                 ticked
   Idle shutdown                   60                 
   Max wait for recording (mins)   10
   Startup before rec (secs)      180
   Wakeup time format             yyyy-MM-dd:hh:mm
   Command to set wakeup          mythshutdown --setwakeup $time
   Server halt command            mythshutdown --shutdown
   pre shutdown command           mythshutdown --check

Note the time format with the ':' not the T.  This works for me but T might be safer as observed by another subscriber.

hope this helps.

Phil

---

### Post by alien878 on 2010-08-01
The file is /var/log/wake_alarm.  The script I posted earlier cat's the bios settings into this file.

The startup command should be empty.

The "T" in the time format was a change in 0.23.  I'm not sure if it was accepted on 0.22.  /var/log/wake_alarm output will tell you if the time is set in BIOS correctly.

(I'm on-the-road for the next couple of weeks, so I may not be able to answer quickly).

---

### Post by BigGeoff on 2010-08-02
alien878
yes I see the line in the script, but there definitely isn't a file with that name in that folder. I will have to do some serious rooting around and see where things are going wrong. Good luck on the road.

PhilWig
It is interesting to see the differences in your settings and those of alien878, maybe a bit more experimentation is required here. Lets hope I don't screw something else up this time ;-D

My thanks to both of you for your continued sufference

Geoff

---

### Post by BigGeoff on 2010-08-10
Back again.

Not been idle but busy, however, I have now reached the tearing out of hair stage. After several minor alterations I returned all the settings to those shown in alien878's post of mythwelcome-set-alarm. One night it recorded a program yet stayed on until morning and the logs seemed to indicate it had been foiled by some housekeeping job that kept getting triggered and preventing shutdown.

I have been through the configuration settings shown in the comments of the script line by line and with the exception of the placing of the file (I have it in /home/geoff/mythwelcome-set-alarm.sh) - everything checks out exactly as shown yet it refuses to wake up but with that one exception seems to shutdown ok. There are no error messages I can see in the backend log, it does the check, the time setting then the shutdown. Just doesn't wake up. I even re-checked with mythwelcome-test-wakeup and thats ok too.

Any more ideas guys cos I'm getting fried by this.

Geoff

---

### Post by alien878 on 2010-08-11
It is odd that you don't have a /var/log/wake_alarm because the backend logs indicate the script is run and that script should throw an error if it can't write to that file.

Anyway.....  Try the following:

1. Log in as mythtv (important) and run:
```
sudo /myth/bin/mythwelcome-set-alarm.sh xxxx
```
where xxxx is the number you get with 
```
date '+%s' -d '+ 5 minutes'
```

Does that create a /var/log/wake_alarm?  If not, that has to be fixed (there should be some error printed to point the way).

2. If /var/log/wake_alarm was created, delete it.  Try setting the Command to Set Wakeup Time to
```
sudo sh -c "/myth/bin/mythwelcome-set-alarm.sh $time"
```(replace with the correct path to your mythwelcome-set-alarm.sh).  If this works, let me know and I'll update the script (I saw someone else do this and didn't know why.... it could be something in your default sh setup)

---

### Post by BigGeoff on 2010-08-13
I have been preparing to go on holiday so have not had time to do anything but can I ask a daft question - how do I log on as mythtv? if I log out as geoff the XFCE login screen  doesn't show mythtv as a user and I don't know what the password would be anyway.

I did alter the mythshutdowns to report in verbose mode and there is lots to look at but still shows no errors!

And I think I have to use bash not sh to get things to work.

Back in a week 

Geoff

---

### Post by alien878 on 2010-08-15
The easiest way to get in as mythtv is ALT-F2 from the frontend then start an xterm.  This should be user mythtv (the id command will tell you for sure).  To reset the mythtv password, use sudo passwd mythtv and enter a new password.

Have fun!

---

### Post by BigGeoff on 2010-08-21
Back from hols.

When I open a terminal (F2 > xterm) is shows geoff@geoff-shuttle:~$ and id just confirms I am logged in as geoff - is that not odd? I can only remember the startup account being mentioned in the installation and I can't find any other mention of it so have I screwed up at the install or just missed a setting somewhere?

Wait - fount it in Mythbuntu control centre it's set to automatically log in as geoff but although there is a dropdown arrow there is no list when you click on it so again I have to ask - did I screw up when I installed?

Geoff

---

### Post by alien878 on 2010-08-21
My mistake.  I was thinking of another distro that used mythtv for the frontend.

You can sudo passwd mythtv to set the mythtv password.  Then su mythtv.

---

### Post by BigGeoff on 2010-08-21
Just looked up the users in applications>system>users and groups and guess what  - there is no mythtv listed as a user just root and geoff. I feel that there is something deeply wrong here, not the least of which involves me not understanding something.

Geoff

---

### Post by alien878 on 2010-08-22
Not all users are listed there.  If you do a ps -ef | grep backend, you can see the user used to run the backend (which will be the one to run the shutdown).  You can still su to that user if you set the password.  The backend isn't showing anything useful.  You might see something if you run the command from the command line.

I'll be travelling again.  I'll check my emails occasionally, but it may take a few days for me to respond.

---

### Post by BigGeoff on 2010-08-26
Finally got some time to work on this but not much.

Managed to successfully change mythtv password and logged on as same. Ran commands and /var/log/wake alarm was created and contained this:
```
rtc_time	: 08:20:19
rtc_date	: 2010-08-26
alrm_time	: 08:22:24
alrm_date	: 2010-08-26
alarm_IRQ	: yes
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: yes
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay

```
and the times confirm that it had just been created and not from an earlier attempt.

The shell command you suggest was also mentioned by PhilWig earlier in the thread and I thought I had tried that once but tried it again anyway. However, if I start up the system then escape the frontend then press F11, I get the setup page but it still shuts down before I can alter the command to set the wakeup time. Have to go now but more work required.

Later: extended the shutdown delay and edited the shutdown command as suggested but still does not wake up. The verbose output from the backend log on shutdown is:
```
2010-08-27 19:15:04.879 Mythshutdown: --status returned: 0
2010-08-27 19:15:04.961 OK to shutdown
2010-08-27 19:15:04.977 Mythshutdown: --check returned: 0
2010-08-27 19:15:04.994 MythSocket(9b44870:8): DownRef: -1
2010-08-27 19:15:05.011 MythSocket(9b44870:8): state change Connected -> Idle
2010-08-27 19:15:05.028 MSocketDevice::close: Closed socket 8
2010-08-27 19:15:05.061 MythSocket(9b44870:-1): delete socket
2010-08-27 19:15:05.117 MythSocket(9b2de60:9): DownRef: 0
2010-08-27 19:15:05.027 ProcessAddRemoveQueues
2010-08-27 19:15:05.159 Construct FD_SET
2010-08-27 19:15:05.176 Waiting on select..
2010-08-27 19:15:05.193 Got data on select
2010-08-27 19:15:05.210 Processing ready reads
2010-08-27 19:15:05.227 MythSocketThread: Total read time: 0ms, on sockets
2010-08-27 19:15:05.244 Reacquired ready read lock
2010-08-27 19:15:05.260 MythSocketThread: readyread thread exit
2010-08-27 19:15:05.291 CheckShutdownServer returned - OK to shutdown
2010-08-27 19:15:05.355 Running the command to set the next scheduled wakeup time :-
						/usr/bin/mythshutdown --setwakeup 2010-08-27T19:30 -v all
2010-08-27 19:15:05.418 (old)Settings::ReadSettings(settings.txt) - No such file
2010-08-27 19:15:05.450 Using runtime prefix = /usr
2010-08-27 19:15:05.467 Using configuration directory = /home/mythtv/.mythtv
2010-08-27 19:15:05.484 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBHostName' = 'localhost'.
2010-08-27 19:15:05.501 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBUserName' = 'mythtv'.
2010-08-27 19:15:05.518 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBPassword' = 'M5nkfpQX'.
2010-08-27 19:15:05.534 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBName' = 'mythconverg'.
2010-08-27 19:15:05.551 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBType' = 'QMYSQL3'.
2010-08-27 19:15:05.585 (old)Settings::ReadSettings(/usr/etc/mythtv/mysql.txt) - No such file
2010-08-27 19:15:05.649 (old)Settings::ReadSettings(/home/mythtv/.mythtv/mysql.txt) - 'DBHostName' = 'localhost'.
2010-08-27 19:15:05.666 (old)Settings::ReadSettings(/home/mythtv/.mythtv/mysql.txt) - 'DBUserName' = 'mythtv'.
2010-08-27 19:15:05.683 (old)Settings::ReadSettings(/home/mythtv/.mythtv/mysql.txt) - 'DBPassword' = 'M5nkfpQX'.
2010-08-27 19:15:05.700 (old)Settings::ReadSettings(/home/mythtv/.mythtv/mysql.txt) - 'DBName' = 'mythconverg'.
2010-08-27 19:15:05.717 (old)Settings::ReadSettings(/home/mythtv/.mythtv/mysql.txt) - 'DBType' = 'QMYSQL3'.
2010-08-27 19:15:05.734 (old)Settings::ReadSettings(./mysql.txt) - No such file
2010-08-27 19:15:05.750 Empty LocalHostName.
2010-08-27 19:15:05.767 Using localhost value of geoff-shuttle
2010-08-27 19:15:05.801 MCP::DefaultUPnP() - No default UPnP backend
2010-08-27 19:15:05.865 Clearing Settings Cache.
2010-08-27 19:15:05.889 New DB connection, total: 1
2010-08-27 19:15:05.912 Connected to database 'mythconverg' at host: localhost
2010-08-27 19:15:05.924 Closing DB connection named 'DBManager0'
2010-08-27 19:15:05.941 Clearing Settings Cache.
2010-08-27 19:15:05.958 Enabling Settings Cache.
2010-08-27 19:15:05.975 Clearing Settings Cache.
2010-08-27 19:15:05.992 Mythshutdown: --setwakeup
2010-08-27 19:15:06.009 Mythshutdown: wakeup time given is: 2010-08-27T19:30
2010-08-27 19:15:06.043 Connected to database 'mythconverg' at host: localhost
2010-08-27 19:15:06.096 MSqlQuery::exec() "DELETE FROM settings WHERE value = 'MythShutdownNextScheduled';"
2010-08-27 19:15:06.151 MSqlQuery::exec() "INSERT INTO settings ( value, data ) VALUES ( 'MythShutdownNextScheduled', '2010-08-27T00:00:00' );"
2010-08-27 19:15:06.218 Running the command to shutdown this computer :-
						/usr/bin/mythshutdown --shutdown -v all
2010-08-27 19:15:06.298 (old)Settings::ReadSettings(settings.txt) - No such file
2010-08-27 19:15:06.332 Using runtime prefix = /usr
2010-08-27 19:15:06.348 Using configuration directory = /home/mythtv/.mythtv
2010-08-27 19:15:06.366 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBHostName' = 'localhost'.
2010-08-27 19:15:06.382 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBUserName' = 'mythtv'.
2010-08-27 19:15:06.399 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBPassword' = 'M5nkfpQX'.
2010-08-27 19:15:06.416 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBName' = 'mythconverg'.
2010-08-27 19:15:06.449 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBType' = 'QMYSQL3'.
2010-08-27 19:15:06.474 (old)Settings::ReadSettings(/usr/etc/mythtv/mysql.txt) - No such file
2010-08-27 19:15:06.530 (old)Settings::ReadSettings(/home/mythtv/.mythtv/mysql.txt) - 'DBHostName' = 'localhost'.
2010-08-27 19:15:06.547 (old)Settings::ReadSettings(/home/mythtv/.mythtv/mysql.txt) - 'DBUserName' = 'mythtv'.
2010-08-27 19:15:06.564 (old)Settings::ReadSettings(/home/mythtv/.mythtv/mysql.txt) - 'DBPassword' = 'M5nkfpQX'.
2010-08-27 19:15:06.581 (old)Settings::ReadSettings(/home/mythtv/.mythtv/mysql.txt) - 'DBName' = 'mythconverg'.
2010-08-27 19:15:06.598 (old)Settings::ReadSettings(/home/mythtv/.mythtv/mysql.txt) - 'DBType' = 'QMYSQL3'.
2010-08-27 19:15:06.615 (old)Settings::ReadSettings(./mysql.txt) - No such file
2010-08-27 19:15:06.631 Empty LocalHostName.
2010-08-27 19:15:06.648 Using localhost value of geoff-shuttle
2010-08-27 19:15:06.666 MCP::DefaultUPnP() - No default UPnP backend
2010-08-27 19:15:06.690 Clearing Settings Cache.
2010-08-27 19:15:06.761 New DB connection, total: 1
2010-08-27 19:15:06.785 Connected to database 'mythconverg' at host: localhost
2010-08-27 19:15:06.797 Closing DB connection named 'DBManager0'
2010-08-27 19:15:06.814 Clearing Settings Cache.
2010-08-27 19:15:06.830 Enabling Settings Cache.
2010-08-27 19:15:06.847 Clearing Settings Cache.
2010-08-27 19:15:06.864 Mythshutdown: --shutdown
2010-08-27 19:15:06.915 Connected to database 'mythconverg' at host: localhost
2010-08-27 19:15:06.957 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'DailyWakeupStartPeriod1' AND hostname IS NULL;"
2010-08-27 19:15:07.022 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'DailyWakeupEndPeriod1' AND hostname IS NULL;"
2010-08-27 19:15:07.038 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'DailyWakeupStartPeriod2' AND hostname IS NULL;"
2010-08-27 19:15:07.055 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'DailyWakeupEndPeriod2' AND hostname IS NULL;"
2010-08-27 19:15:07.071 no daily wakeup times are set
2010-08-27 19:15:07.089 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'MythShutdownNextScheduled' AND hostname IS NULL;"
2010-08-27 19:15:07.105 recording scheduled at: 2010-08-27T00:00:00
2010-08-27 19:15:07.122 Scheduled recording time has already passed. Schedule deleted
2010-08-27 19:15:07.140 MSqlQuery::exec() "DELETE FROM settings WHERE value = 'MythShutdownNextScheduled';"
2010-08-27 19:15:07.156 MSqlQuery::exec() "INSERT INTO settings ( value, data ) VALUES ( 'MythShutdownNextScheduled', '' );"
2010-08-27 19:15:07.173 no wake up time set and no scheduled program
2010-08-27 19:15:07.207 MSqlQuery::exec() "DELETE FROM settings WHERE value = 'MythShutdownWakeupTime';"
2010-08-27 19:15:07.262 MSqlQuery::exec() "INSERT INTO settings ( value, data ) VALUES ( 'MythShutdownWakeupTime', '' );"
2010-08-27 19:15:07.280 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'MythShutdownNvramRestartCmd' AND hostname = 'geoff-shuttle' ;"
2010-08-27 19:15:07.296 everything looks fine, shutting down ...
2010-08-27 19:15:07.314 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'MythShutdownPoweroff' AND hostname = 'geoff-shuttle' ;"
2010-08-27 19:15:07.332 ..
2010-08-27 19:15:07.346 .
2010-08-27 19:15:07.363 shutting down ...
2010-08-28 09:36:17.933 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-08-28 09:36:18.023 Using runtime prefix = /usr
2010-08-28 09:36:18.280 Using configuration directory = /home/mythtv/.mythtv
2010-08-28 09:36:18.476 Empty LocalHostName.
2010-08-28 09:36:18.682 Using localhost value of geoff-shuttle
2010-08-28 09:36:19.173 New DB connection, total: 1
2010-08-28 09:36:19.976 Unable to connect to database!
2010-08-28 09:36:20.091 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

...............................................................................
```

I can only see some references to files not existing, otherwise it all looks error free, although having said that , most if it is above my head..

Geoff

---

### Post by alien878 on 2010-08-29
```
2010-08-27 19:15:06.009 Mythshutdown: wakeup time given is: 2010-08-27T19:30
2010-08-27 19:15:06.151 MSqlQuery::exec() "INSERT INTO settings ( value, data ) VALUES ( 'MythShutdownNextScheduled', '2010-08-27T00:00:00' );"
...
2010-08-27 19:15:07.105 recording scheduled at: 2010-08-27T00:00:00
2010-08-27 19:15:07.122 Scheduled recording time has already passed. Schedule deleted
```
That's weird.  The hour/second was deleted (notice 00:00:00).  I suggest that you add :ss to the time format.

Sometimes, I really wish the myth people would not make unnecessary non-backward compatible changes....

I am travelling again, so I may not answer right away.  Good luck!

---

### Post by BigGeoff on 2010-08-30
OK reverted to previous instruction to set the time, added the :ss to the time format, now it keeps rebooting rather than just shutting down. Assuming that returning a value of 0 means no errors then the time is setting ok now but why the reboot?

```
2010-08-30 17:35:57.423 Mythshutdown: --setwakeup
2010-08-30 17:35:57.440 Mythshutdown: wakeup time given is: 2010-08-30T17:55:00
2010-08-30 17:35:57.457 Connected to database 'mythconverg' at host: localhost
2010-08-30 17:35:57.475 MSqlQuery::exec() "DELETE FROM settings WHERE value = 'MythShutdownNextScheduled';"
2010-08-30 17:35:57.491 MSqlQuery::exec() "INSERT INTO settings ( value, data ) VALUES ( 'MythShutdownNextScheduled', '2010-08-30T17:55:00' );"
2010-08-30 17:35:57.532 Running the command to shutdown this computer :-
						/usr/bin/mythshutdown --shutdown -v all
2010-08-30 17:35:57.628 (old)Settings::ReadSettings(settings.txt) - No such file
2010-08-30 17:35:57.655 Using runtime prefix = /usr
2010-08-30 17:35:57.672 Using configuration directory = /home/mythtv/.mythtv
2010-08-30 17:35:57.689 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBHostName' = 'localhost'.
2010-08-30 17:35:57.706 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBUserName' = 'mythtv'.
2010-08-30 17:35:57.722 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBPassword' = 'M5nkfpQX'.
2010-08-30 17:35:57.739 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBName' = 'mythconverg'.
2010-08-30 17:35:57.756 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBType' = 'QMYSQL3'.
2010-08-30 17:35:57.773 (old)Settings::ReadSettings(/usr/etc/mythtv/mysql.txt) - No such file
2010-08-30 17:35:57.790 (old)Settings::ReadSettings(/home/mythtv/.mythtv/mysql.txt) - 'DBHostName' = 'localhost'.
2010-08-30 17:35:57.823 (old)Settings::ReadSettings(/home/mythtv/.mythtv/mysql.txt) - 'DBUserName' = 'mythtv'.
2010-08-30 17:35:57.879 (old)Settings::ReadSettings(/home/mythtv/.mythtv/mysql.txt) - 'DBPassword' = 'M5nkfpQX'.
2010-08-30 17:35:57.896 (old)Settings::ReadSettings(/home/mythtv/.mythtv/mysql.txt) - 'DBName' = 'mythconverg'.
2010-08-30 17:35:57.913 (old)Settings::ReadSettings(/home/mythtv/.mythtv/mysql.txt) - 'DBType' = 'QMYSQL3'.
2010-08-30 17:35:57.930 (old)Settings::ReadSettings(./mysql.txt) - No such file
2010-08-30 17:35:57.947 Empty LocalHostName.
2010-08-30 17:35:57.964 Using localhost value of geoff-shuttle
2010-08-30 17:35:57.981 MCP::DefaultUPnP() - No default UPnP backend
2010-08-30 17:35:57.998 Clearing Settings Cache.
2010-08-30 17:35:58.038 New DB connection, total: 1
2010-08-30 17:35:58.078 Connected to database 'mythconverg' at host: localhost
2010-08-30 17:35:58.145 Closing DB connection named 'DBManager0'
2010-08-30 17:35:58.162 Clearing Settings Cache.
2010-08-30 17:35:58.179 Enabling Settings Cache.
2010-08-30 17:35:58.196 Clearing Settings Cache.
2010-08-30 17:35:58.213 Mythshutdown: --shutdown
2010-08-30 17:35:58.230 Connected to database 'mythconverg' at host: localhost
2010-08-30 17:35:58.248 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'DailyWakeupStartPeriod1' AND hostname IS NULL;"
2010-08-30 17:35:58.264 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'DailyWakeupEndPeriod1' AND hostname IS NULL;"
2010-08-30 17:35:58.281 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'DailyWakeupStartPeriod2' AND hostname IS NULL;"
2010-08-30 17:35:58.314 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'DailyWakeupEndPeriod2' AND hostname IS NULL;"
2010-08-30 17:35:58.378 no daily wakeup times are set
2010-08-30 17:35:58.396 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'MythShutdownNextScheduled' AND hostname IS NULL;"
2010-08-30 17:35:58.412 recording scheduled at: 2010-08-30T17:55:00
2010-08-30 17:35:58.429 will wake up at next scheduled program
2010-08-30 17:35:58.446 MSqlQuery::exec() "DELETE FROM settings WHERE value = 'MythShutdownWakeupTime';"
2010-08-30 17:35:58.463 MSqlQuery::exec() "INSERT INTO settings ( value, data ) VALUES ( 'MythShutdownWakeupTime', '2010-08-30T17:55:00' );"
2010-08-30 17:35:58.480 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'MythShutdownNvramRestartCmd' AND hostname = 'geoff-shuttle' ;"
2010-08-30 17:35:58.497 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'MythShutdownNvramCmd' AND hostname = 'geoff-shuttle' ;"
2010-08-30 17:35:58.514 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'MythShutdownWakeupTimeFmt' AND hostname = 'geoff-shuttle' ;"
2010-08-30 17:35:58.547 sending command to set time in bios
			sudo /home/geoff/mythwelcome-set-alarm.sh 1283187300
2010-08-30 17:35:58.824 sudo /home/geoff/mythwelcome-set-alarm.sh 1283187300 exited with code 0
2010-08-30 17:35:58.844 everything looks fine, but reboot is needed
2010-08-30 17:35:58.861 sending command to bootloader ...
2010-08-30 17:35:58.878  
2010-08-30 17:35:58.899 ..
```

And I also note that  the file /var/log/wake_alarm does not get created, although it did on the test run the other day.

Geoff

---

### Post by alien878 on 2010-09-10
The missing log file is strange.  Are your mythwelcome-set-alarm.sh and sudoers files correct?

As for the reboot, it looks like you have somehow triggered some old nvram-wakeup reboot code.  I can no longer find the documentation on this it is so old.... you could try setting the reboot command in mythwelcome --setup to be sudo /sbin/poweroff...

---

### Post by BigGeoff on 2010-09-22
Sorry Alien878 I have been so distracted lately - looks like I might be finally moving home and in a short time too so I doubt if I will be able to concentrate on this for a few months now. Many thanks for all you effort, maybe I will open up a new thread when I get the family settled in.

Geoff

---

