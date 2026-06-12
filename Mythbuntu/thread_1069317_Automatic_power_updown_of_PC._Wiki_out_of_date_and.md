---
title: "Automatic power up/down of PC. Wiki out of date and causing problems"
date: 2009-02-13
forum: Mythbuntu
---

### Post by AKADAP on 2009-02-13
I am attempting to get my mythTV system to power up for a scheduled recording and power down when done. I am attempting to follow this wiki article:
[http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup)
but I am running into trouble.

The first issue I ran into is attempting to do this:
```
Here are the commands to check that you have ACPI working.

$powersave -S
  ACPI
```

On Ubunto 8.1, this is not installed. So I installed powersaved. Bad idea. This has broken my computers ability to control the processor clock speed, and brings up an annoying message box on every boot to tell me that this is broken. Even after I uninstalled it.

Next problem is this instruction:
```
  Initiate manually

For an successful manual test you first need to Prepared your Linux distribution and Disable HWclock updates like described in the first section of this article.

Simple test to wake the machine 5 minutes from now

echo 0 > /sys/class/rtc/rtc0/wakealarm
echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm
cat /sys/class/rtc/rtc0/wakealarm

Check 
```

That first line does not work. if I try it I get:
```
$ echo 0 > /sys/class/rtc/rtc0/wakealarm
bash: /sys/class/rtc/rtc0/wakealarm: Permission denied

```
Ok so what if I try as root? I get this:
```
$ sudo echo 0 > /sys/class/rtc/rtc0/wakealarm
bash: /sys/class/rtc/rtc0/wakealarm: Permission denied

```
Huh? I must not have write permission, better check:
```
$ ls -l /sys/class/rtc/rtc0/wakealarm
-rw-r--r-- 1 root root 4096 2009-02-13 17:08 /sys/class/rtc/rtc0/wakealarm

```
WTF? root has write permission but when it tries to write it is denied!???

If i chmod wakealarm to 666, I can write to it, I can follow the instructions and my computer will power on by itself properly, BUT! Next time I boot, the permissions are back to 644.

So, I can't permanently change the permissions, and I can't do the operation with sudo. How am I supposed to make this work?

---

### Post by silverdulcet on 2009-02-14
Unfortunately I do not know how to fix your troubles with powersave, but as to your second problem.

```
sudo su
```

Try the above to get a root prompt:
```
root@hostname:
```
Those tests should work then. When you set it up for the machine to do it automatically, you add commands to the sudoers file so that they can be run by root.

Since you've already successfully woken the machine, you don't need to run them again. 

