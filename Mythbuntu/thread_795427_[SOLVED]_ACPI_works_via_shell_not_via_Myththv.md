---
title: "[SOLVED] ACPI works via shell not via Myththv"
date: 2008-05-15
forum: Mythbuntu
---

### Post by nanofuzzy1 on 2008-05-15
Hi,

When I want to write a date and a time in 'alarm', it works well with:

patrick@mythtv:/etc/init.d$ sudo sh -c 'echo 2008-05-16 09:34:11 > /proc/acpi/alarm'
patrick@mythtv:/etc/init.d$ cat /proc/acpi/alarm
2008-05-16 09:34:11

okay

when I write this command in the mythtvbackend with:

sudo sh -c 'echo $time > /proc/acpi/alarm'

the backendlog shows:

2008-05-14 07:19:15.786 Running the command to set the next scheduled
wakeup time :-
						sudo sh -c 'echo 2008-05-14 07:27:00 > /proc/acpi/alarm'
[sudo] password for mythtv:
2008-05-14 07:19:17.754 Running the command to shutdown this computer :-
						sudo /sbin/halt -p

this is correct, but the computer doesnt start. After a manual start, I can see the following:

patrick@mythtv:~$ cat /proc/acpi/alarm
2008-05-00 07:02:16

the output is always something confused. No day and the time is before(!) the shutdown.

My date format in mythtv is: yyyy-MM-dd hh:mm:ss

please help!

Thank you, patrick

---

### Post by majoridiot on 2008-05-15
> **nanofuzzy1 said:**
> Hi,

When I want to write a date and a time in 'alarm', it works well with:

patrick@mythtv:/etc/init.d$ sudo sh -c 'echo 2008-05-16 09:34:11 > /proc/acpi/alarm'
patrick@mythtv:/etc/init.d$ cat /proc/acpi/alarm
2008-05-16 09:34:11

okay

when I write this command in the mythtvbackend with:

sudo sh -c 'echo $time > /proc/acpi/alarm'

the backendlog shows:

2008-05-14 07:19:15.786 Running the command to set the next scheduled
wakeup time :-
						sudo sh -c 'echo 2008-05-14 07:27:00 > /proc/acpi/alarm'
[sudo] password for mythtv:
2008-05-14 07:19:17.754 Running the command to shutdown this computer :-
						sudo /sbin/halt -p

this is correct, but the computer doesnt start. After a manual start, I can see the following:

patrick@mythtv:~$ cat /proc/acpi/alarm
2008-05-00 07:02:16

the output is always something confused. No day and the time is before(!) the shotdown.

My date format in mythtv is: yyyy-MM-dd hh:mm:ss

please help!

Thank you, patrick

you need to give blind sudo permission for the time set to work... the info on this can be found here:

[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)

check the "sudo" section and make sure that /proc/acpi/alarm is correctly config'ed in visudo.
pay **close** attention to spaces and line-wraps... that's usually why it fails when it looks ok 
on edit.

---

### Post by nanofuzzy1 on 2008-05-15
this is the end of my visudo:

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%mythtv ALL = NOPASSWD: /sbin/shutdown, /usr/bin/MythWakeSet, /proc/acpi/alarm, /usr/bin/MythShutdownCheck, /etc/init.d/mythtv-backend, /usr/bin/mythshutdown, /sbin/halt -p, /usr/bin/mythsettime $time
%patrick ALL = NOPASSWD: /usr/bin/mythsettime

I even added the user patrick.

Can you find any problem?

thanx patrick

---

### Post by nanofuzzy1 on 2008-05-15
I added "$time" for user mythtv, but it didnt change the result. I tried it before without it.
I copied the line from the website you mention.

---

### Post by majoridiot on 2008-05-15
> **nanofuzzy1 said:**
> I added "$time" for user mythtv, but it didnt change the result. I tried it before without it.
I copied the line from the website you mention.

$time is not what mythtv needs sudo privs for... /proc/acpi/alarm is what you want.

your visudo entry for mythtv should look something similar to this, or at *least* include /proc/acpi/alarm

```
%mythtv ALL = NOPASSWD: /sbin/shutdown, /usr/bin/MythWakeSet, /proc/acpi/alarm, /usr/bin/MythShutdownCheck, /etc/init.d/mythtv-backend, /usr/bin/mythshutdown
```

---

### Post by nanofuzzy1 on 2008-05-15
I can not find any difference between your Code and the content of my visudo file. I copied the string from the website you mentioned.

