---
title: "MythTV/Install/WhatNext/ACPIWake"
date: 2008-02-20
forum: Mythbuntu
---

### Post by Rickytoo on 2008-02-20
I am trying to follow this guide (my MB is listed there as working):
[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)
but I'm stuck.

Everything okay up to here:
>Another Test

>Before proceeding, go into the frontend and schedule a recording an hour or .so from now and note the time it starts.

>Now we can test to see if the scripts and their interfaces with MythTV are >set up correctly. First, set /proc/acpi alarm to a known value (again, if your >date/time format is not yyyy-MM-dd hh:mm:ss, adjust as needed):

 >     $ sudo sh -c 'echo "2007-12-12 12:12:12" > /proc/acpi/alarm'

>Then, check to see it was set. You should see something simlar to:

>      $ cat /proc/acpi/alarm
>     2007-**-12 12:12:12

Okay up to here

>Now, fire up the backend to test the write to /proc/acpi/alarm. In this case, we >won't lauch it as a daemon so we can see what is being logged:

>      $ mythbackend &

responds with:

richard@mythtv-desktop:~$ mythbackend &
[1] 7742
richard@mythtv-desktop:~$ 2008-02-20 11:33:41.104 Using runtime prefix = /usr
2008-02-20 11:33:41.122 New DB connection, total: 1
2008-02-20 11:33:41.130 Connected to database 'mythconverg' at host: localhost
2008-02-20 11:33:41.134 Current Schema Version: 1160
Starting up as the master server.
2008-02-20 11:33:41.158 New DB connection, total: 2
2008-02-20 11:33:41.158 Connected to database 'mythconverg' at host: localhost
2008-02-20 11:33:41.161 EITHelper: localtime offset 0:00:00 
2008-02-20 11:33:41.306 New DB connection, total: 3
2008-02-20 11:33:41.307 Connected to database 'mythconverg' at host: localhost
2008-02-20 11:33:41.721 EITHelper: localtime offset 0:00:00 
2008-02-20 11:33:42.251 EITHelper: localtime offset 0:00:00 
2008-02-20 11:33:42.767 EITHelper: localtime offset 0:00:00 
2008-02-20 11:33:43.292 New DB scheduler connection
2008-02-20 11:33:43.292 Connected to database 'mythconverg' at host: localhost
 is defined, but isn't attached to a cardinput.
2008-02-20 11:33:44.684 Main::Registering HttpStatus Extension
2008-02-20 11:33:44.684 mythbackend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2008-02-20 11:33:44.684 Enabled verbose msgs:  important general
/var/lib/mythtv/recordings/nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '/var/lib/mythtv/recordings' exists and that both 
the directory and that file are writeable by this user.

Which is not what I was expecting from the following:

>It should immediately start warning you of impending shutdown, count it down >and then stop. Hit Enter to get a command prompt and then check to see if >MythWakeSet worked:

>      $ cat /proc/acpi/alarm
>      2007-**-01 20:59:00

I would be grateful for some help.
Thanks

---

### Post by dannyboy79 on 2008-02-20
> **Rickytoo said:**
> I am trying to follow this guide (my MB is listed there as working):
2008-02-20 11:33:43.292 Connected to database 'mythconverg' at host: localhost
 is defined, but isn't attached to a cardinput.
2008-02-20 11:33:44.684 Main::Registering HttpStatus Extension
2008-02-20 11:33:44.684 mythbackend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2008-02-20 11:33:44.684 Enabled verbose msgs:  important general
/var/lib/mythtv/recordings/nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '/var/lib/mythtv/recordings' exists and that both 
the directory and that file are writeable by this user.
 

I see 2 major errors within the output when you started mythbackend

first, it says something about a cardinput not be attached. Have you chose a "source" (listings), then a capture device, then associated them together within mythbackend-setup?

it also appears that your permissions aren't right for your recordings directory.

here's what mine looks like whne I issue ls -la

drwxrwsr-x  4 mythtv mythtv 53248 2008-02-20 13:30 /var/lib/mythtv/recordings

OR

it's because you're starting mythbackend as yourself instead of the mythtv user. I am fairly new to linux so I don't know how to start a command as another user. You could try adding yourself to the mythtv group.

---

### Post by majoridiot on 2008-02-26
permissions shouldn't be an issue as long as the user you are logged in as is a member of the 
mythtv group.  you would also get that error if the backend was already running and you tried 
to run another instance.

try shutting down the backend before issuing the command:

```
$ sudo /etc/init.d/mytv-backend stop
$ mythtv-backend &
```

if still no good, try issuing the command as sudo:

```
$ sudo mythtv-backend &
```

---

### Post by Rickytoo on 2008-02-27
Thanks for your replies. Just to clarify, I am using Mythtv version 0.20.2 installed from the live cd. Trying to follow the section 'Another Test' from the guide. I get get the following output which isn't what the guide indicates. Is the guide wrong or is it me? I tried 'sudo mythbackend &' but I still don't get the expected results. It did add me to the mythtv group.
> richard@mythtv-desktop:~$ sudo sh -c 'echo "2008-12-12 12:12:12:" > /proc/acpi/alarm'
[sudo] password for richard:
richard@mythtv-desktop:~$ cat /proc/acpi/alarm
2008-12-12 12:12:12
richard@mythtv-desktop:~$ mythbackend &
[1] 7313
richard@mythtv-desktop:~$ 2008-02-27 12:17:58.599 Using runtime prefix = /usr
2008-02-27 12:17:58.607 New DB connection, total: 1
2008-02-27 12:17:58.611 Connected to database 'mythconverg' at host: localhost
2008-02-27 12:17:58.613 Current Schema Version: 1160
Starting up as the master server.
2008-02-27 12:17:58.619 New DB connection, total: 2
2008-02-27 12:17:58.619 Connected to database 'mythconverg' at host: localhost
2008-02-27 12:17:58.620 EITHelper: localtime offset 0:00:00 
2008-02-27 12:17:58.762 New DB connection, total: 3
2008-02-27 12:17:58.763 Connected to database 'mythconverg' at host: localhost
2008-02-27 12:17:59.132 EITHelper: localtime offset 0:00:00 
2008-02-27 12:17:59.643 EITHelper: localtime offset 0:00:00 
2008-02-27 12:18:00.147 EITHelper: localtime offset 0:00:00 
2008-02-27 12:18:00.660 New DB scheduler connection
2008-02-27 12:18:00.660 Connected to database 'mythconverg' at host: localhost
2008-02-27 12:18:02.031 Main::Registering HttpStatus Extension
2008-02-27 12:18:02.031 mythbackend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2008-02-27 12:18:02.031 Enabled verbose msgs:  important general
/var/lib/mythtv/recordings/nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '/var/lib/mythtv/recordings' exists and that both 
the directory and that file are writeable by this user.

[1]+  Exit 239                mythbackend
richard@mythtv-desktop:~$ sudo mythbackend &
[1] 7333
richard@mythtv-desktop:~$ 2008-02-27 12:19:13.917 Using runtime prefix = /usr
2008-02-27 12:19:13.925 New DB connection, total: 1
2008-02-27 12:19:13.929 Connected to database 'mythconverg' at host: localhost
2008-02-27 12:19:13.931 Current Schema Version: 1160
Starting up as the master server.
2008-02-27 12:19:13.934 New DB connection, total: 2
2008-02-27 12:19:13.935 Connected to database 'mythconverg' at host: localhost
2008-02-27 12:19:13.936 EITHelper: localtime offset 0:00:00 
2008-02-27 12:19:14.077 New DB connection, total: 3
2008-02-27 12:19:14.077 Connected to database 'mythconverg' at host: localhost
2008-02-27 12:19:14.446 EITHelper: localtime offset 0:00:00 
2008-02-27 12:19:14.959 EITHelper: localtime offset 0:00:00 
2008-02-27 12:19:15.463 EITHelper: localtime offset 0:00:00 
2008-02-27 12:19:15.976 New DB scheduler connection
2008-02-27 12:19:15.976 Connected to database 'mythconverg' at host: localhost
2008-02-27 12:19:17.342 Main::Registering HttpStatus Extension
2008-02-27 12:19:17.342 mythbackend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2008-02-27 12:19:17.343 Enabled verbose msgs:  important general
2008-02-27 12:19:17.343 AutoExpire: Found 4 recorders w/max rate of 555 MiB/min
2008-02-27 12:19:17.343 AutoExpire: Required Free Space: 5.3 GB w/freq: 5 min
2008-02-27 12:19:17.984 Reschedule requested for id -1.
2008-02-27 12:19:18.040 Scheduled 1 items in 0.1 = 0.04 match + 0.01 place
2008-02-27 12:19:18.042 Seem to be woken up by USER
2008-02-27 12:20:40.187 EITScanner: Now looking for EIT data on multiplex of channel 16
2008-02-27 12:20:53.483 EITScanner: Now looking for EIT data on multiplex of channel 16
2008-02-27 12:21:01.271 EITScanner: Now looking for EIT data on multiplex of channel 10
2008-02-27 12:21:13.166 EITScanner: Now looking for EIT data on multiplex of channel 12

---

### Post by majoridiot on 2008-02-27
> **Rickytoo said:**
> Trying to follow the section 'Another Test' from the guide. I get get the following output which isn't what the guide indicates. Is the guide wrong or is it me? I tried 'sudo mythbackend &' but I still don't get the expected results. It did add me to the mythtv group.

run the command as sudo...

did you make the changes in mythtv-setup outlined in the step just before that section?

if so, what are your entries for each field on Page 5 "Shutdown and Wakep Options"?

---

### Post by Rickytoo on 2008-02-27
> did you make the changes in mythtv-setup outlined in the step just before that section?

if so, what are your entries for each field on Page 5 "Shutdown and Wakep Options"?

Idle timeout (secs): 30
Max wait for recording (min): 1
Startup before rec. (secs): 200
Wakeup time format: yyyy-MM-dd hh:mm:ss
Set wakeup command: sudo sh -c 'echo $time > /proc/acpi/alarm'
Server halt command: sudo /etc/init.d/mythtv-backend stop
Pre Shutdown check-command: exit 0

---

### Post by Rickytoo on 2008-02-28
I've made some progress. When set to record a programme, it will shut down now, but not wake up.

What I've done:
I mistakenly set the shut-down option on Page 5, 'Shutdown and Wakeup Options' for poweroff kernel. I've changed it to 'sudo shutdown -h -P now'.
I have disabled the timed login feature as described here:
[http://ubuntuforums.org/showthread.php?t=594276&highlight=auto+login](http://ubuntuforums.org/showthread.php?t=594276&highlight=auto+login)

Wakeup problem still to resolve:
This part of the guide aplies to my set-up:
> The following command uses our example time format of yyyy-MM-dd hh:mm:ss and adds 5 minutes to the ACPI alarm. If your time format is different, you will need to adjust the ordering of +00-00-00 00:05:00 to comply.



    *

      $ sudo sh -c 'echo "+00-00-00 00:05:00" > /proc/acpi/alarm'

It is a good idea to check if the command did the job right.

    *

      If the year part looks like "0007" instead of "2007", change +00 with +2000; this worked for Acer Ferrari 3400 laptop and Asus M2NPV-VM motherboard... 
so I changed +00 to +2000 and the wakeup at this point works okay. So does that change the Wakeup time format of yyyy-MM-dd hh:mm:ss on Page 5, 'Shutdown and Wakeup Options'?

Issues with the guide:
The result of entering 'mythbackend &' command (as described in my previous post) doesn't give the results indicated in the guide (so I've ignored that test).
There is no mention of the timed login feature which appears to be a default setting on the installation.

I'd be grateful for any help.

---

### Post by majoridiot on 2008-02-28
> **Rickytoo said:**
> Issues with the guide:
The result of entering 'mythbackend &' command (as described in my previous post) doesn't give the results indicated in the guide (so I've ignored that test).

i fixed that in the guide yesterday, since running it without sudo does not work in all cases.  
the guide now instructs you to run it as sudo.

> **Rickytoo said:**
> There is no mention of the timed login feature which appears to be a default setting on the installation.

there is no mention, because there was no timed login, nor mythbuntu for that matter,
when i originally wrote that guide.  feel free to add the information on disabling timed login 
(as others did for the mythwelcome section) if you want.  if not, i will try to add it soon.

> **Rickytoo said:**
> so I changed +00 to +2000 and the wakeup at this point works okay. So does that change the Wakeup time format of yyyy-MM-dd hh:mm:ss on Page 5, 'Shutdown and Wakeup Options'?

this is a good question- but one i can't answer.  my suggestions are:

check the "page history" of the ACPI wakeup page to see who added your mobo to the list
and PM them for the yyyy settings; or

erase the shutdown command on the mythv-setup page, play around with the yyyy 
part of the time format (maybe 2000 or 20yy?) and then cat /proc/acpi/alarm 
after it "stops" to see what is being written, to work it out by trial-and-error; or

