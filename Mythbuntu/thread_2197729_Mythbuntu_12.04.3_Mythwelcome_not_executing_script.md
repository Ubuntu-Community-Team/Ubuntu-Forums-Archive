---
title: "Mythbuntu 12.04.3: Mythwelcome not executing scripts"
date: 2014-01-05
forum: Mythbuntu
---

### Post by marco.hahn2 on 2014-01-05
I have serious trouble (and been spending some time already) getting mythwelcome executing the "Set wakeup time command", "Server Halt command", and "Pre shutdown check command".

The commands themselves -- if called from a shell -- execute OK (albeit with a different user than "mythtv", but both users have the same entries in the sudoers file). After long testing, I put diagnostic shell scripts instead of calling mythshutdown etc. And these scripts are not executed as well! What is wrong here?

My system is a Mythbuntu 12.04.3 upgraded over an existing Mythbuntu 10.4 installation.

Any help is highly welcome! I will supply additional info if required.

Thanks,
Marco

---

### Post by marco.hahn2 on 2014-01-05
I found out that whereas mythbackend runs as user "mythtv", mythwelcome and mythfrontend do use the standard user on that machine. May this cause the problems?

---

### Post by khPWXxF on 2014-01-09
Yes, getting mythwelcome going can be frustrating!
 
I&#8217;m also using 12.04 &#8211; Welcome is all working apart from the reluctance of mythwelcome to refresh screen when exiting frontend &#8211; purely cosmetic and easily fixed with ^F2 but I froze updates about a year ago so that&#8217;s probably fixed by now.
 
I did a fresh install of 12.04, and transferred database from 9.04 via an intermediate version &#8211; 10.10 I think. The upgrade route failed for me.
 
Yes, backend runs under mythtv,  frontend and welcome under your user.

A few checks:
1.  Anything useful in the logs in /var/log/mythtv?
2..  No remote frontends running?
3, You are not within 15 minutes of next recording?  There is a value for this somewhere in the setup pages but it is ignored (or has a 15 min lower limit?).
4. Your setting up of diagnostic scripts is a good idea &#8211; something like
 
```
#!/bin/bash
echo "$(date +%F" "%T) $(whoami) called $0 $1 $2" >> /home/phil/my.log
exit
 
```
is a very powerful tool but even a simple &#8216;touch&#8217; will tell you lots.
 
5.  Permissions ok?   Eg 755 for your scripts & executables, 666 for log files.
6.  What does your welcome screen say?  Busy?  Closing down?
7.  What do you get if you do this:
```
     
/usr/bin/mythshutdown &#8211;check
echo $?
```
You should get zero if it&#8217;s ready to close down.
 
