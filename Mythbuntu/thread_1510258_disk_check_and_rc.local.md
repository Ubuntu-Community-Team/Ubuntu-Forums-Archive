---
title: "disk check and rc.local"
date: 2010-06-15
forum: Mythbuntu
---

### Post by zapstrap on 2010-06-15
I recently moved to 10.04, and yesterday was the first time the automatic disk check came up when the machine was booting.  There were no problems reported with the disk, but after booting, I noticed that a bunch of stuff was broken.  No lirc, no irexec, and no TV tuners.

It looks like rc.local did not run.  Rebooting fixed the problem, but this should not have happened.  The machine wakes up to make recordings, and one of the tasks rc.local looks after is configuring the tuners in the machine.  If rc.local doesn't run, no tuners are configured, and no recordings are made.  How do I fix this?  Can I force a reboot after disk checking?

---

### Post by zapstrap on 2010-09-09
Anyone?  Since after fsck runs (I assume it's fsck) the machine does not correctly launch the myth backend (or anything else) I would prefer to just reboot after the disk check.  Is there an easy way to do this?

---

### Post by ian dobson on 2010-09-09
Hi,

The fsck is called my the mountall script that is configured/called by the upstart script in /etc/init/ mountall.conf

Maybe try disabling the --deamon option for mountall or maybe the console output option for upstart (I remember seeing a bug with a race condition with console output/tty devices being created too late). Maybe mountall returns an error code if it runs a fsck and you can use this to reboot.

Sorry that I don't have a simple do this and all is OK, but I hope it helps.

Otherwise just add a call for rc.local to your crontab as a @reboot time, nasty but if it works......

Regards
Ian Dobson

---