post to the mythtv mailing list, asking for the correct yyyy settings (be sure to post your mobo
model and vendor- you didn't do that here.)

---

### Post by Rickytoo on 2008-02-29
> **majoridiot said:**
> 
there is no mention, because there was no timed login, nor mythbuntu for that matter,
when i originally wrote that guide.  feel free to add the information on disabling timed login 
(as others did for the mythwelcome section) if you want.  if not, i will try to add it soon.
I hadn't noticed that you were the original writer. People like you that take the time and effort to write such guides enable people like me to explore, learn and to enjoy a sense of achievement when we get something to work, and for that I thank you!
> **majoridiot said:**
> 
play around with the yyyy 
part of the time format (maybe 2000 or 20yy?) and then cat /proc/acpi/alarm 
after it "stops" to see what is being written, to work it out by trial-and-error

I've tried a number of variations, but it only results in the month and day being set to zero.
> **majoridiot said:**
> 
post to the mythtv mailing list, asking for the correct yyyy settings (be sure to post your mobo
model and vendor- you didn't do that here.)
I have posted on this group today regarding the Gigabyte GA-M68SM-S2.

I am beginning to think there is more to it than just the 'wakeup time format', I'm wondering if the $time variable passes the correct information, but I don't have the understanding to be able to check that out.

One other point (warning, possible dumb idea coming up!), I am using a couple of Hauppauge Nova T 500's for which there have been driver issues. I followed the guide here: [http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500 _PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500 _PCI) to resolve that.
From the bit I've read, /proc/acpi/alarm was being deprecated from kernel version 2.6.22, but from what I understand, that's the kernel I'm using together with /proc/acpi/alarm. So I don't understand and I wonder if something is broken by following that guide?

---

### Post by majoridiot on 2008-02-29
> **Rickytoo said:**
> I hadn't noticed that you were the original writer. People like you that take the time and effort to write such guides enable people like me to explore, learn and to enjoy a sense of achievement when we get something to work, and for that I thank you!

you are certainly welcome... we're all here to learn and share info ;)

> **Rickytoo said:**
> I have posted on this group today regarding the Gigabyte GA-M68SM-S2.

i don't know if it helps or not, but the person that added your motherboard did so under
the name "PaulMyket".

a thought on a possible workaround... set the time format (yyy-MM... etc.) to however it was 
when you were able to set the wake time by hand and successfully wake it.  then add the
following line as the *last* line of MythWakeSet:
```
sudo sh -c 'echo "+2000-00-00 00:00:00" > /proc/acpi/alarm'
```

the end of the file should look like this:
```
# set the alarm
echo $utcadj > /proc/acpi/alarm
sudo sh -c 'echo "+2000-00-00 00:00:00" > /proc/acpi/alarm'
```

give that a shot and see if it works.

---

### Post by majoridiot on 2008-03-03
this was followed up on privately and was troubleshooted remotely.  there were two issues causing the problem:

1: the information in the guide concerning /etc/init.d/hwclock.sh was outdated, causing confusion on where to place
the command to write to the alarm.

2: the information concerning "local" time and using a shell command was incorrect and did not work.

both errors were corrected in the guide and everything is working 100%.

---

### Post by dannyboy79 on 2008-03-04
> **majoridiot said:**
> this was followed up on privately and was troubleshooted remotely.  there were two issues causing the problem:

1: the information in the guide concerning /etc/init.d/hwclock.sh was outdated, causing confusion on where to place
the command to write to the alarm.

2: the information concerning "local" time and using a shell command was incorrect and did not work.

both errors were corrected in the guide and everything is working 100%.
excellent for work for being a majoridiot. Just kidding. Seriously, great job on helping him get this working.

---

### Post by Köntzä on 2008-03-07
Ooh how I envy you guys running ACPI...

I did a full reinstall of Ubuntu on my old VDR-box; an IBM Netvista 6286. The thing was designed during the last years of the previous millenium, and came out of the factory sometime around 2000. BIOS is from 2002, and both that and the manuals state ACPI compliance.

I tried every trick I could find from the net on getting this thing to automatically wake up with ACPI. Nothing helped.

I finally reverted to using nvram-wakeup (it worked on the previous installment). Unfortunately I hadn't documented anywhere what options I gave to nvram-wakeup to use it. I didn't want to hose my system by haphazardly setting nvram-wakeup up, as using it carelessly is dangerous. After reading through nvram-wakeup's code, scarce documentation, and the output of guess-help I found the right setup for using nvram-wakeup. The answer was, luckily, in the presets of that app. Command-line options are:
```
--directisa --iwname ibm_pc_300pl
```

But back on the subject of ACPI: Does anyone reading this thread have inside knowledge is ACPI on Netvista 6286 totally unreachable, or did I miss something?

Here's a list of things I tried:
[LIST]
[*]hwclock.sh fix
[*]disabled wakeup from BIOS
[*]recompiled the DSDT (can't believe how many buggy BIOSes  there are regarding DSDT ACPI compliance)
[*]reboot, the shutdown after POST
[/LIST]

Slaínte,
--
Köntzä

---

### Post by bmwman on 2008-09-04
Well, I've been trying to set this thing up for 3 days now It still doesn't work. I'm using Mythwelcome and I followed all the instructions. My PC turn on fine after the test with the 5min, also it shuts down when it's idle. The thing is that it never comes back on for recording. I see the alarm has been set, although I think it's incorrect.
ex. I had a recording scheduled for 10pm and the machine didn't turn on. I turned it on manually I checked the alarm -
```
backend@backend:~$ cat /proc/acpi/alarm
2008-00-00 01:06:24
```It didn't set the date and why is the time 1:06:24 when it should be set for 10pm, i guess that should be 23:00:00 or something. Right before that I did the other test which stops the Backend instead of shut down it did set the date on the alarm. All I changed was the shutdown command.

Here is my other test:
CODE]2008-09-04 22:13:18.240 Using protocol version 40
2008-09-04 22:13:18.913 mythshutdown --startup returned: 1
2008-09-04 22:15:13.201 MythWelcome received a SHUTDOWN_NOW event
2008-09-04 22:15:14.261 Event socket closed. No connection to the backend.[/CODE]

Then ```
backend@backend:~$ cat /proc/acpi/alarm
2008-00-00 01:06:24
``` it's still the same. 

Please help me figure this one out, it's driving me nuts.

---

### Post by bmwman on 2008-09-06
I still can't get this to work. I keep getting this error ```
2008-09-06 10:01:48.308 Running the command to set the next scheduled wakeup time :-
						mythshutdown --setwakeup 2008-09-06 10:25:00
Invalid argument: 10:25:00
```

It seems like the script doesn't convert the time or something. 

please help.

---

### Post by Neon Dusk on 2008-09-06
I think I had the same problem. To fix it put $time in quotes

---

### Post by bmwman on 2008-09-06
> **Neon Dusk said:**
> I think I had the same problem. To fix it put $time in quotes

Do i have to do that in every place in the settings or in script someplace? I use Mythwelcome.

---

### Post by Neon Dusk on 2008-09-06
Think you just need it where you call mythshutdown --setwakeup $time.

So in the backend general config I've got
Command to set Wakeup time: sudo /usr/bin/mythshutdown --setwakeup "$time"

---

### Post by bmwman on 2008-09-06
It seems like sometimes it works and sometimes it doesn't. When i first put the quotes it changed the time but I had the commands to stop the backend instead of shutdown. Then I went back and put Command to shutdown: sudo -H shutdown -h -P now and it didn't work.

BTW I think something is not right with the time format, I get 
```
backend@backend:~$ cat /proc/acpi/alarm
2008-00-00 18:03:58
```

It doesn't set the date properly

---

### Post by bmwman on 2008-09-06
This absolutely doesn't make sense to me. Here're my settings
Backend: ```
**Wakeup time format:**: yyyy-MM-ddThh:mm:ss
**Set wakeuptime Command:** sudo mythshutdown --setwakeup "$time"
**Server halt Command:** sudo -H mythshutdown --shutdown
**Pre Shutdown check-command:** mythshutdown --check
```
Mythwelcome: ```
**nvram-wakeup Command: **/usr/bin/MythWakeSet $time
**nvram-wakeup Restart Command:**
**Command to reboot:** sudo -H shutdown -h -r now
**Command to shutdown:** sudo -H shutdown -h -P now
```

For testing i put **Command to shutdown:** > sudo /etc/init.d/mythtv-backend stop in Mythwelcome and I have a recordind scheduled at 4:30pm - an hour ahead.
The results:
```
backend@backend:~$ cat /proc/acpi/alarm
2008-09-06 19:43:41
```
Looks perfect, right? It sets the date and time correctly.

BUT!!! When I put > **Command to shutdown:** sudo -H shutdown -h -P now in Mythwelcome instead of > sudo /etc/init.d/mythtv-backend stop the machine shuts off and never comes back on. Of coarse I've tried that hundred times I know it won't turn back on so turn it on manually and check the alarm:
```
backend@backend:~$ cat /proc/acpi/alarm
2008-00-00 19:54:52
```

WTF!! I spent days  and it keeps doing it. It works fine for the test but when it acutally shut down, it doesn't set the alarm time properly. 

Please help me fix this!

---

### Post by majoridiot on 2008-09-06
> **bmwman said:**
> This absolutely doesn't make sense to me. Here're my settings
Backend: ```
**Wakeup time format:**: yyyy-MM-ddThh:mm:ss
**Set wakeuptime Command:** sudo mythshutdown --setwakeup "$time"
**Server halt Command:** sudo -H mythshutdown --shutdown
**Pre Shutdown check-command:** mythshutdown --check
```
Mythwelcome: ```
**nvram-wakeup Command: **/usr/bin/MythWakeSet $time
**nvram-wakeup Restart Command:**
**Command to reboot:** sudo -H shutdown -h -r now
**Command to shutdown:** sudo -H shutdown -h -P now
```

For testing i put **Command to shutdown:**  in Mythwelcome and I have a recordind scheduled at 4:30pm - an hour ahead.
The results:
```
backend@backend:~$ cat /proc/acpi/alarm
2008-09-06 19:43:41
```
Looks perfect, right? It sets the date and time correctly.

BUT!!! When I put  in Mythwelcome instead of  the machine shuts off and never comes back on. Of coarse I've tried that hundred times I know it won't turn back on so turn it on manually and check the alarm:
```
backend@backend:~$ cat /proc/acpi/alarm
2008-00-00 19:54:52
```

WTF!! I spent days  and it keeps doing it. It works fine for the test but when it acutally shut down, it doesn't set the alarm time properly. 

Please help me fix this!

is your motherboard listed as "working" in the list at the beginning of that wiki?

if not, you may need to use the "poweroff kernel" option, for the time to be
correctly written to your clock.  this looks to me to be the suspect, since it is
written fine when tested, but does survive the reboot or power off.

---

### Post by bmwman on 2008-09-06
My mobo is GIGABYTE GA-73PVM-S2H. It's not that list but it worked fine with this test ```
$ sudo sh -c 'echo "+00-00-00 00:05:00" > /proc/acpi/alarm'
``` It came back on after 5 min after I shut it off. So it's supposed to work, right? And why is the alarm not written properly when I use the backend stop sommand and not when i use the actual shutdown? Isn't that the same thing?

---

### Post by majoridiot on 2008-09-06
> **bmwman said:**
> My mobo is GIGABYTE GA-73PVM-S2H. It's not that list but it worked fine with this test ```
$ sudo sh -c 'echo "+00-00-00 00:05:00" > /proc/acpi/alarm'
``` It came back on after 5 min after I shut it off. So it's supposed to work, right? And why is the alarm not written properly when I use the backend stop sommand and not when i use the actual shutdown? Isn't that the same thing?

no poweroff kernel needed if that test works ok.

i don't use mythwelcome, but it looks to me like you have an errant sudo problem...

i'd try it again after changing mythbackend setup from:

```
**Set wakeuptime Command:** sudo mythshutdown --setwakeup "$time"
```

to:

```
**Set wakeuptime Command:** mythshutdown --setwakeup $time
```

---

### Post by bmwman on 2008-09-06
Same thing. I changed it to ```
Set wakeuptime Command: mythshutdown --setwakeup $time
``` and did the test with backend stop command - works fine and the alarm its set properly. When i changed it back to shutdown and manually tuned on to check the alarm - it doesnt have the date set again ```
backend@backend:~$ cat /proc/acpi/alarm
2008-00-00 20:54:47
```

BTW is it gonna make any difference if i put it to Stanby or Hibernate for > Command to shutdown: sudo -H shutdown -h -P now and if so what's the commands for that? I'm so frustrated and I'm willing to try anything. Thanks for your help.

---

### Post by majoridiot on 2008-09-06
> **bmwman said:**
> Same thing. I changed it to ```
Set wakeuptime Command: mythshutdown --setwakeup $time
``` and did the test with backend stop command - works fine and the alarm its set properly. When i changed it back to shutdown and manually tuned on to check the alarm - it doesnt have the date set again ```
backend@backend:~$ cat /proc/acpi/alarm
2008-00-00 20:54:47
```

my error... sudo privs were no prob.

from the wiki (emphasis added):

"**NOTE:** The command mythshutdown --setwakeup $time does not write to the /proc/acpi/alarm. It just sets the wakeup time in mythwelcome. The command mythshutdown --shutdown actually writes the time set by the call of mythshutdown --setwakeup to the RTC in the motherboard and should be used for the Server halt Command option. ***If this was sudo shutdown -h -P now, MythBackend will shutdown the machine properly, but it wont wake up to record for the next scheduled recording as the wakeup time is never set to the RTC of the motherboard.***"

---

### Post by bmwman on 2008-09-06
Well with sudo or without it does the same thing. Do you think the machine shuts down too fast before it had a chance to write the whole thing? And can I put it to Stand by insted or it doesn't matter?

P.S. I tried putting the ```
sudo mythshutdown --shutdown
```in the Mythwelcome instead and it did set the alarm but the computer doesn't turn off. The countdown went to 10sec and stopped.

---

### Post by db260179 on 2008-09-07
Hopefully my configs will help you? - the wiki doesnt work properly. What is happening is when the machine shutsdown it is not setting the time properly in the bios, thus the machine never wakes up.

Here is my config files and a screenshot in mythtv-setup

Ive changed the hwclock.sh, slightly - ive set it to cat to a text file the mythtv user home folder, instead of the bios. I found this to be more reliable. In the mythtv-setup some commands i havent used as it doesnt set the time properly!.

People with flaky boards should turn off all wakeup events in the bios as it conflicts.

Also as a side note, ive done loads of testing and found kernel 2.6.24-16 to be the most stable kernel.

---

### Post by bmwman on 2008-09-07
> **db260179 said:**
> Hopefully my configs will help you? - the wiki doesnt work properly. What is happening is when the machine shutsdown it is not setting the time properly in the bios, thus the machine never wakes up.

Here is my config files and a screenshot in mythtv-setup

Ive changed the hwclock.sh, slightly - ive set it to cat to a text file the mythtv user home folder, instead of the bios. I found this to be more reliable. In the mythtv-setup some commands i havent used as it doesnt set the time properly!.

People with flaky boards should turn off all wakeup events in the bios as it conflicts.

Also as a side note, ive done loads of testing and found kernel 2.6.24-16 to be the most stable kernel.

That didn't work for me either ](*,)	](*,)

Btw my kernel is  2.6.24-19-generic. This is what I found someplace   >   *  Kernel > 2.6.22 and higher use /sys/class/rtc/rtc0/wakealarm
    * Kernel < 2.6.21 and lower use /proc/acpi/alarm 

but I don't have such a thing as /sys/class/rtc/rtc0/wakealarm

Another thing i discovered :```
backend@backend:~$ sudo echo "2008-12-29 10:10:04" >/proc/acpi/alarm
bash: /proc/acpi/alarm: Permission denied
```

Why I'm not able to change it with sudo?

---

### Post by bmwman on 2008-09-08
Well, final conclusion is that everything works until the computer shuts down. I have disabled all Wake On events in the BIOS and the MythWakeSet script do set the alarm properly in /etc/acpi/alarm. I think when the computer shuts down and the hwclock.sh is executed, that's what screws up everything else. It does keep the time, but not the date. So If anyone can figure out what needs to be changed? Or can the hwclock.sh be disabed so it doesn't sync the clock at all?

---

### Post by db260179 on 2008-09-08
Send your /var/log/mythtv/*

Here please, gives me an idea of whats going on.

> **bmwman said:**
> Well, final conclusion is that everything works until the computer shuts down. I have disabled all Wake On events in the BIOS and the MythWakeSet script do set the alarm properly in /etc/acpi/alarm. I think when the computer shuts down and the hwclock.sh is executed, that's what screws up everything else. It does keep the time, but not the date. So If anyone can figure out what needs to be changed? Or can the hwclock.sh be disabed so it doesn't sync the clock at all?

---

### Post by bmwman on 2008-09-08
Will do later. I'm at work right now. I don't understand what the > sudo mythshutdown --shutdown is supposed to do. Whatever it does, at the end executes the command for shut down in Mythwelcome. If there is nothing in there the machine doesn't shut off or do anything.

---

### Post by Andrew U.K. on 2008-09-08
Hi,
I'm following with great intrest as I have the same problem. 

I have stopped mucking about with it, changing settings and reloading mythbuntu, thinking a fresh install will help.

I will now be paitent and await the outcome.

Thanks 

Andrew

---

### Post by bmwman on 2008-09-08
> **db260179 said:**
> Send your /var/log/mythtv/*

Here please, gives me an idea of whats going on.
Here is the log folder. My last settings are :
> 
Mythwelcome setup:

nvram-wakeup Command: sudo /usr/bin/MythWakeSet
nvram-wakeup Restart Command: LEAVE BLANK
Command to reboot: sudo shutdown -h -r now
Command to shutdown: sudo /sbin/poweroff

Shutdown/Wakeup Options:

Wakeup time format: yyyy-MM-ddThh:mm
Set wakeuptime Command: sudo mythshutdown --setwakeup $time
Server halt Command: sudo mythshutdown --shutdown
mythalarm-command: BLANK for the time being

And for now I was trying some German MythWakeSet script which works for lot of people but not me again.

> This is the MythWakeSet script I used (from German mythwelcome wiki):

Code:

#!/usr/bin/perl
#
# This script is invoked by mythshutdown to set the wakeup time.
# mythshutdown thinks it's calling nvram-wakeup, and it passes
# "--settime" and a single integer on the command line, which is the
# startup UTC time in seconds since the epoch. We convert it to the form
# understood by the system wakeup script.
#
($sec, $min, $hour, $mday, $mon, $year, $wday, $yday, $isdst) =
gmtime ($ARGV[1]);
$year += 1900;
$mon += 1;
$wakeup_time = sprintf "%4.4u-%2.2u-%2.2u %2.2u:%2.2u:%2.2u", $year,
$mon, $mday, $hour, $min, $sec;
`echo "$wakeup_time" >/proc/acpi/alarm`;

---

### Post by db260179 on 2008-09-08
Please look at my attachment, LOOK at the screenshot carefully! - and copy my settings!

From your logs, you have a lot of errors

2008-09-08 16:31:32.233 Running the command to set the next scheduled wakeup time :-
			sudo mythshutdown --setwakeup 2008-09-08T16:55:00
                                                                ^this is wrong!

2008-09-08 16:31:32.393 Running the command to shutdown this computer :-
						sudo mythshutdown --shutdown
2008-09-08 16:31:34.616 I'm idle now... shutdown will occur in 60 seconds.

The options set in the wiki DONT work!, copy my settings exactly! (in the attachment of my first post) - If you dont it will never work! - my system works fine with my settings.

---

### Post by bmwman on 2008-09-08
Well, with your scripts and settings nothing happens, even the machine doesn't turn off. It keeps cycling from 60sec down and again and again. Here're the new logs. BTW what settings should I put in Mythwelcome, left it blank right now??

P.S. I take that back. It did shut off eventually. I'll find out soon if it comes back on again in 10 min.

---

### Post by bmwman on 2008-09-08
OK here is the latest output:
> 2008-09-08 18:36:50.499 adding: backend as a client (events: 1)
2008-09-08 18:37:30.380 CheckShutdownServer returned - OK to shutdown
2008-09-08 18:37:30.384 Running the command to set the next scheduled wakeup time :-
						sudo /usr/bin/MythtvWakeSet 2008-09-08 18:54:46
2008-09-08 18:37:30.444 Running the command to shutdown this computer :-
						sudo mythshutdown --shutdown

I had a recording set for 7pm and it seems like the alarm was set properly > backend@backend:~$ cat /proc/acpi/alarm
2008-09-08 18:54:46 But the machine didn't come on at  18:54:46. At least it survived reboot :). I feel like getting closer to figure this out.

---

### Post by bmwman on 2008-09-09
Thank you so much or all the help so far. At least now the alarm is being set in the /etc/acpi/alarm and I can see it even after manual reboot. I tested it many times and every time it's stored fine. The computer doesn't turn on on though. I'm not sure what the problem is but it does work if I do the 5 min test > $ sudo sh -c 'echo "+00-00-00 00:05:00" > /proc/acpi/alarm'. I think it might be that the time is being set as a local time and not the UTC. I'm not sure how to tell what my mobo requires UTC or local. For example if i have a recording at 7pm the alarm is stored as 2008-09-08 18:54:46, 5 min before start which is my setting. Isn't that supposed to be 4 hours ahead in UTC or something like that?

---

### Post by Andrew U.K. on 2008-09-09
[QUOTE

The options set in the wiki DONT work!, copy my settings exactly! (in the attachment of my first post) - If you dont it will never work! - my system works fine with my settings.[/QUOTE]

Hi, 
So what happens, does the wiki get changed or amended?

Andrew

---

### Post by bmwman on 2008-09-09
I got mine to set the alarm properly in /etc/acpi/alarm with db260179's scripts and instructions. This is still not 100% working because the time needs to be in UTC I think or whatever else reason.

---

### Post by Andrew U.K. on 2008-09-09
I'm completely new to linux how do I open his scripts?
I unzip them and then what do I use to read them?

Cheers
Andrew

---

### Post by majoridiot on 2008-09-09
> **bmwman said:**
> I got mine to set the alarm properly in /etc/acpi/alarm with db260179's scripts and instructions. This is still not 100% working because the time needs to be in UTC I think or whatever else reason.

this is due entirely to modifications made to the MythWakeSet... all of the time adjustments are commented out.

if you want UTC, which is the way the *original* pre-mythwelcome wiki was written, then this is it:

**MythWakeSet**
```
#!/bin/bash
#
# MythtvWakeSet
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

# adjust this to UTC and store the final wake time
utcadj=$(/bin/date -u -f $temp_stamp +%F\ %T)

# set the alarm
echo $utcadj > /proc/acpi/alarm
```

either replace your current MythWakeSet with this one, or simply cross-check to uncomment the time adjustments that were commented out.

also note the change to the last echo, which replaces a cat to set the time.

if you replace it entirely, do not forget to make it executable with chmod +x and sudo copy it to /usr/bin/

---

### Post by bmwman on 2008-09-09
I did that but it's still giving the local time. Currently I have MythtvWakeSet and MythWakeSet which is the one from the previous post and the one from the Wiki. I tried both and still getting the local time. Can you please look the HWclock.sh in the previous post and see if there is something in there that makes the local time? I looked thru it but I don't really understand code too much. Also how can I tell if my mobo is in UTC or local time? BTW its GIGABYTE GA-73PVM-S2H.

Thanks much.

---

### Post by majoridiot on 2008-09-09
> **bmwman said:**
> I did that but it's still giving the local time. Currently I have MythtvWakeSet and MythWakeSet which is the one from the previous post and the one from the Wiki. I tried both and still getting the local time. Can you please look the HWclock.sh in the previous post and see if there is something in there that makes the local time? I looked thru it but I don't really understand code too much. Also how can I tell if my mobo is in UTC or local time? BTW its GIGABYTE GA-73PVM-S2H.

Thanks much.

knowing whether or not your clock is utc would kinda help, man...

go into bios setup on boot and look at the time the clock says.  if it is ahead of your actual time (probably 4 hours or so)
then, yeah... it's utc.  if it is set to the actual time, then it's not utc.

you are running yourself in circles and confusing things with too many versions of scripts.  to get to the bottom of this
as quickly as possible, post the following info so everyone is on the same page:

is your mobo clock utc or not

*all* of your current wake settings for mythtv-setup and mythwelcome

*all* of the associated scripts as they now exist, including your hwclock.sh, mythwakeset, mythtvwakeset and whatever else that is relevant

a copy of your visudo, to check privileges

having all of this info in one post will go a long way to resolving this more quickly, without everyone having to search through all of your posts.

---

### Post by bmwman on 2008-09-09
OK. I checked the BIOS and it's in UTC, it's 4 hours ahead. This is my MythWakeSet script > #!/bin/bash
# MythtvWakeSet
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

# adjust this to UTC and store the final wake time
utcadj=$(/bin/date -u -f $temp_stamp +%F\ %T)

# set the alarm
echo $utcadj > /proc/acpi/alarm

It's supposed to convert the time to UTC, right? Well, it doesn't. I have a recording set for 8:00pm and the alarm is set for 2008-09-09 19:54:46. 
I'll attach the other scripts as well. Isn't it easier to just change the BIOS to local time? I'm sure it's not as simple as just changing the time but that would solve all my problems.

sudoers:
> %mythtv ALL = NOPASSWD: /sbin/shutdown, /usr/bin/MythtvWakeSet, /proc/acpi/alarm, /usr/bin/MythtvShutdownCheck, /etc/init.d/mythtv-backend, /usr/share/mythtv/myth-halt.sh, /usr/bin/mythshutdown, /usr/bin/MythWakeSet, /usr/bin/MythShutdownCheck

Backend settings
> Wakeup time format:: yyyy-MM-dd hh:mm:ss
Set wakeuptime Command: sudo /usr/bin/MythWakeSet $time
Server halt Command: sudo -H mythshutdown --shutdown
Pre Shutdown check-command: mythshutdown --check

Mythwelcome
> nvram-wakeup Command: blank
nvram-wakeup Restart Command: blank
Command to reboot: sudo /sbin/poweroff
Command to shutdown: sudo /sbin/poweroff

---

### Post by db260179 on 2008-09-10
REMEMBER - The machine will not wakeup if you set a recording to turn the machine on with less than an 1 hour before the program starts! - Its just the way mythtv works!

Your start time seems correct? - 5mins before recording?

the Mythtvwakeset is settng the correct time!

> **bmwman said:**
> OK. I checked the BIOS and it's in UTC, it's 4 hours ahead. This is my MythWakeSet script 

It's supposed to convert the time to UTC, right? Well, it doesn't. I have a recording set for 8:00pm and the alarm is set for 2008-09-09 19:54:46. 
I'll attach the other scripts as well. Isn't it easier to just change the BIOS to local time? I'm sure it's not as simple as just changing the time but that would solve all my problems.

Mythwelcome

You need to add the mythtvwakeset to mythwelcome as follows

Mythwelcome

nvram-wakeup Command: sudo /usr/bin/MythWakeSet $time
nvram-wakeup Restart Command: sudo /usr/share/mythtv/myth-reboot.sh
Command to reboot: sudo /usr/share/mythtv/myth-reboot.sh
Command to shutdown: sudo /usr/share/mythtv/myth-halt.sh

---

### Post by bmwman on 2008-09-10
> **db260179 said:**
> REMEMBER - The machine will not wakeup if you set a recording to turn the machine on with less than an 1 hour before the program starts! - Its just the way mythtv works!

Your start time seems correct? - 5mins before recording?

the Mythtvwakeset is settng the correct time!



You need to add the mythtvwakeset to mythwelcome as follows

Mythwelcome

nvram-wakeup Command: sudo /usr/bin/MythWakeSet $time
nvram-wakeup Restart Command: sudo /usr/share/mythtv/myth-reboot.sh
Command to reboot: sudo /usr/share/mythtv/myth-reboot.sh
Command to shutdown: sudo /usr/share/mythtv/myth-halt.sh

I got it work last night even withouth the Mythwelcome. It was shutting down properly and the only difference i noticed was that if i Lock the shutdown in Mythwelcome, the backend will shut off anyway. I had to change my system time from UTC to local which is not a big deal.Just had to edit one configuration file and switched in the BIOS after the next reboot. BTW do I put nvram-wakeup Command: sudo /usr/bin/MythWakeSet $time as well as Server halt command in the backend? Twice? I will def give it try.

Anyway, I'm a happy  camper now :) Thank you so much.

P.S.>  REMEMBER - The machine will not wakeup if you set a recording to turn the machine on with less than an 1 hour before the program starts! - Its just the way mythtv works! I have mine set to turn on 5 min before recording it still works. I will change it to at least 15min but for the purpose of testing i had it on 5. Also the machine will not turn off if there is a recording in the next 15min. I also love your shutdown Check script. I need to edit it to check if Amarok,Azureus or a Terminal is running, instead of Firefox.

---

### Post by db260179 on 2008-09-10
Good to hear its working!

No harm in putting in the commands.

In the next 1 hour it wont shut off, i've tried.

Yeh the wiki script was a bit useless, so i added my own commands that i commonly use.

> **bmwman said:**
> I got it work last night even withouth the Mythwelcome. It was shutting down properly and the only difference i noticed was that if i Lock the shutdown in Mythwelcome, the backend will shut off anyway. I had to change my system time from UTC to local which is not a big deal.Just had to edit one configuration file and switched in the BIOS after the next reboot. BTW do I put nvram-wakeup Command: sudo /usr/bin/MythWakeSet $time as well as Server halt command in the backend? Twice? I will def give it try.

Anyway, I'm a happy  camper now :) Thank you so much.

P.S. I have mine set to turn on 5 min before recording it still works. I will change it to at least 15min but for the purpose of testing i had it on 5. Also the machine will not turn off if there is a recording in the next 15min. I also love your shutdown Check script. I need to edit it to check if Amarok,Azureus or a Terminal is running, instead of Firefox.

---

### Post by majoridiot on 2008-09-10
> **db260179 said:**
> Yeh the wiki script was a bit useless, so i added my own commands that i commonly use.

if the mythwelcome information in the wiki is inaccurate and/or the scripts "useless", you should feel free
to log in, make the changes so the information is correct and then that section of the wiki will be *useful* to
others.

that's the interesting thing about wikis... when people take the time to update them to keep them accurate, then they serve their *purpose*. ;)

since i do not use mythwelcome, all i am able to verify and maintain is the core of that wiki.  help with keeping the mythwelcome section accurate is not only welcomed, but also *encouraged*.

---

### Post by bmwman on 2008-09-10
majoridiot and db260179, You're both great since spending the time in trying to help people like me. I did had it "semi-working" with wiki guide but the time is not being written properly in hwclock. I don't understand code so I'm not sure what's the difference in the one in the wiki and the one from db260179. Maybe it just doesn't work with the newer boards and works with older ones.
I would definetly spend time and consolidate all the instructions and scripts that worked for me (basically the ones from db260179) and add instructions how to change the time to Local instead of UTC. I'm not a Linux guru but I know most newbies out there need a detailed step by step guide.

---

### Post by Andrew U.K. on 2008-09-10
> **bmwman said:**
> 
I would definetly spend time and consolidate all the instructions and scripts that worked for me (basically the ones from db260179) and add instructions how to change the time to Local instead of UTC. I'm not a Linux guru but I know most newbies out there need a detailed step by step guide.

I would like to thank you both as well. As a newbie it is very daunting seeing all these scripts and things. The step by step guide worked for me also apart from the very end.

I haven't started re-doing the acpi, but I will tomorrow. Now how do I change the time to local from UTC.

Andrew

p.s. you don't get anything to open zip files with mythbuntu so you need to download something to open them. Again as a newbie this causes problems.

---

### Post by bmwman on 2008-09-10
To switch to Local time open a Terminal and type:
```
sudo gedit /etc/default/rcS
```
The file looks like this:
> #
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
UTC=yes
VERBOSE=no
FSCKFIX=no
Just change the line UTC=yes to UTC=no. This should be enough. Just optional you can type this to force immediately:
```
sudo /sbin/hwclock --systohc --localtime
```
And then check to make sure it looks right:
```
sudo /sbin/hwclock --localtime
```

As far as ZIP files, you can install file-roller which handles most types of archives.
In a terminal type:
```
sudo apt-get install file-roller
```
Then to start it in case it doesn't show up as icon simply type "file-roller" in a terminal

---

### Post by Andrew U.K. on 2008-09-10
Thanks for that.
I'm glad you got it all sorted.

Andrew

---

### Post by Lester_Burnham on 2008-09-11
Hi guys,

I'm following this thread also, with interest.
I'm having trouble with mythwelcome receiving a SCHEDULE_CHANGE event which resets the counter for shutdown (I found it easier to troubleshoot what is going on, by running mythwelcome from a terminal). It seems, I need to have it set around 300 secs. I am using EIT guide if that makes a difference.

Any ideas please.

Thanks,
Lester

---

### Post by db260179 on 2008-09-11
No problem. hwclock problem is due to the mythshutdown program not setting time as it shutsdown. As a workaround, i've told it to set the time to a text file in mythtv users home directory. Then it can be cat to /proc/acpi/alarm.

The UTC change is useful. Thanks

> **bmwman said:**
> majoridiot and db260179, You're both great since spending the time in trying to help people like me. I did had it "semi-working" with wiki guide but the time is not being written properly in hwclock. I don't understand code so I'm not sure what's the difference in the one in the wiki and the one from db260179. Maybe it just doesn't work with the newer boards and works with older ones.
I would definetly spend time and consolidate all the instructions and scripts that worked for me (basically the ones from db260179) and add instructions how to change the time to Local instead of UTC. I'm not a Linux guru but I know most newbies out there need a detailed step by step guide.

---

### Post by db260179 on 2008-09-11
Becuase you are using EIT, you need to set the time in the backend, so that it doesn't conflict with the shutdown process.

The default time is 5min i believe. You have set it too 300secs (5mins), which might conflict. Set it to 4mins (245secs)

> **Lester_Burnham said:**
> Hi guys,

I'm following this thread also, with interest.
I'm having trouble with mythwelcome receiving a SCHEDULE_CHANGE event which resets the counter for shutdown (I found it easier to troubleshoot what is going on, by running mythwelcome from a terminal). It seems, I need to have it set around 300 secs. I am using EIT guide if that makes a difference.

Any ideas please.

Thanks,
Lester

---

### Post by bmwman on 2008-09-11
One thing that I've noticed though: Even if I Lock the shutdown from Mythwelcome, if there is nothing else going on, the backend will still shut down the system. It's not that big of a deal but it gets kinda of annoying sometimes.

---

### Post by Andrew U.K. on 2008-09-12
Hi,

I've restarted configuring the acpi wake up after a fresh install of mythbuntu. 

I have used db260179 files and settings (thanks) but I think I have fallen at the first hurdle.

I am following the acpi/whatnext/comunitydocs. When I test the first part (after changiing the hwclock.sh) where you add 5 min to the rtc, turn off and then wait for it to boot up, nothing happens. It works O.K. with the original adaptation to the hwclock.sh. 

Should I be bothering with the tests? Or just follow your files and settings db260179? I'm running frontend and backend on the same computer so I trust I need to run mythwelcome. 

Thanks
Andrew

---

### Post by Neon Dusk on 2008-09-12
> **bmwman said:**
> One thing that I've noticed though: Even if I Lock the shutdown from Mythwelcome, if there is nothing else going on, the backend will still shut down the system. It's not that big of a deal but it gets kinda of annoying sometimes.

It shouldn't - are you checking the result of 'mythshutdown --check' in your MythShutdownCheck script?

---

### Post by spoky99 on 2008-09-12
[I][COLOR="Blue"][QUOTE=bmwman;5740023]Same thing. I changed it to ```
[COLOR="Blue"]Set wakeuptime Command: mythshutdown --setwakeup $time[/COLOR]
``` and did the test with backend stop command - works fine and the alarm its set properly. When i changed it back to shutdown and manually tuned on to check the alarm - it doesnt have the date set again ```
[COLOR="Blue"]backend@backend:~$ cat /proc/acpi/alarm
2008-00-00 20:54:47[/COLOR]
```[/COLOR][/I]
I had the same problem
Using "sudo sh -c 'echo "+00-00-00 00:05:00" > /proc/acpi/alarm'" and shutting down the computer it wake-up themself. But if I write a date into the /proc/acpi/alarm and using cat /proc/acpi/alarm the day and month date is correctly set, but if I shutdown and restart the computer the day date is set to 00.
example
[I]$ date
ven set 12 15:18:33 CEST 2008
$ sudo sh -c 'echo "2008-09-14 10:00:00" > /proc/acpi/alarm'
sudo cat /proc/acpi/alarm 
2008-09-[COLOR="Indigo"]14[/COLOR] 10:00:00
$ sudo reboot
...[/I]

after the reboot

[I]$ sudo cat /proc/acpi/alarm  
2008-09-[COLOR="Red"]00[/COLOR] 10:00:00[/I]

And if I try to set the month don't write it
example:

[I]$ sudo sh -c 'echo "2008-[COLOR="Indigo"]10[/COLOR]-14 10:00:00" > /proc/acpi/alarm'
$ sudo cat /proc/acpi/alarm 
2008-[COLOR="Red"]09[/COLOR]-14 10:00:00[/I]

I search with google how to solve this problem.. but I don't found nothing (or bad english don't make me see the answers)

---

### Post by bmwman on 2008-09-12
Well I see there is a lot of interest about this subject so I'm going to consolidate all the instructions into one.

Step 1: Change your time to local if it's in UTC:

To switch to Local time open a Terminal and type:
```
sudo gedit /etc/default/rcS
```
The file looks like this:
> #
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
UTC=yes
VERBOSE=no
FSCKFIX=no
Just change the line UTC=yes to UTC=no. This should be enough. Just optional you can type this to force immediately:
```
sudo /sbin/hwclock --systohc --localtime
```
And then check to make sure it looks right:
```
sudo /sbin/hwclock --localtime
```

Step2: Provide MythTV user with the needed permissions:
In a Terminal type: ```
export EDITOR=gedit && sudo -E visudo
```

and then add this at the end of the file:
> #Enter the below line, below the %admin line in etc/sudoers

%mythtv ALL = NOPASSWD: /sbin/shutdown, /usr/bin/MythtvWakeSet, /proc/acpi/alarm, /usr/bin/MythtvShutdownCheck, /etc/init.d/mythtv-backend, /usr/share/mythtv/myth-halt.sh, /usr/bin/mythshutdown


Step 3: Copy the attached scripts in their folders accordingly. Might be easier for newbies to open Thunar with "root" permissions and just copy the files easier.
In a Terminal type:
[HTML]sudo Thunar[/HTML]

Step 4: After you copy all the scripts (hwclock.sh, MythtvWakeSet and MythtvShutdownCheck you need put the settings in the backend and Mythwelcome. There is a screenshot of the backend settings attached.

Backend settings:
> **Wakeup time format:** yyyy-MM-dd hh:mm:ss
**Set wakeuptime Command:** sudo /usr/bin/MythtvWakeSet $time (Not sure if this needs to be here since Mythwelcome would set the alarm but it works)
**Server halt Command:** sudo -H mythshutdown --shutdown
**Pre Shutdown check-command:** sudo /usr/bin/MythtvShutdownCheck 

Mythwelcome settings: Pres F11 to bring the settings screen

> **nvram-wakeup Command:** sudo /usr/bin/MythtvWakeSet $time
**nvram-wakeup Restart Command:** sudo /usr/share/mythtv/myth-reboot.sh
**Command to reboot:** sudo /usr/share/mythtv/myth-reboot.sh
**Command to shutdown: **sudo /usr/share/mythtv/myth-halt.sh

I can take credit for the testing and the typing :) The scripts and the other instructions were taken from multiple places but mostly **"db260179"**
Please post if there are any issues so I can adjust the settings.

Good luck! ;)

---

### Post by Andrew U.K. on 2008-09-12
Cheers bmwman, much apreciated.

I will hopefully do this tonight.
 
So I shouldn't worry about doing the tests then?

Andrew

---

### Post by bmwman on 2008-09-12
You can just follow all the steps and it should work. Reboot after you complete everything and then schedule a recording in 1 hours or so later and see what happens. Make sure you don't have Firefox or anything else open because the shutdown script will prevent it. Hope it works for you, if it doesn't then you need to do some troubleshooting.

---

### Post by Andrew U.K. on 2008-09-12
Thanks, will do.

---

### Post by Andrew U.K. on 2008-09-12
Managed to get the changes done before kids got home, myth welcome won't shut down on its own.The clock just resets itself. Any ideas? I have a wireless internet connection does that affect the MythShutdownCheck?

I am now waiting, with a cautious hope for it to start up in about an hour. I'm crossing everthing.

Andrew

---

### Post by Neon Dusk on 2008-09-12
@bmwman

From testing myself I've come up with the following :-

If using MythWelcome then for proper behaviour you need to use mythshutdown --setwakeup instead of MythWakeSet (otherwise when the machine starts from an acpi wake the frontend will start which can then stop the machine shutting back down).

However it seems that mythshutdown --setwakeup need the $time variable enclosed in quotes as it doesn't like the space between the date and time.

So the differences in my config is:-

_Backend Setup_
Command to Set Wakeup time: sudo /usr/bin/mythshutdown --setwakeup "$time"

_MythShutdown/MythWelcome Settings (Press F11 on the MythWelcome screen to access)_
Command to Set Wakeup time: sudo /usr/bin/MythWakeSet $time
Wakeup time format: yyyy-MM-dd hh:mm:ss

Command to shutdown: sudo shutdown -h -P now


I also check the return value from mythshutdown --check in my MythShutdownCheck script
```

#
# MythShutdownCheck
#
#
# returns "1" if yes, stopping shutdown
# returns "0" if ok to shutdown
#

if ps aux | grep uTorrent | grep -q -v grep
then	
	#don't allow shutdown 	
	exit 1
else	
	/usr/bin/mythshutdown --check
	exit $?
fi

```

Another potential problem is that if you're using the EIT guide then the EIT scanner will reset the idle count unles the 'Idle shutdown timeout (secs)' is set to less than 300 in the backend setup

---

### Post by bmwman on 2008-09-12
Sometimes if the backend it's doing something then Mythwelcome is just cycling. Are you using the same machine for backend/frontend? If so, I don't think your wireless has anything to do with it. Also the shutdown check script its checking for things so like I said make sure everything else is closed. Now your log files would be helpfull :)

> Managed to get the changes done before kids got home, myth welcome won't shut down on its own.The clock just resets itself. Any ideas? I have a wireless internet connection does that affect the MythShutdownCheck?

I am now waiting, with a cautious hope for it to start up in about an hour. I'm crossing everthing.

Andrew

---

### Post by bmwman on 2008-09-12
> Command to Set Wakeup time: sudo /usr/bin/mythshutdown --setwakeup "$time"

Totally makes sense. Mine still works because I currently have the Mythwelcome commands blank so the backend its doing all the work.I haven't really had a chance to mess with it. I'm leaving for vacation tomorrow and haven't even packed yet :)so I'll do more tweaking when I come back.

BTW you can disable the Frontend to start, period. I have done it, every time I reboot either manually or form ACPI wake up, the frontent doesn't start and I just have the Mythwelcome screen. You just hit "M" or the info button on your remote when you're at the Mythwelcome screen and uncheck the start Frontend option.

---

### Post by Andrew U.K. on 2008-09-12
Have a good trip. 
I'll recheck everything as it never worked. 
Andrew

---

### Post by bmwman on 2008-09-12
> **Andrew U.K. said:**
> Have a good trip. 
I'll recheck everything as it never worked. 
Andrew

Try this: delete nvram-wakeup Command and nvram-wakeup Restart Command from the Mythwelcome and leave it blank for now. Then in the backend do > nvram-wakeup Command: sudo /usr/bin/MythWakeSet $time
 and 
server halt command: sudo -H mythshutdown --shutdown. 

Exit the Mythwelcome completely. Open a Terminal and type ```
sudo killall mythbackend
sudo killall mythwelcome
``` Then type ```
sudo mythbackend &
```This way you can see what is the backend doing at all times in the terminal and if it's giving any errors.

---

### Post by Neon Dusk on 2008-09-12
@Andrew U.K.
What's your output from cat /proc/acpi/alarm ?

---

### Post by Neon Dusk on 2008-09-12
> **bmwman said:**
> 
BTW you can disable the Frontend to start, period. I have done it, every time I reboot either manually or form ACPI wake up, the frontent doesn't start and I just have the Mythwelcome screen. You just hit "M" or the info button on your remote when you're at the Mythwelcome screen and uncheck the start Frontend option.

That will work as well. However I think it makes sense to automatically start the frontend from a manual startup. I get the MythWelcome screen from an acpi wakeup and the frontend from a manual start.

---

### Post by db260179 on 2008-09-12
Mmm, i had this issue on an old board of mine - ECS KS7A, never got it to work!, so im afraid you board might be one that doesnt work!

> **spoky99 said:**
> [I][COLOR="Blue"][QUOTE=bmwman;5740023]Same thing. I changed it to ```
[COLOR="Blue"]Set wakeuptime Command: mythshutdown --setwakeup $time[/COLOR]
``` and did the test with backend stop command - works fine and the alarm its set properly. When i changed it back to shutdown and manually tuned on to check the alarm - it doesnt have the date set again ```
[COLOR="Blue"]backend@backend:~$ cat /proc/acpi/alarm
2008-00-00 20:54:47[/COLOR]
```[/COLOR][/I]
I had the same problem
Using "sudo sh -c 'echo "+00-00-00 00:05:00" > /proc/acpi/alarm'" and shutting down the computer it wake-up themself. But if I write a date into the /proc/acpi/alarm and using cat /proc/acpi/alarm the day and month date is correctly set, but if I shutdown and restart the computer the day date is set to 00.
example
[I]$ date
ven set 12 15:18:33 CEST 2008
$ sudo sh -c 'echo "2008-09-14 10:00:00" > /proc/acpi/alarm'
sudo cat /proc/acpi/alarm 
2008-09-[COLOR="Indigo"]14[/COLOR] 10:00:00
$ sudo reboot
...[/I]

after the reboot

[I]$ sudo cat /proc/acpi/alarm  
2008-09-[COLOR="Red"]00[/COLOR] 10:00:00[/I]

And if I try to set the month don't write it
example:

[I]$ sudo sh -c 'echo "2008-[COLOR="Indigo"]10[/COLOR]-14 10:00:00" > /proc/acpi/alarm'
$ sudo cat /proc/acpi/alarm 
2008-[COLOR="Red"]09[/COLOR]-14 10:00:00[/I]

I search with google how to solve this problem.. but I don't found nothing (or bad english don't make me see the answers)

---

### Post by bmwman on 2008-09-12
It should work. Mine was doing exactly the same thing but it finally worked. I believe it has to do with the hwclock.sh script. MythWakeSet from the wiki or yours was giving the time (correct or incorrect) but it would just not be there after reboot.

---

### Post by Andrew U.K. on 2008-09-13
Hi,

Here is my mythtv var/log. All of my files are as db260179 posted. I have now changed some of my settings after reading recent posts from bmwman and neon dusk but I can soon change them back.

My machine does not either wake up or shutdown but it has done in the past when I used the acpi/whatnext instructions, but then it would not wake with mythwelcome but it would shutdown.

My output from cat/proc/acpi/alarm seems to show the time when I last set a recording but not the time of the actual recording. 

If anybody could help I would be truly grateful. 
I´m still a beginner at linux but I think I could now follow any instructions.

Many thanks

Andrew

---

### Post by db260179 on 2008-09-13
Looking at you logs, here is a few  problems:

2008-09-13 06:39:25.449 I'm idle now... shutdown will occur in 60 seconds.
[sudo] password for mythtv: 

This means you havent set the /etc/sudoers correctly, look at my examples or bmwman

Follow all my examples and bmwman step-by-step

> **Andrew U.K. said:**
> Hi,

My machine does not either wake up or shutdown but it has done in the past when I used the acpi/whatnext instructions, but then it would not wake with mythwelcome but it would shutdown.

My output from cat/proc/acpi/alarm seems to show the time when I last set a recording but not the time of the actual recording. 

If anybody could help I would be truly grateful. 
I´m still a beginner at linux but I think I could now follow any instructions.

Many thanks

Andrew

---

### Post by Andrew U.K. on 2008-09-13
Will do,

 thanks.

---

### Post by Andrew U.K. on 2008-09-15
bad post sorry

---

### Post by Andrew U.K. on 2008-09-15
It shuts down...But it won´t wake up.
Below is my log.
Again, thanks for the help.
Andrew

2008-09-15 19:47:13.171 Scheduled 1 items in 0.1 = 0.01 match + 0.05 place
2008-09-15 19:47:14.173 I'm idle now... shutdown will occur in 60 seconds.
2008-09-15 19:48:13.280 Preshutdown
2008-09-15 19:48:13.645 CheckShutdownServer returned - OK to shutdown
2008-09-15 19:48:13.653 Running the command to set the next scheduled wakeup time :-
sudo /usr/bin/MythWakeSet 2008-09-15 20:28:10
[sudo] password for mythtv:
2008-09-15 19:48:15.690 Running the command to shutdown this computer :-
sudo -H mythshutdown --shutdown
method return sender=:1.5 -> dest=:1.28 reply_serial=2
int32 0
2008-09-15 19:48:17.668 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

---

### Post by Neon Dusk on 2008-09-16
> **Andrew U.K. said:**
> 
sudo /usr/bin/MythWakeSet 2008-09-15 20:28:10
[sudo] password for mythtv:


It still looks like your sudo permissions are not set-up. Did you edit the file using 'sudo visudo' ?

---

### Post by bmwman on 2008-09-16
Pay attention to details :P
Look at this line:> sudo /usr/bin/MythWakeSet 2008-09-15 20:28:10


It's supposed to be sudo /usr/bin/MythtvWakeSet 2008-09-15 20:28:10

Do you notice the difference? MythWakeSet and MythtvWakeSet is not the same thing :)

---

### Post by Andrew U.K. on 2008-09-18
Cheers bmwman,

Could I just check, should the mythwelcome setting be MythtvWakeSet as well? I haven't had a chance to look at it yet, but will tonight.
 
[I]Mythwelcome settings: Pres F11 to bring the settings screen

Quote:
nvram-wakeup Command: sudo /usr/bin/MythWakeSet $time
[/I]
One other thing, the rtc displays yyyy-MM-dd but when I look at the motherboard manual and clock it displays it as MM-dd-yy. Do I need to change any of the settings to the motherboard format or keep them as yours?

Thanks Andrew

---

### Post by bmwman on 2008-09-18
I would just try with only the backend doing all the work first and make sure it works. Then you should set up the Mythwelcome. Also try the different time formats and see which one works for you. I changed the typo that i had in the instructions, thanks for noticing that :)

Just for the test try these settings:
Backend settings:
> 
Wakeup time format: yyyy-MM-dd hh:mm:ss
Set wakeuptime Command: sudo /usr/bin/MythtvWakeSet $time
Server halt Command: sudo -H mythshutdown --shutdown
Pre Shutdown check-command: sudo /usr/bin/MythtvShutdownCheck
Mythwelcome settings: Pres F11 to bring the settings screen
> 
nvram-wakeup Command: leave blank
nvram-wakeup Restart Command: sudo /usr/share/mythtv/myth-reboot.sh
Command to reboot: sudo /usr/share/mythtv/myth-reboot.sh
Command to shutdown: sudo /usr/share/mythtv/myth-halt.sh

You can try changing the time format in the backend settings and see which one works for your motherboard but test the way it's in the instructions first.

---

### Post by Andrew U.K. on 2008-09-19
Hi bmwman I hope your not looking at this while on vacation.

Well I still seem to be having problems.

I´ve tried changing the date in the BE and then checking with cat /proc/acpi/alarm. All seems fine, I let mythwelcome shutdown then reboot and check, cat /proc/acpi/alarm and the correct time for the program to record is there. When I check the mobo clock in Bios it shows the local time again the same as the cat /proc/acpi/alarm. But it still won wake up.

I have checked the settings and folders and I pretty sure they are correct.

Do you still have the problem with mythwelcome not always being there on FE exit? I have that problem and wonder if I should disable it for the time being? If so any idea how I can stop it coming on?

Anyway my frustration goes on.

Here´s my log with the BE setting of yy-MM-dd hh:mm:ss

2008-09-19 05:36:42.116 Scheduled 1 items in 0.0 = 0.01 match + 0.04 place
2008-09-19 05:36:43.122 I'm idle now... shutdown will occur in 60 seconds.
2008-09-19 05:37:42.231 Preshutdown
2008-09-19 05:37:42.588 CheckShutdownServer returned - OK to shutdown
2008-09-19 05:37:42.601 Running the command to set the next scheduled wakeup time :-
						sudo /usr/bin/MythtvWakeSet 08-09-19 05:58:10 
2008-09-19 05:37:42.648 Running the command to shutdown this computer :-
						sudo -H mythshutdown --shutdown
method return sender=:1.5 -> dest=:1.28 reply_serial=2
   int32 0
2008-09-19 05:37:44.626 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = 16288   AND       networkid        = 9018   AND       transportid      = 12290 AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = 1
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2008-09-19 05:37:44.682 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = 16224   AND       networkid        = 9018   AND       transportid      = 12290 AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = 1
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2008-09-19 05:37:44.918 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = 14976   AND       networkid        = 9018   AND       transportid      = 12290 AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = 1
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2008-09-19 05:37:44.957 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = 15552   AND       networkid        = 9018   AND       transportid      = 12290 AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = 1
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

---

### Post by Andrew U.K. on 2008-09-28
Well I've finished it....Yes I'm happy!

Before I reinstalled mythbuntu I checked the BIOS setup to make sure all the ACPI settings were right and then did a fresh install.

I hadn't checked the bios settings before installing mythbuntu before and had just altered them after install. This I think explains the driver error in my mythtv BE log.

I would like to thank bmwman for his clear instructions.

---

### Post by Lester_Burnham on 2008-09-28
I found I had to disable the "wake on RTC" alarm in the BIOS and now it works fine.

Maybe this part of the wiki should be bolded, as you wouldn't expect to have to disable it to get it to work...

**NOTE: On many boards, when this setting is enabled, it will wake only from a time set and saved from BIOS setup, and not from a time set outside of the BIOS setup environment- as we want. All of the boards the original author of this document needed this setting disabled to correctly wake with ACPI. This is the recommended starting point, but is not mandatory. If you are unable to wake your board at step 1.4, try again after setting this to the opposite in BIOS.**

---

### Post by bmwman on 2008-09-28
> **Andrew U.K. said:**
> Well I've finished it....Yes I'm happy!

Before I reinstalled mythbuntu I checked the BIOS setup to make sure all the ACPI settings were right and then did a fresh install.

I hadn't checked the bios settings before installing mythbuntu before and had just altered them after install. This I think explains the driver error in my mythtv BE log.

I would like to thank bmwman for his clear instructions.

I'm glad you have it working. It took me awhile to fix it myself but I've learned a lot in the process. That's why I love Ubuntu/Linux, I love challenges and learning new things.
;)

---

### Post by Andrew U.K. on 2008-09-28
> **bmwman said:**
> I'm glad you have it working. It took me awhile to fix it myself but I've learned a lot in the process. That's why I love Ubuntu/Linux, I love challenges and learning new things.
;)

I absolutely agree. I nearly caved in and changed to windows/gbpvr but windows seemed so dated and more complicated. I am now a Linux convert, even with all of the frustrations I´ve  felt that I have learned a lot.

Cheers 

Andrew

---

### Post by Stevi on 2008-11-01
Hi,

any ideas how to make this work with intrepid? On hardy (mythbuntu 8.04) this worked like charm but yesterday I upgraded to intrepid (mythbuntu 8.10) and now ACPI WakeUp is broken. I played around with some ideas I found [here](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/259149), [here](http://www.mythtv.org/wiki/index.php/ACPI_Wakeup) and [here](http://www.vdr-wiki.de/wiki/index.php/ACPI_Wakeup) but it still doesn't work. I understand that intrepid uses /sys/class/rtc/rtc0/wakealarm instead of /proc/alarm/rtc but I don't know which settings I have to change!?

An updated [How-To](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake) or some possible solutions would be great.

Thanks in advance! :)

---

### Post by majoridiot on 2008-11-01
> **Stevi said:**
> Hi,

any ideas how to make this work with intrepid? On hardy (mythbuntu 8.04) this worked like charm but yesterday I upgraded to intrepid (mythbuntu 8.10) and now ACPI WakeUp is broken. I played around with some ideas I found [here](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/259149), [here](http://www.mythtv.org/wiki/index.php/ACPI_Wakeup) and [here](http://www.vdr-wiki.de/wiki/index.php/ACPI_Wakeup) but it still doesn't work. I understand that intrepid uses /sys/class/rtc/rtc0/wakealarm instead of /proc/alarm/rtc but I don't know which settings I have to change!?

An updated [How-To](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake) or some possible solutions would be great.

Thanks in advance! :)

if it was working for you before, hopefully you still have the scripts and settings you were
using.  try these fixes:

for your MythWakeSet script:
```
#
# MythWakeSet
#

# set the alarm
echo 0 > /sys/class/rtc/rtc0/wakealarm  # clear it
echo $1 > /sys/class/rtc/rtc0/wakealarm # write the waketime

```

then, in mythbackend wakeup settings, you want the time format to be: **time_t** instead of YYYY:MM:dd etc.

the final changes are to hwclock.sh, similar to as outined in the ubuntu acpi wiki.

the changes you need are:

```
ACPITIME=`cat /proc/acpi/alarm`
```

as described in the wiki, should be changed to:

```
ACPITIME=`cat /sys/class/rtc/rtc0/wakealarm`
```

then substitute this addition to hwclock.sh from the wiki:
```
echo "$ACPITIME" > /proc/acpi/alarm && sleep 1 && echo "$ACPITIME" > /proc/acpi/alarm
```

with this:
```
echo 0 > /sys/class/rtc/rtc0/wakealarm
echo "$ACPITIME" > /sys/class/rtc/rtc0/wakealarm && sleep 1 && echo "$ACPITIME" > /sys/class/rtc/rtc0/wakealarm
```

and you should be good to go.

---

### Post by Stevi on 2008-11-01
Hi majoridiot,

thanks for your answer. I tried your fixes but it didn't work.
From the logs:
```
#
2008-11-02 01:14:55.226 CheckShutdownServer returned - OK to shutdown
#
2008-11-02 01:14:55.231 Running the command to set the next scheduled wakeup time :-
#
                                                sudo -H mythshutdown --setwakeup "1225585200"
#
QTime::fromString: Parameter out of range
#
2008-11-02 01:14:55.329 Running the command to shutdown this computer :-
#
                                                sudo -H mythshutdown --shutdown
#
/bin/date: invalid date `1225598280 '
```
I tried to force ACPI Wakeup:
```
#
root@mytheiram:/home/myth# echo 0 > /sys/class/rtc/rtc0/wakealarm
#
root@mytheiram:/home/myth# echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm
#
root@mytheiram:/home/myth# cat /sys/class/rtc/rtc0/wakealarm
1225587475
#
root@mytheiram:/home/myth# cat /proc/driver/rtc
#
rtc_time : 00:53:10
#
rtc_date        : 2008-11-02
#
alrm_time       : 00:57:55
#
alrm_date       : 2008-11-02
#
alarm_IRQ       : yes
#
alrm_pending    : no
#
24hr            : yes
#
periodic_IRQ    : no
#
update_IRQ      : no
#
HPET_emulated   : yes
#
DST_enable      : no
#
periodic_freq   : 1024
#
batt_status     : okay
```
It didn't come up at alarm time.
I also added /sys/class/rtc/rtc0/wakealarm to sudoers (sudo visudo) and changed time to time_t.
[Here are my hwclockfirst.sh, hwclock.sh (line 157) and MythWakeSet (line 313).](http://mythbuntu.pastebin.com/m199d50b)

Any ideas what's going wrong?

---

### Post by majoridiot on 2008-11-01
> **Stevi said:**
> Hi majoridiot,

thanks for your answer. I tried your fixes but it didn't work.

Any ideas what's going wrong?

first thing you want to look at is the MythWakeSet script- use the one i provided above- *that's it*... all two lines of it.

the rest of the script is doing things you no longer need to do and is definitely not helping anything. ;)

change that first and see what happens.  also- are you *sure* your bios clock is set to UTC and not local time?

---

### Post by Stevi on 2008-11-02
> **majoridiot said:**
> first thing you want to look at is the MythWakeSet script- use the one i provided above- *that's it*... all two lines of it.
Okay. I changed the script.
> **majoridiot said:**
> change that first and see what happens.
Still the same, my computer doesn't wake up :(
> **majoridiot said:**
> also- are you *sure* your bios clock is set to UTC and not local time?
Yes, I'm quite sure. The hardware-clock says 10:32 (in germany it's 11:32) and as far as I know german time is UTC + 1.

With hardy I had to use the bios setting "wake up from S5 with rtc: disabled". Is this still the right setting?

After Upgrading to intrepid "powersave- S" didn't work to check if ACPI is enabled in my kernel and working. For this reason I installed some packages via apt (it also uninstalled some packages automatically - how can I view the apt history?). Maybe now some needed packages are missing?

Thanks for your help, majoridiot.

---

### Post by jb5 on 2008-11-02
I too had to install the 'missing' package after ```
powersave -S
``` did not return ACPI. 

Have you managed to get it to wake up manually?

If you get 'permission denied' when writing to wakealalarm, try:-
```
cat /proc/driver/rtc
sudo sh -c 'echo 0 > /sys/class/rtc/rtc0/wakealarm'
sudo sh -c 'echo `date "+%s" -d "+ 5 minutes"` > /sys/class/rtc/rtc0/wakealarm'
cat /sys/class/rtc/rtc0/wakealarm
cat /proc/driver/rtc
```

After the alarm is set {cat /sys/class/rtc/rtc0/wakealarm} should output some long number & {cat /proc/driver/rtc} should now show the alarm as set.

HTH

---

### Post by Stevi on 2008-11-02
Hi jb5,

I tried what you said without succes :(
```
myth@mytheiram:~$ cat /proc/driver/rtc
rtc_time	: 15:48:52
rtc_date	: 2008-11-02
alrm_time	: 18:00:00
alrm_date	: ****-**-02
alarm_IRQ	: no
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: yes
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay
myth@mytheiram:~$ sudo sh -c 'echo 0 > /sys/class/rtc/rtc0/wakealarm'
[sudo] password for myth: 
myth@mytheiram:~$ sudo sh -c 'echo `date "+%s" -d "+ 5 minutes"` > /sys/class/rtc/rtc0/wakealarm'
myth@mytheiram:~$ cat /sys/class/rtc/rtc0/wakealarm
1225641268
myth@mytheiram:~$ cat /proc/driver/rtc
rtc_time	: 15:49:49
rtc_date	: 2008-11-02
alrm_time	: 15:54:28
alrm_date	: 2008-11-02
alarm_IRQ	: yes
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: yes
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay
```

---

### Post by thestevee on 2008-11-02
hey,

i'm not a pro with this, but maybe i can help. yesterday i upgraded to intrepid as well (fresh install) and luckily the wakeup works for the moment. 

what i did: i did not change the hwclock.sh, but left it as it was. additionally the powersave -S didn't show me anything too, however i didn't install the missing package. 

setting the 5 minutes alarm worked, after changing the command to:
```
sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"
sudo sh -c "echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm"
```

it woke up 5 minutes later... please beware, because i don't know what the sudo sh -c part does exactly, but since i got a "permission denied" i tried it out. 

finally after using the mythtv options of the mythtv acpi wakeup wiki [here]("http://www.mythtv.org/wiki/index.php/ACPI_Wakeup#Using_.2Fsys.2Fclass.2Frtc.2Frtc0.2Fwakealarm") and after adding the sudo sh -c "" to the setwakeup.sh (plus adding this in sudoers) it works!

---

### Post by Stevi on 2008-11-02
Hi thestevee,

thanks for your answer. I thought this could be a kernel bug but if it works on your machine there must be a bug in my configuration. I'll try that out tomorrow. Hopefully I can remember the packages I installed/uninstalled via apt :-(

Today I found out that "cat /proc/driver/rtc" looks correct when using jb5's commands but after directly rebooting the machine within 5 minutes "cat /proc/driver/rtc" appears to be wrong. I think mythbuntu overrides the wakeup-time on shutdown :confused:

I have to got to sleep now. Tomorrow I'll try to use setwakeup.sh to wakeup.

edit:> **thestevee said:**
> what i did: i did not change the hwclock.sh,(...)
thestevee: Didn't you change anything or didn't you change anything *new* (means: Did you do [these](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake#hwclock.sh) changes)? Could you please upload your hwclock.sh? I think I don't have a copy of my old one.

---

### Post by thestevee on 2008-11-02
i didn't do any changes at all to the hwclock.sh. (probably works for my specific board without modification) sorry i can't post the file, because i don't have access to the computer anymore, it's at my parents' home. if you followed the wiki you posted, you should have a backup of the unchanged file in your home directory, called hwclock.sh.bak. try to find it. good luck tomorrow.

what didnt work for me was setting the alarm by hand... strange

i really like this wiki page about the acpi wakeup. it's very well written and pretty detailed, too bad it doesn't work with newer kernels. 

goodnight.sh

---

### Post by jb5 on 2008-11-03
OK Stevi - If it woke up after manually setting the alarm then at least you know that you don't need to change anything in BIOS.

The /proc/drivers/rtc (partially) resets itself **after** waking-up for me also, so that is normal. (AFAIK)

The next things I would check are :-

1) hwclock.sh - as MajorIdiot wrote above change the references from ACPI to RTC.
```
/proc/acpi/alarm
is replaced with
/sys/class/rtc/rtc0/wakealarm
```
It *_may_* well be the case that this modification is no longer necessary, however, it does no harm and works for me after the modifications. 

2) Check the script you have written (the two line script [setalarm.sh]).
Make sure that is executable & is included in your sudoers file, along with the alarm directory /sys/class/rtc/rtc0/wakealarm

3) If you have changed the name of the script from that used previously in your setup (setalarm.sh), make sure you have changed the command in either MythBackEnd or MythWelcome to reflect this!

4) Make sure you have replaced the references to yyyy-MM-dd...etc. with time_t in BOTH  MythBackEnd & MythWelcome.

