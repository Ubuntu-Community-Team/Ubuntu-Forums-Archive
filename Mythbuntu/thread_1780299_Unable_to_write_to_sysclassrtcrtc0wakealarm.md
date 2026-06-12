---
title: "Unable to write to /sys/class/rtc/rtc0/wakealarm"
date: 2011-06-11
forum: Mythbuntu
---

### Post by Blonddeeni on 2011-06-11
Wot Ho. 
My Mythbuntu 11.04-i386 is unable to auto shutdown and restart due to being unable to write to /sys/class/rtc/rtc0/wakealarm.
I have seen other posts concerning this area, but they at least have been able to at least write to the "wakealarm" file.
Whenever I write to it either as a user, user using sudo or even as root nothing happens to the file.

My kernel version "uname -a" returns with :
Linux Grunta202 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 athlon i386 GNU/Linux

My Motherboard: Asus M4N78 SE which worked fine with Mythbuntu 8.10. (Until I got my mythtv and the database schema versions out of sync somehow so I decided to go with 11.04).

I have followed the following help [http://www.mythtv.org/wiki/ACPI_Wakeup#Using_.2Fsys.2Fclass.2Frtc.2Frtc0.2Fwakealarm]("http://www.mythtv.org/wiki/ACPI_Wakeup#Using_.2Fsys.2Fclass.2Frtc.2Frtc0.2Fwakealarm") to the extent of changing my /etc/defaut/rcS to the following:
```
cat /etc/defaut/rcS
TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
#UTC=no
UTC=yes
VERBOSE=no
FSCKFIX=no
# added the next line HWCLOCKACCESS=no
HWCLOCKACCESS=no
```

Changed my /etc/init/hwclock-save.conf
```
description	"save system clock to hardware clock"

start on runlevel [06]

task

script
    . /etc/default/rcS
    [ "$UTC" = "yes" ] && tz="--utc" || tz="--localtime"
    [ "$BADYEAR" = "yes" ] && badyear="--badyear"
    if [ "$HWCLOCKACCESS" != "no" ]; then
	 exec hwclock --rtc=/dev/rtc0 --systohc $tz --noadjfile $badyear
    fi
end script

# The if line and the fi line have been put in by me to
# try and get this machine to autoshutdown / reboot.
```

and even tried making the same change to /etc/init/hwclock.conf (because to my eyes they looked close enough to be the same. I'm really grasping at straws now to do this. But as it made no difference I have reset hwclock.conf back to it's original setting.)

Each change was done then tested after a reboot with:

sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"
sudo sh -c "echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm"
cat /sys/class/rtc/rtc0/wakealarm

But each time the cat /sys/class/rtc/rtc0/wakealarm command comes back with nothing.

Also trying$ cat /proc/driver/rtc showed that there was no alarm pending.
```
rtc_time	: 10:53:28
rtc_date	: 2011-06-12
alrm_time	: 10:31:45
alrm_date	: 2011-06-12
alarm_IRQ	: no
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: yes
BCD		: yes
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay
```

I have also changed the ownership of  /sys/class/rtc/rtc0/wakealarm to mythtv:mythtv.
I have tried all of the above with changing my bios setting to enable rtc alarm, (no go) and currently it is set to "S3" but still no go.

I tried disabling this "HPET" thing mentioned in the above ACPI thread/help, by putting hpet=disable on the end of my grub's linux line (IE: linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=dd079a14-2232-4785-a802-534565a770c9 ro hpet=disable), **but still */sys/class/rtc/rtc0/wakealarm* comes back blank.**

But at least HPET was disabled. $ cat /proc/driver/rtc
```
rtc_time	: 11:15:52
rtc_date	: 2011-06-12
alrm_time	: 11:15:51
alrm_date	: 2011-06-12
alarm_IRQ	: no
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
**HPET_emulated	: no**
BCD		: yes
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay

```

What AM I missing here?

On my 8.10-Mythbuntu setup I only changed the ownership of the wakealarm file to  mythtv:mythtv  and inserted in the /etc/init.d/hwclock.sh file the lines:
if [ "$HWCLOCKACCESS" != "no" ]; then
    exec hwclock --systz $tz --noadjfile $badyear
fi

8.10 worked on this motherboard perfectly, so I am now completely out of ideas.

I am completely stuffed here, and currently the machine stays on 24/7 when it only needs to be on for around 4-5 hours a day. 

Can anyone help please?[-o<

Blonddeeni.

On the bright side this is the only thing to stuff me up on this whole installation. Got the remote, multiple drives, two dvb-s cards etc  all working easy-peasy. :D Considering I've only been fiddling with the GNU/Linux system for three years (evenings occasionally) I reckon that's pretty cool bananas as I was completely computer illiterate before then.

---

### Post by ktmom on 2011-06-12
> **Blonddeeni said:**
> Wot Ho. 
Each change was done then tested after a reboot with:

sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"
sudo sh -c "echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm"
cat /sys/class/rtc/rtc0/wakealarm

But each time the cat /sys/class/rtc/rtc0/wakealarm command comes back with nothing.


I am not much more experienced than you, but the cat /sys/class/rtc/rtc0/wakealarm returning nothing is certainly odd.

The permissions on my file are:
-rw-r--r-- 1 root root 4096 2011-06-12 11:13 /sys/class/rtc/rtc0/wakealarm

This command:  
sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"  
empties out any data already existing in the wakealarm file. Notice that there is only one set of quotes.

This command:
sudo sh -c **[COLOR="Red"]"[/COLOR]**echo **[COLOR="Blue"]`[/COLOR]**date **[COLOR="SeaGreen"]'[/COLOR]**+%s**[COLOR="SeaGreen"]'[/COLOR]** -d **[COLOR="SeaGreen"]'[/COLOR]**+ 5 minutes**[COLOR="SeaGreen"]'[/COLOR]****[COLOR="Blue"]`[/COLOR]** > /sys/class/rtc/rtc0/wakealarm**[COLOR="Red"]"[/COLOR]**
writes the current time plus 5 minutes to the same file and there are four sets of quotes.

If the syntax of the command (i.e. the quotes) are not correct, it will fail quietly and nothing will be written to the file.  It kinda seems that this may be your problem.

Are you copying and pasting the 
sudo sh -c "echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm" 
command into your terminal?

The first quote is a **[COLOR="Red"]"[/COLOR]** (shift next to the enter key)
The second quote is a **[COLOR="Blue"]`[/COLOR]** (shares the same key as the tilda ~)
the third and fourth open and closed are **[COLOR="SeaGreen"]'[/COLOR]** (unshifted next to the enter key)
Then close the second with a **[COLOR="Blue"]`[/COLOR]** (shares the same key as the tilda ~)
And close the first with a **[COLOR="Red"]"[/COLOR]** (shift next to the enter key)

---

### Post by nickrout on 2011-06-12
do you need to change your sudoers file to enable the sudo command to work without using a password?

---

### Post by Blonddeeni on 2011-06-13
I'm back from the underground, literally.

Thanks ktmom, for  your reply.
After looking at it I found the clue I was looking for.

In my 8.10 Mythbuntu to get it working I had to change the "wakealarm" ownership to mythtv:mythtv, and just assumed that I'd have to do the same in 11.04. But from looking very closely at your reply I realised that I could try and leave the wakealarm ownership with root, and see how that goes.

Worked perfectly!
Brilliant, just the nudge I needed.

Thank you very much.

Hi nickrout.

I am about to reveal my ignorance here, I have to read your post very slowly and carefully to try and understand it. (Mr Thicky, that's me. 8-[)

I think that what I would have to do is add a line to be like,

mythtv	ALL=(ALL:ALL) ALL
Is that right?

Or is it where you have to make the line
%mythtv ALL = **NOPASSWD**: /sbin/shutdown, /bin/sh, /usr/bin/setwakeup.sh
in the sudoers file. 
I've done both just to make sure.

Thank you also for your response, as it's making me think and recheck what I had done.

The system is now doing what I need, although it did keep changing the system time to 24 hours into the future whenever it did a restart but was unable to connect to the interweb. Well until I changed the /etc/default/rcS file from "utc=yes" back to "utc=no". 
Again, another hold-over from 8.10 that I just blindly copied.
(We turn everything off when we leave the house, so no interweb here until we flick the power on at the wall for that particular bit of equipment).

Crikey, this copying from old to new can be tricky. #-o
Worked a treat for getting the remote working though.

Cheers to you both for helping me here. I will mark this thread as "Solved", and take a much look closer at what this "sudoers" file is really all about. 
(Syntax, et al).

Cheerio.
Blonddeeni.

---

### Post by ktmom on 2011-06-13
Glad you were able to find the problem.  8.04 to 11.04 is a big hop ;)

The line I would add is the limited one:

%mythtv ALL = NOPASSWD: /sbin/shutdown, /bin/sh, /usr/bin/setwakeup.sh

---

### Post by Blonddeeni on 2011-06-16
I.  Do.  Not.  Believe.  It!

There is no way you can tell me that computers are not nasty little sods sometimes.:evil:

The very next day I am back to square one!
Unable to write to /sys/class/rtc/rtc0/wakealarm. 

And here I thought it was only organisms that could be capricious!

There were three changes I had done.
1) Removed the "Network Manager" program. It seemed to be unable to see my lan card, but /etc/netwrok/interfaces was doing the job. My ip address has to be static as quite often the machine will boot up with no access to a dchp server.
2) Changed the frontend > setup > General > Hostname to the actual name of the computer. The frontend occasionally had trouble connecting to the backend. No idea why.:confused:
3) Changed /etc/default/rcS utc= from "yes" back to "no" (The default). This stopped the machine from starting up with a date/time 12 hours into the future, which would happen whenever it started and could not see the interweb. This is even though I have the date/time set to "manual" in Applications > System > Time & Date.
(I wonder if having the machine on "local time" not utc has something to do with it? Nah, tried that avenue several times). 

