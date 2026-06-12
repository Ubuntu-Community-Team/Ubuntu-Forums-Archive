---
title: "How to combine ACPI wakeup &amp; shutdown/startup scripts"
date: 2009-02-17
forum: Mythbuntu
---

### Post by laffinet on 2009-02-17
Okay, I finally managed to get my shutdown/startup scripts ([here]("http://ubuntuforums.org/showthread.php?t=1067485")) working and I'm thinking of changing/improving things.

So here's what I got at the moment:

The scripts shut down my Mythbox at certain times during the day (based on when I'm not home or asleep) and start it back up again at certain times (to be ready when I wake up, get home etc.)

Unfortunately I do sometimes have recordings scheduled outside the "waking hours" of my system. How do I make the system 
a) stay on
*or*
b) come back on in time 
if that's the case.

I was thinking a combination of my scripts and the Mythbuntu option to write a wakeup time for upcoming recordings to the bios ([here]("http://www.mythtv.org/wiki/ACPI_Wakeup#Integrate_into_mythTV_2"))  but wouldn't know how.

I could forget about my scripts and use the acpi wakeup setup only, however the machine then doesn't turn on automatically at the fixed times set by me.

Any ideas will be much appreciated !

---

### Post by prudentius on 2009-02-21
Hey laffinet,

I recently did something (I think) similar on my mythbox. I wanted to have it startup at certain times (when I come home from work and on the weekends) and shutdown when/after I'm usually going to sleep. Moreover, it should wakeup for scheduled recordings and shutdown afterwards again.

It seems that mythbackend does not become idle as long as a frontend is connected. You might want to keep that in mind when running front- and backend on the same machine...

Here is what I did (combining ideas from the [[link]]("http://www.mythtv.org/wiki/ACPI_Wakeup#Integrate_into_mythTV_2") you mentioned and [[this]]("https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake") I also found).

If you run mythtv-setup (or start MCC and then LauchMythTV setup) under '1. General' on page 5 (Shutdown/Wakeup Options) you want to make some adjustments:

- Set wakeuptime command: Make sure the machine starts up for next recording time (make sure the Wakeup time format is set to time_t):
```

#!/bin/sh
# MythSetWakeup

echo 0 > /sys/class/rtc/rtc0/wakealarm
echo $1 > /sys/class/rtc/rtc0/wakealarm

```


- Server Halt Command: Note that if there is no recording scheduled then myth won't write anything to ../wakealarm. So when shutting down we check first if there is already a programmed wakeup time and whether the next generic wakeup is earlier.

```

#!/bin/sh
# Shutdown the Mythbox

# wake-up time for scheduled recording
WUP=$(cat /sys/class/rtc/rtc0/wakealarm)

# generic wake-up time
#   Mo-Fr @ 6pm, Sa-Su @ 9am
if [ $(date +%u) -le 5 ]; then
   GWU=$(date -d '18:00' +%s)
else
   GWU=$(date -d '09:00' +%s)
fi

# if there is no scheduled recording or
#   next generic wake-up is earlier
#   then set to that time
if [ -z $WUP ] || [ $GWU -lt $WUP ] ; then
   echo 0 > /sys/class/rtc/rtc0/wakealarm
   echo $GWU > /sys/class/rtc/rtc0/wakealarm
fi

mythshutdown -q

```

A quick remark: there is an option 'mythshutdown -l' and 'mythshutdown -u' to lock/unlock mythbackend not letting it shutdown. This should make the next script obsolete, however, I couldn't get it to work...


- Pre Shutdown check-command: (whenever I'm home or on weekends the backend should NOT shutdown, even when idle. See 'man date' for more info)
```

#!/bin/sh
# Check generic running time to shutdown

DAY=$(date +%u)
HOUR=$(date +%k)

if [ $DAY -le 5 ] && [ 1 -le $HOUR ] && [ $HOUR -lt 18 ]; then
   exit 0
elif [ $DAY -ge 6 ] && [ 3 -le $HOUR ] && [ $HOUR -lt 9 ]; then
   exit 0
else
   exit 1
fi

```
This makes sure from Mo-Fr the machine will shutdown between 1am and 6pm, and on weekends between 3am and 9am.

Then make sure mythtv is able to execute this commands by editing 'sudo visudo' accordingly.

---

Recall that you have to stop mythfrontend to have your box shutdown on its own. I still use the remote to manually start/stop mythfrontend at the same time enabling/disabling the screensaver; but you can write a script that stops at certain times.

Hope that helps! Best,
pru

PS: Please, be gentle with critisism I am rather new to being root on linux ;)

---

### Post by laffinet on 2009-02-21
First of all: thanks a lot, this is awesome. This is exactly the same thing I want to achieve (apart from slightly different times and I would like it to wake up 6.30am on weekdays and shut down between say 8am and 4pm on weekdays as well, but once I figured out what your scripts are doing I should be able to modify accordingly).

Some questions though:

1. I'm assuming that you gave these scripts some useful names and then call them up via the "shutdown/wakeup options". Correct ?

2. I'm no expert on scripts, can you provide some more explanation on what some of the stuff is doing. I hope I'm not asking too much, I'm trying to learn so hopefully in the future I won't have to ask too many stupid questions. I also like to know what I'm doing with my machine ;)

a)  ```
if [ $(date +%u) -le 5 ]; then

```

This is obviously checking for weekday. How ? I couldn't find anything on %u (lowercase?). And what is the -le 5 doing ?

b) ```
if [ -z $WUP ] || [ $GWU -lt $WUP ]
```

Way beyond me :D Can you explain a bit ?

