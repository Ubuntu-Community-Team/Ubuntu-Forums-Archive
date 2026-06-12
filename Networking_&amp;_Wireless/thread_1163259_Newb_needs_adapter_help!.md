---
title: "Newb needs adapter help!"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by hellothere2 on 2009-05-18
Here's what I'm getting:

ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper , it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist , it will be ignored in a future release.
WARNING: /etc/modprobe.d/blacklist line 1: ignoring bad line starting with 'lspci'
WARNING: /etc/modprobe.d/blacklist line 4: ignoring bad line starting with 'lspci'
WARNING: /etc/modprobe.d/blacklist line 7: ignoring bad line starting with 'lspci'
WARNING: /etc/modprobe.d/blacklist line 8: ignoring bad line starting with 'lsusb'
WARNING: /etc/modprobe.d/blacklist line 9: ignoring bad line starting with 'lspci'
WARNING: /etc/modprobe.d/blacklist line 10: ignoring bad line starting with 'lspci'
WARNING: /etc/modprobe.d/blacklist line 11: ignoring bad line starting with 'lsusb'
rt2870 : driver installed  
            device (1737:0077) present

Should I worry about the warnings?  At this point, I ignored them and kept going.  The link said to then do this:

uname -m
i686

[B]dmesg | grep -e ndis -e wlan

ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
ndiswrapper (import:242): unknown symbol: ntoskrnl.exe: 'MmGetSystemRoutineAddress'
ndiswrapper (load_sys_files:206): couldn't prepare driver 'rt2870'
ndiswrapper (load_wrap_driver:10:cool:: couldn't load driver rt2870; check system log for messages from 'loadndisdriver'
usbcore: registered new interface driver ndiswrapper
usbcore: deregisterting interface driver ndiswrapper
ndiswrapper (ntoskernel_exit:2671): object ede63a20(2) was not freed, freeing it now
ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
ndiswrapper (import:242): unknown symbol: ntoskrnl.exe: 'MmGetSystemRoutineAddress'
ndiswrapper (load_sys_files:206): couldn't prepare driver 'rt2870'
ndiswrapper (load_wrap_driver:10:cool:: couldn't load driver rt2870; check system log for messages from 'loadndisdriver'
usbcore: registered new interface driver ndiswrapper[/B] 

Now what?

---

### Post by hellothere2 on 2009-05-18
I installed this driver, btw, using ndiswrapper and the CD that came with the wireleusbss networking adapter (Linksys USB54GC).

---

### Post by Crafty Kisses on 2009-05-18
Well the first obvious question is, is your card working? The errors don't actually really mean anything, from the looks of it nothing is actually broken. I'm pretty sure if you rename the listed files, like for example the following:
```
etc/modprobe.d/blacklist
```
Should actually be:
```
etc/modprobe.d/blacklist.conf
```
As it says in the initial error:
```
WARNING: All config files need .conf: /etc/modprobe.d/blacklist
```

---

### Post by Elfy on 2009-05-18
Please do not post duplicates, it can confuse the issue.

Duplicate here [http://ubuntuforums.org/showthread.php?t=1162705](http://ubuntuforums.org/showthread.php?t=1162705)

---

