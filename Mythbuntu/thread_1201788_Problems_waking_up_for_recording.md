---
title: "Problems waking up for recording"
date: 2009-07-01
forum: Mythbuntu
---

### Post by Jayy on 2009-07-01
Yesterday I set a recording for 2 AM in the morning today, and I "suspended" the computer at about 10:30. When I woke up this morning it had not recorded it. I haven't done any changes to the "Startup/Wake up" settings page, so I'm not sure what the problem is. BTW, my motherboard is an Asus M2N68-VM.

---

### Post by laffinet on 2009-07-01
What are your startup/shut down settings ?

---

### Post by Jayy on 2009-07-02
The default. I can give you a screen shot, but I'm not sure how.

---

### Post by laffinet on 2009-07-02
Mythbuntu is not set up to wake up for recording "out of the box".
That is something you have to configure. Depending on how complicated you want it this can be quite easy.
I've done a fairly complicated job [here ]("http://ubuntuforums.org/showthread.php?t=1072905")(with help from [here]("http://www.mythtv.org/wiki/ACPI_Wakeup#Integrate_into_mythTV_2")), but if you just want the machine to shut down when idle and come up for the next recording then your scripts and set up will be much easier.

You basically need 3 scripts:

MythSetWakeup (sets the wake up time)
MythShutdown (shuts the machine down. This can be much simpler if you don't have "generic" wake up times)
MythShutdownCheck (checks if it is ok to shut the machine down. You might not need this, I included this to prevent the machine from shutting down at certain times of the day)

---

### Post by Jayy on 2009-07-02
> **laffinet said:**
> if you just want the machine to shut down when idle and come up for the next recording then your scripts and set up will be much easier.
Yes, that's exactly what I want to do. How exactly do I set up the scripts?

---

### Post by laffinet on 2009-07-02
I recommend to do a bit of reading [here]("http://www.mythtv.org/wiki/ACPI_Wakeup"), gives you a bit of understanding what's going on.

In summary, you have to do the following:

You need to do a few adjustments in mythbackend setup, under '1. General', page 5 (Shutdown/Wakeup Options)

```
Block shutdown: (Do not check if you do not automatically start the front end, and want the system to shut down after an automatic recording.) 

Idle shutdown timeout (secs): idle shutdown time of your choice (if you set this to 0, it will disable auto shutdown) 

Max. wait for recording (min): 10 (which means the machine will not shut down if next recording is within 10 min, adjust to your liking)

Startup before rec. (secs): 600 (If you have not disabled the occasional disk check on boot, make this time long enough to complete the boot & disk check before the recording should start) 

Wakeup time format: time_t 

Command to set Wakeup Time: sudo /usr/bin/MythSetWakeup $time

Server halt command: sudo mythshutdown -q

Pre Shutdown check-command: (leave this blank) 
```
You need to create the MythSetWakeup script in /usr/bin/.
Your script should look like this:

```
#!/bin/sh
# MythSetWakeup

echo 0 > /sys/class/rtc/rtc0/wakealarm
echo $1 > /sys/class/rtc/rtc0/wakealarm
```

---

### Post by Jayy on 2009-07-02
Thank you!! I have just two quick questions. The script should be saved as an .sh file, right? And also, should I turn on all the ACPI and RTC settings in my BIOS? (BTW, we have the same motherboard)

Edit: I have two more questions. Do I need to edit this file? **/etc/default/rcS**     And do I set the RTC Alarm Date in the BIOS to todays date, or "Everyday"? Thanks.

---

### Post by laffinet on 2009-07-02
No worries.

Yes, the script filename should end in .sh. You also have to make it executable. You can do this in the file manager or by running this command:

```
chmod +x MythSetWakeup.sh
```

> Do I need to edit this file? /etc/default/rcS
To be honest I don't really remember. I don;t think I ever did. I would try without and if it doesn't work you can still edit the file. 

> And do I set the RTC Alarm Date in the BIOS to todays date, or "Everyday"?
You don't need to set a date in the BIOS. The script is doing that for you. 

> should I turn on all the ACPI and RTC settings in my BIOS?
From memory I think you have to enable "Power on by RTC" and the two "ACPI" entries. I will check my settings and get back to you (won't be until a few hours from now).

---

### Post by Jayy on 2009-07-06
I tried the test from [here]("http://www.mythtv.org/wiki/ACPI_Wakeup"), and it worked, but Mythbuntu still isn't working. :/

---

### Post by laffinet on 2009-07-06
I'm assuming that the machine didn't come up for a recording.

Can you provide more detail: what test did you do and what worked?

What exactly are your settings on the shutdown/wakeup page, post your scripts.

---

### Post by SiHa on 2009-07-07
> 

[QUOTE]and do I set the RTC Alarm Date in the BIOS to todays date, or "Everyday"?  
You don't need to set a date in the BIOS. The script is doing that for you. [/QUOTE]

> should I turn on all the ACPI and RTC settings in my BIOS?  
[QUOTE]
From memory I think you have to enable "Power on by RTC" and the two "ACPI" entries. I will check my settings and get back to you (won't be until a few hours from now). [/QUOTE]

On some mobo's you need to actually **disable** this feature in the BIOS for this to work successfully.

---

### Post by laffinet on 2009-07-07
Sorry, I never got back to you on that one: I checked my settings and have "power on by RTC" disabled. Since you got the same motherboard you might want to try that.

---

### Post by Jayy on 2009-07-07
```

Startup command: (Blank)

Block shutdown:Unchecked

Idle shutdown timeout (secs): 600

Max. wait for recording (min): 15

Startup before rec. (secs): 600

Wakeup time format: time_t 

Command to set Wakeup Time: sudo /usr/bin/MythSetWakeup $time

Server halt command: sudo mythshutdown -q

Pre Shutdown check-command: (Blank)



```
MythSetWakeup.sh
```
#!/bin/sh
# MythSetWakeup

echo 0 > /sys/class/rtc/rtc0/wakealarm
echo $1 > /sys/class/rtc/rtc0/wakealarm
```This was the test I did:
  
[quote=http://www.mythtv.org/wiki/ACPI_Wakeup#Initiate_manually]

Simple test to wake the machine 5 minutes from now 
 ```
sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"
sudo sh -c "echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm"
cat /sys/class/rtc/rtc0/wakealarm
``` Check 
 ```
cat /proc/driver/rtc
``` This should return a list of parameters. Check the "alrm_time" is 5 minutes into the future and the "alrm_date" is today. Shutdown your computer and see if it comes back up in ~5 min. Note that this command is a powerful debugging tool, letting you see what is currently in the BIOS. 
 ```
sudo shutdown -h now
```[/quote]


I do have "Power on by RTC" disabled.

---

### Post by laffinet on 2009-07-07
I don't see anything too obvious so you might have to run a few checks.

I'm assuming the test you did worked fine and the machine came back up after 5min? That would confirm that your bios settings are ok.

Next thing to do would be to run everything manually. Schedule a recording in the near future (but more than your "max. wait for recording" setting). Add 

```
#!/bin/bash -x
``` 
to the beginning of the scripts, that way it runs step by step and provides outputs for each step. Post the output so we can have a look.

Now run 

```
sudo /usr/bin/MythSetWakeup $time
```
and
```
sudo mythshutdown -q
```
and see if the machine comes up for the recording.

You also have to make sure that MythSetWakeup script is in the visudo file. Might apply to mythshutdown, too, not sure, so just add it as well:

```
sudo visudo
```

edit it so you've got this line in it:

```
%mythtv ALL = NOPASSWD: /usr/sbin/MythSetWakeup, mythshutdown
```

This allows the scripts/commands to run as sudo without the need for a password.

---

### Post by Jayy on 2009-07-07
MythSetWakeup.sh is not in the visudo file, nor is mythshutdown. Is there a way that I can edit the file in a text editor instead of the command line?
Another problem I found, is that I need to set the "Command to set Wakeup Time" to
```
sudo /usr/bin/MythSetWakeup[SIZE=2]**.sh**[/SIZE] $time
```instead of
```
sudo /usr/bin/MythSetWakeup $time
```

---

### Post by laffinet on 2009-07-07
> **Jayy said:**
> MythSetWakeup.sh is not in the visudo file, nor is mythshutdown. Is there a way that I can edit the file in a text editor instead of the command line?

Not that I know of. Command line editor is quite simple to use, just edit what you need to edit, Ctrl+O to save (writeout) and CTRL+X to exit.

> **Jayy said:**
> 
Another problem I found, is that I need to set the "Command to set Wakeup Time" to
```
sudo /usr/bin/MythSetWakeup[SIZE=2]**.sh**[/SIZE] $time
```instead of
```
sudo /usr/bin/MythSetWakeup $time
```

That's weird, I'm sure mine just reads MythSetWakeup

Any luck with running things manually ?

---

### Post by Jayy on 2009-07-07
When I save it, then exit, it gives me the following error:
```
>>> sudoers file: syntax error, line 25 <<<
```What do you think I'm doing wrong?



I'll try testing manually when I get the above problem working.

---

### Post by laffinet on 2009-07-07
Please post the content of your visudo file.

---

### Post by Jayy on 2009-07-08
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults    env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

---

### Post by laffinet on 2009-07-08
You need to add this line

```
%mythtv ALL = NOPASSWD: /usr/sbin/MythSetWakeup, mythshutdown
```

to the end of the file, save it and exit it.

Is that when you get that syntax error ?

---

### Post by Jayy on 2009-07-08
Yes. Except I typed "bin" instead of "sbin". I assume that was just a typo.

---

### Post by laffinet on 2009-07-08
> **Jayy said:**
> Yes. Except I typed "bin" instead of "sbin". I assume that was just a typo.

No, that's just because my scripts are in sbin, not bin. If yours are in bin than your line should read

```
%mythtv ALL = NOPASSWD: /usr/bin/MythSetWakeup, mythshutdown
```

That's not what's causing your syntax error, though. Weird. Did you copy the line *exactly *? Made sure you got the %, the blanks, everything ?

---

### Post by laffinet on 2009-07-08
If that doesn't work try without the % (although that doesn't make sense but I'm getting a bit desperate on this one...):p

---

### Post by Jayy on 2009-07-08
It still gives me the syntax error.


I can save it with the syntax error, but do you think that would be a bad idea?
```
>>> sudoers file: syntax error, line 25 <<<
What now? 
Options are:
  (e)dit sudoers file again
  e(x)it without saving changes to sudoers file
  (Q)uit and save changes to sudoers file (DANGER!)

```

---

### Post by SiHa on 2009-07-08
It would be a **very** bad idea.
If your sudoers file is screwed, you can't use sudo. And of course the most important thing about that is you can't edit your sudoers file, catch 22.

One suggestion, borne out of hard experience.
If you're going to play with your sudoers file, back it up first.```
sudo cp /etc/sudoers /etc/sudoers.bak
```
If you screw it up, you can always boot to the recovery console (2nd entry on the the GRUB menu I think) and drop to a shell prompt, where you are root, so you can copy it back across.

---

### Post by Jayy on 2009-07-08
Okay, thanks for letting me know.

---

### Post by SiHa on 2009-07-08
FWIW, I've just looked the sudoers on my backend.
```
%mythtv ALL=NOPASSWD: /sbin/shutdown, /usr/bin/MythWakeSet, /proc/acpi/alarm, /usr/bin/MythShutdownCheck, /etc/init.d/mythtv-backend, /usr/bin/mythshutdown, /sbin/reboot, /sbin/grub-set-default, /usr/local/bin/checktime
```

There's a bit extra there, but you'll note that there is no space in the ALL=NOPASSWD bit. Also, there must not be any carriage returns in it, it should be on a single line. I have a feeling this caused me a bit of a headache initially, quite apart from the fact that vi is horrid.

---

### Post by Jayy on 2009-07-08
That worked, thanks.

But it still won't start up to record.

---

### Post by SiHa on 2009-07-08
Earlier you said you'd tried the +5 mins test - did that work? At least with that you'll know where the problem lies.

Edit: Sorry earlier post says it did work.

So. The problem is with MythSetWakeup not setting the time properly. You could put a line in the script to copy the set time to a file:> cat /sys/class/rtc/rtc0/wakealarm > ~/alarmtime
To check what time is being set by Myth before the system shuts down. Or just change the 'command to shutdown' to the above, so that you can see what's happening without actually shutting down.

---

### Post by Jayy on 2009-07-08
Yes, it did worked. I'll run it again though to make sure it still works.

---

### Post by AKADAP on 2009-07-08
How is your computer shutting down before the recording? Are you letting MythTV do the shut down, or are you doing it yourself manually?

A MythTV system will only wake for a recording if MythTV did the shut down. That is the only time it sets the wakeup time.

---

### Post by Jayy on 2009-07-08
Yes, I let MythTV do the shut down.

---

### Post by laffinet on 2009-07-08
> **SiHa said:**
> There's a bit extra there, but you'll note that there is no space in the ALL=NOPASSWD bit.

That is weird, I've got the spaces in the ALL = NOPASSWD bit on my sudoer file (as posted above) and everything works fine :confused:

Ah well, glad it works for the OP now.

---

### Post by laffinet on 2009-07-08
Did you run the MythSetWakeup with the 

```
#!/bin/bash -x
```

modification ? What was the output from that ?

---

### Post by SiHa on 2009-07-09
> **laffinet said:**
> That is weird, I've got the spaces in the ALL = NOPASSWD bit on my sudoer file (as posted above) and everything works fine :confused:

Ah well, glad it works for the OP now.


Yes, I think there's some inconsistencies there. I copied and pasted my sudoers line out of the ACPI..Whatnext wiki,and kept getting syntax errors until I noticed that the other lines were missing the spaces.

---

### Post by Jayy on 2009-07-09
I followed [this]("http://ubuntuforums.org/showthread.php?t=1176528") tutorial and got it working. But one problem is that if I'm doing something like web browsing, it will still shut down if I don't lock it. Is there anyway to make it detect that I'm active and not start the idle timer?

---

### Post by laffinet on 2009-07-09
> I followed this tutorial and got it working

Good stuff. Any idea what made it work in the end ? 

> Is there anyway to make it detect that I'm active and not start the idle timer? 

There are various ways you can do this.

The easiest is to keep the frontend running while you do other work. That way the system isn't seen as idle and won't shut down.

You can also modify the script called as "pre-shutdown check command" to include checking for certain applications running, users logged in (remotely), certain times of the day etc. Have a look [here]("http://ubuntuforums.org/showpost.php?p=7564269&postcount=3"), might give you some ideas.

---

### Post by Jayy on 2009-07-09
> **laffinet said:**
> Good stuff. Any idea what made it work in the end ?
I think the clock and time stuff was messed up. My system time was wrong, while the MythTV time was right.


> **laffinet said:**
> There are various ways you can do this.

The easiest is to keep the frontend running while you do other work. That way the system isn't seen as idle and won't shut down.

You can also modify the script called as "pre-shutdown check command" to include checking for certain applications running, users logged in (remotely), certain times of the day etc. Have a look [here]("http://ubuntuforums.org/showpost.php?p=7564269&postcount=3"), might give you some ideas.
Thanks. One more thing, do you think it would be better just to suspend the computer when it is idle, or have it shut down? Like which would be better for the computer's life span?

---

### Post by laffinet on 2009-07-09
I'm not an expert on this at all, but wouldn't think that either makes a noticable difference when it comes to life span. After all, the only difference I can see is that suspend (to ram I guess) won't use the hard drive as much to wake up, but I think that extra use for booting up is negligible compared to the use during normal operation.

---

### Post by Jayy on 2009-07-09
Okay, thanks.

---

### Post by joho500 on 2009-07-10
> **Jayy said:**
> Thanks. One more thing, do you think it would be better just to suspend the computer when it is idle, or have it shut down? Like which would be better for the computer's life span?

I've tried to set up suspend to ram on my (old) backend PC and found it's a lot of work. I kept having problems with cards/drivers not resuming. So I decided to stay with complete shutdown and using Wake-on-Lan from my frontend and other PC's to wake it up.

BTW, the script laffinet mentioned above has an error on the VNC part I added :( . The rest works OK. I'm working on an update.

Joost

---

### Post by SiHa on 2009-07-10
> **Jayy said:**
> I followed [this]("http://ubuntuforums.org/showthread.php?t=1176528") tutorial and got it working.

Glad you got it sorted

---

### Post by Jayy on 2009-07-10
> **joho500 said:**
> I've tried to set up suspend to ram on my (old) backend PC and found it's a lot of work. I kept having problems with cards/drivers not resuming. So I decided to stay with complete shutdown and using Wake-on-Lan from my frontend and other PC's to wake it up.
Okay, thanks. I've had problems  with USB devices not resuming, so I'll just stick with having it shutdown. 

> **joho500 said:**
> BTW, the script laffinet mentioned above has an error on the VNC part I added :( . The rest works OK. I'm working on an update.
That's fine. I don't use VNC, so I'll just delete the VNC part if I use it.

---

