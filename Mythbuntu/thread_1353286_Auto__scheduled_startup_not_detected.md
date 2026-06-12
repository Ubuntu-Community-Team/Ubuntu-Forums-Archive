---
title: "Auto / scheduled startup not detected"
date: 2009-12-12
forum: Mythbuntu
---

### Post by bcgrown on 2009-12-12
I have finally got MythWelcome to automatically start up, record, and shut down when all transcode jobs are done.

I set MythWelcome to automatically start the frontend.  The frontend shouldn't be started if it was a scheduled wake up,  but in fact the front end starts every time.

I added a startup script to mythbackend to output $status and sure enough, it is "user" every time even after a scheduled wake-up.  Mythbackend.log doesn't mention anything about autostart

Under Applications --> Settings --> Sessions and Startup,  I removed mythfrontend and added mythwelcome.

System is Mythbuntu 9.10, mythtv 0.22.

What is the logic behind how $status gets set?

---

### Post by Neon Dusk on 2009-12-12
Are you setting the wakeup time in the database using '/usr/bin/mythshutdown --setwakeup'? during the shutdown procedure?

In the backend set-up I've got 
wakeup time format set to 'yyyy-MM-ddThh:mm:ss' 
command to set Wakeup time: sudo /usr/bin/mythshutdown --setwakeup $time

This sets the wakeup time in the database which mythwelcome will then use to detect if it's a user or scheduled start.

(I write the wakealarm time using the mythwelcome settings)

To get mythwelcome to run instead of mythfrontend you can just edit /etc/mythtv/session-settings and set 'MYTHWELCOME=true'

---

### Post by bcgrown on 2009-12-13
I tried the command and time format that you suggested and the machine never woke up at all.

I am using the setwakeup.sh script from the [[COLOR="Blue"]ACPI Wakeup wiki[/COLOR]]("http://www.mythtv.org/wiki/ACPI_Wakeup#Integrate_into_mythTV")

```

#!/bin/sh
#$1 is the first argument to the script. It is the time in seconds since 1970
#this is defined in mythtv-setup with the time_t argument

echo 0 > /sys/class/rtc/rtc0/wakealarm      #this clears your alarm.
echo $1 > /sys/class/rtc/rtc0/wakealarm     #this writes your alarm
```

Time format is time_t and command to set wakeup time is sudo sh -c "/usr/bin/setwakeup.sh $time"

/etc/sudoers has this line added:
```
%mythtv ALL = NOPASSWD: /sbin/reboot, /sbin/shutdown, /bin/sh, /usr/bin/setwakeup.sh
```

Edit: The wakeup command and time format are the same in the MythWelcome settings page.

---

### Post by Neon Dusk on 2009-12-13
You'll need to add '/usr/bin/mythshutdown' to your sudoers file

You should have different settings in mythtv-setup and mythwelcome. The mythtv-setup values will write the wakeup time to the database and the mythwelcome values will set the bios wakealarm.