c) ```
if [ $DAY -le 5 ] && [ 1 -le $HOUR ] && [ $HOUR -lt 18 ]; then
   exit 0
elif [ $DAY -ge 6 ] && [ 3 -le $HOUR ] && [ $HOUR -lt 9 ]; then
   exit 0
else
   exit 1

```

Again, way beyond my script knowledge. Some explanation would be great.

> **prudentius said:**
> 
Then make sure mythtv is able to execute this commands by editing 'sudo visudo' accordingly.


Can you provide some detail ?

> **prudentius said:**
> 
PS: Please, be gentle with critisism I am rather new to being root on linux ;)

Are you kidding ? This is great !!!

---

### Post by prudentius on 2009-02-22
Hey laffinet,

cool you like the ideas - feels great to be not alone there with all these adjustments ;) Sorry for the long delay in answering, I totally forgot to subscribe to the thread to get a notification (done now).

Alright, back to business. First, you are right I totally forgot about the names for the scripts: The first one (see Set wakeuptime command) is called MythSetWakeup, the next one (see Server Halt Command) is called MythShutdown, and the last one (see Pre Shutdown check-command) is called MythShutdownCheck. I will refer to those later.

Now let's see in more detail what I did with the above mentioned scripts.

> 
a) 
```

if [ $(date +%u) -le 5 ]; then

```
This is obviously checking for weekday. How ? I couldn't find anything on %u (lowercase?). And what is the -le 5 doing ?


You are right, this checks the weekday. '$date +%u' returns a number between 1 and 7: Monday -> 1, Tuesday -> 2, ..., Sunday -> 7. (If you prefer you can it also have return values between 0 and 6, where 0 is Sunday, 1 is Monday ... by '$date +%w')

(Make sure the + is there ... $date %u doesn't work)

The '-le 5' just checks whether the returned value is LessEqual to 5, i.e. for Monday-Friday the if statement is true.

> 
b) 
```

if [ -z $WUP ] || [ $GWU -lt $WUP ]

```
Way beyond me  Can you explain a bit ?


OK, this is probably because I didn't really had nice names ready for the variables ;) If you look at the script again (MythShutdown) in the beginning I first check if there is a recording
```

# wake-up time for scheduled recording
WUP=$(cat /sys/class/rtc/rtc0/wakealarm)

```
and if so the time for the recording is saved to the variable WUP. If there is none, then this variable is just empty.

Then I define the generic wakup times
```

# generic wake-up time
#   Mo-Fr @ 6pm, Sa-Su @ 9am
if [ $(date +%u) -le 5 ]; then
   GWU=$(date -d '18:00' +%s)
else
   GWU=$(date -d '09:00' +%s)
fi

```
Here the variable GWU gets set to 6pm on weekdays, and to 9am on saturday sunday. Adjust them to what you need.

Now
```

if [ -z $WUP ] || [ $GWU -lt $WUP ]

```
does the following: first it checks whether WUP is empty (i.e. there is no upcoming recording) in which case the next wakeup should be at 6pm/9am.
Then there is '||' which stands for a logical 'OR' because if WUP is not empty (so there is some recording scheduled) it might still be that the recording should take place AFTER the next generic wakeup (for instance on the day after tomorrow). Still I want to have the machine come back on tonight...
In either case the generic wakeup time GWU has to be set in the wakealarm...

> 
c) 

```

if [ $DAY -le 5 ] && [ 1 -le $HOUR ] && [ $HOUR -lt 18 ]; then
   exit 0
elif [ $DAY -ge 6 ] && [ 3 -le $HOUR ] && [ $HOUR -lt 9 ]; then
   exit 0
else
   exit 1

```
Again, way beyond my script knowledge. Some explanation would be great.


OK, so as I said, I'm using the idle of mythbackend to shutdown the system. BUT you don't want the box to shutdown at 6.10pm just because after starting at 6pm and you came home at 7 it was idle after 10 minutes. However, if the machine comes up during day or in the middle of the night just for a recording you want it to shutdown after xx minutes of being idle.

So somehow we have to tell myth at certain times it's ok to shutdown, and at some times it's not (you could also supposedly do this with 'mythshutdown -l / -u' but I couldn't get that to work). The other possibilty would be to use a cron to shut the box down at certain times (other than going down because the machine is idle)...

I use the idle shutdown, and the script above tells myth that
```

if [ $DAY -le 5 ] && [ 1 -le $HOUR ] && [ $HOUR -lt 18 ]; then
   exit 0

```
on Monday-Friday, between 1am and before 6pm it's ok to shutdown (exit 0) and similarly for Saturday-Sunday. In any other case, exit 1 will prevent myth from shutting down. (Note that here -lt means LessThan when adapting for your needs.)


> 
[QUOTE] Originally Posted by prudentius  
Then make sure mythtv is able to execute this commands by editing 'sudo visudo' accordingly.


Can you provide some detail ?
[/QUOTE]

Save the scripts somewhere (say /usr/bin), make them executable (sudo chmod +x *scriptname*), and finally run sudo visudo and put the following line there (so myth can run the scripts without using a password):
%mythtv ALL = NOPASSWD: /usr/bin/MythSetWakeup, /usr/bin/MythShutdown, /usr/bin/MythShutdownCheck

I hope this will get your machine to what it should be doing ;)
Best,
   pru

---

### Post by laffinet on 2009-02-22
Hey pru,

thanks a lot for taking the time and explaining everything to me. Helped me a lot !

I've modified the scripts to suit my needs. Haven't had time to test it yet, will probably be another week or so. Might try running them with 

```
#!/bin/bash -x
```

to see what information that gives me.

Anyway, here we go:

MythShutdown
```
#!/bin/sh
# Shutdown the Mythbox

DAY=$(date +%u)
HOUR=$(date +%k)
MINUTE=$(date +%M)

# wake-up time for scheduled recording
WUP=$(cat /sys/class/rtc/rtc0/wakealarm)


# generic wake-up time
#   Mo-Fr @ 6am & 4pm, Sa-Su @ 8am
if [ $DAY -le 5 ] && [ $HOUR -le 16 ] && [ $HOUR -ge 6 ];then
	GWU=$(date -d '16:00' +%s)
elif [ $DAY -le 4 ] || [[ $DAY -eq 7 ] && [ $HOUR -ge 6 ]];then
	GWU=$(date -d '06:00' +%s)
else
	GWU=$(date -d '08:00' +%s)
fi

# if there is no scheduled recording or
#   next generic wake-up is earlier
#   then set to that time
if [ -z $WUP ] || [ $GWU -lt $WUP ] ; then
   echo 0 > /sys/class/rtc/rtc0/wakealarm
   echo $GWU > /sys/class/rtc/rtc0/wakealarm
fi

mythshutdown -q
```

This should set the following wake up times:
Mon-Fri 6.00
Mon-Fri 16.00
Sat-Sun 8.00
OR recording time

MythShutdownCheck
```
#!/bin/sh
# Check generic running time to shutdown

DAY=$(date +%u)
HOUR=$(date +%k)

if [ $DAY -le 5 ] && [ $HOUR -ge 8 ] && [ $HOUR -lt 16 ]; then
   exit 0
elif [ $DAY -le 5 ] && [ $HOUR -ge 0 ] && [ $HOUR -lt 6 ]; then
   exit 0
elif [ $DAY -ge 6 ] && [ $HOUR -lt 8 ]; then
   exit 0
else
   exit 1
fi
```
Mon-Fri 0.00-6.00 ok to shutdown
Mon-Fri 8.00-16.00 ok to shutdown
Sat-Sun 0.00-8.00 ok to shutdown

Hopefully this accomplishest that the machine will be on automatically:
Mon-Fri 6.00-8.00 & 16.00-24.00
Sat-Sun 8.00-24.00

Shut down should not be permitted during these times. Machine will come on for recordings outside these times.

---

### Post by laffinet on 2009-02-23
> **prudentius said:**
> 
Recall that you have to stop mythfrontend to have your box shutdown on its own. I still use the remote to manually start/stop mythfrontend at the same time enabling/disabling the screensaver; but you can write a script that stops at certain times.


Small addition: I found that I probably get away with

```
pkill mythfront
```

in a cronjob set to the right times.

However, what if the machine came up for a recording (outside the usual "waking hours") ? Frontend will be running, cron won't shut it down (because it's not the right time), therefore the machine won't shut down again. Or am I missing something ?

---

### Post by prudentius on 2009-02-23
Hey laffinet,

so after reading through the scripts I have a few remarks:
In MythShutdown:
> ```

#!/bin/sh
# Shutdown the Mythbox

DAY=$(date +%u)
HOUR=$(date +%k)
MINUTE=$(date +%M)

```

You don't use the variable MINUTE later (so far).

> ```

# generic wake-up time
#   Mo-Fr @ 6am & 4pm, Sa-Su @ 8am
if [ $DAY -le 5 ] && [ $HOUR -le 16 ] && [ $HOUR -ge 6 ];then
	GWU=$(date -d '16:00' +%s)
elif [ $DAY -le 4 ] || [[ $DAY -eq 7 ] && [ $HOUR -ge 6 ]];then
	GWU=$(date -d '06:00' +%s)
else
	GWU=$(date -d '08:00' +%s)
fi

```
I am afraid this won't do exactly what you want. Note that " date -d '...' " sets the current date to whatever specified by '...' For instance if "date" returns 'Mon Feb 23 11:13:22 CET 2009' then " date -d '16:00' gives 'Mon Feb 23 16:00:00 CET 2009'. You can also use this with " date -d '+5 minutes' " which returns the current time plus 5 minutes ;)
What I want to say is that, for Monday 4:23pm (i.e. DAY=1 HOUR=16) the first if is true but you set the wakeup time to 4pm...

In that sense you also might want to be careful with shutting down at midnight. It should be fine, since when the shutdown is done it's PAST midnight, so " date -d '...' " will actually set it to some time in the future... Just watch out for this one ;) Also something not to forget I don't know whether you use a 24h or 12h (am/pm) clock...

```

# generic wake-up time
#   Mo-Fr @ 6am & 4pm, Sa-Su @ 8am
if [ $DAY -le 5 ] && [ $HOUR -lt 6 ]; then
	GWU=$(date -d '06:00' +%s)
elif [ $DAY -le 5 ] && [ [ $HOUR -ge 8 ] && [ $HOUR -lt 16 ] ];then
	GWU=$(date -d '16:00' +%s)
else
	GWU=$(date -d '08:00' +%s)
fi

```
This should do the trick, as long as your machine does NOT go down (by idle shutdown ;)) before midnight...

---

Let's see about MythShutdownCheck (yours is fine, I just adapted it timewise to te previous script):
```

#!/bin/sh
# Check generic running time to shutdown

DAY=$(date +%u)
HOUR=$(date +%k)

if [ $DAY -le 5 ] && [ $HOUR -lt 6 ]; then
   exit 0
elif [ $DAY -le 5 ] && [ $HOUR -ge 8 ] && [ $HOUR -lt 16 ]; then
   exit 0
elif [ $DAY -ge 6 ] && [ $HOUR -lt 8 ]; then
   exit 0
else
   exit 1
fi

```
Right now I don't see a reason why this shouldn't work if permissions are set correctly and the wakeup/shutdown options are fine in mythtv-setup...