HTH

EDIT - For info this is my hwclock.sh```
#!/bin/sh
# hwclock.sh	Set and adjust the CMOS clock, according to the UTC
#		setting in /etc/default/rcS (see also rcS(5)).
#
# Version:	@(#)hwclock.sh  2.00  14-Dec-1998  miquels@cistron.nl
#
# Patches:
#		2000-01-30 Henrique M. Holschuh <hmh@rcm.org.br>
#		 - Minor cosmetic changes in an attempt to help new
#		   users notice something IS changing their clocks
#		   during startup/shutdown.
#		 - Added comments to alert users of hwclock issues
#		   and discourage tampering without proper doc reading.

# WARNING:	Please read /usr/share/doc/util-linux/README.Debian.hwclock
#		or /usr/share/doc/util-linux/README.Debian.hwclock
#		before changing this file. You risk serious clock
#		misbehaviour otherwise.

### BEGIN INIT INFO
# Provides:          hwclock
# Required-Start:    mountdevsubfs
# Required-Stop:     $local_fs
# Default-Start:     S
# Default-Stop:      0 6
### END INIT INFO

FIRST=no	# debian/rules sets this to 'yes' when creating hwclockfirst.sh

# Set this to any options you might need to give to hwclock, such
# as machine hardware clock type for Alphas.
HWCLOCKPARS=
ACPITIME=`cat /sys/class/rtc/rtc0/wakealarm` #/proc/acpi/alarm`
hwclocksh()
{
    [ ! -x /sbin/hwclock ] && return 0
    . /etc/default/rcS

    . /lib/lsb/init-functions
    verbose_log_action_msg() { [ "$VERBOSE" = no ] || log_action_msg "$@"; }

    [ "$GMT" = "-u" ] && UTC="yes"
    case "$UTC" in
       no|"")	GMT="--localtime"
		UTC=""
		if [ "X$FIRST" = "Xyes" ] && [ ! -r /etc/localtime ]; then
		    if [ -z "$TZ" ]; then
			log_action_msg "System clock was not updated at this time"
			return 1
		    fi
		fi
		;;
       yes)	GMT="--utc"
		UTC="--utc"
		;;
       *)	log_action_msg "Unknown UTC setting: \"$UTC\""; return 1 ;;
    esac

    case "$BADYEAR" in
       no|"")	BADYEAR="" ;;
       yes)	BADYEAR="--badyear" ;;
       *)	log_action_msg "unknown BADYEAR setting: \"$BADYEAR\""; return 1 ;;
    esac

    case "$1" in
	start)
	    if [ -w /etc ] && [ ! -f /etc/adjtime ] && [ ! -e /etc/adjtime ]; then
		echo "0.0 0 0.0" > /etc/adjtime
	    fi

	    if [ ! -w /etc/adjtime ]; then
		NOADJ="--noadjfile"
	    else
	    	NOADJ=""
	    fi

	    if [ "$FIRST" != yes ]; then
		# Uncomment the hwclock --adjust line below if you want
		# hwclock to try to correct systematic drift errors in the
		# Hardware Clock.
		#
		# WARNING: If you uncomment this option, you must either make
		# sure *nothing* changes the Hardware Clock other than
		# hwclock --systohc, or you must delete /etc/adjtime
		# every time someone else modifies the Hardware Clock.
		#
		# Common "vilains" are: ntp, MS Windows, the BIOS Setup
		# program.
		#
		# WARNING: You must remember to invalidate (delete)
		# /etc/adjtime if you ever need to set the system clock
		# to a very different value and hwclock --adjust is being
		# used.
		#
		# Please read /usr/share/doc/util-linux/README.Debian.hwclock
		# before enablig hwclock --adjust.

		#hwclock --adjust $GMT $BADYEAR
		:
	    fi

	    if [ "$HWCLOCKACCESS" != no ]; then
		log_action_msg "Setting the system clock"

		# Copies Hardware Clock time to System Clock using the correct
		# timezone for hardware clocks in local time, and sets kernel
		# timezone. DO NOT REMOVE.
		if /sbin/hwclock --hctosys $GMT $HWCLOCKPARS $BADYEAR $NOADJ; then
		    #	Announce the local time.
		    verbose_log_action_msg "System Clock set to: `date $UTC`"
		else
		    log_warning_msg "Unable to set System Clock to: `date $UTC`"
		fi
	    else
		verbose_log_action_msg "Not setting System Clock"
	    fi
	    ;;
	stop|restart|reload|force-reload)
	    #
	    # Updates the Hardware Clock with the System Clock time.
	    # This will *override* any changes made to the Hardware Clock.
	    #
	    # WARNING: If you disable this, any changes to the system
	    #          clock will not be carried across reboots.
	    #
	    if [ "$HWCLOCKACCESS" != no ]; then
		log_action_msg "Saving the system clock"
		if [ "$GMT" = "-u" ]; then
		    GMT="--utc"
		fi
		if /sbin/hwclock --systohc $GMT $HWCLOCKPARS $BADYEAR; then
		   	verbose_log_action_msg "Hardware Clock updated to `date`" ;
		fi
	echo "$ACPITIME" > /sys/class/rtc/rtc0/wakealarm && sleep 1 && echo "$ACPITIME" > /sys/class/rtc/rtc0/wakealarm ;
	    else
		verbose_log_action_msg "Not saving System Clock"
	    fi
	    ;;
	show)
	    if [ "$HWCLOCKACCESS" != no ]; then
		/sbin/hwclock --show $GMT $HWCLOCKPARS $BADYEAR
		
	    fi
	    ;;
	*)
	    log_success_msg "Usage: hwclock.sh {start|stop|reload|force-reload|show}"
	    log_success_msg "       start sets kernel (system) clock from hardware (RTC) clock"
	    log_success_msg "       stop and reload set hardware (RTC) clock from kernel (system) clock"
	    return 1
	    ;;
    esac
}

