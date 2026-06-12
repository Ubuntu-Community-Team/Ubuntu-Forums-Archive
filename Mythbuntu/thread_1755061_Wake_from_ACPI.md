---
title: "Wake from ACPI"
date: 2011-05-10
forum: Mythbuntu
---

### Post by phroman on 2011-05-10
Hi everyone.  Running Mythbuntu 10.04 2.6.35-28-generic, Asus P5Q mobo, updated BIOS.  Sorry this post is so long.

I tired to follow the wiki step by step but I'm completely overwhelmed.  All of the instructions kind of seem to go in a circle, and contradict themselves later on in the article.  

I'll try to describe what I've done so far, I hope someone might have some experience with this.  

From the wiki:

Step 1:  If you want to use ACPI to wake up your mythTV system, you first need to ensure that your BIOS supports this functionality.

At the terminal:
```

$ grep -i rtc /var/log/kern.log

```
Output is:
```

user@mythserver:~$ grep -i rtc /var/log/kern.log
May 10 00:03:11 mythserver kernel: [    0.396117] rtc_cmos 00:03: RTC can wake from S4
May 10 00:03:11 mythserver kernel: [    0.396145] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
May 10 00:03:11 mythserver kernel: [    0.396165] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
May 10 00:03:11 mythserver kernel: [    0.397716] Using IPI No-Shortcut mode
May 10 00:03:11 mythserver kernel: [    0.398058] rtc_cmos 00:03: setting system clock to 2011-05-10 07:03:01 UTC (1305010981)
May  9 17:09:12 mythserver kernel: [    0.400166] rtc_cmos 00:03: RTC can wake from S4
May  9 17:09:12 mythserver kernel: [    0.400194] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
May  9 17:09:12 mythserver kernel: [    0.400214] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
May  9 17:09:12 mythserver kernel: [    0.401943] Using IPI No-Shortcut mode
May  9 17:09:12 mythserver kernel: [    0.402283] rtc_cmos 00:03: setting system clock to 2011-05-10 00:09:04 UTC (1304986144)
May 10 06:03:44 mythserver kernel: [    0.396029] rtc_cmos 00:03: RTC can wake from S4
May 10 06:03:44 mythserver kernel: [    0.396056] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
May 10 06:03:44 mythserver kernel: [    0.396077] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
May 10 06:03:44 mythserver kernel: [    0.397807] Using IPI No-Shortcut mode
May 10 06:03:44 mythserver kernel: [    0.398145] rtc_cmos 00:03: setting system clock to 2011-05-10 13:03:35 UTC (1305032615)
user@mythserver:~$

```

NOTE: I know some of the timestamps are different, I've cut and pasted from different attempts, hope its not confusing.

It appears to set the time multiple times, possibly using UTC, but the last one is incorrect.  It appears my system can wake from S4 even though my BIOS only lists S1, S3 or Auto.

My BIOS options for Suspend are: 

S1 (POS) only
S3 only
Auto

I currently have it set to Auto.


Step 2:  Next, check your BIOS for the wakeup alarm function. 

Current BIOS settings are:

ACPI 2.0 Support  - Enabled
ACPI APIC Support - Enabled
Wake from RTC     - Enabled

Check the wakeup alarm function: 

```

user@mythserver:~$ sudo grep -i rtc /var/log/messages

May 10 00:03:11 mythserver kernel: [    0.396117] rtc_cmos 00:03: RTC can wake from S4
May 10 00:03:11 mythserver kernel: [    0.396145] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
May 10 00:03:11 mythserver kernel: [    0.396165] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
May 10 00:03:11 mythserver kernel: [    0.397716] Using IPI No-Shortcut mode
May 10 00:03:11 mythserver kernel: [    0.398058] rtc_cmos 00:03: setting system clock to 2011-05-10 07:03:01 UTC (1305010981)
May  9 17:09:12 mythserver kernel: [    0.400166] rtc_cmos 00:03: RTC can wake from S4
May  9 17:09:12 mythserver kernel: [    0.400194] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
May  9 17:09:12 mythserver kernel: [    0.400214] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
May  9 17:09:12 mythserver kernel: [    0.401943] Using IPI No-Shortcut mode
May  9 17:09:12 mythserver kernel: [    0.402283] rtc_cmos 00:03: setting system clock to 2011-05-10 00:09:04 UTC (1304986144)
May 10 06:03:44 mythserver kernel: [    0.396029] rtc_cmos 00:03: RTC can wake from S4
May 10 06:03:44 mythserver kernel: [    0.396056] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
May 10 06:03:44 mythserver kernel: [    0.396077] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
May 10 06:03:44 mythserver kernel: [    0.397807] Using IPI No-Shortcut mode
May 10 06:03:44 mythserver kernel: [    0.398145] rtc_cmos 00:03: setting system clock to 2011-05-10 13:03:35 UTC (1305032615)
May 10 06:50:33 mythserver kernel: [    0.400080] rtc_cmos 00:03: RTC can wake from S4
May 10 06:50:33 mythserver kernel: [    0.400108] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
May 10 06:50:33 mythserver kernel: [    0.400129] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
May 10 06:50:33 mythserver kernel: [    0.401678] Using IPI No-Shortcut mode
May 10 06:50:33 mythserver kernel: [    0.402018] rtc_cmos 00:03: setting system clock to 2011-05-10 13:50:19 UTC (1305035419)
May 10 07:04:56 mythserver kernel: [    0.695681] rtc_cmos 00:03: RTC can wake from S4
May 10 07:04:56 mythserver kernel: [    0.695702] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
May 10 07:04:56 mythserver kernel: [    0.695717] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
May 10 07:04:56 mythserver kernel: [    0.696799] Using IPI No-Shortcut mode
May 10 07:04:56 mythserver kernel: [    0.697099] rtc_cmos 00:03: setting system clock to 2011-05-10 14:04:43 UTC (1305036283)
May 10 07:13:10 mythserver kernel: [    0.407848] rtc_cmos 00:03: RTC can wake from S4
May 10 07:13:10 mythserver kernel: [    0.407876] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
May 10 07:13:10 mythserver kernel: [    0.407896] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
May 10 07:13:10 mythserver kernel: [    0.409637] Using IPI No-Shortcut mode
May 10 07:13:10 mythserver kernel: [    0.409972] rtc_cmos 00:03: setting system clock to 2011-05-10 14:12:56 UTC (1305036776)

```