In the mythtv-setup you should have :-
Wakeup time format yyyy-MM-ddThh:mm:ss (the T in there is important mythshutdown will probably complain about the format if it's missing)
Command to set Wakeup time: sudo /usr/bin/mythshutdown --setwakeup $time

In the mythwelcome settings :-
Command to set wakeup time: sudo /usr/bin/setwakeup.sh $time (or however you're currently calling setwakeup.sh)
Wakeup time format: time_t (or whatever format you're currently passing to setwakeup.sh)

---

### Post by bcgrown on 2009-12-13
I tried that and still no wakeup.  The $status=auto appears on manual startup, though (I have a startup script that writes $status to a file so I can see what's going on.)  It seems like whatever method mythshutdown uses to set the ACPI wakeup time doesn't work for my hardware.

Edit:
If I do sudo sh -c "echo `date '+%s' -d '+ 3 minutes'` > /sys/class/rtc/rtc0/wakealarm", the PC wakes up at the right time.  If I use mythshutdown to set the wakeup time,  it gets written to /rtc0/wakealarm, but doesn't wake up.  That doesn't make any sense to me at all.  See log below.

```
dave@mythbox:~$ mythshutdown -v schedule --setwakeup 2009-12-13T22:58:00
2009-12-13 22:55:42.984 Using runtime prefix = /usr
2009-12-13 22:55:42.984 Using configuration directory = /home/dave/.mythtv
2009-12-13 22:55:42.985 Empty LocalHostName.
2009-12-13 22:55:42.985 Using localhost value of mythbox
2009-12-13 22:55:42.994 New DB connection, total: 1
2009-12-13 22:55:42.998 Connected to database 'mythconverg' at host: localhost
2009-12-13 22:55:42.998 Closing DB connection named 'DBManager0'
2009-12-13 22:55:42.998 Mythshutdown: --setwakeup
2009-12-13 22:55:42.999 Mythshutdown: wakeup time given is: 2009-12-13T22:58:00
2009-12-13 22:55:42.999 Connected to database 'mythconverg' at host: localhost
dave@mythbox:~$ mythshutdown -v schedule --shutdown
2009-12-13 22:55:49.768 Using runtime prefix = /usr
2009-12-13 22:55:49.769 Using configuration directory = /home/dave/.mythtv
2009-12-13 22:55:49.769 Empty LocalHostName.
2009-12-13 22:55:49.770 Using localhost value of mythbox
2009-12-13 22:55:49.779 New DB connection, total: 1
2009-12-13 22:55:49.783 Connected to database 'mythconverg' at host: localhost
2009-12-13 22:55:49.783 Closing DB connection named 'DBManager0'
2009-12-13 22:55:49.783 Mythshutdown: --shutdown
2009-12-13 22:55:49.784 Connected to database 'mythconverg' at host: localhost
2009-12-13 22:55:49.788 no daily wakeup times are set
2009-12-13 22:55:49.789 recording scheduled at: 2009-12-13T22:58:00
2009-12-13 22:55:49.789 will wake up at next scheduled program
2009-12-13 22:55:49.792 The next wakeup time is less than 15 mins away, not shutting down
dave@mythbox:~$ cat /proc/driver/rtc
rtc_time	: 06:55:57
rtc_date	: 2009-12-14
alrm_time	: 06:59:16
alrm_date	: ****-**-14
alarm_IRQ	: no
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: yes
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay

dave@mythbox:~$ date -u
Mon Dec 14 06:56:44 UTC 2009
dave@mythbox:~$ sudo shutdown -h now

Broadcast message from dave@mythbox
	(/dev/pts/0) at 22:56 ...

The system is going down for halt NOW!

```

---

### Post by Neon Dusk on 2009-12-14
Can't remember if these are default or not but in mythtv-setup you should also have :-
Server halt command : sudo /usr/bin/mythshutdown --shutdown
Pre Shutdown check command: sudo /usr/bin/mythshutdown --check

Mythwelcome:
nvram-wakeup restart command: should be empty
Command to reboot: sudo shutdown -h -r now
Command to shutdown: sudo shutdown -h -P now

From your log it looks like mythshutdown --shutdown didn't run the command to set the wakealarm as a recording was due to start within 15 minutes.

---

### Post by bcgrown on 2009-12-19
Well I eventually made it work but then my system died for a completely unrelated reason,  but of course I didn't save the settings.  ](*,)

I'll try to post the working settings next week when I get some new hardware.

---

### Post by bcgrown on 2009-12-28
In case anyone else has this problem (or I forget), here are the settings that work for me:

_mythbackend (mythtv-setup)_
General --> Screen 3: Disable "Delete files slowly" or else mythtranscode leaves phantom processes running that prevent the backend from going idle

General --> Screen 5
Block shutdown before client connected - DISABLED
Wakeup time format: yyyy-MM-ddThh:mm:ss
Command to set Wakeup Time: sudo mythshutdown --setwakeup $time
Server halt command: sudo mythshutdown --shutdown
Pre Shutdown check-command: sudo mythshutdown --check

_MythWelcome settings (mythwelcome --setup)_
Command to set wakeup time: sudo /usr/bin/setwakeup.sh $time
Wakeup time format: time_t
nvram-wakeup Restart command: (blank)
Command to shutdown: sudo shutdown -h now
Command to start the frontend: /usr/bin/mythfrontend

Save these settings, then run mythwelcome and press I to get into another settings page.

ENABLE "Automatically start myth frontend"

_And this line must be added to sudoers by the command *sudo visudo*_
%mythtv ALL = NOPASSWD: /sbin/shutdown, /bin/sh, /usr/bin/setwakeup.sh, /sbin/reboot,/usr/bin/mythshutdown

---