hwclocksh "$@"
```

---

### Post by Stevi on 2008-11-03
At first thanks to all of your for trying to help me!

> **jb5 said:**
> OK Stevi - If it woke up after manually setting the alarm then at least you know that you don't need to change anything in BIOS.

The /proc/drivers/rtc (partially) resets itself **after** waking-up for me also, so that is normal. (AFAIK)
I think you got me wrong.

The machine doesn't wake up! "cat /proc/driver/rtc" looks correct when using your commands but it doesn't wake up. For this reason I used your commands again (+9 minutes) an rebooted manually within 2 minutes and "cat /proc/driver/rtc" doesn't show the correct alrm_date any more. That's why I think mythbuntu overrides the wakeup-time on shutdown.

I think my bios settings are correct because it worked before I upgraded to intrepid (wake up from rtc is disabled).

I attached my mythwelcome and myth_backend settings and some other files. Maybe one of you sees a wrong setting.

I think the error won't be found in the mythbackend or mythwelcome settings because I'm unable to wakeup manually.

Trying to do this manually:
```
myth@mytheiram:~$ cat /proc/driver/rtcrtc_time    : 16:29:44
rtc_date    : 2008-11-03
alrm_time    : 18:00:00
alrm_date    : ****-**-03
alarm_IRQ    : no
alrm_pending    : no
24hr        : yes
periodic_IRQ    : no
update_IRQ    : no
HPET_emulated    : yes
DST_enable    : no
periodic_freq    : 1024
batt_status    : okay
myth@mytheiram:~$ sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"
myth@mytheiram:~$ cat /proc/driver/rtcrtc_time    : 16:29:59
rtc_date    : 2008-11-03
alrm_time    : 16:34:55
alrm_date    : ****-**-03
alarm_IRQ    : no
alrm_pending    : no
24hr        : yes
periodic_IRQ    : no
update_IRQ    : no
HPET_emulated    : yes
DST_enable    : no
periodic_freq    : 1024
batt_status    : okay
myth@mytheiram:~$ sudo sh -c "echo `date '+%s' -d '+ 6 minutes'` > /sys/class/rtc/rtc0/wakealarm"
myth@mytheiram:~$ cat /proc/driver/rtcrtc_time    : 16:30:22
rtc_date    : 2008-11-03
alrm_time    : 16:36:18
alrm_date    : 2008-11-03
alarm_IRQ    : yes
alrm_pending    : no
24hr        : yes
periodic_IRQ    : no
update_IRQ    : no
HPET_emulated    : yes
DST_enable    : no
periodic_freq    : 1024
batt_status    : okay
```

But it didn't wakeup at 16:36 :(

I tried so many settings that I'm a little bit confused and frustrated. I also reinstalled powernowd instead of powersaved. Maybe I try a clean install of Mythbuntu 8.10.

Again: Thanks for your help!

---

### Post by Stevi on 2008-11-03
Maybe this could be a kernel bug. Today I found this [Kernel Bug Tracker Bug Page](http://bugzilla.kernel.org/show_bug.cgi?id=11411).
[quote="Stefan Bauer"](...)Other users at VDR Portal reported the same
issue with the following boards:
MSI K8NGM2-FID
ASUS M2A-VM HDMI(...)[/quote]
I have a ASUS Pundit2-M2A690G. On the german VDR Portal I found a [patch](http://www.vdr-portal.de/board/thread.php?postid=747607#post747607):
```
--- drivers/rtc/rtc-cmos.c.save	2008-08-20 20:11:37.000000000 +0200
+++ drivers/rtc/rtc-cmos.c	2008-08-23 10:51:41.000000000 +0200
@@ -213,6 +213,8 @@
 	sec = t->time.tm_sec;
 	sec = (sec < 60) ? BIN2BCD(sec) : 0xff;
 
