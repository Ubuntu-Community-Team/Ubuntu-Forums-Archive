---
title: "Mythbuntu, torrents and ISP Fair Use Policies"
date: 2008-07-17
forum: Mythbuntu
---

### Post by Sangoma-1701D on 2008-07-17
Hi all,

I've been an avid Myth fan and user for the last few years. Starting with Ubuntu with Myth and moving about 12 months ago over to the (I must say) excellent Mythbuntu.
Anyway, during my years of use I have also been an avid torrent user. So at first I left my Mythbox on 24/7, no problem for downloading torrents. Then I got stingy and decided I only wanted my box on when recording. My ISP also started to get stingy with it's fair use policy re: downloading; but with most things once I read the FUP I realised they did not monitor FUP downloading between midnight and 9am!
So, long story, but basically I thought I would share my modified MythWakeSet and MythShutdownCheck scripts which always start my machine just after midnight and keep the box up until 9am to allow my torrents to work away during non-monitoring hours.

The original scripts and ACPI wakeup/shutdown (excellent) guide that I used are at:

[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake]("https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake")

MythWakeSet
```
#!/bin/bash
#
# MythWakeSet
#
# set mythtv wake-up time with UTC-adjusted time
# added daily torrent download schedule startup and shutdown to avoid fair use policy monitoring
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

# FUP additions from here

# get tomorrows date
fup_tomorrow=$(/bin/date --date="1 day" +%Y-%m-%d)

# set a string to be a space
space=" "

# ISP fair-use policy non-monitoring start time [hh:mm:ss] (add a few minutes to be on the safe side)
fup_start_time="00:02:00"

# add tomorrows date to $fup_start-time [yyyy:MM:dd]
fup_start_date=$fup_tomorrow$space$fup_start_time

# Read the date in *locale* time format and tag the time-zone info to $fup_start-date
fup_start_date_localeadd=$(/bin/date --date="$fup_start_date" +%F\ %T\ %z)
fup_start_date=$fup_start_date_localeadd

# adjust this to UTC and store the final $fup_start
fup_start=$(/bin/date --date="$fup_start_date" +%F\ %T)

# get the date-times in timestamp
fup_start_epoch=$(/bin/date --date="$fup_start" +%s)
utcadj_epoch=$(/bin/date --date="$utcadj" +%s)

# check to see if the wake time is after $fup_start
if [ "$utcadj_epoch" -ge "$fup_start_epoch" ]
then
 # the wake up time IS after $fup_start - therefore reset wakeup time to $fup_start 
 utcadj=$fup_start
fi

# set the alarm
echo $utcadj > /proc/acpi/alarm

```

MythShutdownCheck
```
#!/bin/bash
#
# MythShutdownCheck
#
#

# get todays date
fup_today=$(/bin/date +%Y-%m-%d)

# get now
fup_now=$(/bin/date +%s)

# set a string to be a space
space=" "

# ISP fair-use policy non-monitoring start time [hh:mm:ss] (add a few minutes to be on the safe side)
fup_start_time="00:02:00"

# add todays date to $fup_start-time [yyyy:MM:dd]
fup_start=$fup_today$space$fup_start_time

# ISP fair-use policy non-monitoring end time [hh:mm:ss] (subtract a few minutes to be on the safe side)
fup_end_time="08:58:00"

# add todays date to $fup_start-time [yyyy:MM:dd]
fup_end=$fup_today$space$fup_end_time

# get the date-times in timestamp
fup_start_epoch=$(/bin/date --date="$fup_start" +%s)
fup_end_epoch=$(/bin/date --date="$fup_end" +%s)

# check to see if the time now is after $fup_start_epoch
if [ "$fup_now" -ge "$fup_start_epoch" ]
then
 # check to see if the time now is before $fup_end_epoch
 if [ "$fup_now" -lt "$fup_end_epoch" ]
 then
  # the machine is currently on during the Fair User Policy non-checking time - DO NOT SHUTDOWN!!!
  exit 1
 else
  exit 0
 fi
else
 exit 0
fi
```

The code is not particularly elegant, but it works.
Just to complete the story I use Azureus and have it launching using the 'Applications' -> 'Settings' -> 'Autostarted Applications' interface. I also use the Speed Scheduler ([http://azureus.sourceforge.net/plugin_details.php?plugin=SpeedScheduler]("http://azureus.sourceforge.net/plugin_details.php?plugin=SpeedScheduler"))  plugin to stop my torrents during FUP monitoring hours.

To stop Azureus cleanly (prevents the pop-up warning window) I have used the following script as the 'Server Halt Command' in MythBackend setup:

/usr/bin/MythKillAzureus
```

ps -o pid h -C java | xargs kill

sleep 5

sudo shutdown -h -P now

```

The 'sleep 5' code ensures that Azureus is closed before shutdown starts.
Don't forget to make the script executable with:

```
sudo chmod +x /usr/bin/MythKillAzureus
```

Remember to add '/bin/kill' and '/usr/bin/MythKillAzureus' to your Myth user using visudo, or the above line will not work!

Hope that all makes sense.

Cheers,

Sangoma-1701D

---