Note that it will break if you're unlucky enough that a recording stops, say, on Monday at 15:49 and after 10(?) minutes idle the system decides to shut down at 15:59 and sets the wakeup time to 16:00. In this case, the system might not be fast enough to shutdown in time... ;) But how often will that happen :D


> 
However, what if the machine came up for a recording (outside the usual "waking hours") ? Frontend will be running

Exactly, that's why I don't autostart the frontent but use the remote to start. As far as recordings are concerned you don't need the frontend to be running to record (just the backend running is enough).

Best,
pru

---

### Post by laffinet on 2009-02-23
> **prudentius said:**
> 
You don't use the variable MINUTE later (so far).


Forgot to delete that, was planning to use minutes but didn't in the end (for startup times like 6.20am etc.)

> **prudentius said:**
> 

Quote:
Code:

# generic wake-up time
#   Mo-Fr @ 6am & 4pm, Sa-Su @ 8am
if [ $DAY -le 5 ] && [ $HOUR -le 16 ] && [ $HOUR -ge 6 ];then
	GWU=$(date -d '16:00' +%s)
elif [ $DAY -le 4 ] || [[ $DAY -eq 7 ] && [ $HOUR -ge 6 ]];then
	GWU=$(date -d '06:00' +%s)
else
	GWU=$(date -d '08:00' +%s)
fi

I am afraid this won't do exactly what you want. Note that " date -d '...' " sets the current date to whatever specified by '...' For instance if "date" returns 'Mon Feb 23 11:13:22 CET 2009' then " date -d '16:00' gives 'Mon Feb 23 16:00:00 CET 2009'. You can also use this with " date -d '+5 minutes' " which returns the current time plus 5 minutes
What I want to say is that, for Monday 4:23pm (i.e. DAY=1 HOUR=16) the first if is true but you set the wakeup time to 4pm...


I'm afraid I don't get it :(
Are you saying the wake up time will be set to the wrong date ?

> **prudentius said:**
> 
What I want to say is that, for Monday 4:23pm (i.e. DAY=1 HOUR=16) the first if is true but you set the wakeup time to 4pm...

OK, so if I change it to (note the -lt instead of -le in the first if):
```
# generic wake-up time
#   Mo-Fr @ 6am & 4pm, Sa-Su @ 8am
if [ $DAY -le 5 ] && [ $HOUR -lt 16 ] && [ $HOUR -ge 6 ];then
	GWU=$(date -d '16:00' +%s)
elif [ $DAY -le 4 ] || [[ $DAY -eq 7 ] && [ $HOUR -ge 6 ]];then
	GWU=$(date -d '06:00' +%s)
else
	GWU=$(date -d '08:00' +%s)
fi

```
it should work, shouldn't it ?
Note: I had that extra elif in there so it sets the wake up to 6:00am on Monday and 8:00am on Saturday/Sunday. Yours would set the Monday morning wake up to 8.00am.

> **prudentius said:**
> 
Code:

#!/bin/sh
# Check generic running time to shutdown

DAY=$(date +%u)
HOUR=$(date +%k)

if [ $DAY -le 5 ] && [ $HOUR -lt 6 ]; then
   exit 0
elif [ $DAY -le 5 ] && [ $HOUR -ge 8 ] && [ $HOUR -lt 16 ]; then
   exit 0
elif [ $DAY -ge 6 ] && [ $HOUR -lt 8 ]; then
   exit 0
else
   exit 1
fi

Doesn't that do exactly what mine does (even the same times) ? Or am I missing something again ?

---

### Post by laffinet on 2009-02-23
> **prudentius said:**
> 
Exactly, that's why I don't autostart the frontent but use the remote to start. As far as recordings are concerned you don't need the frontend to be running to record (just the backend running is enough).


Another thought: what if I added 

```
pkill mythfront
```

to the MythShutdown script. Wouldn't that take care of it ?

---

### Post by prudentius on 2009-02-24
> 
```

# generic wake-up time
#   Mo-Fr @ 6am & 4pm, Sa-Su @ 8am
if [ $DAY -le 5 ] && [ $HOUR -lt 16 ] && [ $HOUR -ge 6 ];then
	GWU=$(date -d '16:00' +%s)
elif [ $DAY -le 4 ] || [[ $DAY -eq 7 ] && [ $HOUR -ge 6 ]];then
	GWU=$(date -d '06:00' +%s)
else
	GWU=$(date -d '08:00' +%s)
fi

```
it should work, shouldn't it ?
Note: I had that extra elif in there so it sets the wake up to 6:00am on Monday and 8:00am on Saturday/Sunday. Yours would set the Monday morning wake up to 8.00am.

The elif checks for DAY -le 4 (which is Mo-Th) OR DAY = 7 and HOUR>=6. I don't see why this does something special for Monday only. However, I would recommend not to have if and elif statements to overlap, in the sense that "Monday 8am" yields 'true' in the if and the elif.

The script I typed was intended to do
> 
Hopefully this accomplishest that the machine will be on automatically:
Mon-Fri 6.00-8.00 & 16.00-24.00
Sat-Sun 8.00-24.00


The MythShutdownCheck I just rewrote (yours is fine as mentioned) to have the time checks similar as in the wakeup script (orderwise).

> 
Another thought: what if I added 
Code:
pkill mythfront
to the MythShutdown script. Wouldn't that take care of it ?

I don't think this will help, because the MythShutdown script is called only if the backend is idle, which won't happen as long as a frontend is connected...

---

### Post by laffinet on 2009-02-24
First of all: thanks again for spending all this time checking my script and helping me ! Much appreciated.

Now that I reread my script (and I've done that many times already, believe me), I don't quite understand why I did what I did :oops: (been a while since I've done any programming).

Ahhh, just had a moment. I was about to write how I don't understand how your script does the Mon 6.00am wakeup when I finally got it (and fully understood your "doesn't idle shut down before midnight" comment). Stupid me. 8-[
Your script works for that situation because when the machine shuts down idle at the end of Sunday, it will actually be Monday, so $DAY -le 5 is true. D'Oh. How did I miss that ???


> **prudentius said:**
> 
The MythShutdownCheck I just rewrote (yours is fine as mentioned) to have the time checks similar as in the wakeup script (orderwise).


Okay, that makes sense.


> **prudentius said:**
> 
I don't think this will help, because the MythShutdown script is called only if the backend is idle, which won't happen as long as a frontend is connected...

Okay, didn't think of that. I guess I'll have to go with your method of not starting the frontend on startup. 

Thanks a lot again !

---

### Post by prudentius on 2009-02-24
No worries, I spent quite some time configuring my box as well (still not totally happy with everything). Trust me I had some ](*,) moments myself ;) I'm glad the ideas were some help to you...

> 
Your script works for that situation because when the machine shuts down idle at the end of Sunday, it will actually be Monday, so $DAY -le 5 is true. D'Oh. How did I miss that ???


Yes, I'm sorry I should have mentioned that somewhere. It's not a problem for my shutdown times since they are way past midnight, but I realized that when I saw that you wanted to have your machine shutdown at that very critical time ;) Should have commented the scripts accordingly...