+	if (cmos->wake_off)
+		cmos->wake_off(dev);
 	hpet_set_alarm_time(t->time.tm_hour, t->time.tm_min, t->time.tm_sec);
 	spin_lock_irq(&rtc_lock);
 
@@ -247,6 +249,8 @@
 	}
 
 	spin_unlock_irq(&rtc_lock);
+	if (t->enabled && cmos->wake_on)
+		cmos->wake_on(dev);
 
 	return 0;
 }

```
Could this be the right thing for me? Is it possible to try this patch with ubuntu? I never did this before.

Thanks in advance.

edit: Just for interest I tried to automatically wake_up my laptop. I only had to ```
sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"
sudo sh -c "echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm"
```
and it worked like charm. I don't know what's wrong with my mythbuntu-machine. Tomorrow I'll try a clean install.

---

### Post by Stevi on 2008-11-13
Just for info: It's a kernel-bug, see [bugzilla](http://bugzilla.kernel.org/show_bug.cgi?id=12013).

---

### Post by divbo on 2008-11-14
Can someone tell me is is possible to setup ACPIWake if your using the new kernal /sys/class/rtc/rtc0/wakealarm and your bios doesn't have an option to enable UTC time?

I've been trying to get this working for a while now. I've managed to shutdown when Idle and perform the simple test: wake the machine 5 minutes from now:
> echo 0 > /sys/class/rtc/rtc0/wakealarm
echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm
cat /sys/class/rtc/rtc0/wakealarm

But I can't the schedule startup correct. This is because of UTC time/Local time confusion. If I go into bios the clock is set as GMT time but the schedule start time looks to be set in local time.

I've tried Ubuntu helps MythWakeSet script but this returned an error.
> #!/bin/sh

# inspired from [http://www.mythtv.org/wiki/index.php/ACPI_Wakeup](http://www.mythtv.org/wiki/index.php/ACPI_Wakeup)
# and [https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)
#
# MythWakeSet
#
# set mythtv wake-up time with UTC-adjusted time
#
# use: MythWakeSet date time      
# ex.: MythWakeSet 2008-11-02 20:15:00
# See also 'man date' for date/time-formats.

# TimeZone, use +0100 for GMT+1
TZ="+0100" 

LOG=/var/log/mythtv/mythbackend.log

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


Error:
> 2008-11-15 09:32:19.420 Running the command to set the next scheduled wakeup time :-
                                                sudo /usr/bin/MythWakeSet 1226702280
date: invalid date `1226702280  +1100'
date: invalid date `1226702280 '



And Wiki's setwakeup.sh script
> #!/bin/sh
#$1 is the first argument to the script. It is the time in seconds since 1970
#this is defined in mythtv-setup with the time_t argument

echo 0 > /sys/class/rtc/rtc0/wakealarm      #this clears your alarm.
echo $1 > /sys/class/rtc/rtc0/wakealarm     #this writes your alarm


This writes to bios OK but is resulting in the time difference problem.

Any help would be much appreciated!! I hate wasting all this electricity but I don't want to miss my TV programs! :)

---

### Post by tafkaz on 2008-11-20
hi everybody.
Any news on this?
I am having the same problem with an ASUS Pundit. It just wont wake up anymore...
The board in my Pundit seems to be an ASUS M2N8L ACPI BIOS Revision 0404.
@Stevi: Did you try the patch and if it worked...tell me how you did it ! :-)
Thanx

---

### Post by Stevi on 2008-11-20
> **tafkaz said:**
> 
@Stevi: Did you try the patch and if it worked...tell me how you did it ! :-)
Hi,
no, I didn't patch. It's another bug so the patch wouldn't work. According to this [comment](http://bugzilla.kernel.org/show_bug.cgi?id=12013#c3) it's possible to revert to /proc/acpi/alarm but I didn't try. At the moment I'm following the [kernel bug tracker](http://bugzilla.kernel.org/show_bug.cgi?id=12013) until a fix is released.

---

### Post by tafkaz on 2008-11-20
ahhh....that's a pity...
i am following the kernel bug tracker too now...actually the last comment was mine...
I really hope this'll be fixed soon....
i don't want my machine to be running day and night....
all in all the switch to intrepid fixed the issue i had with the alsa-sound, but left me with a whole bunch of new problems...
as my fritzUSB-Wlan stick doesn't want to work 100% here anymore (as it has to be done with ndiswrapper now), i am also looking for a good out of the box running usb-Wireless stick...
anyone has a good suggestion ?

---

### Post by Stevi on 2008-11-20
> **tafkaz said:**
> 
as my fritzUSB-Wlan stick doesn't want to work 100% here anymore (as it has to be done with ndiswrapper now), i am also looking for a good out of the box running usb-Wireless stick...
anyone has a good suggestion ?
On my Mythbuntu-Machine I'm running a WLan-stick called TP-Link TL-WN321G. It works out of the box and it's really cheap (about 10 &#8364; in germany).

---

### Post by tafkaz on 2008-11-23
alright.....
just ordered one.....thanx for the hint !
any news on the wakeup bug ?

---

### Post by Stevi on 2008-11-27
Great news: The box is able to wakeup with the kernel option "hpet=disable". Yeah!

You can change this permanently in /boot/grub/menu.lst (For example: defoptions=hpet=disable. Then type "sudo update-grub" into a terminal and reboot). This works definitly for ASUS Pundit2-M2A690G.

---

### Post by tafkaz on 2008-11-29
ahhh bugger...
it didnt help here....so i seem to have a different problem...
i am working on it...

---

### Post by silverdulcet on 2008-12-03
I have ACPIWake functioning just fine with my /usr/bin/setwakeup.sh $time script entered into mythtv-setup. I have tested it, and it wakes up just the way it should. The problem I'm having is that I can't get it to work with Mythwelcome. I change the set wakeuptime in mythtv-setup to
```
Set wakeuptime Command: sudo -H mythshutdown --setwakeup "$time"
```

The time format is set to time_t in both mythtv-setup and Mythwelcome. I change the Set Wakeup Time command in Mythwelcome to
```
Command to Set Wakeup Time: sudo /usr/bin/setwakeup.sh $time
```

This is the error I get from mythbackend.log
```
Error:2008-12-03 12:09:18.993 Mythshutdown: --setwakeup
2008-12-03 12:09:18.993 Mythshutdown: wakeup time given is: 1228328036
QTime::fromString: Parameter out of range
QDate::setYMD: Invalid date 1228-28-36
2008-12-03 12:09:18.993 Mythshutdown: --setwakeup invalid date format (1228328036)
			must be yyyy-MM-ddThh:mm:ss
