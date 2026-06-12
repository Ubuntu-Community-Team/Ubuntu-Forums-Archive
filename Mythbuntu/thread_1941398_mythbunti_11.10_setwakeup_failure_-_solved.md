---
title: "mythbunti 11.10 setwakeup failure - solved"
date: 2012-03-15
forum: Mythbuntu
---

### Post by tobiz on 2012-03-15
I've finally got my clean install mythbuntu 0.24, ubuntu 11.10, gnome 3 system to shutdown on no user logged in and start on RTC for next recording date/time (see [http://www.mythtv.org/wiki/ACPI_Wakeup]("http://www.mythtv.org/wiki/ACPI_Wakeup")).  The major problem was the system would not power down on system shutdown, including "sudo shutdown -h now", the system would hang but not power off (it wasn't as simple as this, but I won't go into the whole mess).  The solution, discovered by others, is to stop the network prior to powering down (there seems to be a basic problem with 11.10 in this area and this a work around and not a fix to the fundamental problem).  My fix was to incorporate this into the checklogin.sh script.  I changed the script to:

#!/bin/bash
# Check to see if anyone is currently logged in or if the machine was recently switched on.
# Echoed text appears in log file. It can be removed and --quiet added to the 
# grep command once you are satisfied that mythTV is working properly.
# Exit codes:-
# 2 - Machine recently switched on, don't shut down.
# 1 - A user is logged in, don't shut down.
# 0 - No user logged in, OK to shut down.

# Customizable variables
MIN_UPTIME=10   # Minimum up time in minutes
# End of customizable variables

# Get a date/time stamp to add to log output
DATE=`date +%F\ %T\.%N`
DATE=${DATE:0:23}

UPTIME=`cat /proc/uptime | awk '{print int($1/60)}'`

if [ "$UPTIME" -lt "$MIN_UPTIME" ]; then
    echo $DATE Machine uptime less than $MIN_UPTIME minutes, don\'t shut down.
    exit 2
fi

if who -q | grep "users=0"; then
    echo $DATE No users are logged in, ok to shut down.
[B]# Added the following line
    sudo sh -c "/etc/init.d/networking stop"[/B]
    exit 0
  else
    echo $DATE Someone is still logged in, don\'t shut down.
    exit 1
fi 

You also need to update /etc/sudoers, by sudo visudo, to:
%mythtv ALL = NOPASSWD: /sbin/shutdown, /bin/sh, /usr/bin/setwakeup.sh, **/etc/init.d/networking**

With these minor updates it works for me.

---

