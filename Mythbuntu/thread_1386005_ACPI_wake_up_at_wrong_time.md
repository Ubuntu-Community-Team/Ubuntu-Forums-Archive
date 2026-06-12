---
title: "ACPI wake up at wrong time"
date: 2010-01-20
forum: Mythbuntu
---

### Post by radnor on 2010-01-20
Hello to all!

I have a small problem.  Last night I set the system clock to UTC.  I did not check it this morning so I am assuming it is still UTC. (No RTC write back upon shutdown)  A sample recording was to start at 0700.

```
1263988500  <--  This is time_t

rtc_time : 06:50:04 <--  This is my LOCAL time
rtc_date : 2010-01-20 
alrm_time : 11:55:00 <-- 5 minutes before rec time UTC adjusted.  WHY?!?
alrm_date : 2010-01-20 
alarm_IRQ : yes 
alrm_pending : no 
24hr : yes 
periodic_IRQ : no 
update_IRQ : no 
HPET_emulated : no 
DST_enable : no 
periodic_freq : 1024 
batt_status : okay
```

rc.S file is:
```
#
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.

TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=no
VERBOSE=no
FSCKFIX=no
## (ADDED THE FOLLOWING)
HWCLOCKACCESS=no
```

My question is, do I have something messed up in the DB which is adjusting the alarm time?  Not sure where to look for this.

Thank you for the help!!!

Todd

---

### Post by radnor on 2010-01-20
can time_t (from BE setup) converted to UTC?  I'm looking to do this on the general tab.  Such as: time_t +%u???

---

