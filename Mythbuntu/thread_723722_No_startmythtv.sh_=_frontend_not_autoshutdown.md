---
title: "No startmythtv.sh = frontend not autoshutdown"
date: 2008-03-13
forum: Mythbuntu
---

### Post by Blonddeeni on 2008-03-13
Hi There. 
Absolute beginner in the whole Forum /posting world, so I hope I'm in the correct place, and have the message format readable. 
My apologies if I have stuffed this up.

I Love the Mythbuntu setup. Only having one hassle, and probably due
to the fact I've wandered off into an unstable? SVN system sidegrade/upgrade? thingy.

I am running a backend / frontend on the same machine. Further specs are at the end of this post.

I've been trying to get my mythfrontend to shut down after an automatic start up, but no 
success so far. The system will auto-shutdown if I manually close the frontend and have no
other users (Me myself or I) logged on. It will then automatically restart and record a 
program, but once completed all of it's tasks, will not shutdown again because the 
frontend is running. (Unless I once again close the frontend manually).

I have not been able to get past this problem, and feel that it is something to do with the version
of mythtv that I am running, which does not come with the file: "/usr/share/mythtv/startmythtv.sh".
I have just now tried using the file "/etc/mythtv/session-settings" and enabling the two lines;
# Enable mythwelcome
# MYTHWELCOME=true
(by removing the "#" of course), and then continuing the instructions in the guide found at:

"https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake?" and doing the modification
in MythWakeSet of:

# store the wake time passed from mythbackend
##echo $1\ $2 > $temp_stamp
tmp=`echo $2 | awk -F: '{print strftime("%Y-%m-%dT%T", $1)}'`
tmp1=`echo $tmp | awk 'BEGIN { FS = "T" } { print $1 }'`
tmp2=`echo $tmp | awk 'BEGIN { FS = "T" } { print $2 }'`
echo $tmp1\ $tmp2 > $temp_stamp

And following the instructions on changing the setups in both mythwelcome and mythbackend.
[NB: This is the first time I had ever seen the Mythwelcome screen. Untill then, had always ended up
in the frontend screen].

Unfortunetly the system failed to automatically restart. So I am back to the original situation.
IE: If the frontend is not running, AND no other user is logged on, then the system will autoshutdown,
    wait for a recording time, restart and record, and remain running until I manually exit the frontend.
    Again, I suspect the fact that I have no startmythtv.sh. The only reference to it that I have found on my
system is in the file:

cat /usr/share/mythtv/mythfrontend.sh
#!/bin/sh
# Mario Limonciello, March 2007
# partially merged with startmythtv.sh by Michael Haas, October 2007

But learned the hard way NOT to tamper with this file at all. I tried putting the instructions from the guide
into the end of the file, 
IE: #start mythtv frontend software
    #exec mythfrontend
    sleep 5
    exec mythwelcome
 
and got a nasty loop occuring, consisting of a blank blue mythtv screen, that would replicate itself
every 5 seconds. D'OH!
Fixed by booting into Linux Recovery mode and re-editing the file to remove my screw-up.

My system consists of the following:
 - Motherboard m2npv-vm
 - cpu amd64 X2 5200+
 - 1GB Ram DDR800
 - 2 x 500G sata hard drives, (lvm to make 800G storage)
 - Mythbuntu (7.10) Gutsy Gibbon [if I understand the labelling system correctly. No gaurrentees].
 - Linux 2.6.22-14-generic #1 SMP Fri Feb 1 04:59:50 UTC 2008 i686 GNU/Linux
 - mythbackend --version
    Source code version     : Unknown
    SVN branch              : trunk
    Library API version     : 0.21.20080114-1
    Network Protocol Version: 38
    Options compiled in:
       linux debug using_oss using_alsa using_arts using_jack using_backend
       using_dbox2 using_dvb using_firewire using_frontend using_hdhomerun
       using_iptv using_ivtv using_joystick_menu using_lirc using_opengl_vsync

