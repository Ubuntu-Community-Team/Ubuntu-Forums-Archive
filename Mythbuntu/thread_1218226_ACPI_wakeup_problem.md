---
title: "ACPI wakeup problem"
date: 2009-07-20
forum: Mythbuntu
---

### Post by yocec on 2009-07-20
I have upgrade from 7.10 to 9.04 so for ACPI wakeup I had to use /sys/class/rtc/rtc0/wakealarm instead /proc/acpi/alarm.

On 7.10 everything worked fine I used to do
echo "2009-05-07 01:00:00" >/proc/acpi/alarm

And my Pc wake up every morning at 1 AM.
Why every morning ?
Because my BIOs don't seem to use date for Wake up (only time) and its OK for me.




On 9.04 I've copied this script :
#! /bin/bash
SECS=`date -u --date "$1" +%s`
echo 0 > /sys/class/rtc/rtc0/wakealarm
echo $SECS > /sys/class/rtc/rtc0/wakealarm


If I launch my script like this :
myscript.sh "2009-07-08 17:15:00"

I have this in /proc/driver/rtc :
rtc_time : 17:07:39
rtc_date : 2009-07-08
alrm_time : 17:15:00
alrm_date : 2009-07-08
alarm_IRQ : yes


If I stop my PC and wait 8 minutes my PC wakeup, it's OK.


BUT

if I manually re-start my PC before date/time alarm I have this in /proc/driver/rtc :
rtc_time : 17:07:39
rtc_date : 2009-07-08
alrm_time : 17:15:00
alrm_date : ****-**-**
alarm_IRQ : no


The ** don't worried me it seems to confirm that my BIOS don't use date.

But alarm_IRQ = no is more disturbing, because if I re-stop my PC before date/time alarm it don't wake up anymore.



In conclusion during start my ACPI wakeup parameters are modified, and ACPI wakeup with rtc works fine only if I don't start my PC between the moment I set the wakeup parameters and the wakeup date/time.



Any suggestion ?


I can create a script to set wakeup parameter during all shutdown (where to call it ?) BUT I don't like it because everything worked fine in 7.10



Have met same situation ?

Thanks

Yoann

---

