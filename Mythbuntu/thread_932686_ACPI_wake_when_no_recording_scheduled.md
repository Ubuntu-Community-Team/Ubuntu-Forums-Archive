---
title: "ACPI wake when no recording scheduled"
date: 2008-09-28
forum: Mythbuntu
---

### Post by poz on 2008-09-28
Following the directions to set MythTV to schedule ACPI wakeup in the [[COLOR="DeepSkyBlue"]ACPI Wake guide[/COLOR]]("https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake") works for me on my ASUS M2N61-AX motherboard, with the exception that if there are no scheduled recordings, the system will continue to boot daily at the last scheduled recording time.  (I am not yet using MythWelcome.)

Apparently, my /proc/acpi/alarm was getting its day and month fields overwritten with zeroes when no recording was scheduled, so that
2008-09-30 01:56:40  would be changed to
2008-00-00 01:56:40

I found a [[COLOR="DeepSkyBlue"]phoronix post[/COLOR]]("http://phoronix.com/forums/showthread.php?t=4277") from someone who seemed to be dealing with the same issue.  The fixes there didn't work for me, though; they had the effect of preventing any wakeups from getting scheduled at all.  Curiously, none of the posts on [[COLOR="DeepSkyBlue"]this ACPI thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=702310&highlight=mythtv+acpi") seem to involve mystery wakeups issues.

First I tried editing MythWakeSet, but it seems MythWakeSet doesn't write out anything when there is no recording scheduled.  So next I made a modification to /etc/init.d/hwclock.sh that seems to fix the issue for my system.  I changed the added line suggested by the ACPI Wake guide:

```
echo "$ACPITIME" > /proc/acpi/alarm && sleep 1 && echo "$ACPITIME" > /proc/acpi/alarm
```

to the following:
```
if [ "`echo "$ACPITIME" | grep "00-00"`" ]; then
  echo "+2100-00-00 00:00:00" > /proc/acpi/alarm && sleep 1 && \
echo "+2100-00-00 00:00:00" > /proc/acpi/alarm
else
  echo "$ACPITIME" > /proc/acpi/alarm && sleep 1 && \
echo "$ACPITIME" > /proc/acpi/alarm
fi
```

This workaround seems to fix the issue for me, as long I bother to boot the system again within a hundred years. :)

---