[By the way, I have only managed to get this far due to the absolutely excellent guide found at the site
"https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake?" which I belive was written
by a member called "majoridiot". Thank you so very much :) Whooo Hooo, it's been most enjoyable. Easy to
read and all steps follow-able :-))  ]


My Level of knowledge is as follows.

My experience with linux started 3 months ago, where all I knew was how to spell Linux, and three
commands; cp ls and clear. Since then I have wandered around the interweb,tried to follow threads,
tortured a mate who does know a few linux things, and have figured out how to get the following working.

 - lirc remote(s) [For Technisat SkyStar 2DVB-S card(s).]
 - An external serial modem (my only internet connection, max line speed has been 31.2K )
 - A Composite Tv to computer connection: Monitor is a LCD display.
 - Two DVB-S cards
 - Limited ethernet between this Mythbuntu box, a knoppix box (Pentium III 450 MHz, 20G hdd) and a Powerbook 
   Mac.

So if there is anyone of less knowledege than me out there (hard to concieve), I could give limited info, from
a raw newbie viewpoint, on those few points.

Well, that's it from me.
I'm Hoping someone can help with the frontend problem.

Cheers

"Eccles for King folks".

---

### Post by CanMan23 on 2008-03-15
Hi,
first a word of caution -- started with Mythbuntu a week ago or so, cause I wanted to update my old (SuSE based) MythTV. So some of the points/hints given might not be correct for your set-up. 
However I had exactly the same issue with my old set-up (the new one is not yet in a stage to look at this, but I started to thing about it).

Ok, here's what I did on my old system:
[LIST=1]
[*]Create a custom "autostart" script
[*]In the script find out the "next wakeup time"
[*]If it is more than 15min (or whatever you want) in the future - call original autostart script for the frontend
[*]If not, just have the backend running to record the setting
[*]Have the "power" button of the remote control linked to the original autostart script
[/LIST]

The above allowed me to start the PC and have the frontend started normally, if I started the PC to watch TV/recordings.
If the PC woke up to record something, no frontend would be started and once finished it would shut down.
If I would want to watch something while the PC was already running to record something or I would start I to close to a start of a recording, I need to press the "power" button on the remote to get the frontend. 

Worked real great for me.

And yes I was looking for the startmythtv.sh -- I could not find it :confused:
What I figured is that in ~/.config/autostart/mythtv.desktop the relevant settings are "stored".

So the plan (no yet done, might work or not) is:
[LIST=1]
[*]Create a custom autostart xxx.desktop entry to invoke a custom script
[*]Remove the original mythtv.desktop file - well back it up somewhere
[*]Let the script check, if the frontend should be started or not
[*]If yes, start frontend like the mythtv.desktop file would have
[*]If no, just do nothing
[*]Set-up remote control to allow start of frontend, if not yet running
[/LIST]

I hope this makes some sense for you and helps to give you an idea on how to achieve the "clever" frontend start.

---

### Post by Blonddeeni on 2008-03-16
Thanks CanMan23.
I figured that was what I might have to do. IE: write a script to intercept the frontend startup. Just had no idea where to look.
 Slight problem, so far I've only written one script; gets the modem working from the desktop. Time to rummage around How-to's to learn the syntax for scripts.

Thank you for the pointer on where to look, (~/.config/autostart/mythtv.desktop) and the sequence to arrange things. Time to do a "Partimage save" of my system again and then start experimenting.

This is going to be hilarious.:grin:
Cheers.

"Why can't it ever go to the Goram plan?"  - Cpt Malcom Reynolds.

---

### Post by CanMan23 on 2008-03-17
Hi Blonddeeni,
once I have my boxes migrated I will need to have such a script developed myself. Happy to post it here, but that will probably take another couple of days.

And doing it yourself, is always better....one learns a lot more.

Cheers.

---

### Post by CanMan23 on 2008-03-18
Hi,
here we go....

