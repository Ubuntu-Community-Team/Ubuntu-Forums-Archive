---
title: "acpi how-to for mythbuntu"
date: 2008-09-10
forum: Mythbuntu
---

### Post by spoky99 on 2008-09-10
I read and try to make work a lot of how-to about auto wake-up using acpi tool (and not nvram-wakeup) and no one is specific for mythbuntu
   Mythbuntu is quite different from ubuntu and a lot of how-to for ubuntu talk about script or tool of old release and sometime talk of configuration file that is not present in mythbuntu.
   I uderstand that using mythwelcome my be solve problem.
   I see some reply in this forum that talk about mythwelcome for help someone that ave a trouble using it but I don't fount one simple document that show me what I could do.
   Someone know how I could find one how-to for mytbuntu 8.04 or could write it?
thank's

---

### Post by morganre on 2008-10-18
Have you found a solution to your problem yet? I build a system over a year ago and still do not having it working as it should yet. I have gone through the howto and it appears to be functioning properly. It will record a show if it is left on. It wake duringthe test but not for recordings.

Asus P5B-VM
pchdtv5500
4 gb memory
1 tb Harddrive

---

### Post by spoky99 on 2008-11-05
I don't found any solution... I understand that my motherboard don't work with acpi, is possible set hour and minute but is not possible set the day.
I'm still working to understand how make it work with nvram-wakeup :)

---

### Post by db260179 on 2008-11-05
Try this thread, me and bmwman contributed a small howto

[http://ubuntuforums.org/showthread.php?t=702310](http://ubuntuforums.org/showthread.php?t=702310)

> **spoky99 said:**
> I read and try to make work a lot of how-to about auto wake-up using acpi tool (and not nvram-wakeup) and no one is specific for mythbuntu
   Mythbuntu is quite different from ubuntu and a lot of how-to for ubuntu talk about script or tool of old release and sometime talk of configuration file that is not present in mythbuntu.
   I uderstand that using mythwelcome my be solve problem.
   I see some reply in this forum that talk about mythwelcome for help someone that ave a trouble using it but I don't fount one simple document that show me what I could do.
   Someone know how I could find one how-to for mytbuntu 8.04 or could write it?
thank's

---

### Post by davidgeeee on 2008-12-06
I have an Asrock M266 motherboard and I can't seem to get it to work.

It has RTC alarm in the Bios and I can set it to wake up in the BIOS and it works.  When I try to:

cat /sys/class/rtc/rtc0/wakealarm

I get no response.  When I:

sudo sh -c 'echo "+00-00-00 00:05:00" > /sys/class/rtc/rtc0/wakealarm'

I get no resonse.  When I:

cat /proc/acpi/alarm 

I get:

cat: /proc/acpi/alarm: No such file or directory

I am assuming I need to use /sys/class/rtc/rtc0/wakealarm.
Is that right?
If I should post this somewhere else, please let me know...

Oh, this is the BIOS info from the nvram-wakeup command:

nvram-wakeup:  - The addresses you found out (read README.mb)
nvram-wakeup:  - Mainboard vendor:   ""
nvram-wakeup:  - Mainboard type:     "M266 2.00"
nvram-wakeup:  - Mainboard revision: "00000000"
nvram-wakeup:  - BIOS vendor:        "American Megatrends Inc."
nvram-wakeup:  - BIOS version:       "P1.90"
nvram-wakeup:  - BIOS release:       "09/15/2003"

---

### Post by Stevi on 2008-12-08
> **davidgeeee said:**
> I am assuming I need to use /sys/class/rtc/rtc0/wakealarm.
Is that right?

Yes, for Mythbuntu 8.10 that's right. Try [this](http://ubuntuforums.org/showthread.php?t=702310&page=11) thread. And have a look at this [wiki](http://www.mythtv.org/wiki/index.php/ACPI_Wakeup#Using_.2Fsys.2Fclass.2Frtc.2Frtc0.2Fwakealarm).

---

### Post by davidgeeee on 2008-12-08
Thanks, Stevi

Do you know how to add something to 'sudoers' as it says here:

> Change the permissions of the file so that it can execute

chmod +x /usr/bin/setwakeup.sh


If required add the script to your /etc/sudoers 

---

### Post by Stevi on 2008-12-08
> **davidgeeee said:**
> Do you know how to add something to 'sudoers' as it says here:
```
sudo visudo
```
[See here.](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake#sudo) Add what you need to the end of that file but be careful. You can exit with StRG+X. You will be asked if you want to save your changes.

---

### Post by davidgeeee on 2008-12-08
Ahhh..

So I add it to the line that starts:  "%mythtv All...." right?

Is your unit fully functional now?

---

### Post by Stevi on 2008-12-08
> **davidgeeee said:**
> So I add it to the line that starts:  "%mythtv All...." right?
Yes.
> **davidgeeee said:**
> Is your unit fully functional now?
Yes it is!

---

