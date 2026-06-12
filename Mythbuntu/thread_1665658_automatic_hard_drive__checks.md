---
title: "automatic hard drive  checks"
date: 2011-01-12
forum: Mythbuntu
---

### Post by itlarson on 2011-01-12
Is there a way to automate those hard drive checks that occur sometimes when I re-boot the computer?  It seems like it should be possible to do them late at night as a cron job.  There would still need to be some way to check if anything was recording first and re-schedule.

---

### Post by thatguruguy on 2011-01-12
The automatic hard drive check is done by fsck. You shouldn't run it on a mounted file system, which is why it happens at boot time (prior to the file system being mounted).

---

### Post by AKADAP on 2011-01-12
> **itlarson said:**
> Is there a way to automate those hard drive checks that occur sometimes when I re-boot the computer?  It seems like it should be possible to do them late at night as a cron job.  There would still need to be some way to check if anything was recording first and re-schedule.

I think the drive test must happen when the drive is unmounted, so it can't be done if your system is running all the time.
If you have your system shut down when idle, it can interfere with recordings unless you figure out how long the disk test takes and make sure the system boot up early enough to get a disk test out of the way before the recording is scheduled to start. (this is what I do)
see:
[http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup)

You can also set up the system to boot at a specific time to do something like a backup. If this is set up, you can hit the 'c' key when it asks you to scan the disks on boot, and scan will happen at the scheduled wakeup time in the middle of the night. (I also do this).
see:
[http://www.mythtv.org/wiki/Using_ACPI_%26_MythTV_to_run_other_applications](http://www.mythtv.org/wiki/Using_ACPI_%26_MythTV_to_run_other_applications)

---

### Post by stevanbt on 2011-01-13
Hi,
I had a similar problem, this is my setup...

I have a dedicated backend that uses ACPI wake to startup and shutdown automatically - as long as there are no recordings and no users logged on.

All worked ok, except for when the box started up and was due to scan a disk - it would take a good while to check the disk and would delay being available.

So, what I wanted to do was (at shutdown) check if a disk check was due at next startup - if it was simply reboot (the disk check will happen, then the box will be idle and shut itself down), if no disk check was due the box will simply shutdown.

I edited /usr/bin/MythWakeSet like so:-
```

#!/bin/sh

#sb added this script from https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake as /proc/acpi/alarm no
#longer exists since kernel upgrade

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

# check the various partitions to see if any are due to be ckecked 
# at next boot, if they are then simply reboot now.
if /usr/bin/reset_fsck
then
  echo "No drives require checking at next boot, therefore wake will be set as normal" >> $LOG

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

else
  echo "One or more drives are due to be checked at next boot, rebooting now" >> $LOG
  sudo /sbin/shutdown -r now
  sleep 60
fi


```

and created a new file /usr/bin/reset_fsck referencing each partition to be checked in the for statement:-
```

#!/bin/bash
# check each device in turn

for device in /dev/sda1 /dev/sdb1 /dev/sdb2 /dev/sdb4 /dev/sdc1
do   
  cur_count=$(sudo tune2fs -l $device | awk '/Mount count:/ { print $3 }')
  max_count=$(sudo tune2fs -l $device | awk '/Maximum mount count:/ { print $4 }') 
  if [ $cur_count -ge $max_count ]; then 
  # if one device needs checking at next boot then don't bother checking any of the others
    exit 1
  fi
done

exit 0


```

Hope this helps, Steve.

---

### Post by itlarson on 2011-01-22
Thanks for the replies.  Alternatively, is there just a way to abort disk checks and boot?  The splash screen says you can press c to abort, but that's a #### lie.

---

### Post by tgm4883 on 2011-01-22
> **itlarson said:**
> Thanks for the replies.  Alternatively, is there just a way to abort disk checks and boot?  The splash screen says you can press c to abort, but that's a #### lie.

Pressing the letter to skip works for me. Are you possibly using a USB keyboard that isn't available at that time?

---