```

It won't accept the epoch time format. Is there something I'm missing in the configuration of either mythtv-setup or mythwelcome? Its so close to working perfectly I just need to get Mythwelcome working. It looks like it breaks down when trying to pass the wakeup time from mythbackend to mythwelcome.

---

### Post by Stevi on 2008-12-03
> **silverdulcet said:**
> The time format is set to time_t in both mythtv-setup and Mythwelcome.
In mythtv-setup it also didn't work for me with time_t. Try yyyy-MM-ddThh:mm. This works for me. I attached some screenshots with my settings. HTH.

---

### Post by silverdulcet on 2008-12-03
> In mythtv-setup it also didn't work for me with time_t. Try yyyy-MM-ddThh:mm. This works for me. I attached some screenshots with my settings. HTH.

That is all it took to fix it. I guess mythshutdown --setwakeup expects the time in the format above. Then when mythwelcome runs the script to set the wakeup time in the bios it converts it from that format to the time_t (or epoch time) format. 

Thanks for your help! :p

---

### Post by davidgeeee on 2008-12-14
Help!  I think I have followed this thread correctly but the computer doesn't wakeup from an automated shutdown.  I can manually set a wakeup time with 

> 
echo 0 > /sys/class/rtc/rtc0/wakealarm
echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm
cat /sys/class/rtc/rtc0/wakealarm


and then do a 

> shutdown -h now

and the computer will shutdown and restart in 5 minutes.  Can anyone see anything wrong in the following log file that might point to where the problem is?


> 
2008-12-14 06:10:09.501 New DB connection, total: 3
2008-12-14 06:10:09.584 Connected to database 'mythconverg' at host: localhost
2008-12-14 06:10:10.193 New DB scheduler connection
2008-12-14 06:10:10.375 Connected to database 'mythconverg' at host: localhost
2008-12-14 06:10:10.654 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-12-14 06:10:10.721 Main::Registering HttpStatus Extension
2008-12-14 06:10:10.757 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-12-14 06:10:10.854 Enabled verbose msgs:  important general
2008-12-14 06:10:10.902 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-12-14 06:10:13.503 Reschedule requested for id -1.
2008-12-14 06:10:15.515 Scheduled 4 items in 2.0 = 1.60 match + 0.41 place
2008-12-14 06:10:15.836 Seem to be woken up by USER
2008-12-14 06:10:50.894 MainServer::HandleAnnounce Playback
2008-12-14 06:10:50.902 adding: MythBackend as a client (events: 0)
2008-12-14 06:10:50.905 MainServer::HandleAnnounce Monitor
2008-12-14 06:10:50.907 adding: MythBackend as a client (events: 1)
2008-12-14 06:11:07.034 I'm idle now... shutdown will occur in 600 seconds.
2008-12-14 06:11:30.507 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-12-14 06:21:06.545 MainServer::HandleAnnounce Monitor
2008-12-14 06:21:06.547 adding: MythBackend as a client (events: 0)
2008-12-14 06:21:06.550 MainServer::HandleAnnounce Monitor
2008-12-14 06:21:06.552 adding: MythBackend as a client (events: 1)
2008-12-14 06:21:06.628 CheckShutdownServer returned - OK to shutdown
2008-12-14 06:21:06.644 Running the command to set the next scheduled wakeup time :-
						sudo /usr/bin/setwakeup.sh
2008-12-14 06:21:06.695 Running the command to shutdown this computer :-
						sudo mythshutdown --shutdown
2008-12-14 06:21:09.089 I'm idle now... shutdown will occur in 600 seconds.
2008-12-14 06:25:18.415 Using runtime prefix = /usr
2008-12-14 06:25:18.478 Empty LocalHostName.
2008-12-14 06:25:18.479 Using localhost value of MythBackend
2008-12-14 06:25:18.618 New DB connection, total: 1
2008-12-14 06:25:18.666 Connected to database 'mythconverg' at host: localhost
2008-12-14 06:25:18.695 Closing DB connection named 'DBManager0'
2008-12-14 06:25:18.702 Connected to database 'mythconverg' at host: localhost
2008-12-14 06:25:18.710 New DB connection, total: 2
2008-12-14 06:25:18.714 Connected to database 'mythconverg' at host: localhost
2008-12-14 06:25:18.785 Current Schema Version: 1214
Starting up as the master server.
2008-12-14 06:25:20.533 New DB connection, total: 3
2008-12-14 06:25:20.684 Connected to database 'mythconverg' at host: localhost
2008-12-14 06:25:21.302 New DB scheduler connection
2008-12-14 06:25:21.329 Connected to database 'mythconverg' at host: localhost
2008-12-14 06:25:21.563 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-12-14 06:25:21.568 Main::Registering HttpStatus Extension
2008-12-14 06:25:21.570 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-12-14 06:25:21.579 Enabled verbose msgs:  important general
2008-12-14 06:25:21.624 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-12-14 06:25:24.487 Reschedule requested for id -1.
2008-12-14 06:25:27.120 Scheduled 4 items in 2.6 = 1.72 match + 0.91 place
2008-12-14 06:25:27.532 Seem to be woken up by USER
2008-12-14 06:26:02.056 MainServer::HandleAnnounce Playback
2008-12-14 06:26:02.064 adding: MythBackend as a client (events: 0)
2008-12-14 06:26:02.067 MainServer::HandleAnnounce Monitor
2008-12-14 06:26:02.068 adding: MythBackend as a client (events: 1)
2008-12-14 06:26:41.484 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

---

### Post by Stevi on 2008-12-14
Are you using Mythwelcome?

---

### Post by davidgeeee on 2008-12-14
Stevi,

That is how I get it to automatically shutdown.  MythWelcome gives me the countdown then shuts down.  Do you have any ideas?

---

### Post by davidgeeee on 2008-12-14
Stevi 

Just tried the setup from your screenshot above and got this:

> 2008-12-14 07:07:35.004 I'm idle now... shutdown will occur in 600 seconds.
2008-12-14 07:08:18.636 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-12-14 07:17:34.495 MainServer::HandleAnnounce Monitor
2008-12-14 07:17:34.497 adding: MythBackend as a client (events: 0)
2008-12-14 07:17:34.500 MainServer::HandleAnnounce Monitor
2008-12-14 07:17:34.502 adding: MythBackend as a client (events: 1)
2008-12-14 07:17:34.572 CheckShutdownServer returned - OK to shutdown
2008-12-14 07:17:34.586 Running the command to set the next scheduled wakeup time :-
						sudo -H mythshutdown --setwakeup.sh 2008-12-16T16:50:00
Invalid argument: --setwakeup.sh
Usage of mythshutdown
-w/--setwakeup time      (sets the wakeup time. time=yyyy-MM-ddThh:mm:ss
                          doesn't write it into nvram)
-t/--setscheduledwakeup  (sets the wakeup time to the next scheduled recording)
-q/--shutdown            (set nvram-wakeup time and shutdown)
-x/--safeshutdown        (equal to -c -t -q.  check shutdown possible, set
                           scheduled wakeup and shutdown)
-p/--startup             (check startup. check will return 0 if automatic
                                                           1 for manually)
-c/--check flag          (check shutdown possible
                          flag is 0 - don't check recording status
                                  1 - do check recording status (default)
                          returns 0 ok to shutdown
                                  1 reset idle check)
-l/--lock                (disable shutdown. check will return 1.)
-u/--unlock              (enable shutdown. check will return 0)
-s/--status flag         (returns a code indicating the current status)
                          flag is 0 - don't check recording status
                                  1 - do check recording status (default)
                          0 - Idle
                          1 - Transcoding
                          2 - Commercial Flagging
                          4 - Grabbing EPG data
                          8 - Recording - only valid if flag is 1
                         16 - Locked
                         32 - Jobs running or pending
                         64 - In a daily wakeup/shutdown period
                        128 - Less than 15 minutes to next wakeup period
                        255 - Setup is running
-v/--verbose debug-level (Use '-v help' for level info
-h/--help                (shows this usage)
2008-12-14 07:17:34.837 Running the command to shutdown this computer :-
						sudo mythshutdown --shutdown
2008-12-14 07:17:37.297 I'm idle now... shutdown will occur in 600 seconds.
2008-12-14 07:20:58.113 Using runtime prefix = /usr
2008-12-14 07:20:58.164 Empty LocalHostName.
2008-12-14 07:20:58.171 Using localhost value of MythBackend
2008-12-14 07:20:58.316 New DB connection, total: 1
2008-12-14 07:20:58.363 Connected to database 'mythconverg' at host: localhost
2008-12-14 07:20:58.382 Closing DB connection named 'DBManager0'
2008-12-14 07:20:58.388 Connected to database 'mythconverg' at host: localhost
2008-12-14 07:20:58.393 New DB connection, total: 2
2008-12-14 07:20:58.406 Connected to database 'mythconverg' at host: localhost
2008-12-14 07:20:58.448 Current Schema Version: 1214
Starting up as the master server.
2008-12-14 07:21:00.336 New DB connection, total: 3
2008-12-14 07:21:00.479 Connected to database 'mythconverg' at host: localhost
2008-12-14 07:21:01.133 New DB scheduler connection
2008-12-14 07:21:01.263 Connected to database 'mythconverg' at host: localhost
2008-12-14 07:21:01.549 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-12-14 07:21:01.582 Main::Registering HttpStatus Extension
2008-12-14 07:21:01.584 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-12-14 07:21:01.586 Enabled verbose msgs:  important general
2008-12-14 07:21:01.643 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-12-14 07:21:04.407 Reschedule requested for id -1.
2008-12-14 07:21:06.725 Scheduled 4 items in 2.3 = 1.61 match + 0.70 place
2008-12-14 07:21:06.949 Seem to be woken up by USER
2008-12-14 07:21:43.249 MainServer::HandleAnnounce Playback
2008-12-14 07:21:43.258 adding: MythBackend as a client (events: 0)
2008-12-14 07:21:43.261 MainServer::HandleAnnounce Monitor
2008-12-14 07:21:43.263 adding: MythBackend as a client (events: 1)

---

### Post by Stevi on 2008-12-14
> **davidgeeee said:**
> ```
2008-12-14 07:17:34.586 Running the command to set the next scheduled wakeup time :-
sudo -H mythshutdown --setwakeup.sh 2008-12-16T16:50:00
Invalid argument: --setwakeup.sh
```

Did you set up "setwakeup.sh" [correctly](http://ubuntuforums.org/showpost.php?p=6091183&postcount=95) and added that file to sudoers?

---

### Post by davidgeeee on 2008-12-14
I am trying:
> 
sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"
sudo sh -c "echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm"
now.  Can I used a shutdown command or do I have to let MythWelcome shut it down?

---

### Post by Stevi on 2008-12-14
MythWelcome has to do this. Because before shutting down it tells the machine when it has to wakeup. 

Try a recording that is about 30 minutes in the future.

---

### Post by davidgeeee on 2008-12-14
It seems to want to NOT shut down if the upcoming recording is less than 2 hours in the future.  Is that a setting I missed somewhere?  And is there a place in the backend or frontend setup where I specify that I want MythWelcome?  Cuz I have to start Mythwelcome from the command prompt.

---

### Post by Stevi on 2008-12-14
> **davidgeeee said:**
> It seems to want to NOT shut down if the upcoming recording is less than 2 hours in the future.  Is that a setting I missed somewhere?
Mmmhh, I have no problem like that. Maybe it's a problem with the delay time between two recordings? I set it to [1 minute](http://media.ubuntuusers.de/forum/attachments/1726031/Screenshot.png).

> **davidgeeee said:**
> And is there a place in the backend or frontend setup where I specify that I want MythWelcome?  Cuz I have to start Mythwelcome from the command prompt.
[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake#Mythbuntu%208.10](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake#Mythbuntu%208.10)
> Mythbuntu 8.10

edit '/etc/mythtv/session-settings' like this:

$ sudo nano /etc/mythtv/session-settings

Uncomment the line reading

      #MYTHWELCOME=true

it should look like this

      MYTHWELCOME=true

---

### Post by davidgeeee on 2008-12-14
Okay this is what my log looks like now:

> 2008-12-14 16:20:17.142 MainServer::HandleAnnounce Monitor
2008-12-14 16:20:17.144 adding: MythBackend as a client (events: 1)
2008-12-14 16:20:17.209 CheckShutdownServer returned - OK to shutdown
2008-12-14 16:20:17.244 Running the command to set the next scheduled wakeup time :-
						sudo -H mythshutdown --setwakeup 2008-12-16T16:50:00
2008-12-14 16:20:17.542 Running the command to shutdown this computer :-
						sudo mythshutdown --shutdown
/usr/bin/MythWakeSet: 18: cannot create : Directory nonexistent
date: invalid date `1229464200  -0500'
date: invalid date `1229464200 '
Running /usr/bin/MythWakeSet to set the wakeup time to 1229464200
echo 0 > /sys/class/rtc/rtc0/wakealarm
echo  > /sys/class/rtc/rtc0/wakealarm
rtc_time	: 21:20:18
rtc_date	: 2008-12-14
alrm_time	: 21:25:17
alrm_date	: ****-12-14
alarm_IRQ	: no
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: no
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay
2008-12-14 16:20:20.170 I'm idle now... shutdown will occur in 300 seconds.
2008-12-14 16:48:48.226 Using runtime prefix = /usr
2008-12-14 16:48:48.289 Empty LocalHostName.
2008-12-14 16:48:48.294 Using localhost value of MythBackend
2008-12-14 16:48:48.429 New DB connection, total: 1
2008-12-14 16:48:48.465 Connected to database 'mythconverg' at host: localhost
2008-12-14 16:48:48.485 Closing DB connection named 'DBManager0'
2008-12-14 16:48:48.491 Connected to database 'mythconverg' at host: localhost
2008-12-14 16:48:48.501 New DB connection, total: 2
2008-12-14 16:48:48.506 Connected to database 'mythconverg' at host: localhost
2008-12-14 16:48:48.584 Current Schema Version: 1214
Starting up as the master server.
2008-12-14 16:48:50.455 New DB connection, total: 3
2008-12-14 16:48:50.625 Connected to database 'mythconverg' at host: localhost
2008-12-14 16:48:51.125 New DB scheduler connection
2008-12-14 16:48:51.253 Connected to database 'mythconverg' at host: localhost
2008-12-14 16:48:51.341 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-12-14 16:48:51.345 Main::Registering HttpStatus Extension
2008-12-14 16:48:51.346 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-12-14 16:48:51.352 Enabled verbose msgs:  important general
2008-12-14 16:48:51.413 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-12-14 16:48:54.277 Reschedule requested for id -1.
2008-12-14 16:48:57.576 Scheduled 4 items in 3.3 = 2.22 match + 1.08 place
2008-12-14 16:48:57.683 Seem to be woken up by USER
2008-12-14 16:49:32.365 MainServer::HandleAnnounce Playback
2008-12-14 16:49:32.373 adding: MythBackend as a client (events: 0)
2008-12-14 16:49:32.376 MainServer::HandleAnnounce Monitor
2008-12-14 16:49:32.377 adding: MythBackend as a client (events: 1)
2008-12-14 16:50:11.270 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-12-14 16:56:49.784 I'm idle now... shutdown will occur in 300 seconds.

Boy, something looks messed up now.  Any clues?

---

### Post by davidgeeee on 2008-12-14
Just saw your last post Stevi, I have fixed the MythWelcome in the "session-settings"
Thanks.  Will reboot now after setting a recording 45 minuted in the future.

---

### Post by Stevi on 2008-12-14
> **davidgeeee said:**
> ```