So there it is, no auto shutdown and wakeup. . . . . . or is it?

Whilst trying everything I could think of, and was at the stage of just preparing a large post full of my various settings, EG: cat(s) of /etc/default/rcS,  hwclock-save.conf and /proc/driver/rtc, plus how they all looked over various reboots, I stumbled across a very useful program.

/usr/sbin/rtcwake.

Check it out yourself next time you have a terminal open, and have a look with:
man rtcwake

Long story short, my /usr/bin/setwakeup.sh now looks like this:

```
#!/bin/sh

# I Am going to use rtcalarm as I STILL cannot use /sys/class/rtc/rtc0/wakealarm

# To use rtcwake. -l means use local time. -t means set the wakeup time to
# what follows, and it has to be an Epoch time. $1 is the time string from
# mythbackend. -m is to use the following standby mode which here is "no". This
# means to set the alarm but NOT to shutdown the machine.
# Yes, rtcalarm can set the wakeup time, and then save the machine State to
# either memory &/or disk. Wheeee.

sudo rtcwake -lt$1 -m no
```


Sweeet.

Hmmmm "rtcwake" and then there's "wakealarm" in the "rtc"/rtc0 directory? They must be connected somehow.

So really I should unmark this thread "Solved" as I have not figured out how to write to /sys/class/rtc/rtc0/wakealarm, but instead **have** figured out a work around.