First of all: There is a seeting in the "General" section of the mythtv-setp that allows to specify a command to be run, once the backend started. A parameter (I think either AUTO or USER) will be passed to indicate what the backend things about this start.
Such a command could start the frontend, if the parameter equals USER and do nothing otherwise. If the "Autostart" file (mythtv.desktop) is removed that could be an option to solve the issue.

Another approach is to have a custom autostart'ed script to do all the work.
I prefer that approach cause it gives me full control and allows to have other tasks executed as well (e.g. a small display of the status of some processes like EPG update, backend, frontend, lirc daemon, slave backend up/down etc.)

This is what I did (works for me):
a) Remove ~/.config/autostart/mythtv.desktop (it's actually a link only)
b) Create ~/.config/autostart/myth-runner.desktop to invoke my own script
c) Have the own script perform all tasks wanted incl. potential mythfrontend start

Start mythfrontend, if a user start is assumed.
Created a small Python script to check current time against RTC settings. It returns either:
AUTO or
USER

So in the custom start script there is something like:
```

  W=`/MythTV/WOA/checkWakeup.py`
   # For the records
   echo $W >> /MythTV/Control/wakeup-times.log
   AUTO=`echo $W | grep "AUTO" | wc -l`
   if [ $AUTO -eq 1 ]; then
   {
      echo `date` " RTC Autostart assumed - not starting frontend" >> /MythTV/Control/runFrontend.log
      exit 0
   }
   else
   {
      echo `date` " Starting Frontend (user start assumed)" >> /MythTV/Control/runFrontend.log
      /usr/bin/mythfrontend --service # start ...real
   }
   fi

```Please note: Prior to the above code it is checked, if the frontend is already running. If so, no action is performed.
Also there is a log file written of the result of the Python script. Just to be able to tweak the settings.

And here is the Python script (checkWakeup.py)
```

#!/usr/bin/python

################################################################################
# Check reason for system wakeup agains programmed wakeup time.
# An additional / alternative could be performed against "next recordings"
################################################################################
import time
import subprocess
import re
################################################################################
# Settings:
# -- NV_SEC
#    Seconds allowed between check and programmed nvram-wakeup time
#    If (Now - WakeupTime) <= NV_SEC: Programmed wakeup else user wakeup
NV_SEC=120
# -- USE_UTC
#    NVRAM-WAKEUP reports time in UTC (cause RTC is set to UTC) or not
NV_UTC=True
# -- NV_CMD
#    Command to read nvram wakeup time. Probably requires usgae of sudo and
#    edit of /etc/sudoers to work without need to enter a password
#    If executed as root this is however not needed
NV_CMD="sudo /usr/local/bin/nvram-wakeup -A -C /MythTV/WOA/nvram-wakeup.conf"
class nvWakeupTime(object):
        def __init__(self):
                self.day  = 0
                self.hour = 0
                self.min  = 0
                self.sec  = 0
                self.act  = False
                self.diff = 0
                if NV_UTC:
                        self.now = time.localtime()
                else:
                        self.now = time.gmtime()
        def get(self):
                try:
                        p = subprocess.Popen(NV_CMD, shell=True, stdout=subprocess.PIPE)
                        out = p.communicate()[0]
                except Exception, e:
                        #print "Error:",str(e)
                        return False
                l = repr(out)
                mo = re.search("WakeUp\\s+:\\s+(\\w+)",l)
                if mo == None: return False # Can not find status Enabled/Disabled
                if mo.group(1) == "Disabled": self.act = False
                else:                         self.act = True
                mo = re.search("Day\\s+:\\s+(\\d+)",l)
                if mo == None: return False # Can not find day
                self.day = int(mo.group(1))
                mo = re.search("Hour\\s+:\\s+(\\d+)",l)
                if mo == None: return False # Can not find hour
                self.hour = int(mo.group(1))
                mo = re.search("Minute\\s+:\\s+(\\d+)",l)
                if mo == None: return False # Can not find minute
                self.min = int(mo.group(1))
                mo = re.search("Second\\s+:\\s+(\\d+)",l)
                if mo == None: return False # Can not find second
                self.sec = int(mo.group(1))
                return True
        def isAutoWakeup(self):
                if not self.act: return False             # nvram-wakeup not active at all
                if self.now[2] != self.day: return False # days do not match
                # Calculate difference in seconds between nvram-start time and now
                sec_nv  = self.hour * 3600 + self.min * 60 + self.sec
                sec_now = self.now[3] * 3600 + self.now[4] + self.now[5]
                self.diff    = sec_now - sec_nv
                if self.diff < 0: return False       # NVRAM Wakeup in future
                if self.diff <= NV_SEC: return True  # In allowed range
                else:                   return False # Not in range

if __name__ == "__main__":
        nv = nvWakeupTime()
        if nv.get():
                # Was able to read the wakeup time, calc difference
                auto  = nv.isAutoWakeup()
                s_now = time.strftime("%d %H:%M:%S",nv.now)
                if auto: print "WAKEUP: AUTO (%d) [RTC: Enabled:%s, Day:%d %02d:%02d:%02d / Now: %s ]" % (nv.diff, nv.act, nv.day, nv.hour, nv.min, nv.sec, s_now)
                else:    print "WAKEUP: USER (%d) [RTC: Enabled:%s, Day:%d %02d:%02d:%02d / Now: %s ]" % (nv.diff, nv.act, nv.day, nv.hour, nv.min, nv.sec, s_now)
        else:
                print "WAKEUP: ERROR"

```Please note the settings at the start of the Python file. The will probably need some adjustment.