sudo -H mythshutdown --setwakeup 2008-12-16T16:50:00
2008-12-14 16:20:17.542 Running the command to shutdown this computer :-
sudo mythshutdown --shutdown
/usr/bin/MythWakeSet: 18: cannot create : Directory nonexistent
```

I'm a little bit confuse right now. Did you create MythWakeSet or setwakeup.sh? I'm using MythWakeSet and for this reason this an be found in [my settings](http://media.ubuntuusers.de/forum/attachments/1726031/Screenshot-Untit.png). I think otherwise you should change this to setwakeup.sh.

---

### Post by davidgeeee on 2008-12-14
I put setwakeup back in the "Command to set wakeup" box in the F11 on Mythwelcome. Rebooting...

---

### Post by davidgeeee on 2008-12-15
I fixed the setting "Wait for recording".  Was set at 120 minutes, DUH!

MythWelcome is now logging so that must be working.

Setting to record in 15 minutes.  Should shutdown in 5 minutes and start 5 minutes after that.  Will post results....

---

### Post by davidgeeee on 2008-12-15
> **Stevi said:**
> I'm a little bit confuse right now. Did you create MythWakeSet or setwakeup.sh? I'm using MythWakeSet and for this reason this an be found in [my settings](http://media.ubuntuusers.de/forum/attachments/1726031/Screenshot-Untit.png). I think otherwise you should change this to setwakeup.sh.

I changed back to setwakeup.sh

---

### Post by davidgeeee on 2008-12-15
It seems I may have been using the wrong guide.  Is [[COLOR="Blue"]this[/COLOR]]("https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake#Mythbuntu%208.10") the one I should use if I am using the "/sys/class/rtc/rtc0/wakealarm"?

---

### Post by davidgeeee on 2008-12-15
> **Stevi said:**
> I'm a little bit confuse right now. Did you create MythWakeSet or setwakeup.sh? I'm using MythWakeSet and for this reason this an be found in [my settings](http://media.ubuntuusers.de/forum/attachments/1726031/Screenshot-Untit.png). I think otherwise you should change this to setwakeup.sh.

Stevi,

I just re-read the whole thread and have finally noticed where the old alarm stuff end and the new alarm stuff begins.  You mentioned that you were going to do a fresh install of Mythbuntu 8.10.  Can you tell me the steps you did and didn't do since then?  I am afraid that I have incorporated some /proc/acpi/alarm information in my setting and/or scripts and will have to re-install as well.  Thanks

---

### Post by Stevi on 2008-12-15
> **davidgeeee said:**
> Can you tell me the steps you did and didn't do since then?
I created MythWakeSet 
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
And changed [sudoers](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake#sudo).
```
%mythtv ALL = NOPASSWD: /sbin/shutdown, /usr/bin/MythWakeSet, /sys/class/rtc/rtc0/wakealarm, /usr/bin/MythShutdownCheck, /etc/init.d/mythtv-backend, /usr/bin/mythshutdown
```
And I changed my settings to the following. Added:
[http://media.ubuntuusers.de/forum/attachments/1726031/Screenshot.png](http://media.ubuntuusers.de/forum/attachments/1726031/Screenshot.png)
[http://media.ubuntuusers.de/forum/attachments/1726031/Screenshot-Untit.png](http://media.ubuntuusers.de/forum/attachments/1726031/Screenshot-Untit.png)

Mmhh, and I think that's it.

edit: You can also take a look at [this wiki](http://www.mythtv.org/wiki/index.php/ACPI_Wakeup#Using_.2Fsys.2Fclass.2Frtc.2Frtc0.2Fwakealarm).

---

### Post by davidgeeee on 2008-12-16
Should I be able to issue the "sudo -H mythshutdown --setwakeup $time" command from the command line?

> davidgeeee@MythBackend:~$ cat /proc/driver/rtc
rtc_time	: 09:48:51
rtc_date	: 2008-12-16
alrm_time	: 00:00:00
alrm_date	: ****-**-01
alarm_IRQ	: no
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: no
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay
davidgeeee@MythBackend:~$ sudo echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm
[sudo] password for davidgeeee: 
davidgeeee@MythBackend:~$ cat /proc/driver/rtcrtc_time	: 09:49:51
rtc_date	: 2008-12-16
alrm_time	: 09:54:41
alrm_date	: 2008-12-16
alarm_IRQ	: yes
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: no
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay
davidgeeee@MythBackend:~$ sudo mythshutdown --safeshutdown
davidgeeee@MythBackend:~$ sudo -H mythshutdown --setwakeup $time
mythshutdown: Missing argument to -w/--setwakeup option
davidgeeee@MythBackend:~$ sudo -H mythshutdown --setwakeup "$time"
QDateTime::fromString: Parameter out of range
davidgeeee@MythBackend:~$ 


---

### Post by silverdulcet on 2008-12-16
> Should I be able to issue the "sudo -H mythshutdown --setwakeup $time" command from the command line?

I wasn't able to unless I typed in an actual date instead of using the $time variable. So you could try a date that matches the format you specified in the Mythbackend setup:
```
yyyy-MM-ddThh:mm
```

For example:

> sudo -H mythshutdown --setwakeup "2008-12-17T12:30"

Then see if it accepts the date format. Are you still having trouble I take it? If so what errors are recorded in the logs?

Just to check where we currently are. Can you take a screenshot of your Mythbackend setup and your Mythwelcome setup screen? Then copy and paste the contents of your script that sets the wakeup time in the bios (specify whether its /usr/bin/MythWakeSet.sh or /usr/bin/setwakeup.sh). Finally post the contents of your sudoers file. In this way we can make sure that with all your trial and error something hasn't been configured slightly wrong.

---

### Post by davidgeeee on 2008-12-16
> **silverdulcet said:**
> 
Just to check where we currently are. Can you take a screenshot of your Mythbackend setup and your Mythwelcome setup screen? Then copy and paste the contents of your script that sets the wakeup time in the bios (specify whether its /usr/bin/MythWakeSet.sh or /usr/bin/setwakeup.sh). Finally post the contents of your sudoers file. In this way we can make sure that with all your trial and error something hasn't been configured slightly wrong.

I will do this soon.  I just found an error in hwclock.sh where I had a quote mark(') instead of an accent grave (`).  Jeez and I hope that was it...