Maybe the solution is not so nice after all, but anyways it is also partly the reason why I rewrote your MythShutdownCheck, since it was easier (for me) to check correctness if the times are in chronological order.

> 
[QUOTE]I don't think this will help, because the MythShutdown script is called only if the backend is idle, which won't happen as long as a frontend is connected...

Okay, didn't think of that. I guess I'll have to go with your method of not starting the frontend on startup. 
[/QUOTE]
I thought about killing frontend via some cronjob as well: you could write another script (to be run via cron) that checks the current time (every x minutes) and if it happens to be during the time you're not home this script kills mythfrontend. After another y minutes the backend will become idle and shutdown the box (with the scripts you already have).
However, I didn't try that yet, since doing it with the remote (using the kill command 'kill mythfrontend.real')

Let me know if that works out for you...
All the best,
pru

---

### Post by laffinet on 2009-02-27
Okay, finally set everything up. Wouldn't mind if you could have a look at my settings in the Backend setup and tell me if everything is OK:

Startup command: blank
Block shutdown before client connected: checked
Idle shutdown: 300
Max. wait for recording: 15
Startup before recording: 180
Wakeup time format: time_t
Command to setup Wakeup time: MythSetWakeup
Server halt command: MythShutdown
Pre shutdown check command: MythShutdownCheck

Thanks.

---

### Post by prudentius on 2009-02-27
> **laffinet said:**
> Startup command: blank
Block shutdown before client connected: checked
Idle shutdown: 300
Max. wait for recording: 15
Startup before recording: 180
Wakeup time format: time_t
Command to setup Wakeup time: MythSetWakeup
Server halt command: MythShutdown
Pre shutdown check command: MythShutdownCheck


Personally, I would uncheck the "Block shutdown before client connected" option, otherwise the system won't go down after coming up just for a recording (so without starting, i.e. connecting, a frontend first). I think this would suit your needs since probably you won't manually startup the frontend in the morning between 6-8am?

For the last 3 entries I think you have to specify the entire path to the scrits (but I might be mistaken). I use something like 
```

Command to setup Wakeup time: sudo /usr/bin/MythSetWakeup $time
Server halt command: sudo /usr/bin/MythShutdown
Pre shutdown check command: sudo /usr/bin/MythShutdownCheck

```
(you have to pass the $time argument to the MythSetWakeup script)

Other than that it looks fine and should work (might want to check again that the scripts are executable and visudo is setup correctly). Let me know if everything's fine ;)

Best,
pru

---

### Post by laffinet on 2009-02-27
Okay, I changed the mythtv setup stuff to what you said (my scripts are in /usr/sbin though). So every line is now preceded by:
```
sudo /usr/sbin/
```

And I added $time to the MythSetWakeup line.

This is the line in visudo:
```
%mythtv ALL = NOPASSWD: /usr/sbin/MythSetWakeup, /usr/sbin/MythShutdown, /usr/sbin/MythShutdownCheck
```

Here are the permissions for the scripts, would think they are ok:
```
-rwxr-xr-x 1 root    root        106 2009-02-27 16:55 MythSetWakeup
-rwxr-xr-x 1 root    root        376 2009-02-27 16:59 MythShutdown
-rwxr-xr-x 1 root    root        287 2009-02-27 16:52 MythShutdownCheck

```

> I think this would suit your needs since probably you won't manually startup the frontend in the morning between 6-8am?

Not quite sure what you mean by this. I currently have the system set up without the frontend starting automatically. Which means that at the times the system comes up automatically (6am weekdays, 4pm weekdays, 8am weekends) I start the frontend via a button on the remote (which calls a small script). When leaving I shut the frontend down via button on remote (which calls a small script) again.
Which triggered a thought: if the system doesn't shut down idle when a frontend is running, doesn't that make the MythShutdownCheck script obsolete in a way (assuming I always have a frontend running when at home) ?

---

### Post by prudentius on 2009-02-28
Hey laffinet,
from what I see your setup should work as intended ;)

