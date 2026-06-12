---
title: "MythWake waking up an hour early"
date: 2010-05-25
forum: Mythbuntu
---

### Post by gwagchunks on 2010-05-25
Hello everyone

Mythwelcome has been working really well, or so I thought. I recently noticed that the box is booting up an hour before a recording. I guess it has done it since DST. I thought it had been working as recordings where available (but I noticed that the frontend was starting up automatically and keeping the box up (fixed this now, so now nothing is getting recorded!)). The BIOS time is fine and the date command returns the correct time. Here is the backendlog:

```

2010-05-21 23:59:50.224 CheckShutdownServer returned - OK to shutdown
2010-05-21 23:59:50.233 Running the command to set the next scheduled wakeup time :-
						sudo -H mythshutdown --setwakeup "2010-05-22 06:36:10"
2010-05-21 23:59:50.360 Running the command to shutdown this computer :-
						sudo -H mythshutdown --shutdown
Running /usr/bin/MythWakeSet to set the wakeup time to 2010-05-22 06:36:10
echo 0 > /sys/class/rtc/rtc0/wakealarm
echo 1274506570 > /sys/class/rtc/rtc0/wakealarm
rtc_time	: 23:59:49
rtc_date	: 2010-05-21
alrm_time	: 05:36:10
alrm_date	: 2010-05-22
alarm_IRQ	: yes
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: yes
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay
2010-05-21 23:59:52.589 I'm idle now... shutdown will occur in 120 seconds.
2010-05-22 05:37:10.126 Using runtime prefix = /usr
2010-05-22 05:37:10.190 Empty LocalHostName.
2010-05-22 05:37:10.199 Using localhost value of htpc
2010-05-22 05:37:10.267 New DB connection, total: 1
2010-05-22 05:37:10.316 Connected to database 'mythconverg' at host: localhost
2010-05-22 05:37:10.349 Closing DB connection named 'DBManager0'
2010-05-22 05:37:10.361 Connected to database 'mythconverg' at host: localhost
2010-05-22 05:37:10.363 New DB connection, total: 2
2010-05-22 05:37:10.381 Connected to database 'mythconverg' at host: localhost
2010-05-22 05:37:10.412 Current Schema Version: 1214
Starting up as the master server.
2010-05-22 05:37:10.770 New DB connection, total: 3
2010-05-22 05:37:10.782 Connected to database 'mythconverg' at host: localhost
2010-05-22 05:37:14.875 Channel(/dev/video0) Warning: You have not set an external channel changing
			script for a composite or s-video input. Channel changing will do nothing.
2010-05-22 05:37:15.131 New DB scheduler connection
2010-05-22 05:37:15.134 Connected to database 'mythconverg' at host: localhost
2010-05-22 05:37:15.218 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-05-22 05:37:15.293 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-05-22 05:37:16.685 Main::Registering HttpStatus Extension
2010-05-22 05:37:16.727 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-05-22 05:37:16.947 mythbackend version: 0.21.20080304-1 www.mythtv.org
2010-05-22 05:37:17.143 Enabled verbose msgs:  important general
2010-05-22 05:37:17.550 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-05-22 05:37:18.187 Reschedule requested for id -1.
2010-05-22 05:37:47.820 MainServer::HandleAnnounce Monitor
2010-05-22 05:37:48.782 adding: htpc as a client (events: 0)
2010-05-22 05:37:48.565 Scheduled 46 items in 30.4 = 28.62 match + 1.76 place
2010-05-22 05:37:48.909 MainServer::HandleAnnounce Monitor
2010-05-22 05:37:49.514 Seem to be woken up by USER
2010-05-22 05:37:49.910 UPnpMedia: BuildMediaMap VIDEO scan starting in :/media/Mybook/mythtv/videos:
2010-05-22 05:37:49.910 adding: htpc as a client (events: 1)
2010-05-22 05:37:50.463 UPnpMedia: BuildMediaMap Done. Found 58 objects
2010-05-22 05:37:50.949 MainServer::HandleAnnounce Monitor
2010-05-22 05:37:51.038 adding: htpc as a client (events: 0)
2010-05-22 05:37:51.080 MainServer::HandleAnnounce Monitor
2010-05-22 05:37:51.149 adding: htpc as a client (events: 1)
2010-05-22 05:37:51.175 I'm idle now... shutdown will occur in 120 seconds.

```