So I'm hoping that if someone else is having troubles in this area, posting this thread "Solved" yet using "rtcwake" instead, may help them to get around their problem.
However if this is not correct behaviour, please let me know and I will gladly change this thread from Solved.

Cheers all for your time.
Thank you Kindly.
Blonddeeni.

---

### Post by felixfurtak on 2011-08-21
Hey Blonddeeni,

Thanks for the fix. I had exactly the same problem with not being to write to wakealarm (or read it).

It used to work flawlessly in lucid 10.04 and then it mysteriously stopped working. I'm guessing an update was to blame, but I could never get to the bottom of which one.

However, you fix works fine for me. Thanks again.

Felix
:D:D:D:D:D

---

### Post by Docter on 2011-08-21
Thanks for this as I was having similar problems. I still couldn't get it to work so I wrote a bash script to kludge my way around it. This gets executed by cron at regular intervals and is far from perfect. I wanted it to update on shutdown by storing it in rc0.d, but mysql wont accept connections at that time or, indeed, on startup (grrr). The other problem is UTC time needs adjusting and this script further adjusts that for British Summer time. It needs more conditionals and other tweaks, but it works for now:

```
#!/bin/sh
#This script will set the rtc wakeup alarm.
#It is designed to run as a cron job and will update 
#/sys/class/rtc/rtc0/wakealarm if it is blank
#or if a new time has been set before one currently stored
#otherwise it will leave it as it is

#Mysql manual query, kept for posterity
#data=$(mysql -N -h localhost -u mythtv -pmythtv -e "use mythconverg;select data from settings where value='MythShutdownNextScheduled'")

#set path
PATH=/usr:/sbin:/bin:/usr/local/bin:usr/sbin:/usr/bin:.

#Store content of wakealarm in $content
content=$(cat /sys/class/rtc/rtc0/wakealarm)

#Output to logfile
exec 1>>/home/doc/rcwake.log
echo

#mythshutdown -t updates the Mysql dbase and returns the time of next recording according to settings stored in backend
schedwake=$(mythshutdown -t -v important)

#gets last 19 chars from mythshutdown output which is date in ISO9006 format, as used by mysql
date=${schedwake#${schedwake%???????????????????}}

#Convert to epoch
epo=$(date --date="$date" +%s)
#for some reason it is 6 hours out, so get out hack hammer
epo=$(($epo+(60*60*6)))
#Adjust for summertime +1hour
adjepo=$(($epo+3600))

#If it is blank
if [ -z "$content" ]; then
echo "$(date) Blank. Setting..."
echo "$date"
echo
#Set rtcwake alarm, sets /sys/class/rtc/rtc0/wakealarm
/usr/sbin/rtcwake -lt $epo -m no
echo "$(date)  \$content = $content"
echo "$(date)  \$adjepo = $adjepo"

#Else If an earlier time has been set meanwhile
elif [ "$content" -gt "$adjepo" ]; then
echo "$(date)  Earlier startup time set"
echo "$date"
echo
#Set rtcwake alarm, sets /sys/class/rtc/rtc0/wakealarm
/usr/sbin/rtcwake -lt $epo -m no
echo "$(date)  \$content = $content"
echo "$(date)  \$adjepo = $adjepo"

#Else If the two values are identical
elif [ "$content" -eq "$adjepo" ]; then
echo "$(date) Time is equal"
fi
```

Maybe it will be useful for someone else.

---