8.  If it helps you, I took notes when I set up welcome.  Rather terse but they are in this thread under my preferred alias of PhilB:
[http://www.mythtvtalk.com/hibernate-myth-backend-wake-up-recordings-16831/](http://www.mythtvtalk.com/hibernate-myth-backend-wake-up-recordings-16831/)
 
9.  When you do finally get it going, you&#8217;ll find that the exit from frontend needs a prompt.  Introduced I think in 12.04.  If you want to avoid this, set  frontend > setup > edit keys > main menu > exit to Esc and Exitprompt to blank.

Best wishes
Phil

---

### Post by tuat2 on 2014-01-09
It may sound like a dumb question, but I actually ran into the same problem.

There is a switch in the backend setup called "Wait for Frontend", which prevents any shutdown action before there wasn't at lease one fronend connecting to the backend. Did you untick that one?


You didn't write, whether the idle timer actually reaches zero, so another problem may be EIT scan. If you are using OTA-EIT, you may want to set the "max idle time" to a value lower than 300 seconds (I use 240). Per default, the EIT-scanner runs every 5 minutes and resets the shutdown timer. There was a patch to prevent the EIT-scanner from resetting the shutdown timer, but that never really worked reliably.

For testing I recommend to use a /etc/sudoers line like this:
```

%mythtv ALL = NOPASSWD: ALL

```
That'll prevent issues with sudo-rights. Later on, you may use a line like this to restrict sudo access:
```

%mythtv ALL = NOPASSWD: /sbin/shutdown, /bin/sh, /usr/bin/setwakeup.sh, /usr/bin/mythshutdown

```

I hope I could help.

---

### Post by marco.hahn2 on 2014-01-12
Thanks for the help, Phil.

I partially followed up on the leads you provided:
2: No remote frontends running.
3: More than 15 minutes time till next recording.
5: Permissions OK for my diagnostic script, mythshutdown, log files, storage directories for log files.
6: Welcome says "Idle".
7: I get zero.

I then followed also up with the other reply from tuat2 (see below).

---

### Post by marco.hahn2 on 2014-01-12
The "wait for frontend" tick is set, but I went to frontend and out again, so the shutdown actions should be executed.

The OTA-EIT max idle time was already at less than 300s.

I changed /etc/sudoers to the testing code you suggested (even though I already thought to have everything sudoable as with the second code example).



After trying this and Phils ideas and nothing happening as quick as before with v0.24 on Ubuntu 11.04, all the sudden the countdown timer starts (but does not decrease as before in 10s decrements) and after about twice the announced time, the box suddenly shuts down?! I did some further testing (recording 20 minutes in the future) and everything looks fine.

Thanks for the help, it works now. I do not really know which of the actions did the trick, but I will restrict /etc/sudoers, as this is my prime suspect.

The most important lecture was to be patient. My old installation was faster with shutting down, did not have redraw-problems in mythwelcome and was also exactly telling me the remaining count down time. This one does not, but seems to work right now.

---

### Post by tuat2 on 2014-01-12
I have the same issue with the idle timer/mythwelcome sceeen not updating properly. It was introduced in 0.25-fixes at some point (I guess). For me, it only updates about once very 60 seconds. If I am lucky.

If shutdown takes twice the idle time, the EIT scanner probably reset it once. I'd consider it a "working solution", tho. ^^

---

### Post by marco.hahn2 on 2014-01-14
This whole thing is weird. Sunday afternoon everything looks fine, normal use and several automatic starts occurring just as planned (albeit with a sometimes long wait before status updates in mythwelcome).

Yesterday evening I tried mythmote and MythTV Android Frontend from my tablet, and all the sudden shutdown is not occurring anymore! Even switching off the tablet and doing several reboots of the mythtv machine from the shell did not help.

This morning, the machine suddenly reboots instead of shutting down.

/var/log/mythtv/mythbackend.log is the only file with new information. It only contains logs about setting the shutdown timer, unchanged (except for the times set) since before it worked, when it worked and now.

However, the output of mythshutdown --shutdown -v shows differs: see mythshutdown.20140112211240.3935.log.txt for a successful shutdown and mythshutdown.20140114051514.2920.log.txt for a failed shutdown (this morning).

Any ideas?

---

### Post by alien878 on 2014-01-14
Looking at the logfiles, it appears you are using the old nvram_wakeup and it fails when it detects that a reboot is needed.  You should check the nvram reboot command you are using works and is in the sudoers file.

However:  There have been a lot of changes since 10.4.  I would recommend using ACPI wakeup instead of nvram wakeup.  It now works with almost all systems, is much simpler and (in my opinion) more reliable.  It also avoids the whole reboot thing.

Check out [http://www.mythtv.org/wiki/Mythwelcome](http://www.mythtv.org/wiki/Mythwelcome) for details.  It eventually points you to the ACPI page where the required mythwelcome setwakeup.sh is located.

---

### Post by marco.hahn2 on 2014-01-14
nvram_wakeup has a long history on my installation. :-/ I was using it years ago, but I am not right now, the logs are misleading. (In the code, I found parts where nvram-wakeup is contained hardcoded.) At some point during installation, I got errors about missing nvram_wakeup and installed the package, however, then I discovered that I was missing a valid nvram-wakeup.conf for my system. Thus I renamed /usr/sbin/nvram-wakeup. In fact, I am using ACPI wakeup (as is also evident from the fact that in BIOS no wakeup times are set).

To add to the confusion: Yesterday evening (without any further intervention), the system resumed working correctly?! The latest logs correspond to the good one from the first attachment.

---

### Post by alien878 on 2014-01-15
The error log indicates that the system is trying to do an nvram reboot.  It will do this occasionally do this if the system thinks nvram is being used.  I.e. There is a good chance the problem will come back.

What are your mythwelcome settings?  In particular, check that nvram restart is blank (completely blank, no spaces).

EDIT:  Actually, looking at the log, I see other nvram stuff going on that shouldn't be there.  Probably best if you post all your mythwelcome settings.

---

### Post by marco.hahn2 on 2014-01-28
Lately, the system is working OK in more than 90% of all shutdowns. Probably, I just have to be much more patient with the shutdown routines than with my previous mythTV installation.

Thanks for the help, I mark this thread as solved.

---

