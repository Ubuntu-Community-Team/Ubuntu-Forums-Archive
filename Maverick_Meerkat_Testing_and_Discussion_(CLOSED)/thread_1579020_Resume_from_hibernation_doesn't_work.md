---
title: "Resume from hibernation doesn't work"
date: 2010-09-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by fuzzdk on 2010-09-21
Hi.

I have a x61s Thinkpad. When I hibernate everything seems to work fine. But when I reboot to resume, it just starts as if no hibernation was done. It has actually worked before in 10.04, but started failing after some upgrade of 10.04.

I have looked at
[https://wiki.ubuntu.com/DebuggingKer...ibernateResume](https://wiki.ubuntu.com/DebuggingKer...ibernateResume)

but that only seems to be about fixing if the hibernation doesn't work, and the last lines of /var/log/pm-suspend.log is:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Tue Sep 21 10:29:47 CEST 2010: performing hibernate

So to me it looks like hibernation worked, but resuming hibernation do not.

So my question is, if there is any way to see why it doesn't resume from the hibernation? E.g. any log file that says why it doesn't consider the hibernated
session.

---

### Post by prshah on 2010-09-21
> **fuzzdk said:**
> any way to see why it doesn't resume from the hibernation? 

When you hibernate, the information is written into the swap. There are various things you can check:

a) Do you have enough swap space? (Ideally, 1.1~1.5 times your RAM memory). If you do not have enough swap, hibernation will still report a "success"; but that is really an acpi acknowledgement that switching to a hibernation state was a success.

b) Check the "resume" kernel parameter in /boot/grub/menu.lst (or /etc/default/grub if using grub2); it should point to your swap space (Eg: resume=/dev/sdXX or resume="UUID=somechars")

c) make sure you do not have the kernel parameters "noresume"

Please post back details if you need more help.

Unfortunately there is no log file that you can check to see why hibernation has not "thawed". You can grep your dmesg for "thaw" to see messages related to failed resume, but you won't find any if the resume has not started in the first place.

---

### Post by fuzzdk on 2010-09-21
> **prshah said:**
> 
b) Check the "resume" kernel parameter in /boot/grub/menu.lst (or /etc/default/grub if using grub2); it should point to your swap space (Eg: resume=/dev/sdXX or resume="UUID=somechars")


Thanks a lot! That was exactly what was missing. Now hibernate works again. :)

---