Can anyone help please? Thanks

---

### Post by Neon Dusk on 2010-05-25
Looks like your RTC clock is in local time.

Can you post the MythWakeSet script that you're using?

---

### Post by gwagchunks on 2010-05-25
> **Neon Dusk said:**
> Looks like your RTC clock is in local time.

Can you post the MythWakeSet script that you're using?

Hi

It's from this link:

[http://ubuntuforums.org/showthread.php?t=1176528](http://ubuntuforums.org/showthread.php?t=1176528)

and here is the code:

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

I changed the time zone from +0100 to +0000, but just copying it up I've noticed that its commented out!!! Whoops:redface:

I have just changed it back to +0100 and I'm waiting to see if it will wakeup in about 20 mins time. I'll let you know!

---

### Post by gwagchunks on 2010-05-25
Well that didn't work.

The alarm time is really wrong now

Log attached:

```

2010-05-25 17:17:42.015 I'm idle now... shutdown will occur in 120 seconds.
2010-05-25 17:19:41.180 MainServer::HandleAnnounce Monitor
2010-05-25 17:19:41.210 adding: htpc as a client (events: 0)
2010-05-25 17:19:41.210 MainServer::HandleAnnounce Monitor
2010-05-25 17:19:41.211 adding: htpc as a client (events: 1)
2010-05-25 17:19:41.253 CheckShutdownServer returned - OK to shutdown
2010-05-25 17:19:41.260 Running the command to set the next scheduled wakeup time :-
						sudo -H mythshutdown --setwakeup "2010-05-25 17:56:10"
2010-05-25 17:19:41.400 Running the command to shutdown this computer :-
						sudo -H mythshutdown --shutdown
Running /usr/bin/MythWakeSet to set the wakeup time to 2010-05-25 17:56:10
echo 0 > /sys/class/rtc/rtc0/wakealarm
echo 1274806570 > /sys/class/rtc/rtc0/wakealarm
rtc_time	: 17:19:41
rtc_date	: 2010-05-25
alrm_time	: 17:24:41
alrm_date	: ****-**-25
alarm_IRQ	: no
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: yes
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay
2010-05-25 17:19:43.550 I'm idle now... shutdown will occur in 120 seconds.
2010-05-25 18:04:21.108 Using runtime prefix = /usr
2010-05-25 18:04:21.197 Empty LocalHostName.


```

Help!

---

### Post by Neon Dusk on 2010-05-25
You could try the settings in MythTV [Wiki](http://www.mythtv.org/wiki/ACPI_Wakeup) -> Mythwelcome users 

You'll need to change your Myth Backend, MythWelcome settings and check your sudoers file

For a bios in local time the setwakeup.sh script should be (I've adding in extra logging commands)
```

#!/bin/sh
#
# set ACPI Wakeup time
# usage: setwakeup.sh seconds
#    seconds - number of seconds from epoch to UTC time (time_t time format)
#
# set UTCBIOS to true if bios is using UTC time
# set UTCBIOS to false if bios is using local time

UTCBIOS=false
LOG=/var/log/mythtv/mythbackend.log

if $UTCBIOS
then
    #utc bios - use supplied seconds
    SECS=$1
else
    #non utc bios - convert supplied seconds to seconds from
    #epoch to local time
    SECS=`date -u --date "\`date --date @$1 +%F" "%T\`" +%s`
fi

echo "Running $0 to set the wakeup time to $1" >> $LOG

echo 0 > /sys/class/rtc/rtc0/wakealarm       # clear alarm
echo $SECS > /sys/class/rtc/rtc0/wakealarm   # write the waketime
cat /proc/driver/rtc >> $LOG

```

Someone else has had issues using the instructions you've followed [thread=1483962]Mythshutdown problem after upgrading to 10.04[/thread]. So if you're planning on upgrading to 10.04 this may also solve problems in the future.

---

### Post by gwagchunks on 2010-05-25
Thanks for the reply

I'll have to try it tomorrow now, Wife will want to watch EastEnders and then there's the Lost finale to watch!

Keep you posted.

Thanks

---

