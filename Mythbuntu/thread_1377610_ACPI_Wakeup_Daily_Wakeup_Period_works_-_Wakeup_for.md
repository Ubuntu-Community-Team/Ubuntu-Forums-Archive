---
title: "ACPI Wakeup: Daily Wakeup Period works - Wakeup for recording does not"
date: 2010-01-10
forum: Mythbuntu
---

### Post by Stevi on 2010-01-10
Hello,

a few weeks ago I upgraded Mythbuntu from 9.04 to 9.10. Everything worked fine except ACPI Wakeup. My computer didn't wake up. At first I thought it could have to do something with [this]("http://ubuntuforums.org/showpost.php?p=8501812&postcount=32") bug ("shut down before 24:00 hours - the wakeup time $GWU would always get set to a time in the past").

But then I found out that my daily Wakeup/Shutdown period (in german: tägliches Start/Stop Intervall) from Mythwelcome works. Today I set the daily Wakeup Time to one hour in the future and my computer woke up properly.

So I think the command or script used by "wakeup for recordings" should be the same as used by Mythwelcome for daily Wakeup/shutdown. But I don't know what I have to change.

Any ideas what I should change to make wakeup for recordings work? Please help me! :)

Thanks in advance

Stevi.

---

### Post by laffinet on 2010-01-11
How exactly have you set up your system to shut down and wake up ?

Where do you tell the system to wake up for the next recording ?

Did it work when you were running 9.04 ?

---

### Post by Stevi on 2010-01-12
> **laffinet said:**
> How exactly have you set up your system to shut down and wake up ?

Where do you tell the system to wake up for the next recording ?


Hi Laffinet,

thanks for your reply. My settings:

```
#
# MythWakeSet
#
# set mythtv wake-up time with UTC-adjusted time
#

# set the alarm
sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm" # clear it
sudo sh -c "echo $1 > /sys/class/rtc/rtc0/wakealarm" # write the waketime

```

```
sudo visudo:
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%mythtv ALL = NOPASSWD: /sbin/shutdown, /usr/bin/MythWakeSet, /proc/acpi/alarm,$


```

Mythwelcome and relevant backend settings are attached as png files.

> 
Did it work when you were running 9.04 ?
Yes.

Any ideas?

---

### Post by laffinet on 2010-01-12
Could it be that it should just read:

```
sudo -H /usr/bin/MythWakeSet $time
```

without the "" ?

I'm also not sure about the 

```
sudo sh -c
```

in your script. Have you tried without it, eg just

```
echo 0 > /sys/class/rtc/rtc0/wakealarm 
echo $1 > /sys/class/rtc/rtc0/wakealarm 
```

---

### Post by Stevi on 2010-01-13
I'll try in about nine hours when I'm home from work :)

---

### Post by Stevi on 2010-01-14
Mmmhh, yesterday I played around with a few settings but the computer still doesn't wake up :(

Does anybody know what's the difference between setting a daily wakeup perid and setting a wakeup to record something? How does this exactly work?

---

### Post by Neon Dusk on 2010-01-14
They're should not be any difference - the same script should get used to set the wakealarm.

Can you change your MythWakeSet script to 
```

#!/bin/bash
#
# MythWakeSet
#
# set mythtv wake-up time with UTC-adjusted time
#

LOG=/var/log/mythtv/mythbackend.log

echo "Running $0 to set the wakeup time to $1" >> $LOG

sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm" # clear it
sudo sh -c "echo $1 > /sys/class/rtc/rtc0/wakealarm" # write the waketime
cat /proc/driver/rtc >> $LOG


```

and then post your /var/log/mythtv/mythbackend.log after a successful and unsuccessful wakeup?

Could you also post what Wakeup/Shutdown Periods you've got set in MythWelcome?

---

### Post by Stevi on 2010-01-14
Hi Neo Dusk,

I changed MythWakeSet and will post my log in about 2 hours.

I have a WakeUp period from from 6 pm to 10 pm (18:00-22:00 german time)

---

### Post by Stevi on 2010-01-14
For Info: I changed the daily wakeup time to see if it works.