I would also check out the later posts in this thread:
[http://ubuntuforums.org/showthread.php?t=702310]("http://ubuntuforums.org/showthread.php?t=702310")

The wiki still has some good information. Just make sure it and the posts in that thread are referring to the rtc method, since the acpi one is no longer used. 

If you run into any other troubles or need clarification feel free to post again. :P

---

### Post by freak42 on 2009-02-14
about your echo//sudo problems

I think echo is NOT a standalone app but a command from your shell .. therefore sudo cannot elevate its rights, because your shell is already running.

sudo su works
but you can also use this:
sudo bash

then you have a shell with the 'right' rights..

hth

---

### Post by AKADAP on 2009-02-14
> **freak42 said:**
> about your echo//sudo problems

I think echo is NOT a standalone app but a command from your shell .. therefore sudo cannot elevate its rights, because your shell is already running.

sudo su works
but you can also use this:
sudo bash

then you have a shell with the 'right' rights..

hth

Ok, this sounds plausible. 
How does one distinguish between built in commands in bash and executables? It is not like I've ever run across a listing of Linux/bash commands with descriptions of what they do anywhere.

---

### Post by AKADAP on 2009-02-14
> **silverdulcet said:**
> Unfortunately I do not know how to fix your troubles with powersave, but as to your second problem.

```
sudo su
```

Try the above to get a root prompt:
```
root@hostname:
```
Those tests should work then. When you set it up for the machine to do it automatically, **you add commands to the sudoers file** so that they can be run by root.

Since you've already successfully woken the machine, you don't need to run them again. 

I would also check out the later posts in this thread:
[http://ubuntuforums.org/showthread.php?t=702310]("http://ubuntuforums.org/showthread.php?t=702310")

The wiki still has some good information. Just make sure it and the posts in that thread are referring to the rtc method, since the acpi one is no longer used. 

If you run into any other troubles or need clarification feel free to post again. :P

The stuff in bold I'm not so clear on. I assume the sudoers file lets one run scripts & executables from a script as superuser. I've read the man page, but like most man pages, they never bother to concisely state the purpose of the command or file they are documenting. That must be inferred from the myriad options that are described.
So to clarify what I am not clear on, am I enabling the script to run as superuser, or a user to be superuser, or a user to run a script as superuser or something else entirely?
In the mean time, I'm going to go read that thread you linked.

---

### Post by AKADAP on 2009-02-14
> **silverdulcet said:**
> Unfortunately I do not know how to fix your troubles with powersave,

On reading the thread you linked someone mentioned re-installing "powernow" I looked at the dependancies of powersaved and found that it would uninstall powernow.

Taking a wild guess, I installed powernow, this restored my computers ability to control the processor speed.

So for once, I was able to undo a screwup without having to re-install Ubuntu \\:D/

---

### Post by silverdulcet on 2009-02-14
> **AKADAP said:**
> The stuff in bold I'm not so clear on. I assume the sudoers file lets one run scripts & executables from a script as superuser. I've read the man page, but like most man pages, they never bother to concisely state the purpose of the command or file they are documenting. That must be inferred from the myriad options that are described.
So to clarify what I am not clear on, am I enabling the script to run as superuser, or a user to be superuser, or a user to run a script as superuser or something else entirely?
In the mean time, I'm going to go read that thread you linked.

[http://ubuntuforums.org/showpost.php?p=6374963&postcount=130]("http://ubuntuforums.org/showpost.php?p=6374963&postcount=130")

The specific post linked above has information on the /etc/sudoers file. It consists of allowing the mythtv user to run MythShutdownCheck, start/stop/restart myth-backend, run your MythSetWake script, and finally shutdown the system without requiring a password. It also lists the configuration options for myth-backend and MythWelcome. Its a way of only allowing the mythtv user limited superuser access to the commands it needs to set the RTC clock, start/stop myth-backend and shutdown the system.

---

### Post by AKADAP on 2009-02-15
> **silverdulcet said:**
> [http://ubuntuforums.org/showpost.php?p=6374963&postcount=130]("http://ubuntuforums.org/showpost.php?p=6374963&postcount=130")

The specific post linked above has information on the /etc/sudoers file. It consists of allowing the mythtv user to run MythShutdownCheck, start/stop/restart myth-backend, run your MythSetWake script, and finally shutdown the system without requiring a password. It also lists the configuration options for myth-backend and MythWelcome. Its a way of only allowing the mythtv user limited superuser access to the commands it needs to set the RTC clock, start/stop myth-backend and shutdown the system.
Thank you, I will have a look.

This brings me to another issue that has been bothering me. Why must myth directly control the wakeup clock itself? Shouldn't this be a kernal controlled resource handled by something like cron so that multiple applications could request that the PC be on at a particular time and cron could decide when to wake the computer next?
I'm also planning to use this computer as my desktop, and there needs to be a good way of handling situations like me deciding to shut the system down while the system is recording (destroying the recording in the process). It would be nice to have some daemon that could decide not to actually shut the system down when something important was going on (like a recording) and wait for that to complete before actually shutting the system off. Have it do something like hibernate if the user is logged in & idle for a long time, but shut down if it is sitting at the login screen doing nothing.

---

### Post by silverdulcet on 2009-02-15
> **AKADAP said:**
> Thank you, I will have a look.

This brings me to another issue that has been bothering me. Why must myth directly control the wakeup clock itself? Shouldn't this be a kernal controlled resource handled by something like cron so that multiple applications could request that the PC be on at a particular time and cron could decide when to wake the computer next?
I'm also planning to use this computer as my desktop, and there needs to be a good way of handling situations like me deciding to shut the system down while the system is recording (destroying the recording in the process). It would be nice to have some daemon that could decide not to actually shut the system down when something important was going on (like a recording) and wait for that to complete before actually shutting the system off. Have it do something like hibernate if the user is logged in & idle for a long time, but shut down if it is sitting at the login screen doing nothing.

This is what MythWelcome does. You configure it so that it will not shutdown if there is a recording scheduled within X minutes. You also set a timeout value, so that when you exit Mythfrontend it checks whether there is a recording within X minutes, if there is not it will shutdown after the timeout value you have assigned. When it wakes up for a recording, it only loads Mythwelcome. If no one hits enter/OK to start the Mythfrontend then it shuts down after it has recorded something. It will never shutdown as long as Mythfrontend is running.

---

### Post by NautiusMaximus on 2009-02-15
I would also like to make use of automatic power up and down of my PC. Thanks for the warning about the wiki.

I see that the wiki has been edited a couple of times today. Do I have a reasonable chance of getting things to work if I follow the instructions now?

Mythbuntu 8.10.

Thanks
NM

---

### Post by AKADAP on 2009-02-15
> **silverdulcet said:**
> This is what MythWelcome does. You configure it so that it will not shutdown if there is a recording scheduled within X minutes. You also set a timeout value, so that when you exit Mythfrontend it checks whether there is a recording within X minutes, if there is not it will shutdown after the timeout value you have assigned. When it wakes up for a recording, it only loads Mythwelcome. If no one hits enter/OK to start the Mythfrontend then it shuts down after it has recorded something. It will never shutdown as long as Mythfrontend is running.

I have been looking at mythwelcome, but I don't think it does what I need it to do. It appears to me that mythwelcome is intended for a standalone myth box that is not intended to work as a desktop as well. It appears that it runs as an application after an auto-login as the myth user.

What I need is an equivalent of mythwelcome that replaces the login screen. The idea being the system will boot to the login screen & display the status of the system (status of the myth back end, whether it is recording etc), and shut the system down if nothing important is happening or is scheduled to happen shortly, and no one has logged in.
It doesn't look to me that mythwelcome works this way.

---

### Post by AKADAP on 2009-02-15
> **NautiusMaximus said:**
> I would also like to make use of automatic power up and down of my PC. Thanks for the warning about the wiki.

I see that the wiki has been edited a couple of times today. Do I have a reasonable chance of getting things to work if I follow the instructions now?

Mythbuntu 8.10.

Thanks
NM

I was the one to make the edits. I plan to attempt to get this working today though I have not yet convinced myself that this is compatible with using the system as a desktop as well.

---

### Post by AKADAP on 2009-02-15
I think I am missing something fundamental.

When does mythbackend decided to shutdown the system?
When does it decide to run the shutdown test script?
Is it when it has completed a recording?
Every x minutes when it isn't doing something?
When mythfrontend exits?

I tried setting up the shutdown/wake stuff with a dummy shutdown command, and ran mythbackend in a terminal to monitor its activity, but it never attempts to shut down.

I'm confused. :confused:

---

### Post by AKADAP on 2009-02-18
I found a mistake in my setup. Idle shutdown time was zero which disabled auto shutdown.

I attempted to run an experiment today by scheduling a recording about an hour into the future, stop running everything and waiting. The fifteen minutes I had specified as the idle timeout passed and nothing happened. So I shut the system down manually.
The specified 15 minutes before recording came and went with nothing happening. so I powered on my system. The computer began recording properly without my having to log in, so at least one thing worked properly. I wanted to see if the system would shut down by itself afterwards, but I had to abort that experiment because in the mean time I nearly cut the tip of my left index finger off with an ax. (took 7 stitches). It is a real pain trying to type with 9 fingers.

---

### Post by silverdulcet on 2009-02-18
> **AKADAP said:**
> I found a mistake in my setup. Idle shutdown time was zero which disabled auto shutdown.

I attempted to run an experiment today by scheduling a recording about an hour into the future, stop running everything and waiting. The fifteen minutes I had specified as the idle timeout passed and nothing happened. So I shut the system down manually.
The specified 15 minutes before recording came and went with nothing happening. so I powered on my system. The computer began recording properly without my having to log in, so at least one thing worked properly. I wanted to see if the system would shut down by itself afterwards, but I had to abort that experiment because in the mean time I nearly cut the tip of my left index finger off with an ax. (took 7 stitches). It is a real pain trying to type with 9 fingers.

Have you verified that your /usr/bin/MythWakeSet script works? Try issuing this command, then shutting down the system normally:
```
MythWakeSet `date -u '+%s' -d '+ 2 minutes'`
```
If all goes well then the system should wake itself up in ~2 minutes.

You are probably correct about MythWelcome not being right for you if you are using it as a desktop. In that case, there are a couple of changes to be made. If you haven't already, disable MythWelcome by doing the opposite of these instructions:
[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake#Mythbuntu%208.10]("https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake#Mythbuntu%208.10")

Basically Comment out MYTHWELCOME=true like so:
/etc/mythtv/session-settings
```
#MYTHWELCOME=true
```

Once you've disabled Mythwelcome we can see if we can get to set the wakeup time and shutdown the system when you set it to. Please see the wiki link Mythshutdown:
[http://www.mythtv.org/wiki/Mythshutdown]("http://www.mythtv.org/wiki/Mythshutdown")
By using the command:
```
mythshutdown --lock
```and ```
mythshutdown --unlock
```

You are able to prevent/allow mythtv from shutting down your system. You could put them in a script and run them from a panel icon. People have written scripts to check whether a certain user is logged in that will enable/disable shutdown as well. I don't have any experience with that, but if you do some google searching you might find examples of those.

Your Mythtv Shutdown/Wakeup Options should look something like this:
```
Wakeup time format: time_t
Command to set Wakeup Time: /usr/bin/MythWakeSet $time
Server halt command:sudo -H mythshutdown --shutdown
```

---

### Post by AKADAP on 2009-02-18
> **silverdulcet said:**
> Have you verified that your /usr/bin/MythWakeSet script works? Try issuing this command, then shutting down the system normally:
```
MythWakeSet `date -u '+%s' -d '+ 2 minutes'`
```
If all goes well then the system should wake itself up in ~2 minutes.


Attempting this pointed out a couple of mistakes. The first being that I called my script setwake.sh, but used MythtvWakeSet in mythbackendsetup. While fixing that, I noticed that my shutdown command was a garbled mix of the temporary echo command I had put in for testing, and the normal shut down command. I don't think I was thinking clearly yesterday. Perhaps that is why I cut my finger.

When I figured out the correct name for setwake.sh, it worked fine. Of course Ubuntu chose this boot to check the disk. Good thing I was paying attention, it took 16 minutes to complete the test. I had allowed only 15 minutes before the recording, I would have missed the recording if I had left that at 15 minutes.

> 
You are probably correct about MythWelcome not being right for you if you are using it as a desktop. In that case, there are a couple of changes to be made. If you haven't already, disable MythWelcome by doing the opposite of these instructions:
[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake#Mythbuntu%208.10]("https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake#Mythbuntu%208.10")

Basically Comment out MYTHWELCOME=true like so:
/etc/mythtv/session-settings
```
#MYTHWELCOME=true
```


I had never enabled mythwelcome, so I had nothing to do. That line was already commented out.
> 

Once you've disabled Mythwelcome we can see if we can get to set the wakeup time and shutdown the system when you set it to. Please see the wiki link Mythshutdown:
[http://www.mythtv.org/wiki/Mythshutdown]("http://www.mythtv.org/wiki/Mythshutdown")
By using the command:
```
mythshutdown --lock
```and ```
mythshutdown --unlock
```

You are able to prevent/allow mythtv from shutting down your system. You could put them in a script and run them from a panel icon. People have written scripts to check whether a certain user is logged in that will enable/disable shutdown as well. I don't have any experience with that, but if you do some google searching you might find examples of those.

This looks ideal for what I want. I can put mythshutdown --lock into a script that runs when i log in, and mythshutdown --unlock into a script when I log out, I can let mythtv worry about shutting down the computer.
This does have a lock count doesn't it?
> 
Your Mythtv Shutdown/Wakeup Options should look something like this:
```
Wakeup time format: time_t
Command to set Wakeup Time: /usr/bin/MythWakeSet $time
Server halt command:sudo -H mythshutdown --shutdown
```

---

### Post by AKADAP on 2009-02-18
Ran experiment again, failed again. checked mythtv-setup again, found wrong time format, and $Time instead of $time. will run test again tomorrow.

settings are now:
Startup command: (blank)
Block shutdown before client connected: (unchecked)
Idle shutdown timeout (secs): 300
Max. wait for recording (min): 60
Startup before rec. (secs): 1200
Wakeup time format time_t
Command to set Wakeup Time: /usr/bin/setwakeup.sh $time
Server halt command: sudo mythshutdown --shutdown
Pre Shutdown check-command: MythtvShutdownCheck

I have verified that MythtvShutdownCheck and setwakeup.sh work.
This might work

---

### Post by silverdulcet on 2009-02-19
> **AKADAP said:**
> Ran experiment again, failed again. checked mythtv-setup again, found wrong time format, and $Time instead of $time. will run test again tomorrow.

settings are now:
Startup command: (blank)
Block shutdown before client connected: (unchecked)
Idle shutdown timeout (secs): 300
Max. wait for recording (min): 60
Startup before rec. (secs): 1200
Wakeup time format time_t
Command to set Wakeup Time: /usr/bin/setwakeup.sh $time
Server halt command: sudo mythshutdown --shutdown
Pre Shutdown check-command: MythtvShutdownCheck

I have verified that MythtvShutdownCheck and setwakeup.sh work.
This might work

Just a quick note this setting you have:
Pre Shutdown check-command: MythtvShutdownCheck

This is the old way of doing it. Much of what people would put into the MythShutdownCheck is now performed by mythshutdown itself. 

```
mythshutdown --lock
mythshutdown --unlock
```

Those commands are both toggles. You run the first it locks mythtv from shutting down. You run the second it now unlocks it and it will shutdown if nothing is being recorded, no commflag or user jobs are running and no scheduled recordings fall within your configured times. This is all handled by:

Pre Shutdown check-command: mythshutdown --check

That is not to say that your MythShutdownCheck script won't work, but unless you want some customized thing for mythtv to check before shutting down I'd stick with the officially supported mythshutdown --check which has most of the common features that people would put into their own MythShutdownCheck.

---

### Post by AKADAP on 2009-02-19
> **silverdulcet said:**
> Just a quick note this setting you have:
Pre Shutdown check-command: MythtvShutdownCheck

This is the old way of doing it. Much of what people would put into the MythShutdownCheck is now performed by mythshutdown itself. 

```
mythshutdown --lock
mythshutdown --unlock
```

Those commands are both toggles. You run the first it locks mythtv from shutting down. You run the second it now unlocks it and it will shutdown if nothing is being recorded, no commflag or user jobs are running and no scheduled recordings fall within your configured times. This is all handled by:

Pre Shutdown check-command: mythshutdown --check

That is not to say that your MythShutdownCheck script won't work, but unless you want some customized thing for mythtv to check before shutting down I'd stick with the officially supported mythshutdown --check which has most of the common features that people would put into their own MythShutdownCheck.

The only reason I haven't done something like this yet is that I haven't figured out what scripts get run when I login and logout so that I can put mythshutdown --lock in the login script, and mythshutdown --unlock in the logout script.

---

### Post by silverdulcet on 2009-02-19
> **AKADAP said:**
> The only reason I haven't done something like this yet is that I haven't figured out what scripts get run when I login and logout so that I can put mythshutdown --lock in the login script, and mythshutdown --unlock in the logout script.

I would suggest putting mythshutdown --lock in your Autostarted Applications. Applications>Xfce Settings Manager>Autostarted Applications. If you are using gnome-desktop I think its under System menu somewhere as Session Settings. 

For when you log out, try placing mythshutdown --unlock in your /etc/gdm/PostSession/Default file, before the line.
```
exit 0

```

---

### Post by AKADAP on 2009-02-19
> **silverdulcet said:**
> I would suggest putting mythshutdown --lock in your Autostarted Applications. Applications>Xfce Settings Manager>Autostarted Applications. If you are using gnome-desktop I think its under System menu somewhere as Session Settings. 

For when you log out, try placing mythshutdown --unlock in your /etc/gdm/PostSession/Default file, before the line.
```
exit 0

```

There is no "Applications>Xfce Settings Manager>Autostarted Applications" on my system.

There is however a /etc/gdm/PostLogin/Default.sample file. I gave created a /etc/gdm/PostLogin/Default file with these contents:
```
#!/bin/sh
#
# Script to prevent MythTV from automatically shutting down computer when user is logged in.

mythshutdown --lock

exit 0

```
I figure if I am using the /etc/gdm/PostSession/Default to close the lock, I should use the same system to open it.

---

### Post by AKADAP on 2009-02-20
I have deleted /etc/gdm/PostLogin/Default because I read the documentation and found that /etc/gdm/PreSession/Default is run after PostLogin, so I put the mythshutdown --lock there instead. I think this makes for a more symmetric lock/unlock.

I had a partial success with the previous method (the MythtvShudownCheck method), the system shut down from the login prompt after a delay while the myth backend was idle, but it did not restart for a scheduled recording. I think the mythshutdown --check method is a better choice, so I am attempting that.

---

### Post by AKADAP on 2009-02-20
Progress! I have verified that the lock is set when I am logged in,
```
~$ mythshutdown --check
~$ echo $?
1
~$ 
``` and that Ubuntu will shut down after an idle period while sitting at the login prompt.

Now all I have to do is get it to power on the computer for scheduled actions (recording, downloading schedules etc.).

I don't know why this isn't working yet.

---

### Post by silverdulcet on 2009-02-20
> **AKADAP said:**
> Progress! I have verified that the lock is set when I am logged in,
```
~$ mythshutdown --check
~$ echo $?
1
~$ 
``` and that Ubuntu will shut down after an idle period while sitting at the login prompt.

Now all I have to do is get it to power on the computer for scheduled actions (recording, downloading schedules etc.).

I don't know why this isn't working yet.

You posted earlier when you manually set the waketime from the commandline and shutdown the system it powered up on its own correct?
```
sudo -H /usr/bin/setwakeup.sh `date -u '+%s' -d '+ 5 minutes'`
```

I noticed in my previous post I might have not put the sudo -H in front of the MythWakeSet command. On your mythtv-setup page, try changing it to look like this.
```
Command to set Wakeup Time: sudo -H /usr/bin/setwakeup.sh $time
```

Be sure to double check the actual name of the script you are using for setting your RTC wakealarm. It doesn't matter what you call it. Just in the last few posts I've seen you list both "setwake.sh" and "setwakeup.sh".

If setting the rtc wakealarm works from the command line, it should work from within your Mythtv-setup Shutdown/Wakeup Options.

---

### Post by AKADAP on 2009-02-20
> **silverdulcet said:**
> You posted earlier when you manually set the waketime from the commandline and shutdown the system it powered up on its own correct?
```
sudo -H /usr/bin/setwakeup.sh `date -u '+%s' -d '+ 5 minutes'`
```

I have never used the -H option with sudo. My setwakeup.sh has the reqired sudo commands in it already, so I only need to run the setwakeup.sh command itself without the additional sudo in front of it. And yes, it does properly cause the computer to power on.
> 
I noticed in my previous post I might have not put the sudo -H in front of the MythWakeSet command. On your mythtv-setup page, try changing it to look like this.
```
Command to set Wakeup Time: sudo -H /usr/bin/setwakeup.sh $time
```

Be sure to double check the actual name of the script you are using for setting your RTC wakealarm. It doesn't matter what you call it. Just in the last few posts I've seen you list both "setwake.sh" and "setwakeup.sh".

If setting the rtc wakealarm works from the command line, it should work from within your Mythtv-setup Shutdown/Wakeup Options.

The name is setwakeup.sh, and yes I have verified this.

The only documentation I trust at the moment is the following:
```
~$ mythshutdown --help
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

```
If you look at the --shutdown option, it claims to "set nvram-wakeup time and shutdown". Wouldn't this overwrite the wakeup time I set with setwakeup.sh?
I tried replacing my setwakeup.sh command with mythshutdown --setscheduledwakeup, but in spite of manually running this with the -v all option showing it setting the correct time, this does not work either.
I may attempt to go back to the setwakeup.sh command, and replace the mythshdown --shutdown with shutdown -h now. At least that will not attempt to overwrite the wakeup time.

---

### Post by silverdulcet on 2009-02-20
> **AKADAP said:**
> I have never used the -H option with sudo. My setwakeup.sh has the reqired sudo commands in it already, so I only need to run the setwakeup.sh command itself without the additional sudo in front of it. And yes, it does properly cause the computer to power on.


The name is setwakeup.sh, and yes I have verified this.

The only documentation I trust at the moment is the following:
```
~$ mythshutdown --help
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

```
If you look at the --shutdown option, it claims to "set nvram-wakeup time and shutdown". Wouldn't this overwrite the wakeup time I set with setwakeup.sh?
I tried replacing my setwakeup.sh command with mythshutdown --setscheduledwakeup, but in spite of manually running this with the -v all option showing it setting the correct time, this does not work either.
I may attempt to go back to the setwakeup.sh command, and replace the mythshdown --shutdown with shutdown -h now. At least that will not attempt to overwrite the wakeup time.

You might be correct. Give it a try, you could also just use
```
Server halt command: poweroff
```

However, it is my understanding that the options on the Mythtv-setup Shutdown/Wakeup Options menu are the variables used by mythshutdown. Which is just a script. So when it says that mythshutdown --shutdown sets the nvram wakeup time, it calls the script that you have entered into that Options menu. You can test this by adding this line to your setwakeup.sh
/usr/bin/setwakeup.sh
```
#!/bin/sh
logger "setwakeup.sh called with $1"
sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm" #this clears your alarm.
sudo sh -c "echo $1 > /sys/class/rtc/rtc0/wakealarm" #this writes your alarm 
```

Then check your syslog the entry placed by logger when mythshutdown --shutdown calls setwakeup.sh

---

### Post by AKADAP on 2009-02-20
Another post, another failed experiment.

I tried the "sudo -H /usr/bun/setstartup.sh $time" method. It did not work.

---

### Post by AKADAP on 2009-02-21
Yet another failure.
I tried replacing "mythshudown --shutdown" with "shutdown -h now"

Is there any way to log the error messages during these failures?

---

### Post by AKADAP on 2009-02-21
And again.
I tried sudo -H mythshutdown -safeshutdown.
I deleted the setwakeup.sh

Next I will put back the setwakeup.sh on the assumption that mythshutdown --safeshutdown would call the setwakeup.sh command.

Be REALLY nice if I could find some good documentation on what these commands & options actually do.

---

### Post by AKADAP on 2009-02-22
I have a clue!!!!!

I did 
```
sudo mythshutdown --safeshutdown -v all >mythlog

```
but that told me nothing because the shutdown was locked, so I did
```
mythshutdown --unlock
sudo mythshutdown --safeshutdown -v all >mythlog

```
The system shut down
I powered it back on and looked at the mythlog file:
```
2009-02-21 21:49:18.260 Using runtime prefix = /usr
2009-02-21 21:49:18.260 Empty LocalHostName.
2009-02-21 21:49:18.260 Using localhost value of Compromise
2009-02-21 21:49:18.261 MCP::DefaultUPnP() - No default UPnP backend
2009-02-21 21:49:18.265 New DB connection, total: 1
2009-02-21 21:49:18.269 Connected to database 'mythconverg' at host: localhost
2009-02-21 21:49:18.269 Closing DB connection named 'DBManager0'
2009-02-21 21:49:18.269 Clearing Settings Cache.
2009-02-21 21:49:18.269 Enabling Settings Cache.
2009-02-21 21:49:18.269 Clearing Settings Cache.
2009-02-21 21:49:18.269 Mythshutdown: --check
2009-02-21 21:49:18.269 Mythshutdown: --status
2009-02-21 21:49:18.312 isRecording: Attempting to connect to master server...
2009-02-21 21:49:18.313 Connected to database 'mythconverg' at host: localhost
2009-02-21 21:49:18.313 MSqlQuery: SELECT data FROM settings WHERE value = 'MasterServerIP' AND hostname = 'Compromise' ;
2009-02-21 21:49:18.313 MSqlQuery: SELECT data FROM settings WHERE value = 'MasterServerIP' AND hostname IS NULL;
2009-02-21 21:49:18.314 MSqlQuery: SELECT data FROM settings WHERE value = 'MasterServerPort' AND hostname = 'Compromise' ;
2009-02-21 21:49:18.314 MSqlQuery: SELECT data FROM settings WHERE value = 'MasterServerPort' AND hostname IS NULL;
2009-02-21 21:49:18.314 MythSocket(16a0260:4): new socket
2009-02-21 21:49:18.314 MSqlQuery: SELECT data FROM settings WHERE value = 'WOLbackendReconnectWaitTime' AND hostname = 'Compromise' ;
2009-02-21 21:49:18.314 MSqlQuery: SELECT data FROM settings WHERE value = 'WOLbackendReconnectWaitTime' AND hostname IS NULL;
2009-02-21 21:49:18.314 MSqlQuery: SELECT data FROM settings WHERE value = 'WOLbackendConnectRetry' AND hostname = 'Compromise' ;
2009-02-21 21:49:18.314 MSqlQuery: SELECT data FROM settings WHERE value = 'WOLbackendConnectRetry' AND hostname IS NULL;
2009-02-21 21:49:18.314 Connecting to backend server: 192.168.63.9:6543 (try 1 of 5)
2009-02-21 21:49:18.314 MythSocket(16a0fb0:5): new socket
2009-02-21 21:49:18.315 MythSocket(16a0fb0:5): attempting connect() to (192.168.63.9:6543)
2009-02-21 21:49:18.315 MythSocket(16a0fb0:5): state change Idle -> Connected
2009-02-21 21:49:18.315 write ->  5 21      MYTH_PROTO_VERSION 40
2009-02-21 21:49:18.315 read  <-  5 13      ACCEPT[]:[]40
2009-02-21 21:49:18.315 Using protocol version 40
2009-02-21 21:49:18.315 write ->  5 24      ANN Monitor Compromise 0
2009-02-21 21:49:18.321 read  <-  5 2       OK
2009-02-21 21:49:18.321 MythSocket(16a0260:4): attempting connect() to (192.168.63.9:6543)
2009-02-21 21:49:18.321 MythSocket(16a0260:4): state change Idle -> Connected
2009-02-21 21:49:18.321 write ->  4 24      ANN Monitor Compromise 1
2009-02-21 21:49:18.324 read  <-  4 2       OK
2009-02-21 21:49:18.324 MythSocket: readyread thread start
2009-02-21 21:49:18.324 MythSocket(16a0260:4): UpRef: 1
2009-02-21 21:49:18.324 MSqlQuery: SELECT cardid FROM capturecard ORDER BY cardid
2009-02-21 21:49:18.325 write ->  5 35      QUERY_REMOTEENCODER 1[]:[]GET_STATE
2009-02-21 21:49:18.325 read  <-  5 1       0
2009-02-21 21:49:18.325 write ->  5 35      QUERY_REMOTEENCODER 2[]:[]GET_STATE
2009-02-21 21:49:18.325 read  <-  5 1       0
2009-02-21 21:49:18.325 write ->  5 35      QUERY_REMOTEENCODER 3[]:[]GET_STATE
2009-02-21 21:49:18.325 read  <-  5 1       0
2009-02-21 21:49:18.325 write ->  5 35      QUERY_REMOTEENCODER 4[]:[]GET_STATE
2009-02-21 21:49:18.325 read  <-  5 1       0
2009-02-21 21:49:18.326 MSqlQuery: SELECT data FROM settings WHERE value = 'MythShutdownLock' AND hostname IS NULL;
2009-02-21 21:49:18.326 MSqlQuery: SELECT data FROM settings WHERE value = 'JobQueueWindowStart' AND hostname = 'Compromise' ;
2009-02-21 21:49:18.327 MSqlQuery: SELECT data FROM settings WHERE value = 'JobQueueWindowEnd' AND hostname = 'Compromise' ;
2009-02-21 21:49:18.327 JobQueue: Currently set to run new jobs from 00:00 to 23:59
2009-02-21 21:49:18.327 JobQueue: HasRunningOrPendingJobs: checking for jobs starting before: Sat Feb 21 22:04:18 2009
2009-02-21 21:49:18.327 New DB connection, total: 2
2009-02-21 21:49:18.327 Connected to database 'mythconverg' at host: localhost
2009-02-21 21:49:18.328 MSqlQuery: SELECT data FROM settings WHERE value = 'AutoCommflagWhileRecording' AND hostname = 'Compromise' ;
2009-02-21 21:49:18.328 MSqlQuery: SELECT data FROM settings WHERE value = 'AutoCommflagWhileRecording' AND hostname IS NULL;
2009-02-21 21:49:18.328 MSqlQuery: SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
2009-02-21 21:49:18.328 JobQueue: GetJobsInQueue: findJobs search bitmask 4, found 9 total jobs
2009-02-21 21:49:18.329 JobQueue: GetJobsInQueue: Ignore 'Flag Commercials' Job for 1051 @ 20090218170800 in Finished state.
2009-02-21 21:49:18.329 JobQueue: GetJobsInQueue: Ignore 'Flag Commercials' Job for 1071 @ 20090218195600 in Finished state.
2009-02-21 21:49:18.329 JobQueue: GetJobsInQueue: Ignore 'Flag Commercials' Job for 1051 @ 20090218215600 in Finished state.
2009-02-21 21:49:18.329 JobQueue: GetJobsInQueue: Ignore 'Flag Commercials' Job for 2051 @ 20090219205600 in Finished state.
2009-02-21 21:49:18.329 JobQueue: GetJobsInQueue: Ignore 'Flag Commercials' Job for 1953 @ 20090220094900 in Finished state.
2009-02-21 21:49:18.329 JobQueue: GetJobsInQueue: Ignore 'Flag Commercials' Job for 1953 @ 20090220095300 in Finished state.
2009-02-21 21:49:18.329 JobQueue: GetJobsInQueue: Ignore 'Flag Commercials' Job for 1953 @ 20090220115600 in Finished state.
2009-02-21 21:49:18.329 JobQueue: GetJobsInQueue: Ignore 'Flag Commercials' Job for 1953 @ 20090220163500 in Finished state.
2009-02-21 21:49:18.329 JobQueue: GetJobsInQueue: Ignore 'Flag Commercials' Job for 1953 @ 20090220164500 in Finished state.
2009-02-21 21:49:18.329 MSqlQuery: SELECT data FROM settings WHERE value = 'DailyWakeupStartPeriod1' AND hostname IS NULL;
2009-02-21 21:49:18.330 MSqlQuery: SELECT data FROM settings WHERE value = 'DailyWakeupEndPeriod1' AND hostname IS NULL;
2009-02-21 21:49:18.330 MSqlQuery: SELECT data FROM settings WHERE value = 'DailyWakeupStartPeriod2' AND hostname IS NULL;
2009-02-21 21:49:18.330 MSqlQuery: SELECT data FROM settings WHERE value = 'DailyWakeupEndPeriod2' AND hostname IS NULL;
2009-02-21 21:49:18.345 Mythshutdown: --status returned: 0
2009-02-21 21:49:18.345 OK to shutdown
2009-02-21 21:49:18.345 Mythshutdown: --check returned: 0
2009-02-21 21:49:18.345 write ->  5 19      QUERY_GETALLPENDING
2009-02-21 21:49:18.347 read  <-  5 10160   0[]:[]24[]:[]House (Manual Record)[]:[]Mon Feb 23 20:00:00 2009[]:[][]:[][]:[]2021[]:[]2.1[]:[]KTVU-DT[]:[]KTVU-DT[]:[][]:[]0[]:[]0[]:[]1235448000[]:[]1235451600[]:[]0[]:[]0[]:[]0[]:[]Compromise[]:[]2[]:[]4[]:[]4[]:[]0[]:[]-1[]:[]9[]:[]5[]:[]15[]:[]6[]:[]1235447880[]:[]1235451720[]:[]0[]:[]0[]:[]Default[]:[]0[]:[][]:[][]:[][]:[]1235281733[]:[]0.000000[]:[]1900-01-01[]:[]0[]:[]Default[]:[]0[]:[]0[]:[]Default[]:[]0[]:[]0[]:[]0[]:[]Chuck (Manual Record)[]:[]Mon Feb 23 20:00:00 2009[]:[][]:[][]:[]3081[]:[]8.1[]:[]KSBW-DT[]:[]KSBW-DT[]:[][]:[]0[]
...
lots & lots of scheduled events deleted for clarity
2009-02-21 21:49:18.348 setScheduledWakeupTime: At least one scheduled recording found.
2009-02-21 21:49:18.348 MSqlQuery: SELECT data FROM settings WHERE value = 'RecordPreRoll' AND hostname = 'Compromise' ;
2009-02-21 21:49:18.349 MSqlQuery: SELECT data FROM settings WHERE value = 'RecordPreRoll' AND hostname IS NULL;
2009-02-21 21:49:18.349 MSqlQuery: SELECT data FROM settings WHERE value = 'StartupSecsBeforeRecording' AND hostname = 'Compromise' ;
2009-02-21 21:49:18.349 MSqlQuery: SELECT data FROM settings WHERE value = 'StartupSecsBeforeRecording' AND hostname IS NULL;
2009-02-21 21:49:18.349 Mythshutdown: --setwakeup
2009-02-21 21:49:18.349 Mythshutdown: wakeup time given is: 2009-02-23T19:36:00
2009-02-21 21:49:18.350 MSqlQuery: DELETE FROM settings WHERE value = 'MythShutdownNextScheduled';
2009-02-21 21:49:18.350 MSqlQuery: INSERT INTO settings ( value, data ) VALUES ( 'MythShutdownNextScheduled', '2009-02-23T19:36:00' );
2009-02-21 21:49:18.350 Mythshutdown: --shutdown
2009-02-21 21:49:18.350 MSqlQuery: SELECT data FROM settings WHERE value = 'DailyWakeupStartPeriod1' AND hostname IS NULL;
2009-02-21 21:49:18.350 MSqlQuery: SELECT data FROM settings WHERE value = 'DailyWakeupEndPeriod1' AND hostname IS NULL;
2009-02-21 21:49:18.351 MSqlQuery: SELECT data FROM settings WHERE value = 'DailyWakeupStartPeriod2' AND hostname IS NULL;
2009-02-21 21:49:18.351 MSqlQuery: SELECT data FROM settings WHERE value = 'DailyWakeupEndPeriod2' AND hostname IS NULL;
2009-02-21 21:49:18.351 no daily wakeup times are set
2009-02-21 21:49:18.351 MSqlQuery: SELECT data FROM settings WHERE value = 'MythShutdownNextScheduled' AND hostname IS NULL;
2009-02-21 21:49:18.351 recording scheduled at: 2009-02-23T19:36:00
2009-02-21 21:49:18.352 will wake up at next scheduled program
2009-02-21 21:49:18.352 MSqlQuery: DELETE FROM settings WHERE value = 'MythShutdownWakeupTime';
2009-02-21 21:49:18.352 MSqlQuery: INSERT INTO settings ( value, data ) VALUES ( 'MythShutdownWakeupTime', '2009-02-23T19:36:00' );
2009-02-21 21:49:18.352 MSqlQuery: SELECT data FROM settings WHERE value = 'MythShutdownNvramRestartCmd' AND hostname = 'Compromise' ;
2009-02-21 21:49:18.353 MSqlQuery: SELECT data FROM settings WHERE value = 'MythShutdownNvramRestartCmd' AND hostname IS NULL;
2009-02-21 21:49:18.353 MSqlQuery: SELECT data FROM settings WHERE value = 'MythShutdownNvramCmd' AND hostname = 'Compromise' ;
2009-02-21 21:49:18.353 MSqlQuery: SELECT data FROM settings WHERE value = 'MythShutdownNvramCmd' AND hostname IS NULL;
2009-02-21 21:49:18.353 MSqlQuery: SELECT data FROM settings WHERE value = 'MythShutdownWakeupTimeFmt' AND hostname = 'Compromise' ;
2009-02-21 21:49:18.354 MSqlQuery: SELECT data FROM settings WHERE value = 'MythShutdownWakeupTimeFmt' AND hostname IS NULL;
2009-02-21 21:49:18.354 sending command to set time in bios
			/usr/bin/nvram-wakeup --settime 1235446560
2009-02-21 21:49:18.355 /usr/bin/nvram-wakeup --settime 1235446560 exited with code 127
2009-02-21 21:49:18.355 everything looks fine, shutting down ...
2009-02-21 21:49:18.356 MSqlQuery: SELECT data FROM settings WHERE value = 'MythShutdownPoweroff' AND hostname = 'Compromise' ;
2009-02-21 21:49:18.356 MSqlQuery: SELECT data FROM settings WHERE value = 'MythShutdownPoweroff' AND hostname IS NULL;
2009-02-21 21:49:18.356 ..
2009-02-21 21:49:18.356 .
2009-02-21 21:49:18.356 shutting down ...
2009-02-21 21:49:18.419 MythSocket(16a0fb0:5): DownRef: -1
2009-02-21 21:49:18.419 MythSocket(16a0fb0:5): state change Connected -> Idle
2009-02-21 21:49:18.419 MythSocket(16a0fb0:-1): delete socket
2009-02-21 21:49:18.419 MythSocket(16a0260:4): DownRef: 0
2009-02-21 21:49:18.419 MythSocket(16a0260:4): DownRef: -1
2009-02-21 21:49:18.420 MythSocket(16a0260:4): state change Connected -> Idle
2009-02-21 21:49:18.420 MythSocket(16a0260:-1): delete socket
2009-02-21 21:49:18.420 MythSocket: readyread thread exit
```
Its calling /usr/bin/nvram-wakeup! It is not even looking at the script I created. There is no nvram-wakeup on my system! nvram-wakeup does not even support the /sys/class/rtc/rtc0/wakealarm method that newer kernals use!
So, it looks like I have to rename my script to /usr/bin/nvram-wakeup and change the $1 to $2 so the correct parameter gets used.
What a bloody kludge:shock:](*,):evil:

---

### Post by AKADAP on 2009-02-22
Yes, this worked. Last night, for the first time my computer shut down, than woke at the proper time, recorded a show then shut down again.
I need to run a few experiments to answer a few questions and attempt to make my solution a little less kludgy before posting it.

---

### Post by AKADAP on 2009-02-22
My testing today has proven that in spite of some hints to the contrary, the mythshutdown --lock & mythshutdown --unlock properly implement a lock count, so I no longer have any worries about the method I used to prevent myth from turning off the computer when I am logged in.

Also I have determined that the reason that my previous attempts to get the computer to wake failed was because I did not have the "sh" command in the sudoers file.

A bit more testing is required to verify I have things right.

---

### Post by AKADAP on 2009-02-23
> **AKADAP said:**
> My testing today has proven that in spite of some hints to the contrary, the mythshutdown --lock & mythshutdown --unlock properly implement a lock count, so I no longer have any worries about the method I used to prevent myth from turning off the computer when I am logged in.

Also I have determined that the reason that my previous attempts to get the computer to wake failed was because I did not have the "sh" command in the sudoers file.

A bit more testing is required to verify I have things right.

](*,) Arghhhh!!! It may have nothing to do with the "sh" command! I have now found two typos in my sudoers file (a missing 'e' and a missing comma). When I finally get this working properly, I'll have to clean out a bunch of cruft from the sudoers file to get it down to the minimum required.

---

### Post by dannyboy79 on 2009-02-23
just curious, I wish to set this up some day to save electricity. I am curious, what if I want to turn my computer on to work on something else but a recording is coming up, what would happen. Also, do you have a PVR-150 or PVR-250 or PVR-350 in your mix? If so, what is your recordings hard drive specs, what CPU, what RAM etc etc. Thanks so much not trying to get off topic but I am getting ivtv0 error located here: [http://ubuntuforums.org/showthread.php?t=1074717](http://ubuntuforums.org/showthread.php?t=1074717)

---

### Post by AKADAP on 2009-02-23
> **dannyboy79 said:**
> just curious, I wish to set this up some day to save electricity. I am curious, what if I want to turn my computer on to work on something else but a recording is coming up, what would happen. Also, do you have a PVR-150 or PVR-250 or PVR-350 in your mix? If so, what is your recordings hard drive specs, what CPU, what RAM etc etc. Thanks so much not trying to get off topic but I am getting ivtv0 error located here: [http://ubuntuforums.org/showthread.php?t=1074717](http://ubuntuforums.org/showthread.php?t=1074717)

I have two HDHomeRun boxes, two of the inputs go to antennas, two of them go to cable. (the only reason I have cable is that it made my internet connection cheaper).
The computer is an intel i7 processor on an Asus P6T Delux motherboard, 6GB ram and a seagate 1.5 Tb drive. I had intended to run the backend on an via Epia M6000 motherboard, but I have been unable to get any version of linux that will run on that.

The setup I am attempting, is to have the system auto boot when it needs to record, and shut itself down when sitting at the login screen when it has nothing to do. If I need to use the computer for other things, I just turn it on (if it is not already on) and login. Myth will still run & record in the background, but if I am logged in, it will not shut down. When I am done, I log out and myth will shut it down when it is idle.

I do not have a PVR-Anything. I do have an ATI HDTV wonder that I have not yet installed that was given to me by a friend who was totally disgusted with the quality of the software and drivers provided by ATI for Windows.

I don't know anything about the error you are getting. I have no need nor intention of recording analog TV. Everything I am recording is precompressed digital data, so all the backend needs to do is stream it to disk. This is why I thought I could get away with that via motherboard as a backend. Probably could have if I could have gotten Linux installed on it.

---

### Post by AKADAP on 2009-02-24
I now have this working and will attempt to summarize. Apparently, I am not allowed to mark this thread as solved.

A script is necessary to set the SRAM Power on clock.
I was attempting to follow this wiki article [http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup), so I named my script /usr/bin/setwakeup.sh It contains:
```
#!/bin/sh
#$1 is the first argument to the script. It is the time in seconds since 1970
#this is defined in mythtv-setup with the time_t argument
#This must be run as superuser

echo about to clear wake time
echo 0 > /sys/class/rtc/rtc0/wakealarm      #this clears your alarm.
echo about to set wake time to $1
echo $1 > /sys/class/rtc/rtc0/wakealarm     #this writes your alarm
echo wake time should be set
exit 0
```
To create this file you will probably have to run your editor with sudo so the file is owned by root.
Once you create this file you must change its permissions to make it executable:
```
sudo chmod +x /usr/bin/setwakeup.sh
```

The extra echo commands (first, third, and fifth echo lines) can be deleted once you have finished debugging your setup, but they are useful to tell if the script is actually being run since this text shows up in /var/log/mythtv/mythbackend.log.
A useful tool for monitoring the log in Ubuntu is System>Administration>System Log. Use File>open to open the log file and it will continuously update to show new messages that appear in the log.

To keep mythTV from shutting down your system when you are logged in and using the computer for other purposes, we must add the following lines to the following files:
To /etc/gdm/PreSession/Default add the following lines just before "exit 0" in the file.```
#Prevent MythTV from shutting down the system when you are logged in.
mythshutdown --lock
```To /etc/gdm/PostSession/Default add the following lines just before "exit 0" in the file.```
#Allow MythTV to automatically shut the system down.
mythshutdown --unlock
```

With this setup, you will power up the computer and login exactly the way you do now to use the computer, but rather than selecting shutdown when you are done, you instead select logout and leave it at the login prompt. If Myth has nothing to do, it will shut the computer off from the login prompt after a short delay.

Before we set up the Myth back end, we need to give the myth user permission to do some sudo commands without needing a password, so in a terminal run:```
sudo visudo
```
then type in your password.
Add the following line at the end of the file.
```
%mythtv ALL = NOPASSWD: /sbin/shutdown, /bin/sh, /usr/bin/setwakeup.sh
```
Save the file (default editor in Ubuntu uses ctl-o to save)
and exit the editor (default editor in Ubunto uses ctl-x to exit)
It might be necessary to reboot the computer to activate this change.

Now run System>Administration>MythTV Backend Setup
Click OK to close down mythbackend
type in your password
Select General
Select next
Select next
Select next
You should now be at the "Shutdown/Wakeup Options" page.

Startup command: should be blank

Block shutdown before client connected: should be unchecked.

Idle shutdown timeout (secs): must be nonzero to enable Myth to shut down the system. Also this is the number of seconds you will have to type in your username and password during login so don't set it too short! I have mine set to 180 to give me 3 minutes to login. Note that for some reason Myth will quite often reset the shutdown timer even though it is idle (you can watch this happening in the log file), so it might actually take quite a bit longer than the time specified here before MythTV shuts down the computer. This number should be viewed as a minimum.

Max. wait for recording (min): This will prevent MythTV from shutting down the computer if a recording is scheduled less than the specified number of minutes from the current time. This should be longer than the "Startup before rec." time to prevent Myth from shutting off the computer between the time Myth powered on the computer and the time the recording begins. (Myth may be idiot proof here, but I'm paranoid and did not want to take the time to test this) I have mine set to 60.

Startup before rec. (secs): This is how many seconds before the scheduled time the computer will be powered up. No computer powers up instantly, so this makes sure that the computer is powered on and ready so it does not miss the beginning of the show you wish to record. If you are using your system as a desktop and still have the system check the hard disk every N boots, you wish to time how long it takes to boot when doing the disk check and make sure this time is longer than a disk check boot. Otherwise you could cut off the beginning of your recording. On my system, a diskcheck boot takes 16 minutes, so I have this set to the maximum of 1200 seconds (20 minutes).

Wakeup time format: This is the format that time is put into when it is sent to the script that sets the wakeup time in the SRAM. For recient kernels, this needs to be "time_t".
Command to set Wakeup Time: This is the command that needs to execute to set the wakeup time. On my system I have:```
sudo sh -c "/usr/bin/setwakeup.sh $time"
```sudo because it must be done as root, sh because "echo" is a built in shell command, so to get it to run as root, the shell must be running as root.

Server halt command: This is the command that MythTV uses to shut down the computer. You may be tempted to use "mythshutdown --safeshutdown" (or another mythshutdown option) if you look at what "mythshutdown --help" has to say, but don't do it. mythshutdown is intended to be used in user scripts, and much of what it does is redundant here. Worse, the way mythshutdown tries to set the NVRAM wakeup alarm is obsolete. It is hardwired to call /usr/bin/nvram-wakeup which is probably not installed on your computer. But don't go install that because the stuff I read about this implies that it uses a method of setting the NVRAM that is no longer supported and will not work! You can get it to work by making your own nvram-wakeup script, but I'm not going there. 
For this use the standard Linux shudown:```
sudo shutdown -h now
```

Pre Shutdown check-command: This is the command MythTV uses to determine if there is anything (other than stuff it knows about) that should prevent it from shutting down. I used ```
mythshutdown --check
``` [SIZE="1"][COLOR="Red"]It may be possible to leave this blank since the mythbackend may not even call this until the lock count goes to zero, but again I was too lazy to test this.[/COLOR][/SIZE] (I wanted to use strikeout on this text (line through center of text) but that does not seem to be an option on this forum). I went and tested this. This command is necessary, otherwise MythTV ignores the "mythshutdown --lock" lock count.

Select next a bunch of times to finish the setup
hit esc to exit the menu
hit ok to exit the aplication
close the terminal window it leaves up
click on ok to run myth fill data base.
and hope everything works. If it doesn't look at the log files, that is where I finally got a clue as to what was going on.
Many thanks to others who posted in this thread who helped me get this together.

I'm going to go watch some TV.

PS I did "Disable hwclock updates" like the wiki suggests, but I'm not sure it does anything. The "HWCLOCKACCESS=no" line added to the /etc/default/rcS file is not documented as an available option in the man page for rcS.

---

### Post by AKADAP on 2009-02-25
Additional notes:
Something attached to the UPnP server and transferring data will NOT prevent MythTV from shutting down the system.

---

### Post by dannyboy79 on 2009-02-25
if there's a mythtv frontend being used in another room and watching recordings from the backend, that would prevent mythtv backend from shutting down wouldn't it? I use my xbox with xbmcmythtv installed on it so it is accessing the mythtv database etc etc. I wonder if you could also throw something in this whole thing such that some program or code could parse the command "ps aux" and see if /usr/bin/btdownloadgui.py is running and if so, that would also prevent the computer from being shut down. Or any torrent program for example. that would be really awesome then.

---

### Post by AKADAP on 2009-02-25
> **dannyboy79 said:**
> if there's a mythtv frontend being used in another room and watching recordings from the backend, that would prevent mythtv backend from shutting down wouldn't it? I use my xbox with xbmcmythtv installed on it so it is accessing the mythtv database etc etc. I wonder if you could also throw something in this whole thing such that some program or code could parse the command "ps aux" and see if /usr/bin/btdownloadgui.py is running and if so, that would also prevent the computer from being shut down. Or any torrent program for example. that would be really awesome then.
I currently only have one myth box, but I believe an external front end would prevent the system from shutting down. You would however need to implement the wake on lan feature so that the external front end could power up the backend when it was off.

If you can figure out a way of identifying that some process is running, you can modify the "Pre Shutdown check-command:" script to prevent  myth from shutting down. 
But perhaps it would be easier to modify the task itself by putting a "mythshutdown --lock" at the beginning of it and "mythshutdown --unlock" when the task completes.

---

### Post by AKADAP on 2009-02-27
This is incomplete and out of date, but it would have been nice to have found it earlier:
[http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend)

---

### Post by AKADAP on 2009-03-15
Bad news.
I don't think the mythshutdown --lock method works reliably.

I don't believe that the lock count gets cleared when the computer reboots, and I don't believe that the scripts in "/etc/gdm/PostSession/Default" always get called when they should.

I was out of town for a week, and I don't believe my computer shut off at all in that period.
I found I had to call mythshutdown --unlock 3 times before mythshutdown --check would return zero. That means there were two extra locks that should not have been there.
There had been a power outage that forced my computer to reboot, and I had manually rebooted once in the meantime. which I think accounted for the two extra locks. Both of which would have bypassed the script that should have called mythshutdown --unlock.

I need to come up with a different solution to prevent shutdown when I am logged in.

What commands are available to see who is logged into a particular machine?

---

### Post by 4dognight on 2009-03-15
try the command 'last'
It will show if someone is still logged in.

---

### Post by AKADAP on 2009-03-15
> **4dognight said:**
> try the command 'last'
It will show if someone is still logged in.

I threw together this script:```
if
last | grep "still logged in"
then
echo Someone is still logged in! Don\'t shut down!
exit 1
else
echo Noone is logged in, ok to shut down.
exit 0
fi
```

This seems to work with manual testing, I'll try it as a replacement for what I currently have.

---

### Post by AKADAP on 2009-03-16
Yes that new script is working. Now I just need to patch up that wiki.

---

### Post by AKADAP on 2009-06-01
> **AKADAP said:**
> I threw together this script:```
if
last | grep "still logged in"
then
echo Someone is still logged in! Don\'t shut down!
exit 1
else
echo Noone is logged in, ok to shut down.
exit 0
fi
```

This seems to work with manual testing, I'll try it as a replacement for what I currently have.

This script failed for the first time today. I'm not sure how yet, but for some reason it thought no one was logged in when I was logged in and using Firefox. It shut down the computer, and looking in the logs it had printed the "Noone is logged in, ok to shut down." message.

---

### Post by Caps18 on 2009-06-03
This is a feature I would like to see implemented.  My computer would only need to be on for a few hours a day instead of 24/7.  It would save me a lot in electricity and wear and tear on components.

If I could turn on the computer from the remote and turn it off from the remote when done, (and it would look at when the next scheduled recording was to know when to turn on next(or would turn on to download the TV guide every other day)).

This sounds like a cool feature.  Maybe I will look at implementing it on my Mythbuntu machine.

---

### Post by AKADAP on 2009-06-03
> **Caps18 said:**
> This is a feature I would like to see implemented.  My computer would only need to be on for a few hours a day instead of 24/7.  It would save me a lot in electricity and wear and tear on components.

If I could turn on the computer from the remote and turn it off from the remote when done, (and it would look at when the next scheduled recording was to know when to turn on next(or would turn on to download the TV guide every other day)).

This sounds like a cool feature.  Maybe I will look at implementing it on my Mythbuntu machine.

With what I have set up, I never explicitly turn off my computer, merely log out. My being logged out gives mythTV permission to shut down the computer if it has nothing to do. It will automatically turn on the computer for recordings, or I can turn it on and use it without affecting recordings.

I use my computer primarily as a desk top and do not have a remote control for it.

The only difficulty I see with what you want is how to get the computer to turn on with the remote. I think most of what you want is handled by mythwelcome.

---

### Post by 4dognight on 2009-06-04
> **AKADAP said:**
> 

The only difficulty I see with what you want is how to get the computer to turn on with the remote. .

I had it set to wake up from USB in my BIOS. My remote is connected via a usb port. SO when I pressed a button on the remote, it would wake the server.

---

### Post by Caps18 on 2009-06-04
Is there a way to map a remote key to be able to shut down the computer?

---

### Post by AKADAP on 2009-06-05
> **Caps18 said:**
> Is there a way to map a remote key to be able to shut down the computer?

I think what you really want is a remote key to exit mythTV front end, and let the back end decide when to shut down the computer. Otherwise you could interrupt recordings.

Unless of course your machine is a front end only box.

---

### Post by AKADAP on 2009-07-01
> **AKADAP said:**
> This script failed for the first time today. I'm not sure how yet, but for some reason it thought no one was logged in when I was logged in and using Firefox. It shut down the computer, and looking in the logs it had printed the "Noone is logged in, ok to shut down." message.

This script failed again today. Here is the log:
```
2009-07-01 10:40:34.619 I'm idle now... shutdown will occur in 180 seconds.
2009-07-01 10:42:32.085 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
User   tty7         :0               Wed Jul  1 10:26   still logged in   
Someone is still logged in! Don't shut down!
2009-07-01 10:43:35.676 I'm idle now... shutdown will occur in 180 seconds.
User   tty7         :0               Wed Jul  1 10:26   still logged in   
Someone is still logged in! Don't shut down!
2009-07-01 10:46:36.705 I'm idle now... shutdown will occur in 180 seconds.
User   tty7         :0               Wed Jul  1 10:26   still logged in   
Someone is still logged in! Don't shut down!
2009-07-01 10:49:37.737 I'm idle now... shutdown will occur in 180 seconds.
User   tty7         :0               Wed Jul  1 10:26   still logged in   
Someone is still logged in! Don't shut down!
2009-07-01 10:52:38.778 I'm idle now... shutdown will occur in 180 seconds.
Noone is logged in, ok to shut down.
2009-07-01 10:55:37.805 CheckShutdownServer returned - OK to shutdown
2009-07-01 10:55:37.811 Running the command to set the next scheduled wakeup time :-
						sudo sh -c "/usr/bin/setwakeup.sh 1246509480"
about to clear wake time
about to set wake time to 1246509480
wake time should be set
2009-07-01 10:55:37.869 Running the command to shutdown this computer :-
						sudo shutdown -h now
```

It looks like either the last command failed, or the grep command failed, I can't determine which.

I have modified my script such that if it thinks no one is logged in it will run the test test again before exiting. as well as echoing the results of the last command and the grep command separately so I can identify the culprit.

---

### Post by AKADAP on 2009-10-13
I don't know if the latest failure I had is the same as the previous one, but at least this one I understand.
The shutdown script failed on my first login on October 1st. This is because Ubuntu deletes the file used by last once a month. It does this after you log in, so the line in the file that says "still logged in" is not there, so grep does not find it and allows the system to shut down.

I have modified my script to use the "w" command instead and allow shutdown only when it sees " 0 user" (the leading space is important, or it would shut down on "10 users").
```
w >/tmp/tmplast
cat /tmp/tmplast
if 
# The leading space is important!
  grep " 0 user" /tmp/tmplast
  then
    echo Noone is logged in, ok to shut down.
    exit 0
  else
    echo Someone is still logged in, don\'t shut down! 
    exit 1
fi

```

---

### Post by AKADAP on 2009-10-13
I updated the wiki with a slightly modified version of the script (less debugging info).

---