So there is just one thing left to do: What happens if checkWakeup.py assumes an automatic start, but it's actually a start by the user?

I added to my custom start script a line like:
/usr/bin/irexec" "-d /MythTV/Control/irexecrc

and have a corresponding irexecrc (for my PVR-350 remote)
```

begin
   prog = irexec
   button = Power
   config = /MythTV/Control/runFrontend.sh irexec
end

begin
   prog = irexec
   button = Red
   config = /usr/Control/redButton.sh
end

begin
   prog = irexec
   button = Green
   config = /MythTV/Control/greenButton.sh
end

begin
   prog = irexec
   button = Blue
   config = /MythTV/Control/blueButton.sh
end

begin
   prog = irexec
   button = Yellow
   config = /MythTV/Control/yellowButton.sh
end

```The referenced runFrontend.sh script is actually also invoked by the custom start script to start the frontend, if it's not already running.


So putting it all together we have:
a) a custom ~/.config/autostart entry calling a custom start script
b) a custom start script starting irexec and the frontend, if a user start was detected by checkWakeup.py
c) the checkWakeup.py Python script.
d) a custom irexec config to allow the frontend start even if not started by b)


Hope all this makes some sense and can be tweaked for your needs. :)

Cheers !

---

### Post by CanMan23 on 2008-03-18
Hi,
just found that there is an **error in checkWakeup.py !** :(

It needs to be:
```

....snip....
class nvWakeupTime(object):
        def __init__(self):
                self.day  = 0
                self.hour = 0
                self.min  = 0
                self.sec  = 0
                self.act  = False
                self.diff = 0
                if **not** NV_UTC:
                        self.now = time.localtime()
                else:
                        self.now = time.gmtime()
....snip....

```
Sorry for that -- posted to quickly (not all tests done).

---

### Post by Blonddeeni on 2008-03-21
Holy Computer Programmer BatMan! 
I spend two days in the dark, (literally; that's my job), and you go and do all that work.
I will definitely give it all a go, but probably not until Tuesday. Yep, back into the dark again.
I had been thinking about how it all might hang together, and figured out which files to call and wot not, and then you go "BLING",  and there it is.
Choice One!
I will enjoy trying to figure out how each piece of each line works in your script. .:)

Thank you very much CanMan23.:-D

I hope the rest of your conversion from suse is going well.

Cheers.
B.

"And we will rule this land; and call it... This Land".

---

### Post by CanMan23 on 2008-03-22
Hi,
ups another error found -- probably should not post alpha code .... :confused:

Ok, in checkWakeup.py there is an error in calculating the seconds elapsed until "now".

It reads in isAutoWakeup:
```

                # Calculate difference in seconds between nvram-start time and now
                sec_nv  = self.hour * 3600 + self.min * 60 + self.sec
                sec_now = self.now[3] * 3600 + self.now[4] + self.now[5]

```

Clearly it needs to be:
```

                # Calculate difference in seconds between nvram-start time and now
                sec_nv  = self.hour * 3600 + self.min * 60 + self.sec
                sec_now = self.now[3] * 3600 + **self.now[4] * 60** + self.now[5]

```

Once more sorry for that....

@Blonddeeni : Hope the stuff works for you -- have fun sorting it all out.
In case of questions etc. let me know, might be able to help.
Have fun in the dark :)