---

### Post by rr33333 on 2008-12-16
welcome to our website: [www.voguejordan.com](www.voguejordan.com) ,We hope become your reliable shoes supplier in China. Authentic Shoes with original box,we insists that " Customer the highest, Quality first ". Our products include Air Jordan series,Mix jordan series, Air max Shoes series, Air force one, Nike shox series shoes, Adidas Shoes, Timberland Shoes, Prada Shoes,Gucci shoes,puma shoes,lv bags, and Bape, Lacoste,Polo T-shirt,Evisu hoody,Evisu coat etc. we are looking forward to building sincere and long-term business relationships with you.

---

### Post by davidgeeee on 2008-12-16
Holy Cr*p it's -23 degrees Celsius here!  As I ran out of the house I think my machine shutdown and woke up by it self.  Will have to check in about 10 hours.

If it was a frozen mirage and my machine is still wacked, I will post the items that SilverDulcet mentioned.  Actually either way I will post them so it might help someone else.

Thanks to everyone so far!!!:KS

---

### Post by davidgeeee on 2008-12-17
> **silverdulcet said:**
> 
Just to check where we currently are. Can you take a screenshot of your Mythbackend setup and your Mythwelcome setup screen? Then copy and paste the contents of your script that sets the wakeup time in the bios (specify whether its /usr/bin/MythWakeSet.sh or /usr/bin/setwakeup.sh). Finally post the contents of your sudoers file. In this way we can make sure that with all your trial and error something hasn't been configured slightly wrong.

IT WORKS!!!   Thanks to Stevi, db260179, SilverDulcet, bmwman for all the help!
 
Here's my hwclock.sh
> #!/bin/sh
# hwclock.sh	Set and adjust the CMOS clock, according to the UTC
#		setting in /etc/default/rcS (see also rcS(5)).
#
# Version:	@(#)hwclock.sh  2.00  14-Dec-1998  [email]miquels@cistron.nl[/email]
#
# Patches:
#		2000-01-30 Henrique M. Holschuh <hmh@rcm.org.br>
#		 - Minor cosmetic changes in an attempt to help new
#		   users notice something IS changing their clocks
#		   during startup/shutdown.
#		 - Added comments to alert users of hwclock issues
#		   and discourage tampering without proper doc reading.

# WARNING:	Please read /usr/share/doc/util-linux/README.Debian.hwclock
#		before changing this file. You risk serious clock
#		misbehaviour otherwise.

### BEGIN INIT INFO
# Provides:          hwclock
# Required-Start:    mountdevsubfs
# Required-Stop:     $local_fs
# Default-Start:     S
# Default-Stop:      0 6
### END INIT INFO

FIRST=no	# debian/rules sets this to 'yes' when creating hwclockfirst.sh

# Set this to any options you might need to give to hwclock, such
# as machine hardware clock type for Alphas.
HWCLOCKPARS=
ACPITIME=`cat /sys/class/rtc/rtc0/wakealarm`
hwclocksh()
{
    [ ! -x /sbin/hwclock ] && return 0
    . /etc/default/rcS

    . /lib/lsb/init-functions
    verbose_log_action_msg() { [ "$VERBOSE" = no ] || log_action_msg "$@"; }

    [ "$GMT" = "-u" ] && UTC="yes"
    case "$UTC" in
       no|"")	GMT="--localtime"
		UTC=""
		if [ "X$FIRST" = "Xyes" ] && [ ! -r /etc/localtime ]; then
		    if [ -z "$TZ" ]; then
			log_action_msg "System clock was not updated at this time"
			return 1
		    fi
		fi
		;;
       yes)	GMT="--utc"
		UTC="--utc"
		;;
       *)	log_action_msg "Unknown UTC setting: \"$UTC\""; return 1 ;;
    esac

    case "$BADYEAR" in
       no|"")	BADYEAR="" ;;
       yes)	BADYEAR="--badyear" ;;
       *)	log_action_msg "unknown BADYEAR setting: \"$BADYEAR\""; return 1 ;;
    esac

    case "$1" in
	start)
	    if [ -w /etc ] && [ ! -f /etc/adjtime ] && [ ! -e /etc/adjtime ]; then
		echo "0.0 0 0.0" > /etc/adjtime
	    fi

	    if [ ! -w /etc/adjtime ]; then
		NOADJ="--noadjfile"
	    else
	    	NOADJ=""
	    fi

	    if [ "$FIRST" != yes ]; then
		# Uncomment the hwclock --adjust line below if you want
		# hwclock to try to correct systematic drift errors in the
		# Hardware Clock.
		#
		# WARNING: If you uncomment this option, you must either make
		# sure *nothing* changes the Hardware Clock other than
		# hwclock --systohc, or you must delete /etc/adjtime
		# every time someone else modifies the Hardware Clock.
		#
		# Common "vilains" are: ntp, MS Windows, the BIOS Setup
		# program.
		#
		# WARNING: You must remember to invalidate (delete)
		# /etc/adjtime if you ever need to set the system clock
		# to a very different value and hwclock --adjust is being
		# used.
		#
		# Please read /usr/share/doc/util-linux/README.Debian.hwclock
		# before enabling hwclock --adjust.

		#/sbin/hwclock --adjust $GMT $BADYEAR
		:
	    fi

	    if [ "$HWCLOCKACCESS" != no ]; then
		log_action_msg "Setting the system clock"

		# Copies Hardware Clock time to System Clock using the correct
		# timezone for hardware clocks in local time, and sets kernel
		# timezone. DO NOT REMOVE.
		if /sbin/hwclock --hctosys $GMT $HWCLOCKPARS $BADYEAR $NOADJ; then
		    #	Announce the local time.
		    verbose_log_action_msg "System Clock set to: `date $UTC`"
		else
		    log_warning_msg "Unable to set System Clock to: `date $UTC`"
		fi
	    else
		verbose_log_action_msg "Not setting System Clock"
	    fi
	    ;;
	stop|restart|reload|force-reload)
	    #
	    # Updates the Hardware Clock with the System Clock time.
	    # This will *override* any changes made to the Hardware Clock.
	    #
	    # WARNING: If you disable this, any changes to the system
	    #          clock will not be carried across reboots.
	    #
#	ACPITIME='cat /sys/class/rtc/rtc0/wakealarm`
	    if [ "$HWCLOCKACCESS" != no ]; then
		log_action_msg "Saving the system clock"
		if [ "$GMT" = "-u" ]; then
		    GMT="--utc"
		fi
		if /sbin/hwclock --systohc $GMT $HWCLOCKPARS $BADYEAR; then
		    verbose_log_action_msg "Hardware Clock updated to `date`"
		fi
	    else
		verbose_log_action_msg "Not saving System Clock"
	    fi
#	echo 0 > /sys/class/rtc/rtc0/wakealarm
	echo "$ACPITIME" > /sys/class/rtc/rtc0/wakealarm && sleep 1 && echo "$ACPITIME" > /sys/class/rtc/rtc0/wakealarm
	    ;;
	show)
	    if [ "$HWCLOCKACCESS" != no ]; then
		/sbin/hwclock --show $GMT $HWCLOCKPARS $BADYEAR
	    fi
	    ;;
	*)
	    log_success_msg "Usage: hwclock.sh {start|stop|reload|force-reload|show}"
	    log_success_msg "       start sets kernel (system) clock from hardware (RTC) clock"
	    log_success_msg "       stop and reload set hardware (RTC) clock from kernel (system) clock"
	    return 1
	    ;;
    esac
}

hwclocksh "$@"

Here's my setwakeup.sh
> #!/bin/sh
#$1 is the first argument to the script. It is the time in seconds since 1970
#this is defined in mythtv-setup with the time_t argument
#Changed from 
#echo 0 > /sys/class/rtc/rtc0/wakealarm      #this clears your alarm.
#echo $1 > /sys/class/rtc/rtc0/wakealarm     #this writes your alarm
#To this on 20081214
sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"      #this clears your alarm.
sudo sh -c "echo $1 > /sys/class/rtc/rtc0/wakealarm"     #this writes your alarm

Here is my MythWakeSet:

> #
#!/bin/sh

# inspired from [http://www.mythtv.org/wiki/index.php/ACPI_Wakeup](http://www.mythtv.org/wiki/index.php/ACPI_Wakeup)
# and [https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)
#
# MythWakeSet
#
# set mythtv wake-up time with UTC-adjusted time
#
sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm" # clear it
sudo sh -c "echo $1 > /sys/class/rtc/rtc0/wakealarm" # write the waketime


sudoers file:
> %admin ALL=(ALL) ALL
%mythtv ALL = NOPASSWD: /sbin/shutdown, /usr/bin/MythWakeSet, /sys/class/rtc/rtc0/wakealarm, /usr/bin/MythShutdownCheck, /etc/init.d/mythtv-backend, /usr/bin/mythshutdown, /usr/bin/welcome, /usr/bin/mythwelcome, /usr/bin/eject, /bin/mount, /bin/umount, /usr/bin/nuvexport, /usr/bin/nuvexport-xvid, /bin/sh, /usr/bin/setwakeup.sh, /usr/bin/setwakeup


Hope this helps someone!  Cheers!

[ATTACH]96681[/ATTACH]

[ATTACH]96682[/ATTACH]

---

### Post by majoridiot on 2008-12-17
/me wonders if anyone is updating the mythbuntu wiki for this or not...?

---

### Post by davidgeeee on 2008-12-17
> **majoridiot said:**
> /me wonders if anyone is updating the mythbuntu wiki for this or not...?

The wiki mentions that it SHOULD be updated but no one, has as of a few days ago.  There is very little chat about this so maybe it is automatic for most machines?!?

---

### Post by thor999 on 2010-01-02
Well, I am new here (and to Linux as well) and running mythbuntu 9.04, and cannot find a hwclock.sw anywhere on my system, yet, in a terminal, I can "hwclock --" and produce output "Sat 02 Jan 2010 02:52:59 AM CST  -0.378141 seconds". I am pretty much stuck 'til I can edit hwclock.sh, which does not exist on my system. Any ideas? Is it something new? Also, sorry to revitalize an old thread, but I need help, I want to record programs w/out wasting electricity, and I have learned Linux STRICTLY for MythTv and have somehow gotten far enough so that this is the only problem left unsolved! Also, I can use the wake command in terminal and it works just fine, FWIW yet cannot obtain success w/ the Mythwelcome portion of this tut. 
    Conicidentally, my hardware clock is in local time, as is my system clock, regardless of what changes I make w/ the hwclock command, anyone have an idea on that one? Being as how I am new to this, I notice that when people threaten to return to windoze out of frustration, they get prompt help; is this a requirement, or a shameful action, worthy of flamage?
    O.K. this is new: after installing all the files previously attached, I now get an alarm 5 hrs and 5 mins in the future w/ the command:
mom@mom-desktop:/etc/init.d$ sudo sh -c "echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm"
mom@mom-desktop:/etc/init.d$ cat /proc/driver/rtcrtc_time    : 16:14:06
rtc_date    : 2010-01-02
alrm_time    : 21:23:30
alrm_date    : 2010-01-02
alarm_IRQ    : yes
alrm_pending    : no
24hr        : yes
periodic_IRQ    : no
update_IRQ    : no
HPET_emulated    : no
DST_enable    : no
periodic_freq    : 1024
batt_status    : okay
mom@mom-desktop:/etc/init.d$ 
    Any ideas on that? hwclock IS the same as system clock...

---

