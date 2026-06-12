---
title: "MythTV - Scheduling ShutDown Script?"
date: 2009-01-03
forum: Mythbuntu
---

### Post by gneville on 2009-01-03
Hi,

I have done a bit of searching for a shutdown script which will turn off my (Mythbuntu) MythTV Backend/Frontend (All in one) machine at a time I specify. I have come across MythWelcome/MythShutdown, but I can't see it fits what I require.

The Idea:

A GUI within the MythTV Menus, where I put in a Date & Time of when I would like the machine to turn off. This could change from Day to Day, sometimes it maybe not needed at all, Therefore an Enabled/Disabled button as well. It would come in useful if there was something that needed to be recorded and the PC not be left on all night.

Does anyone know of any sort of plugin that enables this such feature? I don't need the Machine to bootup again at a set time, just want to turn off and thats it.

I could probably Write something to work within MythWeb using PHP and some sort of Crontab insertion/removale when needed. But wondering if theres anything better?

Thanks

---

### Post by volkswagner on 2009-01-03
> **gneville said:**
> Hi,

I have done a bit of searching for a shutdown script which will turn off my (Mythbuntu) MythTV Backend/Frontend (All in one) machine at a time I specify. I have come across MythWelcome/MythShutdown, but I can't see it fits what I require.

The Idea:

A GUI within the MythTV Menus, where I put in a Date & Time of when I would like the machine to turn off. This could change from Day to Day, sometimes it maybe not needed at all, Therefore an Enabled/Disabled button as well. It would come in useful if there was something that needed to be recorded and the PC not be left on all night.

Does anyone know of any sort of plugin that enables this such feature? I don't need the Machine to bootup again at a set time, just want to turn off and thats it.  When myth wakes to record it will remain powered on until the frontend is manually exited.

I could probably Write something to work within MythWeb using PHP and some sort of Crontab insertion/removale when needed. But wondering if theres anything better?

Thanks

I think MythShutdown is what you are after.  You don't need mythWelcome for it to work.  You can control it easily with one of two ways.

A key component of MythShutdown...It will not shutdown at idle of a frontend is connected.

(1) Disable auto start of MythFrontend.  Obviously if you power on manually you will need to start it.  This will let the pc turn on to record and automatically shutdown when done.

(2)Keep auto start of MythFrontend enabled.  This way the pc will only automatically shutdown when you exit the frontend and no other pc is logged  into the machine.  When the PC wakes to record, it will stay on until the Frontend is manually exited.

---

### Post by Caps18 on 2009-01-05
This is a feature I would like to see integrated with the program schedule and times I know I will possibly watch TV.  Most nights I know I'm not recording anything from 1am-3pm, so it would save me a lot of electric costs if a sleep mode or intelligent showdown, startup commands were implemented.

I may have to think about upgrading to the next version if this feature was there.

---

### Post by matthewgeier on 2009-01-05
> **Caps18 said:**
> This is a feature I would like to see integrated with the program schedule and times I know I will possibly watch TV.  Most nights I know I'm not recording anything from 1am-3pm, so it would save me a lot of electric costs if a sleep mode or intelligent showdown, startup commands were implemented.

I may have to think about upgrading to the next version if this feature was there.

 It already is - I've been using mythshutdown, ACPI wakeup for 12 months. My mythbox spends most of it's time turned off, waking up 10 minutes before a recording is due. Or at least did.

 Unfortunately, it's now broken, last week I upgraded to 8.10 from 8.04. After fixing up the wake up scripts to reflect the new kernel interface to the RTC, I find mythshutdown is writing the next scheduled wake-up time into the RTC alarm (in my case 1am) and not the next scheduled recording time.

 I haven't tried disabling my 1am wakeup yet to see what wakeup time it then uses. 1am is when I run my schedule grabber script, so if nothing else, the machine wakes up at 1am, runs mythfilldatabase and then turns itself off again. It used to work great :-)

---

### Post by pjw1965 on 2009-01-05
[http://www.mythtv.org/wiki/index.php/ACPI_Wakeup]("http://www.mythtv.org/wiki/index.php/ACPI_Wakeup") may help.
or even better:
[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake]("https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake#Mythbuntu%208.10")
and try my modified script to set the time:

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

---

### Post by Caps18 on 2009-01-06
While I'm sure that something like that would work, I'm looking for some nice and easy UI inside MythTV to do this.  But at the same time be able to wake up from standby at night if I choose to watch something.  It also needs to be really reliable since I travel for a week or two at a time and can't check on the computer.

---

