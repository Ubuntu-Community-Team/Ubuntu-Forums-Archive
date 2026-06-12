---
title: "Help with MythTV ACPI Shutdown/Wakeup"
date: 2009-10-09
forum: Mythbuntu
---

### Post by se99paj on 2009-10-09
I am currently trying to do my bit for the environment and my electricity bill by getting my mythtv box to shutdown and wakeup by itself by following the instructions here:[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)

At the moment I have got to step 2.5 but I have hit on a snag, the date/time that is stored when I run "cat /proc/acpi/alarm" the day doesn't return so the date comes back as "2009-10-00 21:00:00" I have tried changing the date format in Mythtv but I can't seem to get the day to appear. I know that some mobos do not support the month field but do some also not support the day field? Is there a definitive way to find out, I've read the manual but there isn't much detail.

Also are the steps on 3.7 correct? it seems odd that you need to change the settings in mythbackend after getting it to work correctly in the earlier steps.

---

### Post by SiHa on 2009-10-09
Have you tried manually setting the alarm to five minutes in the future i.e:
```
$ sudo sh -c 'echo "+00-00-00 00:05:00" > /proc/acpi/alarm'
``` As the guide suggests?

The reason I ask is that my system shows the day as eg "2009-10-00 21:00:00" **after** it has woken up. Or, more importantly **before** a wakeup time has been set. In other words, maybe Mythwakeset isn't managing to successfully set the clock at all.

If manually setting the clock works, but Mythwakeset doesn't, it's probably a permissions issue - check the section on editing your sudoers file.

---

### Post by se99paj on 2009-10-09
Thanks for the quick response, when I run:
```
$ sudo sh -c 'echo "+00-00-00 00:05:00" > /proc/acpi/alarm'
```
and then run
```
cat /proc/acpi/alarm
```
The time does increase by 5 minutes, from memory it does include the day so it returns 2009-10-09 21:00:00 instead of 2009-10-00 21:00:00

Also if I shutdown the PC does reboot 5 minutes later.

Also I think the permissions are good as I can change the alarm time using the MythWakeSet script.

To be honest I can get most of the functionality to work as I can get the PC to shutdown and restart automatically, and when using MythWakeSet the time is correctly entered into the alarm so it does turn on at the correct time. But my concern is the date isn't entered correctly, month and year are fine but the day value is always zero. This leads me to think that if I have a 3 day gap where I don't need any recordings the PC will turn itself on and off at the same time over those 3 days until it gets to the day where the recording should actually happen. Its not the end of the world if thats the case but I'd prefer it if it didn't need to do that.

---

### Post by SiHa on 2009-10-09
Can you try this?

Ubuntu 'remembers' if you've typed your sudo password for about 20 minutes, so it's important to let this time-out in oorder to test this properly.

On a fresh boot (or after not using 'sudo' for half an hour), run Mythwakeset from a terminal, as you have before. Are you prompted for a password? If yes, then it's your sudoers file. If no, then I'm not sure what else it could be if you have the commands entered in the backend setup exactly as they are in the guide.

To check Mythwakeset is running successfully from the backend you could add a statement at the end of the Mythshutdown line in your backend setup:```
sudo /usr/bin/MythWakeSet $time [COLOR="Red"]&& touch ~/Mythwake.log[/COLOR]
```This will simply create the file Mythwake.log in your home directory if it doesn't exist, and set the last access date and time. It will only do this if Mythwakeset exits with status 0(no errors).

---

### Post by se99paj on 2009-10-09
I'll give this a go this evening and post back here.

---

### Post by Mrazek on 2009-10-26
Hello,
 
for first attempts read this: [http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup)
And for integration to mythtv read this: [http://ubuntuforums.org/showthread.php?t=1176528&highlight=acpi+wakeup](http://ubuntuforums.org/showthread.php?t=1176528&highlight=acpi+wakeup) (including my last reply in this thread, there are very important notes there :-))
After implementing these tutorials my mythtv wakes and shuts down with absolutely no problem!

---

