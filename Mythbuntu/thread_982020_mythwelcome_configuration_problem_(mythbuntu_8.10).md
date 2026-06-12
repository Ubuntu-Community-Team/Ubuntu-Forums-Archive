---
title: "mythwelcome configuration problem (mythbuntu 8.10)"
date: 2008-11-14
forum: Mythbuntu
---

### Post by spoky99 on 2008-11-14
I'm using mythbuntu 8.10 I want use the nvram-wakeup.
My motherboard isn't official supported but, using the nvram-wakeup script, I found the correct nvram-wakeup.conf file and I understand that I could reboot the computer for make work nvram-wakeup but I'm not in able to understand how I could set mythwelcome and mythtv-setup for make work it.
this is my configuration of mythwelcome
command to Set Wakeup Time: sudo /usr/sbin/nvram-wakeup -A -C /etc/nvram.wakeup.conf --settime $time
Wakeup time format: time_t
nvram-wakeup Restart Command: sudo /sin/grub-set-default 5
Command to reboot: sudo /sbin/reboot
Command to shutdown: sudo /sbin/poweroff
Command to run Xterm xterm -fa Courier -fs 14
Command to start frontend: /usr/bin/mythfrontend

mythtv-setup
Startup command: "blank"
Block shutdown before client connected: selected
Idle shutdown timeout (secs): 15
Max. wait for recording (min): 10
Startup before rec. (secs): 120
Wakeup time format: yyyy-MM-dd hh:mm
Command to set Wakeup Time: sudo -H /usr/bin/mythshutdown --setwakeup $time
Server halt command: sudo -H /usr/bin/mythshutdown --shutdown
Pre Shutdown check-command: /usr/bin/mythshutdown --check

I start with mythwelcome, i select one recording program and when I exit from mythtv mythwelcome open it's windows, show me the future recorded program, start the count down and the computer goes down but... don't reboot immediately and don't write in the bios. What error I made?
I think that is a time format problem, I don't understand why in some configuration text i put the $time in some other time_t and... I set the time format to yyyy-MM-dd hh:mm.
If $time is one variable.. what application convert day, hour and minute in "seconds since unix epoch"?
thanks for help

---

### Post by Roebi on 2008-11-18
Hello,

Have you checked this thread:
[http://ubuntuforums.org/showthread.php?t=305751](http://ubuntuforums.org/showthread.php?t=305751)

This works perfectly for me, since two years already.

On some motherboards, a restart is necessary in order to set the wake-up time. So you need to reboot and tell the GRUB loader to power off. It is all explained in the thread above.


Good luck,

Roebi

---

### Post by spoky99 on 2008-11-18
> **Roebi said:**
> Hello,

Have you checked this thread:
[http://ubuntuforums.org/showthread.php?t=305751](http://ubuntuforums.org/showthread.php?t=305751)

This works perfectly for me, since two years already.

On some motherboards, a restart is necessary in order to set the wake-up time. So you need to reboot and tell the GRUB loader to power off. It is all explained in the thread above.


Good luck,

Roebi
I just make it, my mobo for make work nvram-wakeup could reboot and poweroff. I modified grub, understand what is the default number etc etc.
My problem is that I'm not sure of the "configuration text" into mythwelcome and I also see that the new version of mythwelcome add a new configuration line that aren't in the past how-to.
I had also some problem with visudo, it work for a wile only from terminal ad after the same command line ask the password, and I suppose that mythwelcome don't work for this reason.
Did you know if mythwelcome launch the commad like the user or.. like mythtv user?

---