> 
[QUOTE]
I think this would suit your needs since probably you won't manually startup the frontend in the morning between 6-8am?  

Not quite sure what you mean by this.
[/QUOTE]

My remark was to having the option "Block shutdown before client connected:" checked. IF you have that enabled you HAVE to connect with a frontend before the system will go down again. That means, (if checked) your backend comes up in the morning at 6am but WON'T go down at 8am unless you startup the frontend...

> 
Which triggered a thought: if the system doesn't shut down idle when a frontend is running, doesn't that make the MythShutdownCheck script obsolete in a way (assuming I always have a frontend running when at home) ?


That is true, however, I want the system to be running when I come home (regardless of time: 6pm or 10pm). Unless you're at home the same very time every day and also startup the frontend in time (that is, within "wakeup time + time system takes to start + backend idle time") your system will go down again.
That's why there's the workaround with the script ... If you come up with a more elegant solution let me know, it somewhat bothers me too ;)

Best,
pru

---

### Post by laffinet on 2009-03-04
Sorry for not replying for a while. Still haven't been able to thoroughly test the setup. Shutdown works ok, but can't confirm wake up yet.

One thing that still bugs me is that starting the frontend using a button on the remote often starts two instances (more [here]("http://ubuntuforums.org/showthread.php?p=6812352#post6812352") and above). Haven't found a solution yet. 
What script are you using to start the frontend ?

---

### Post by prudentius on 2009-03-04
> **laffinet said:**
> 
One thing that still bugs me is that starting the frontend using a button on the remote often starts two instances (more [here]("http://ubuntuforums.org/showthread.php?p=6812352#post6812352") and above). Haven't found a solution yet. 
What script are you using to start the frontend ?


Hm, that didn't happen for me; frankly I don't have an idea what would cause that. I'll attach my script to start/stop frontend - maybe that helps.

I assume you use irexec(?) to start the frontend-script, so the following should be found somewhere in the definitions for lirc:
```

begin
  prog = irexec
  button = power
  config = *path_to_script*./MythTV
end

```

Then this script MythTV does the following:
```

#!/bin/sh
# Script to start/stop MythTV
#

LOG=/var/log/mythtv/mythfrontend.log
MYTH=$(pidof mythfrontend.real)

if [ -z $MYTH ]; then
   echo Starting mythfrontend, remote power ON >> $LOG
   mythfrontend &
   xset s off
   xset -dpms
else
   echo Stopping mythfrontend, remote power OFF >> $LOG
   kill $MYTH
   xset s on
   xset +dpms
fi

```

FYI: the xset commands are to turnoff screensaver (xset s off) and screen blanking (xset -dpms) as long as the frontend is running.

best,
pru

---

### Post by laffinet on 2009-03-04
Same problem with that script unfortunately. 50% of the time two frontends start. Very annoying. No idea how to stop that.:(

---

### Post by prudentius on 2009-03-04
Hm, just out of curiosity: is it *exactly* 50% of the time ?

Do you have any other IR devices nearby, that could cause interference? (I learned that the hard way with a squeeze-musicbox in range. Appearantly, the musicbox itself (not triggered by the corresponding remote) would sometimes send IR signals and confuse my mythtv... Was quite funny to find out values for my remote.rem file ;)

Have you tried the following:
```

begin
  prog = irexec
  button = power
  config = echo Testing the remote.
end

```
and see if pressing the button once does in fact produce the text output twice?

---

### Post by laffinet on 2009-03-04
It's not exactly 50%, just perceived. 

One thing I noticed is that if I run irw and press a button on the remote it sometimes registers once, sometimes twice, eg:

```
 irw
000000037ff07ba3 00 Green mceusb

```

and

```
irw
000000037ff07ba3 00 Green mceusb
000000037ff07ba3 01 Green mceusb
```

So I guess the button gets registered twice sometimes. No idea how to stop that, though.
I already have the line "repeat = 0" in my mythtv lirc file, however that didn't change a thing.

> config = echo Testing the remote.


Where would that be displayed ? So far I haven't been able to get an "echo" output displayed when pressing a button.

---

### Post by prudentius on 2009-03-04
OK that *is* weird, could it be that your remote is broken; well, other than first-guess trials which you probably already did (vary pressure, intervals in which buttons pressed; change batteries, try different remote if you have another one) nothing comes to my mind what could be the problem...

The 'echo' works if you start irexec (instead of irw) and then hit the button - see the code, program=irexec...

But since you have multiple button registering happening in irw, I doubt there is a difference with irexec.

---

### Post by laffinet on 2009-03-11
Just letting you know I fixed the repeated button problem. Someone in the other thread mentioned it might be irexec running twice, which is exactly what happened. Unticked 'Infrared' in austostarted apps and now only one irexec is running on startup and everything works fine.

Still don't know why two irexecs got started in the first place but my problem is fixed, so I'm happy.

---

### Post by prudentius on 2009-03-11
Nice ;)

---

### Post by jeanseb on 2009-03-13
Hello,
I have a problem with MythTV 0.21 and Intrepid.
Although I set it up to recompute wakeup time, it seems the script never gets called.

If, as root, I "su mythtv" and manually call the script, it works as intended.
But the script never seems to be called by the mythbackend.

I got the same setup to work with Gutsy, and I don't understand what goes wrong here.

My wakeup script has the following rights attached (just chowned it to mythtv for another round of testing)
> -rwxr-xr-x 1 mythtv mythtv 493 2009-03-13 20:20 /usr/local/bin/MythWakeUp.sh

