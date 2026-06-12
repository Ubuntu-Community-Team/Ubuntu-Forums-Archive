---
title: "Monitor wont come back after it gets shutoff"
date: 2008-01-26
forum: Multimedia &amp; Video
---

### Post by gideonidoru on 2008-01-26
Hi everyone :)  Thanks for taking the time to read my thread. Basically what's happening is when I enable power management/screensaver options my monitor wont turn back on after DPMS shuts it down. I have tried hititng keys and such but to no avail, when tapping the caps lock key my keyboard light doesnt come on which says to me the computer froze. 

Also to be clear, I'm only having DPMS shutdown my monitor and not touch anything about my PC (not standby/shutdown anything) 

I'm using Ubuntu 7.10, a Samsung SyncMaster 225BW @ 1680x1050. I have an ATI X1600 and the latest (8.10) official ATI drivers. Also I have an APC X S 800 backup unit.

Ive tried manually setting just DPMS options in my xorg.conf with a manual setting for powering off the monitor. 

Thanks again!

---

### Post by gideonidoru on 2008-01-26
bump, posted at a weird hour

---

### Post by gideonidoru on 2008-01-27
Worked with soundray in the #Ubuntu channel about it for awhile. Tried a variety of commands to shut it off and all of them seemed to work well (no freezes) except when running:

> mark@isildin:~$ /etc/acpi/screenblank.sh 
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xset:  unable to open display ":0"

Same results when ran as SUDO, also the program [Brightside]("http://packages.ubuntu.com/dapper/gnome/brightside") would freeze my computer when setting an edge option to "Enter DPMS Off Mode". Weird I know. Any suggestions?

---