---

### Post by majoridiot on 2008-05-15
> **nanofuzzy1 said:**
> I can not find any difference between your Code and the content of my visudo file. I copied the string from the website you mentioned.

the sudo for writing to the alarm is what is tripping you up.

copy-and-pasting long lines into a terminal can be dodgy... make *sure* there are no extra spaces or 
characters, that all of the commas are there, etc.

99.9% of the time, that is why that fails.

if you can't find anything, copy and paste your visudo here for troubleshooting.

---

### Post by nanofuzzy1 on 2008-05-15
I pasted it in my second post. Please see it above. I just pasted the end.

---

### Post by majoridiot on 2008-05-15
> **nanofuzzy1 said:**
> I pasted it in my second post. Please see it above. I just pasted the end.

if the %mythv line is line-wrapped, like it is in your post, then visudo again and put it all on one line.

and if they are still there, remove the "-p" from /sbin/halt and $time from the settime.

in your case, i think it should be:

```
%mythtv ALL = NOPASSWD: /sbin/shutdown, /usr/bin/MythWakeSet, /proc/acpi/alarm, /usr/bin/MythShutdownCheck, /etc/init.d/mythtv-backend, /usr/bin/mythshutdown, /sbin/halt, /usr/bin/mythsettime
```

---

### Post by nanofuzzy1 on 2008-05-15
I made the changes you proposed but the result is the same:

mythbackendlog:
2008-05-15 22:49:23.185 Running the command to set the next scheduled wakeup time :-
						sudo sh -c 'echo 2008-05-15 22:57:00 > /proc/acpi/alarm'

result (shuts down, no reboot, reboot manually):

patrick@mythtv:~$ cat /proc/acpi/alarm 
2008-05-00 09:34:11

This is the time I saved manually for testing purposes before. So mythv didnt change it at all.

Thank you for your help. Do you have another ideas?

My visudo (it has no breaks, I checked it):

%admin ALL=(ALL) ALL
%mythtv ALL = NOPASSWD: /sbin/shutdown, /usr/bin/MythWakeSet, /proc/acpi/alarm, /usr/bin/MythShutdownCheck, /etc/init.d/mythtv-backend, /usr/bin/mythshutdown, /sbin/halt, /usr/bin/mythsettime
%patrick ALL = NOPASSWD: /usr/bin/mythsettime, /proc/acpi/alarm

---

### Post by majoridiot on 2008-05-15
> **nanofuzzy1 said:**
> I made the changes you proposed but the result is the same:

mythbackendlog:
2008-05-15 22:49:23.185 Running the command to set the next scheduled wakeup time :-
						sudo sh -c 'echo 2008-05-15 22:57:00 > /proc/acpi/alarm'

result (shuts down, no reboot, reboot manually):

patrick@mythtv:~$ cat /proc/acpi/alarm 
2008-05-00 09:34:11

This is the time I saved manually for testing purposes before. So mythv didnt change it at all.

Thank you for your help. Do you have another ideas?

My visudo (it has no breaks, I checked it):

%admin ALL=(ALL) ALL
%mythtv ALL = NOPASSWD: /sbin/shutdown, /usr/bin/MythWakeSet, /proc/acpi/alarm, /usr/bin/MythShutdownCheck, /etc/init.d/mythtv-backend, /usr/bin/mythshutdown, /sbin/halt, /usr/bin/mythsettime
%patrick ALL = NOPASSWD: /usr/bin/mythsettime, /proc/acpi/alarm

there is no longer a sudo prompt in your backend log (like your first post had), so you fixed that much.

you stated in your first post that you could write ok to the alarm, but it failed with mythtv.  you never said
whether or not you actually tested it waking up manually.  

have you manually written a test time, verified it wrote ok and shut it down to see if it wakes that way?

---

### Post by nanofuzzy1 on 2008-05-16
Yes, waking up manually works perfect.

I changed in mythtvbackend the command to using mythsettime. The backendlog shows the correct time to write to acpi but the result is still strange. I got 16:16:16 as time and no day value. Btw, no more sudo prompt. Thanks!

Could it be that Mythtv shows me 24h and the comp also uses 24h, but mythtv gives 12am/pm to the comp? How can I find it out?

---

### Post by majoridiot on 2008-05-16
> **nanofuzzy1 said:**
> Yes, waking up manually works perfect.

I changed in mythtvbackend the command to using mythsettime. The backendlog shows the correct time to write to acpi but the result is still strange. I got 16:16:16 as time and no day value. Btw, no more sudo prompt. Thanks!