My MythWakeUp.sh script is:
> #!/bin/sh
#$1 is the first argument to the script. It is the time in seconds since 1970
#this is defined in mythtv-setup with the time_t argument

echo "setwakeup starting for $SECS" >> /var/log/mythtv/mythbackend.log
echo "Rescheduling wakeup time to $1"
SECS=`date -u --date "$1" +%s`
echo 0 > /sys/class/rtc/rtc0/wakealarm      #this clears your alarm.
echo $SECS > /sys/class/rtc/rtc0/wakealarm     #this writes your alarm
echo "setwakeup set to $SECS" >> /var/log/mythtv/mythbackend.log

Visudo reads for mythtv:
> %mythtv ALL = NOPASSWD: /sbin/shutdown, /bin/sh, /usr/local/bin/MythWakeUp.sh, /sys/class/rtc/rtc0/wakealarm

And the mythtv-setup configuration reads:
> date format: yyyy-MM-dd hh:mm:ss
Mythwakeset command: sudo /usr/local/bin/MythWakeUp.sh $time

Mythbackend log does not show anything, as if the script never got called.
Did not find anything meaningful (for me) in auth.log

I'd be grateful if someone could help me.

---

### Post by laffinet on 2009-03-16
Can't see anything at first glance that is wrong.

You say it seems the script never gets called. Have you tested this ?

---

### Post by jeanseb on 2009-03-17
Yes, I had the script create a temp file in /home/mythtv first thing.
When the script was run manually, the temp file was created.
But in normal operation mode, mythtv backend would never have that file created.

---

### Post by prudentius on 2009-03-20
Hmmm that sounds weird...

Have you checked that your backend actually becomes idle? (in the backend.log you should be able to read lines like "Mythtvbackend is idle... shutting down in xx minutes")

Note that your backend does not become idle if a frontend is connected (in particular if you run front- and backend on the same machine, you have to stop frontend first before ANY wakeupscript gets called).

Another thing that I can think of right now is: make sure in the mythtv setup
```

Startup command: blank
Block shutdown before client connected: **UNchecked**
Idle shutdown: 300

```
the option should most likely be unchecked (for testing at least). If it is checked, however, your backend will NOT become idle as long as no frontend gets connected and then "disconnected" again (i.e. shutdown frontend). Then and only then will the backend go idle and after 300secs call the wakeup script...

Sorry I can't think of anything else right now...

---

### Post by jeanseb on 2009-03-20
Interesting stuff, thank you.
By decreasing the idle shutdown, I had my script called.

But it was only called because I also set it to be the shutdown script.

I could have lived with that,but $time does not seemed to be passed then, so no valid wakeup time can be set.

My test setup:
> Wakeup script: sudo sh -c "/usr/local/bin/MythWakeUp.sh $time 'wake'"
Shutdown script: sudo sh -c "/usr/local/bin/MythWakeUp.sh $time 'Stop'"

And the first line of the script goes:
> echo Received "$1" and "$2" >> /var/log/mythtv/mythbackend.log

