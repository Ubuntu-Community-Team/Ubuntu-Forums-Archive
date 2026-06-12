---
title: "myth wake up one hour later"
date: 2013-02-24
forum: Mythbuntu
---

### Post by abtabt on 2013-02-24
hello need some help

mythbuntu cd 12.04 installed and updated 

i use mythwelcome

i have a problem its start one hour late

14.00 starts 15.00 etc

i have time zone sweden and i belive +1

i have use this info  [http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup)

but how can i correct this i use this script

can i put some in this script too fix that ?

i use this setwakeup.sh



setwakeup.sh 
#!/bin/sh
#
# set ACPI Wakeup time
# usage: setwakeup.sh seconds
# seconds - number of seconds from epoch to UTC time (time_t time format)
#
# set UTCBIOS to true if bios is using UTC time
# set UTCBIOS to false if bios is using local time

UTCBIOS=true

if $UTCBIOS
then
#utc bios - use supplied seconds
SECS=$1
else
#non utc bios - convert supplied seconds to seconds from
#epoch to local time
SECS=`date -u --date "\`date --date @$1 +%F" "%T\`" +%s`
fi

echo 0 > /sys/class/rtc/rtc0/wakealarm # clear alarm
echo $SECS > /sys/class/rtc/rtc0/wakealarm # write the waketime

or is the backend about 

Time offset for XMLTV listings
None	If your local time zone does not match the time zone returned by XMLTV, use this setting to have mythfilldatabase adjust the program start and end times. None disables this feature, Auto automatically detects your local time zone.	Leave this alone if you're an American using the SchedulesDirect XML service.

or is this something else

have some one any idea ??

---

### Post by alien878 on 2013-02-25
This looks like a problem that was fixed a few weeks ago.

Do you have the mythtv repositories enabled so you are getting the latest fixes?  You need to enable Mythbuntu-repos in the MCC.

---

### Post by abtabt on 2013-02-25
> **alien878 said:**
> This looks like a problem that was fixed a few weeks ago.

Do you have the mythtv repositories enabled so you are getting the latest fixes?  You need to enable Mythbuntu-repos in the MCC.

thanks for info i will try that 

but i have 0.25 0.26 0.27
witch one will i choose ???

---

### Post by alien878 on 2013-02-26
You probably want 0.26 (0.27 is still under development).

Before you change it though, check which version you are currently running (mythtv --version, I think).  If you are running 0.25, I definitely recommend backing up before going to 0.26.  Actually, you probably want to back up even if you are on 0.26 just to be safe.

Some people may think I'm paranoid, but I take an image of my boot drive before any updates.  This has saved me a few times :)

---

