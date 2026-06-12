---
title: "Shut Down/Wake Up of PC using MythTV"
date: 2009-10-28
forum: Mythbuntu
---

### Post by bsntech on 2009-10-28
Hi folks,

I came across a site that explains how to setup MythTV to setup the RTC clock in the BIOS to automatically awaken once a certain time is hit and to also shutdown if there are not any recordings in x minutes.

Site:

[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake?action=edit]("https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake?action=edit")

And also:

[http://ubuntuforums.org/showthread.php?t=1176528]("http://ubuntuforums.org/showthread.php?t=1176528")

On the first site listed, it indicates that the ECS GF8200A motherboard is supported (which is what I have).

With 9.10 Karmic, the first part about updating the hwclock.sh file doesn't seem to be valid anymore - because this file does not exist.

I have confirmed that the file to modify in 9.10 Karmic for the clock is:

/sys/class/rtc/rtc0/wakealarm

However, when I have this file read, nothing is returned:

user@HTPC:~$ cat /sys/class/rtc/rtc0/wakealarm
user@HTPC:~$ 

The guide says it should return the RTC format.  If I read /proc/driver/rtc:

user@HTPC:~$ cat /proc/driver/rtc
rtc_time	: 18:22:36
rtc_date	: 2009-10-28
alrm_time	: 17:13:20
alrm_date	: ****-10-**
alarm_IRQ	: no
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: yes
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay


To me, that shows that the alarm time is 17:13:20 (which I set correctly at previous attempts).  I'm not sure what to make of the alrm_date though - it has the asterisk's in the year and date locations - and only shows the month (10).

So, the next step of the guide was to set the clock for five minutes out:

$ sudo sh -c 'echo "+00-00-00 00:05:00" > /sys/class/rtc/rtc0/wakealarm'

When doing this, the updates show they took affect and the date field is also filled out:

user@HTPC:~$ cat /proc/driver/rtc
rtc_time	: 18:33:52
rtc_date	: 2009-10-28
alrm_time	: 18:38:48
alrm_date	: ****-10-28
alarm_IRQ	: no
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: yes
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay


Now - here is the problem.  I shut the computer down expecting it to turn back on - but nope!  It won't turn back on at all.

I tried this with the setting in the BIOS for waking on RTC in both disabled and enabled mode - but neither of them work.

Does anyone have any other suggestions to try?  Sorta bad that I just started the guide and it isn't working from the get-go.

---

### Post by bsntech on 2009-10-28
Fixed it - I had to do the following to get the time to set correctly:

sudo sh -c "echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm"

and then in the /etc/default/rcS file, I had to make the following entry:

HWCLOCKACCESS=no

---

### Post by Cuppa-Chino on 2009-11-02
Interesting I also had wake up problems and the 9.04 method ie as above did not work for me -- probably due to the passage:
> and then in the /etc/default/rcS file, I had to make the following entry:

HWCLOCKACCESS=no 

what I did to fix setting of wake up time in rtc is the following:

I found this report of a modified echo 
[http://www.gossamer-threads.com/lists/mythtv/users/402454#402454]("http://www.gossamer-threads.com/lists/mythtv/users/402454#402454")

I tried it out (did not adjust any hpet) and confirmed it worked, then I rewrote the setwake script to the following:

```
#!/bin/sh
#$1 is the first argument to the script. It is the time in seconds since 1970
#this is defined in mythtv-setup with the **time_t** argument

# Current time and date
NOW=`date "+%b %d %H:%M:%S"`

#current time in seconds
NOWSECS=`date -d "$NOW" "+%s"`

# calculate the delta time
DELTATIME=`expr $1 - $NOWSECS`
echo "$NOW set deltatime $DELTATIME set exact time $1" >> /home/[COLOR="RoyalBlue"]YOURHOMEDIRCTORY[/COLOR]/wakeup.log ##this writes a log of the alarm into zour home directory

sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm ###this clears the alarm

sudo sh -c "echo +$DELTATIME > /sys/class/rtc/rtc0/wakealarm" ###this writes the alarm as seconds from now

```

save the script (mousepad or gedit save as setwakeup.sh
make it executable with sudo chmod +x setwakeup.sh
copy it into /usr/bin with sudo cp setwakeup.sh /usr/bin


then I set the time format to time_t in mythtv-setup and change the time setting command to sudo /usr/bin/setwakeup.sh $time

hope this helps

---