Step 3: UTC, localtime and BIOS date format.  I do not have an explicit setting in my BIOS to choose UTC time, so don't know if its using it or not.

```

user@mythserver:~$ cat /proc/driver/rtc
rtc_time	: 16:15:50
rtc_date	: 2011-05-10
alrm_time	: 23:14:37
alrm_date	: 2011-05-10
alarm_IRQ	: yes
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: yes
BCD		: yes
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay
user@mythserver:~$

```

Step 4: I disabled HWclock updates.


Step 5:  I ran the following commands as described to try and set, then test the alarm time.

sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"
sudo sh -c "echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm"
cat /sys/class/rtc/rtc0/wakealarm
 

```

user@mythserver:~$ sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"
user@mythserver:~$ sudo sh -c "echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm"
user@mythserver:~$ cat /sys/class/rtc/rtc0/wakealarm
1305065423
user@mythserver:~$ cat /proc/driver/rtc
rtc_time	: 15:05:42
rtc_date	: 2011-05-10
alrm_time	: 22:10:23
alrm_date	: 2011-05-10
alarm_IRQ	: yes
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: yes
BCD		: yes
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay
user@mythserver:~$

```

The alarm is not set for 5 minutes into the future, but to 7 hours and 5 minutes into the future, as pointed out by Dan_R in the reply below.

I moved down to the section about Setting alarm when BIOS clock is in localtime.  

At the terminal:

```
SECS=`date -u --date "2008-12-22 10:45:00" +%s`
```

At the terminal: 
```
echo 0 > /sys/class/rtc/rtc0/wakealarm
```

and it returned: permission denied.  Same result with sudo. 

I'm in over my head but will keep looking of course.  I'd love to not have my system running 24/7 if possible.  Any help here would be very, very appreciated, Thanks!

---

### Post by Dan_R on 2011-05-10
I'm sorry that this doesn't fix your problem, but you will notice the alarm time has been set after running 

```
sudo sh -c "echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm
``` to roughly 6 hours and 5 minutes instead of just 5 minutes. I had this same problem over a year ago and don't remember the fix.

Also if you do get the localtime command working, that exact command will put your alarm time in the past and show something similar to ****-12-22
Try running something similar as root, for example below is 11pm
```

SECS=`date -u --date "2011-05-10 23:00:00" +%s`
```Last note, your system is getting the correct epoch time, noted by the 1305065423 which is Tue, 10 May 2011 22:10:23 GMT. The problem lies where the system uses the epoch time for the alarm, as said above it is adding 6 hours. Hopefully this at least points you in the right direction.

---

### Post by phroman on 2011-05-11
Hi Dan_R, thanks for your reply.

The only thing I can see is that from the output of:

```
$ cat /proc/driver/rtc
```

is that the alarm time is set to 7 hours and 5 minutes ahead, which would account for my location, west coast, USA, which is -8 GMT, minus 1 hour for daylight savings, is 7 hours.  Don't know why rtc_time is local time, and it looks like its passing UTC time to the BIOS for the alarm.  Is the rtc_time the BIOS time? If so its not UTC, correct? 

I read about disabling hpet in /etc/default/grub.conf, which I did, with no change.


> 
Try running something similar as root, for example below is 11pm

SECS=`date -u --date "2011-05-10 23:00:00" +%s`


```
user@mythserver:~$ sudo SECS=`date -u --date "2011-05-10 23:15:00" +%s`
usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-p prompt]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U username] [-u
            username|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] file ...
user@mythserver:~$ 

```

I ran it without sudo, returned no error or other output.

I'm not clear on what the next 2 commands from the wiki actually do, but I tried them and I got Permission Denied, even with sudo:

```
user@mythserver:~$ SECS=`date -u --date "2011-05-10 22:10:00" +%s`
user@mythserver:~$ echo 0 > /sys/class/rtc/rtc0/wakealarm
-bash: /sys/class/rtc/rtc0/wakealarm: Permission denied
user@mythserver:~$ sudo echo 0 > /sys/class/rtc/rtc0/wakealarm
-bash: /sys/class/rtc/rtc0/wakealarm: Permission denied
user@mythserver:~$ 
```

```
user@mythserver:~$ cat /proc/driver/rtc
rtc_time	: 22:02:59
rtc_date	: 2011-05-10
alrm_time	: 04:31:42
alrm_date	: ****-**-**
alarm_IRQ	: no
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: no
BCD		: yes
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay
user@mythserver:~$ 

```

I'll keep plugging away, thank's for your help.

---

### Post by Dan_R on 2011-05-11
I don't know why but you cannot run that command unless you're logged in as root, so you have to do "sudo su" and log in with the root password. Then retry those commands and you should be allowed at that point.

---

