---
title: "Turn LiveTV off after X hours"
date: 2010-01-19
forum: Mythbuntu
---

### Post by sk8er3810 on 2010-01-19
This is a tricky problem.  My girlfriend tends to leave the LiveTV on when she leaves the house.  This eats up my hard drive space very quickly over an 8-10 hour period when we are either not home, or out of the house.  I've tried to get her to remember but it she still forgets.  Is there a way to automatically exit LiveTV after X amount of time?(Sleep is not an option since one has to manually do it).  Is there a parental controls type of ability in MythTV?

---

### Post by azmyth on 2010-01-19
There was talk of a watchdog but I don't think it ever happened. I was running into this problem as well. Heck, even I forgot. I ended up writing a script to kill the FE and issue a command to shut the TV off through the RS232. Likewise, the script does the opposite when the TV is off. It's tied to the power button using irexec to execute the script.

---

### Post by sk8er3810 on 2010-01-19
That sounds like a very plausible solution.  Would you mind posting your scripts?

---

### Post by mathog on 2010-01-19
> **sk8er3810 said:**
> This is a tricky problem.  My girlfriend tends to leave the LiveTV on when she leaves the house.  This eats up my hard drive space very quickly over an 8-10 hour period when we are either not home, or out of the house.  I've tried to get her to remember but it she still forgets.  Is there a way to automatically exit LiveTV after X amount of time?(Sleep is not an option since one has to manually do it).  Is there a parental controls type of ability in MythTV?

This is indeed a tricky problem.  

To do this "right" there must be some way of telling whether or not there is somebody using the machine, and traditionally that has been accomplished by monitoring keyboard/mouse IO.  Sadly, as far as I know, mythtv does not expose a bit to indicate 'io from user within time X', which could be used for the shutdown.  

Assuming your system uses a remote then the easiest place to cut in for this would be at irexec.  I don't think irexec does this currently, but it should be easy to modify the code so that every time it sees a button it does the equivalent of:

   date > /var/run/ir_last_button_time

Once that exists the rest is easy.

Also modify the irexec startup script to run the code above before starting irexecd, and before starting your shutdown script.  Otherwise your script may see the ultimate button press from the last session and immediately shut down. 

Have the system start your shutdown script which checks the time in ir_last_button_time and executes a poweroff once it is past the number of hours you set for idle.  The simplest way would have it run in cron.hourly, but you could set it to run continuously and sleep for 10 minutes or so before checks.  (Sounds like you also need a way to turn off the physical display, but you seem to know how to do that already via  serial line.)

If implemented properly this should be nearly painless, but I predict that some day you will be watching something long (Jerry Lewis telethon for instance), neglect to use the remote past the timeout period, and find the system shutting down.

---

### Post by SiHa on 2010-01-19
There has been a LiveTVIdleTimout field in Myth since at least 8.04. Back then you has to insert it into the mysql database manually (and I could never get it to work). The good news is that as of MythTV 0.22 - Mythbuntu 9.10 this is an option in the frontend setup, can't remember exactly where it is, probably in 'General' somewhere.
I have mine set to 60 minutes, and after this time an OSD window pops up and says 'Are you still watching?' if ignored it will stop LiveTV and return to the menu after 60secs, otherwise you, just hit 'OK' on the remote to say 'Yes'.

---

### Post by sk8er3810 on 2010-01-19
Awesome.  I just set it for 240 minutes / 4 hours.  It's the first screen in TV Settings->Playback.  However linking the mythtv "power off" to turn the TV off as well is still a good idea.

---

### Post by SiHa on 2010-01-19
> **sk8er3810 said:**
> However linking the mythtv "power off" to turn the TV off as well is still a good idea.

Certainly is.

I was also toying with the idea of knocking up a little circuit that would sense a voltage on the Hotplug_Detect pin of the HDMI socket (ie, TV is 'ON') to switch on the Mythbox. Haven't quite had a chance to play around with that yet though.

---

### Post by LowSky on 2010-01-19
The best option is to limit live record time, or to turn it off entirely so it doesn't use your hard drive for countless hours.

-- Could you use a universal remote like the Logitech Harmony and have it turn off mulitple devices at the same time. Heck you could program it to not turn off the PC but to just exit Live TV watching???? Just trying to think here...

---

### Post by sk8er3810 on 2010-01-19
> I was also toying with the idea of knocking up a little circuit that would sense a voltage on the Hotplug_Detect pin of the HDMI socket (ie, TV is 'ON') to switch on the Mythbox. Haven't quite had a chance to play around with that yet though.
That would be a cool hack.
> -- Could you use a universal remote like the Logitech Harmony and have it turn off mulitple devices at the same time. Heck you could program it to not turn off the PC but to just exit Live TV watching???? Just trying to think here...
I hear the Harmony series remotes are great but they are a little out of my price range.  I have a Radioshack universal remote that I believe has that functionality.  I also bought a few Media Center remotes that work pretty well out of the box with Mythbuntu's control centre remote config(needs a little tweaking but the main functionality is there).  Anyone know where I can get a TUX insert for my Media Center button?

I want my frontend-only such that when I press the power button (on the remote) it will shutdown the computer after 30 seconds(press again within 30 seconds cancels the shutdown). And my backend/frontend combo the power button (on the remote) only exits LiveTV.  Ugh, so much configuration, so little time :(

---

### Post by nickrout on 2010-01-19
> **sk8er3810 said:**
> This is a tricky problem.  My girlfriend tends to leave the LiveTV on when she leaves the house.  This eats up my hard drive space very quickly over an 8-10 hour period when we are either not home, or out of the house.  I've tried to get her to remember but it she still forgets.  Is there a way to automatically exit LiveTV after X amount of time?(Sleep is not an option since one has to manually do it).  Is there a parental controls type of ability in MythTV?

upgrade to girlfriend 2.0?

I knew I had seen it somewhere:

[http://www.gossamer-threads.com/lists/mythtv/users/322750](http://www.gossamer-threads.com/lists/mythtv/users/322750)

---

### Post by SiHa on 2010-01-20
> I knew I had seen it somewhere:

[http://www.gossamer-threads.com/list...v/users/322750](http://www.gossamer-threads.com/list...v/users/322750)
That's the baby, just didn't work for me.

Almost certainly user error though.

---