Could it be that Mythtv shows me 24h and the comp also uses 24h, but mythtv gives 12am/pm to the comp? How can I find it out?

i have no idea what your mythsettime script contains, so it's hard to say what it is doing.

i would recommend using the MythWakeSet script from the ACPI wake guide, as it is known to work.
the script itself and the instructions on how to use it are fairly clear.  be sure to change
the command in the backend as instructed, and to add /usr/bin/MythWakeSet to your visudo
for mythtv user.

you can check to see if it is setting the correct time by temporarily removing your halt -p
shutdown command and checking /proc/acpi/alarm after the script has run.  the time will be UTC
adjusted.

if your mobo clock is not UTC, simply remove everything between #!/bin/bash and #set the alarm.

---

### Post by nanofuzzy1 on 2008-05-16
Okay! You are my hero - almost!
The right time is writen to alarm - great:

2008-05-16 20:35:20.498 Running the command to set the next scheduled wakeup time :-
						sudo /usr/bin/MythWakeSet 2008-05-16 20:42:00
2008-05-16 20:35:20.513 Running the command to shutdown this computer :-....

BUT

The immediate test with cat ... returns:

patrick@mythtv:~$ cat /proc/acpi/alarm 
2008-05-16 18:42:00

This is two hours in the past. We have summer time so it is UTC +2 hours. I used the MythWakeSet in the original version and the "cutted" version as you told me. Astonishingly, the cat shows in each case the same, wrong result.

Please, one more time a great idea!

---

### Post by majoridiot on 2008-05-16
> **nanofuzzy1 said:**
> Okay! You are my hero - almost!
The right time is writen to alarm - great:

2008-05-16 20:35:20.498 Running the command to set the next scheduled wakeup time :-
						sudo /usr/bin/MythWakeSet 2008-05-16 20:42:00
2008-05-16 20:35:20.513 Running the command to shutdown this computer :-....

BUT

The immediate test with cat ... returns:

patrick@mythtv:~$ cat /proc/acpi/alarm 
2008-05-16 18:42:00

This is two hours in the past. We have summer time so it is UTC +2 hours. I used the MythWakeSet in the original version and the "cutted" version as you told me. Astonishingly, the cat shows in each case the same, wrong result.

Please, one more time a great idea!

getting closer... ;)

is the time in the "timestamp" file in your home directory, correct, or is it off by 2 hours
as well?

also, do you have your locale and time-zone set correctly?  you might also check to see if there
are any tzdata updates, etc. that you have not applied.

---

### Post by nanofuzzy1 on 2008-05-16
Sorry, there is no file "timestamp" in my homedirectory (patrick). What do you mean??
What is the locale?
Time-zone is Vienna - correct.
I applied all updates.
The mainboard is on local time.

---

### Post by majoridiot on 2008-05-16
> **nanofuzzy1 said:**
> Sorry, there is no file "timestamp" in my homedirectory (patrick). What do you mean??
What is the locale?
Time-zone is Vienna - correct.
I applied all updates.
The mainboard is on local time.

sorry... timestamp would be in /home/mythtv.

try replacing MythWakeSet with this and see what happens:

```
#!/bin/bash
#
# MythWakeSet
#
# set mythtv wake-up time with UTC-adjusted time
#

# temp file for working with time
temp_stamp=/home/mythtv/timestamp

# store the wake time passed from mythbackend
echo $1\ $2 > $temp_stamp

# Read the date in *locale* time format and tag the time-zone info to the wake time
localeadd=$(/bin/date -f $temp_stamp +%F\ %T\ %z)
echo $localeadd > $temp_stamp

# set the alarm
echo $localeadd > /proc/acpi/alarm
```

---

### Post by nanofuzzy1 on 2008-05-16
in /home/mythtv/timestamp I found:

2008-05-16 20:42:00 +0200

20:42 would have been the correct time. Obviously "somebody" calculated the time minus this two hours. Who is the bad guy?

Wow, you made my own script! Unfortunately, there is no change: 

2008-05-16 22:03:02.903 Running the command to set the next scheduled wakeup time :-
						sudo /usr/bin/MythWakeSet 2008-05-16 22:07:00
2008-05-16 22:03:02.951 Running the command to shutdown this computer :-
						ssudo /sbin/halt -p


patrick@mythtv:~$ cat /proc/acpi/alarm 
2008-05-16 20:07:00

---

