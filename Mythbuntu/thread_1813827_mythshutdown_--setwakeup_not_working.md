---
title: "mythshutdown --setwakeup not working"
date: 2011-07-28
forum: Mythbuntu
---

### Post by Quadari on 2011-07-28
Hello all,

I am attempting to configure my mythbuntu box (front- and back-end in one) to automatically shutdown when idle and wakeup when it needs to record or when I tell it to.

In general I'm following the instructions on this page:
[http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup)

When I test the automatic turning on, by using these commands:
```
sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"
sudo sh -c "echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm"
cat /proc/driver/rtc
```

Then /proc/driver/rtc correctly shows the alrm_time and alrm_date and if I shut the computer down it does indeed turn itself back on in 5 minutes.  So I'm pretty convinced that that is working.

I then set up my mythbackend and mythshutdown settings (almost) as indicated on the mythtv wiki page linked above.  So just to be complete, here are the settings:
In mythtv-setup > General > Shutdown/Wakeup Options:
```
Startup command:
Block shutdown before client connected: unchecked
Idle shutdown timeout (secs): 600
Maximum wait for recording (mins): 60
Startup before recording (secs): 600
Wakeup time format: yyyy-MM-ddThh:mm:ss
Command to set wakeup time: mythshutdown --setwakeup $time
Server halt command: mythshutdown --shutdown
Pre-shutdown-check command: mythshutdown --check && checklogin.sh
```

My mythwelcome --setup settings are:
```

Command to Set Wakeup Time: sudo sh -c "/usr/bin/setwakeup.sh $time"
Wakeup time format: time_t
nvram-wakeup Restart Command:
Command to reboot: /sbin/reboot
Command to shutdown: sudo shutdown -h now
Command to run Xterm: xterm
Command to run to start the Frontend: /usr/bin/mythfrontend
```

So now on to the problem.  When I set the wakealarm time manually it works.  Example:

```

$ sudo sh -c "echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm"
$ cat /proc/driver/rtc 
rtc_time	: 16:32:49
rtc_date	: 2011-07-28
alrm_time	: 16:37:47
alrm_date	: 2011-07-28
alarm_IRQ	: yes
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: no
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay

```

However, when I try to have mythshutdown set the wakeup time it just doesn't work.  The following commands (I think) first clear the wakealarm and then try to set it using mythshutdown.  I will also have mythshutdown be slightly verbose, in case it helps people help me debug this.
```

$ sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"
$ mythshutdown -w 2011-07-29T10:48:00 -v important
2011-07-28 11:35:49.528 Using runtime prefix = /usr
2011-07-28 11:35:49.528 Using configuration directory = /home/mymythuser/.mythtv
2011-07-28 11:35:49.530 Empty LocalHostName.
2011-07-28 11:35:49.557 New DB connection, total: 1
2011-07-28 11:35:49.567 Closing DB connection named 'DBManager0'
2011-07-28 11:35:49.585 Mythshutdown: wakeup time given is: 2011-07-29T10:48:00
$ cat /proc/driver/rtc 
rtc_time	: 16:36:59
rtc_date	: 2011-07-28
alrm_time	: 16:41:46
alrm_date	: ****-**-28
alarm_IRQ	: no
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: no
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay

```


So to me, that looks like mythshutdown was unsuccessful at setting the alarm to wake the computer.  I know that in practice it also doesn't work as if I turn the computer off it will not wakeup to make recordings.

If it's needed, I'm on Ubuntu 10.04.3 LTS, Linux 2.6.32-33-generic and my mythtv version numbers are:
```

MythTV Version   : v0.24.1-58-g760c8db
MythTV Branch    : fixes/0.24
Network Protocol : 63
Library API      : 0.24.20110505-1
QT Version       : 4.6.2

```


I've sort of reached my limit in terms of knowledge of the situation, so I am grateful for any help or suggestions people have.

Thanks! =;

---

### Post by Neon Dusk on 2011-07-29
mythshutdown -w will only write the wakeup time to the database not to the bios.

For testing I usually add 
```

LOG=/var/log/mythtv/mythbackend.log

echo "Running $0 to set the wakeup time to $1" >> $LOG

```

to to start of setwakeup.sh

and ```
cat /proc/driver/rtc >> $LOG
``` to the end. Then check mythbackend.log after myth has tried to shut down it self. You can change the MythShutdown/MythWelcome shutdown command so that it doesn't actually shutdown (for testing)

---

