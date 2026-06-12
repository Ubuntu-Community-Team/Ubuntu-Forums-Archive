---
title: "Backend boot and fsck ideas"
date: 2009-08-20
forum: Mythbuntu
---

### Post by stevanbt on 2009-08-20
Hi,
I have a separate FE & BE.  I have a number of minor issues which I'm getting round to looking at now.  

My BE is only ever on to either record a program or if the FE is running.  When the FE boots up it issues a Wake on LAN which boots the BE (this should be automatic but isn't and is something I need to ask about in another thread).

Occasionally the BE performs a disk check - depending on the partition being checked this can take a while and hence the FE is unusable until it's finished the check.  Obviously this can be a pain if the BE has been woken up by the FE or to record a tv programme (I know I can set the BE to wake up 15 mins before a recording, but it would still be an issue for the FE).

What do other people do (I'm sure my setup isn't particularly rare)?

I guess I'd like the BE to be able to tell when a disk check is about to be performed on any disk and delay it until 4am say when it isn't in use.

Does this sound achievable?

Thanks, Steve.

---

### Post by klc5555 on 2009-08-21
> **stevanbt said:**
> Hi,
I have a separate FE & BE.  I have a number of minor issues which I'm getting round to looking at now.  

My BE is only ever on to either record a program or if the FE is running.  When the FE boots up it issues a Wake on LAN which boots the BE (this should be automatic but isn't and is something I need to ask about in another thread).

Occasionally the BE performs a disk check - depending on the partition being checked this can take a while and hence the FE is unusable until it's finished the check.  Obviously this can be a pain if the BE has been woken up by the FE or to record a tv programme (I know I can set the BE to wake up 15 mins before a recording, but it would still be an issue for the FE).

What do other people do (I'm sure my setup isn't particularly rare)?

I guess I'd like the BE to be able to tell when a disk check is about to be performed on any disk and delay it until 4am say when it isn't in use.

Does this sound achievable?

Thanks, Steve.

I don't think the ext3 bootup sequence allows for the bootup fsck to be manipulated in quite that fashion. The fsck check is performed at boot before the affected partition is mounted.

However, if the machine happens to be awakened and running at, say, 4 AM, I imagine a little shell script could be written that unmounts all the non-root partitions and drives, does an fsck on them, and then remounts these non-root partitions and drives. (Or the script could simply shut the machine down after fsck without remounting.)If such a script were set up as, say, a weekly (or more frequent) cron job in the dark of night it would obviate the "/dev/blah mounted X times since last check, check forced" on these partitions when you boot the machine up for normal daily use, since a check will have been performed. You'd still have to deal with a 1 out of 27x or so fsck on the root partition, which, if it's the standard Mythbuntu <12G root partition, will complete in under a minute.

Another solution might be to move the non-root partitions on the BE from ext3 to something like xfs, which will avoid the bootup fsck on those partitions. This was the solution I chose for my master BE, where, when one of the 1TB storage drives was due, the fsck ran 50 minutes.

---

### Post by stevanbt on 2009-09-11
Hi,
I've made some progress with this.  I've written a script (copied most of it from this thread [http://ubuntuforums.org/showthread.php?t=908043&highlight=tune2fs]("http://ubuntuforums.org/showthread.php?t=908043&highlight=tune2fs")) that will check all drives to see if they will be checked at next boot:-

```

#!/bin/bash
# check each device in turn

for device in /dev/sda1 /dev/sda3 /dev/sda5 /dev/sda6 /dev/sda7 /dev/sdb1 /dev/s
db2 /dev/sdb3
do   
  cur_count=$(sudo tune2fs -l $device | awk '/Mount count:/ { print $3 }')
  max_count=$(sudo tune2fs -l $device | awk '/Maximum mount count:/ { print $4 }
') 
  if [ $cur_count -ge $max_count ]; then 
  # if one device needs checking at next boot then don't bother checking any of the others
    exit 1
  fi
done

exit 0


```

I now call it from /usr/bin/MythWakeSet:-

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
fi

```

My thinking was that if MythWakeSet was called the machine was in the process of being powered down, but if one or more drives was due to be checked at next boot then simply reboot the machine (no need to set the wake time) - and the disks would be checked.

The only problem that I seem to have is that the ```
sudo /sbin/shutdown -r now
``` at the foot of the MythWakeSet doesn't appear to work.  I've added the shutdown and tune2fs commands to sudoers file:-

```

steve@marple:~$ sudo -l
User steve may run the following commands on this host:
    (ALL) ALL
    (root) NOPASSWD: /sbin/tune2fs
    (root) NOPASSWD: /sbin/shutdown
    (root) NOPASSWD: /usr/bin/MythWakeSet
    (root) NOPASSWD: /proc/acpi/alarm
    (root) NOPASSWD: /usr/bin/MythShutdownCheck
    (root) NOPASSWD: /etc/init.d/mythtv-backend
    (root) NOPASSWD: /usr/bin/mythshutdown


```

Any suggestions?

Thanks, Steve.

---