Working daily WakeUp
```
...
2010-01-14 19:46:27.749 CheckShutdownServer returned - OK to shutdown
2010-01-14 19:46:27.757 Running the command to set the next scheduled wakeup time :-
						sudo -H mythshutdown --setwakeup 2010-01-14T23:52
SSDP::PerformSearch - did not write entire buffer.
SSDP::PerformSearch - did not write entire buffer.
2010-01-14 19:46:29.012 Running the command to shutdown this computer :-
						sudo -H mythshutdown --shutdown
SSDP::PerformSearch - did not write entire buffer.
SSDP::PerformSearch - did not write entire buffer.
Running /usr/bin/MythWakeSet to set wakeup time to Â§1
rtc_time	: 18:46:30
rtc_date	: 2010-01-14
alrm_time	: 19:15:00
alrm_date	: 2010-01-14
alarm_IRQ	: yes
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: no
DST_enable	: no
periodic_freq	: 1024
batt_status	: dead
2010-01-14 20:15:48.029 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
...
```
Not working wakeup for recording
```
...
2010-01-14 20:22:31.838 Running the command to set the next scheduled wakeup time :-
						sudo -H mythshutdown --setwakeup 2010-01-14T20:52
SSDP::PerformSearch - did not write entire buffer.
SSDP::PerformSearch - did not write entire buffer.
2010-01-14 20:22:33.000 Running the command to shutdown this computer :-
						sudo -H mythshutdown --shutdown
SSDP::PerformSearch - did not write entire buffer.
SSDP::PerformSearch - did not write entire buffer.
Running /usr/bin/MythWakeSet to set wakeup time to Â§1
rtc_time	: 19:22:34
rtc_date	: 2010-01-14
alrm_time	: 19:07:00
alrm_date	: 2010-01-15
alarm_IRQ	: yes
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: no
DST_enable	: no
periodic_freq	: 1024
batt_status	: dead
2010-01-14
...
```
Strangely the command (sudo -H mythshutdown --setwakeup 2010-01-14T23:52) is correct due to the upcoming recording. But the alarm time is totally different to the setwakeup command. The alarm-time always shows the time I set for daily wakeup period. I don't understand what's happening there.

---

### Post by Neon Dusk on 2010-01-14
> 
Strangely the command (sudo -H mythshutdown --setwakeup 2010-01-14T23:52) is correct due to the upcoming recording


This only sets the 'MythShutdownNextScheduled' value in the settings table of the database. The alarm time is set when mythshutdown --shutdown calls your MythWakeSet script.


> 
Running /usr/bin/MythWakeSet to set wakeup time to Â§1


This shows a problem - you should see a number like 1263509885 here instead of Â§1. So a corrupt value is getting sent to MythWakeSet - however that doesn't explain how the daily wakeup time is getting sent to to the wakeup alarm.

When mythshutdown --shutdown is called it will check when the next daily wakeup time and next recording is. It will then send the earliest time to the script set in mythwelcome.

If you want to try further testing then set-up the system as follows:-
```

mythshutdown --lock 

```
to prevent the system shutting down itself


In mythwelcome --setup 

remove the sudo before the shutdown command 
```

shutdown -h -P now

```

so that it will go through the process but not actually shutdown

set the command to set wakeup time to
```

sudo -H /usr/bin/MythWakeSet $time

```

remove time_t as the wakeup time format (in case this is corrupt in the database). Finish to save the changes.

go back into mythwelcome --setup and re-enter time_t as the wakeup time format

from a terminal window run
```

mythshutdown --setscheduledwakeup
mythshutdown --shutdown -v important

```
You should see further dubugging info.

After you've finished testing put back the sudo in the shutdown command
```

sudo shutdown -h -P now

```

unlock the system
```

mythshutdown --unlock

```

---

### Post by Stevi on 2010-01-17
Thx, Neon Dusk.

I changed my settings as described and played around with a few settings. Daily Wakeup still works. I disabled daily wakeup but nothing changed. I still get the corrupt value "Â§1".
Manually setting the wakeup alarm also works: 
> **Neon Dusk said:**
> 
```

mythshutdown --setscheduledwakeup
mythshutdown --shutdown -v important

```

I think there's something wrong with Mythwelcome. Is it possible to reinstall only Mythwelcome without touching the rest of the system?

---

### Post by Neon Dusk on 2010-01-17
You could enable the [auto build](http://www.mythbuntu.org/auto-builds) but that will update all the mythtv packages.

It would be interesting to see what the following db query returns
```

mysql -u mythtv -p
<enter password> (found in /etc/mythtv/mysql.txt as DBPassword)

use mythconverg;
SELECT * FROM settings WHERE value = 'MythShutdownNextScheduled' AND hostname IS NULL;
SELECT * FROM settings WHERE value = 'MythShutdownWakeupTimeFmt';

```

---

### Post by Stevi on 2010-01-17
```
myth@mytheiram:~$ mysql -u mythtv -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 183
Server version: 5.1.37-1ubuntu5 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> use mythconverg;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> SELECT * FROM settings WHERE value = 'MythShutdownNextScheduled' AND hostname IS NULL;
+---------------------------+------+----------+
| value                     | data | hostname |
+---------------------------+------+----------+
| MythShutdownNextScheduled |      | NULL     | 
+---------------------------+------+----------+
1 row in set (0,00 sec)

mysql> SELECT * FROM settings WHERE value = 'MythShutdownWakeupTimeFmt';
+---------------------------+--------+-----------+
| value                     | data   | hostname  |
+---------------------------+--------+-----------+
| MythShutdownWakeupTimeFmt | time_t | mytheiram | 
+---------------------------+--------+-----------+
1 row in set (0,00 sec)

mysql> 

```

---

### Post by Neon Dusk on 2010-01-17
Ok, I think I see the problem.

From your previous screenshots in the mythtv backend set-up you have :-

```

Wakeup time format: yyyy-MM-ddThh:mm

```

This should be

```

Wakeup time format: yyyy-MM-ddThh:mm:ss

```

---

### Post by Stevi on 2010-01-17
That's it!!! :D

Thank you so much. Unbelievable, I added "*:ss*" and it's working again. Great!


Again, thank you for your help Neon Dusk! :)

---

