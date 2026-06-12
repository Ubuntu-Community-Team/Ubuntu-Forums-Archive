---
title: "ACPI: Correct Time Settings without internet"
date: 2011-05-05
forum: Mythbuntu
---

### Post by TelepathicSpy on 2011-05-05
Hello everybody,

I have a little problem concerning my combined Mythbuntu frontend/backend computer (Mythbuntu 10.04 with MythTV 0.24). With ACPI Wakeup it uses Hibernation to shut itself down which works very well (although I needed a lot of time to achieve this). There is still one problem left:

Time and Date is synchronized with internet servers. But in cases of having no access to it, the clock is wrong, obviously, as the computer itself uses UTC and I live in Germany (UTC + 1). Surely I know that I can change the clock in Mythbuntu to set it to "Manual" and then set the time myself. But the next time the computer wakes from hibernation, the clock is UTC again!

I think this is because I disabled the HWClock updates as it is proposed in the MythTV wiki (cf link below). But now I have no idea how I could manage it that the computer performs all my recordings (hibernating between those) when I have no access to the internet. I would be very happy, if you have any!

Thank you very much, Dirk

[http://www.mythtv.org/wiki/ACPI_Wakeup#Disable_HWclock_updates](http://www.mythtv.org/wiki/ACPI_Wakeup#Disable_HWclock_updates)

---

### Post by TelepathicSpy on 2011-05-08
One idea that came to my mind: Is there a tool / command that I could use in a script to set the clock to the correct time? 

Would be great if I could just hand in my timezone to the tool / command as it would be quite complicated to compute if it is summertime or not. Ideas, anyone?

Thanks in advance, Dirk

---

### Post by alien878 on 2011-05-09
Sounds like you aren't using the timezone settings the best way.

The system will work best if you set the time in the BIOS to UTC.  Then tell the computer what timezone you are in.  I believe the command to set the timezone is sudo tzselect.

Then, if NTP is not available, the BIOS time read at startup will be good (or at least as good as the clock itself is).

Note:  The HWCLOCK changes mentioned in the wiki are no longer necessary on my box.  You might want to check if they can be removed on your box so the BIOS time will be kept closer to real time.

More info: [https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

(if you can't set the BIOS to UTC because it is dual booting to windows, there is an alternative on this web page at the bottom)

---

### Post by TelepathicSpy on 2011-05-10
Thank you very much for the answer, I will test removing the HWCLOCK changes. The BIOS time is already UTC, by the way, and there is no Windows on it.

---

### Post by alien878 on 2011-05-10
If your clock is UTC, you shouldn't be having problems with it changing to UTC.  I suspect your problem is with an incorrect timezone setting.  The timezone does not change the clock.  It only changes how times are displayed.

Also note that Germany is currently UTC+2 at the moment.

I suggest you run tzselect and chose Europe/Germany (actually, Europe/Berlin, but tzselect asks the country).

When working, the output of date and date -u should be something like:
```
allen@violet:~$ date
Tue May 10 10:57:11 CEST 2011
allen@violet:~$ date -u
Tue May 10 08:57:12 UTC 2011
allen@violet:~$ 
```In the winter, the TZ will automatically be set to CET instead of CEST.

---

### Post by TelepathicSpy on 2011-05-10
It seems to work now (I will test this further).

I did a "sudo tzselect", chose Europe/Germany and edited /etc/default/rcS to change UTC to yes and HWCLOCKACCESS to yes  (don't know if both is necessary).

I do not know why this works now as I have chosen my timezone via GUI before; it was already set to Germany. Or does tzselect save it to another location than the GUI?

Anyway, thank you very much!

Dirk

---

### Post by alien878 on 2011-05-11
The GUI and command line timezone settings should be the same.  I just recommended the tzsetup as I couldn't remember the GUI command.

I think the UTC and HWCLOCKACCESS settings are probably what fixed the problem.  When UTC=no, it assumed the bios was in local time when it was in UTC.  While HWCLOCKACCESS=no meant that the BIOS clock was never "corrected".

---

