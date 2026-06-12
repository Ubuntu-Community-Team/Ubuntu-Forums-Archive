---
title: "ASUS M2NPV-VM &amp; Shutdown/Wakeup"
date: 2007-10-22
forum: Mythbuntu
---

### Post by kyfehr on 2007-10-22
I am wondering if anyone else uses this motherboard (M2NPV-VM) and if they have gotten the ACPI Shutdown/Wakeup to work.

I have tried all the guides for setting the alarm and it does not work - is there a setting that needs to be used for this motherboard??

Any direction here is great. Thank you again.

kyfehr

---

### Post by spoky99 on 2007-10-28
I had one similar problem with other mb ([http://ubuntuforums.org/showthread.php?t=566642](http://ubuntuforums.org/showthread.php?t=566642))
In my motherborad acpi work, the problem is that when I power-off mythtv and the computer mythtv don't set the $time variable used by the scripts for to set the wakeup date and time and the script could not work
I see that the $time variable is corectly write only after mythtv automatic shutdown after a programmed recording event.
I'm waiting help from someone

---

### Post by skg on 2007-10-29
I have a computer with M2NPV-VM and it wakes up by acpi alarms.

I have disabled synchronization with the hardware clock on the mb, by adding "HWCLOCKACCESS=no" in /etc/default/rcS

I know this is not an optimal solution but it might be a place to start. I have tried to follow the guide on [https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)
and modified hwclock.sh but that didn't solve the problem.

regards
Stefan

---

### Post by kyfehr on 2007-10-29
Thanks Stefan,

I will try that

---

### Post by kyfehr on 2007-12-12
Just wanted to say.. that I was finally able to try changing the rcS file and it worked.. ACPI (testing worked) now working to get the system to do it automatically..

---

