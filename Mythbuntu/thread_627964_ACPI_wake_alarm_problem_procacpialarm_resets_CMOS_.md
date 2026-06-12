---
title: "ACPI wake alarm problem: /proc/acpi/alarm resets CMOS clock and date"
date: 2007-11-30
forum: Mythbuntu
---

### Post by purdueee on 2007-11-30
I have searched all over the web for a solution to this and I found one similar issue on a mail list post without any responses. The poster shares my brand of mobo, but this was a while ago:

[http://www.mythtv.org/pipermail/mythtv-users/2006-December/160583.html](http://www.mythtv.org/pipermail/mythtv-users/2006-December/160583.html)

Note that his correct time remained, but my time and date are both reset.

I followed the instructions at: [http://www.mythtv.org/wiki/index.php/ACPI_Wakeup](http://www.mythtv.org/wiki/index.php/ACPI_Wakeup)

setting /proc/acpi/alarm works-- I shut the system down and it wakes up as expected.

The problem is that the CMOS clock and date are reset to Jan 1st 12AM of the current year.

This problem only exhibits on a boot from the alarm, manual boots seem to function as expected.

System specs:
Mythbuntu 7.10 64bit version, up-to-date installed within the last 7 days from the official live CD, no kernel changes or any other packages intalled.

Mobo: Biostar TF7050-M2

Does anyone have any ideas?

---

### Post by tohc1 on 2007-12-11
You could always set up one of the automatic clock adjustment programs - not sure what there called as I've never used them but they contact a time server on the internet and change the system clock accordingly.

If you set it to run when the PC boots - at least you will have the right time.

Not sure what else you can do.

I think this may the sort of thing...

[http://ubuntuforums.org/showthread.php?t=928](http://ubuntuforums.org/showthread.php?t=928)

---

### Post by curryrice71 on 2008-09-16
Were you able to resolve this? I am running into this same problem now too. It's not a huge deal because I can get ntp to update after the OS finally boots up, but now since the CMOS date and time is wrong, linux/ubuntu thinks that the drives have not been checked for like 996 days and it checks the hard drives every time it boots.

---