Output in the log:
> Received Stop and 
date: invalid date `Stop'
Rescheduling wakeup time to  from Stop
setwakeup set to 

---

### Post by prudentius on 2009-03-20
Hm, I'm sorry but I don't see why your script wouldn't get called as wakeup but only when shutting down... (have you tried with another script for wakeup, something that just echos a test string?)

On a sidenote if you set "date format: yyyy-MM-dd hh:mm:ss" to "date format: time_t" instead you already get the correct format you want to echo to /sys/class/rtc/rtc0/wakealarm (so no converting needed in your script).

So long
pru

---

### Post by jeanseb on 2009-03-22
I finally wrote some ugly hack around this (warning, this may make some eyes sore...)

mythshutdown being able to compute the next wakeup time, I fetch the date from its verbose output and have it forced into bios.

For what it's worth, here's what my wakeup script now looks like:

> #!/bin/sh

T=`mythshutdown -t -v database | grep '.*INSERT.*[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]T[0-9][0-9]:[0-9][0-9]:[0-9][0-9]'`
jour=`expr match "$T" '.*\([0-9][0-9][0-9][0-9]\-[0-9][0-9]\-[0-9][0-9]\)T'`
heure=`expr match "$T" '.*T\([0-9][0-9]\:[0-9][0-9]\:[0-9][0-9]\)'`

SECS=`date -u --date "$jour $heure" +%s`
echo "Rescheduling wakeup time to $SECS from $jour $heure" >> /var/log/mythtv/mythbackend.log
echo 0 > /sys/class/rtc/rtc0/wakealarm      #this clears your alarm.
echo $SECS > /sys/class/rtc/rtc0/wakealarm     #this writes your alarm
echo "setwakeup set to $SECS" >> /var/log/mythtv/mythbackend.log
exit 1

I keep the "exit 1" statement to prevent my machine from actually shutting down, because for now, I'll have this script launched every time the idle timeout is reached (and I'll keep it low, say 2 minutes).

I intend to gradually improve this to have it actually manage machine shutdown as well, but that's not a priority for the moment.

---

### Post by mega30000 on 2009-12-15
Guys - I found these posts most helpful.  After some effort I was able to get this working as well.  The only problem I seemed to run into (which seemed to be alluded to in post#7) was that if I shut down before 24:00 hours - the wakeup time $GWU would always get set to a time in the past.

I believe I have solved that issue and now I can set the shutdown time for a time earlier than 24:00 hours. 

Hopefully this helps someone else.  Comments are welcome.

(NOTE:  I am running Ubuntu9.10, Myth0.22, on a GIGABYTE GA-MA770-UD3 motherboard.)

[PHP]IDLE SHUTDOWN TIMEOUT: 600
MAX WAIT FOR RECORDING: 15
STARTUP BEFORE RECORDING: 120
WAKEUP TIME FORMAT: time_t
COMMAND TO SET WAKEUP TIME: sudo sh -c "/usr/bin/MythSetWakeup.sh $time"
SERVER HALT COMMAND: sudo sh -c "/usr/bin/MythShutdown.sh"
PRE SHUTDOWN CHECK COMMAND: sudo /usr/bin/MythShutdownCheck.sh
[/PHP]



[PHP]
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
HWCLOCKACCESS=no[/PHP]

[PHP]#!/bin/sh
#MythSetWakeup.sh
#$1 is the first argument to the script. 
#It needs to come in the following format:  "2008-12-22 10:45:00"
#this is defined in mythtv-setup 

echo 0 > /sys/class/rtc/rtc0/wakealarm
echo $1 > /sys/class/rtc/rtc0/wakealarm


LOG=/var/log/mythtv/mythbackend.log
  echo "echo 0 > /sys/class/rtc/rtc0/wakealarm" >>$LOG
  echo "echo $SECS > /sys/class/rtc/rtc0/wakealarm" >>$LOG
  cat /proc/driver/rtc  >>$LOG[/PHP]

[PHP]#!/bin/sh
# Check generic running time to shutdown
#MythShutdownCheck

DAY=$(date +%u)
HOUR=$(date +%k)


LOG=/var/log/mythtv/mythbackend.log 

echo "MythShutdownCheck $DAY : $HOUR" >>$LOG 


if [ $DAY -le 4 ]; then
	if [ $HOUR -ge 23 ] || [ $HOUR -lt 16 ]; then
		echo "-*-*-*-*-*MythShutdownCheck-*-*-*-*-*" >>$LOG 
	  	echo "mon-thur shutdown before 4pm, after 11pm" >>$LOG
	  	echo "MythShutdownCheck is ok to shutdown: DAY:$DAY HOUR:$HOUR" >>$LOG 
	   	exit 0
	fi
elif [ $DAY -ge 6 ] && [ $HOUR -ge 2 ] && [ $HOUR -lt 8 ]; then
  echo "-*-*-*-*-*MythShutdownCheck-*-*-*-*-*" >>$LOG 
  echo "MythShutdownCheck: Fri-Sat Night after 2am to before 8am">>$LOG
  echo "MythShutdownCheck is ok to shutdown: DAY:$DAY HOUR:$HOUR" >>$LOG 
  exit 0
elif [ $DAY -ge 7 ] && [ $HOUR -ge 23 ]; then
#sun after 11
  echo "-*-*-*-*-*MythShutdownCheck-*-*-*-*-*" >>$LOG 
  echo "MythShutdownCheck: sun after 11pm" >>$LOG
  echo "MythShutdownCheck is ok to shutdown: DAY:$DAY HOUR:$HOUR" >>$LOG 
   exit 0
else
   exit 1
fi
[/PHP]



[PHP]#!/bin/sh
# MythShutdown
# Shutdown the Mythbox

LOG=/var/log/mythtv/mythbackend.log 

# wake-up time for scheduled recording
WUP=$(cat /sys/class/rtc/rtc0/wakealarm)
DAY=$(date +%u)


# generic wake-up time
#   Mo-Fr @ 4pm, Sa-Su @ 8am
if [ $(date +%u) -le 4 ] ; then
   echo "MythShutdown Mon-Thur set for 4pm today or 4pm tommorrow the next day" >>$LOG 
   	GWU=$(date -d '16:00' +%s)
	if [ $(date +%k) -ge 4 ]; then
		GWU=$(($GWU+86400))
	fi
elif [ $(date +%u) -ge 7 ] && [ $(date +%k) -ge 23 ]; then
      echo "MythShutdown Sun after 11 set for 4pm the next day" >>$LOG 
      GWU=$(date -d '16:00' +%s)
	GWU=$(($GWU+86400))
else
   echo "MythShutdown Sun-am or Sat set 8am the next day" >>$LOG 
   GWU=$(date -d '08:00' +%s)
fi


# if there is no scheduled recording or
#   next generic wake-up is earlier
#   then set to that time
if [ -z $WUP ] || [ $GWU -lt $WUP ] ; then
   echo 0 > /sys/class/rtc/rtc0/wakealarm
   echo $GWU > /sys/class/rtc/rtc0/wakealarm
  echo "MythShutdown overwrote WUP with GWU time on DAY:$DAY" >>$LOG 
fi


  echo "MythShutdown WUP:$WUP  GWU:$GWU" >>$LOG 
  cat /proc/driver/rtc  >>$LOG




#mythshutdown -q
#i dont think mythshutdown -q works right
#going back to sudo sbin hd
sudo /sbin/halt -p
[/PHP]

---

### Post by Stevi on 2009-12-23
Hi mega3000,

I think I have the same problem. I upgraded from 9.04 to 9.10 and my computer doesn't wakeup if the recording is only a few hours in the future.

I tried your scripts but they didn't work as expected - my computer shuts down all the time.

My scripts look different to yours. So could you please post the scripts you used before this problem appeared? So I can see what you changed and I can probably see what I have to change in my scripts.

Thx in advance.

---

### Post by mega30000 on 2009-12-23
Stevi,

I am on nthe road for several weeks and will not be back by my pc.

i used the comments that are sent to the mythbackend log to help debug the scripts.  these are in #MythShutdownCheck.sh.

one suggestion is to comment out the sudo /sbin/halt -p line in  Mythshutdown.sh which will keep you from shutting down while you check the logs for debugging.

---