---

### Post by Blonddeeni on 2008-03-24
Hello CanMan23.
I've emerged from The Dark with a wonderfull head cold.:cry:

Whilest in The Dark, had a think on doing a compare of the alarm time vs the system time.

I was going to get the alarm time using cat /proc/acpi/alarm |grep "alrmtime" and send it into a variable > $1
Do the same to the system date and then compare the two variables ($1 and $2)

EG:  IF Alrmtime equal to or less than system time
            Then run backend only boot script
             Else run normal boot script
        fi.

Well it works in my head, but couldn't figure out how to even grep the "time string" from the alarm, away from the whole string.  (eg: grep   15:30:00 from 2008-03-23 15:30:00 ).#-o

As you can see, for some reason  my versiion of linux uses acpi, so I will have to go through your scripts and hopefully change nvram to acpi.

But have a few days off now, and weather going naff so will stay indoors and do some decent time on all this.

I'll let you know how it all goes.
Cheers.
B

---

### Post by Blonddeeni on 2008-03-27
Hoorrayyy, it works!   :biggrin:

It Really does, just not the way I had thought at the beginning.
A bit different from my original intentions. 

While going through your posts, and trying to figure out which bits of nvram to change to acpi, It hit me that when I turn on the computer (1 button), and then the tv, (2nd button) every time just to do a bit more work on all this: that you had given me the answer in between your scripts.
Simply, use the remote to activate the frontend. (3rd button).

Thanks to you I knew where to look for the boot up sequence, ~/.config/autostart/mythtv.desktop and modify that.
How to use irexec and point it to a specific lircrc.
What I could put in that lircrc. (I chose: ... config = /usr/bin/mythfrontend.real).

Then wrote a modification to the MythShutdownCheck.sh to check for specific user(s).

So now my system will turn on, record, turn off, over and over. If I want it to stay on, (from either a manual boot or an auto-startup), all I have to do is use my remote to start a frontend, or if I choose, simply login as a listed user which can either sit in the background that MythShutdownCheck keeps checking to see if it is logged in, or it can be the one I am logged in as; for when I'm using the rest of the computer for "computery stuff".

Cool.

Again, could not have achieved this without your help.
Thanks CanMan23.



"I love it when a plan comes together"

---

### Post by CanMan23 on 2008-03-27
Hi,
as I never came across a MB that fully supports /proc/acpi/alarm I wasn't even thinking along that line.

Guess you should stick with it and not switch to nvram-wakeup if there is no need.

On the "grep the alarm time", it might be an idea to write the alarm time to a special file, when setting it and than retrieve it from there when needed.

E.g. if you have a shell script that receives the wakeup time and set's it in /proc/acpi/alarm in the required format, you might as well do a:
echo $WAKEUP > /myWakepupFile

Once the system starts again and it's checked if it's an automatic or user start just
read the file content and compare.

Another option might be to use the touch command to set the time of a control file and later use stat to get the date/time back.

Have fun playing with it.

Cheers.

---

### Post by CanMan23 on 2008-03-28
Blonddeeni,

great you got it working !

Seams that another post from me is somewhere lost in the forum wilderness...

Anyway, was just trying to give options on the ACPI alarm usage. But as long as it works for you, well all fine.

Have fun using MythTV :)

---

### Post by Blonddeeni on 2008-09-01
Just an update of how it's all hanging together I suppose.
Here is my MythShutdownCheck file, which checks for a dummy user I made which only keeping the system running if I'm working on it; and do not wish to have a frontend running. (EG: I may have logged in via my laptop).

$ cat /usr/bin/MythShutdownCheck 
#!/bin/bash
#
# MythShutdownCheck
#
# checks to see if either  user 'nobby' is
# logged in before idle shutdown,or if mythtranscode
# is running. If you do not have a frontend running, 
# then log in as nobby to stop system shutdown.
#
# returns "1" if yes, stopping shutdown
# returns "0" if ok to shutdown

if top -b -n 1 |grep -q transcode ; then
	exit 1
 else if who |grep -q nobby ; then
	exit 1
   else
	exit 0
 fi
fi

Here is how I get the remote to run the frontend from the desktop screen:

$cat ~/.config/autostart/mythtv.desktop 
[Desktop Entry]
Exec=/usr/bin/irexec -d /home/USER/.lircrc

And my .lircrc file has this at the beginning of it:
# '0' Button on remote to start mythfrontend using irexec
# from a desktop screen.
begin
  remote = technisat
  prog = irexec
  button = 0
  config = /usr/bin/mythfrontend.real
end

And that is it really.

Sort of on the subject as it has to do with Mythtv, as I have the mythconverg database being backed up to a second hard drive, I did not want it to be backed up EVERY time the system starts, just once a day. So on the first boot of the day, I wrote a wee script that checks the current day with a file that was written to during the previous bootup. If the file is different, then the backup gets done. If the same, it doesn't happen.

Here's the small checking script:
 s1=$(date +%d)
 s2=$(cat /media/sdb2/mysqlbackups/2day)
if [ $s1 = $s2 ] ; then
    exit 0
  else

[at this point you can put in your main script]

 date +%d > /media/sdb2/mysqlbackups/2day
fi

The last line (not the "fi" one) writes the day of the month to a file called 2day. It is this file which gets referenced to at the beginning of the script.
You can of course use a cron job to do all this, but I just liked having it all checked once and then left alone. 
Here's the entire script for backing up the mythconverg database, which I found somewhere, and unfortunately cannot remember where so cannot thank the writer.

cat mysqlbackup.script 
#!/bin/sh
# Dumps the mythconverg database - daily backup
# Keeps the last 7 days
# Compares the last time this was run with now, and if it
# has been run today, will not redo.
# Keeps a backup each day, for a rotating maximum of 7 days

 s1=$(date +%d)
 s2=$(cat /media/sdb2/mysqlbackups/2day)
if [ $s1 = $s2 ] ; then
# echo "This message is to show that the mythconverg backup has"
# echo "already been done today."
    exit 0
  else
    DAY=`/bin/date +%u`
    rm /media/sdb2/mysqlbackups/mythdb_$DAY.sql.bz2
    DUMPFILE="mythdb_$DAY.sql.bz2"
    sudo /usr/bin/mysqldump -u mythtv -pmysqlpassword mythconverg -c |\
      /bin/bzip2 -cq9 > /media/sdb2/mysqlbackups/$DUMPFILE
    date +%d > /media/sdb2/mysqlbackups/2day
#echo "The mythconverg backup happened at this time today."
fi
exit 0

# To restore (assuming that you've dropped the database)
# $ mysql -u root
#   mysql>create database mythconverg;
#   mysql>exit;
# $ mysql -u mythtv -pmysqlpassword mythconverg < mythtv_backup.sql (or wherever
# it is residing. /media/sdb2/mysqlbackups I think. Take note of which
# day you're restoring from.)

cheerio.

---

