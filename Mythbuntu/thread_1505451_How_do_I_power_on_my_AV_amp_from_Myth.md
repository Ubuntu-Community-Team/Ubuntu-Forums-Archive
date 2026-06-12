---
title: "How do I power on my AV amp from Myth?"
date: 2010-06-09
forum: Mythbuntu
---

### Post by tobiz on 2010-06-09
My 8.10 Mythbuntu setup drives the screen via an HDMI connection through a Marantz SR5002. The SR5002 can be put put into and woken up from a power saving state via commands to its RS232 port from the Myth box, this I've tested. Question is where in the Mythbuntu startup scripts can a script be run to wake up the SR5002, as early a possible, certainly before X starts?  Also where in the shutdown sequence can a script be run to put the SR5002 to sleep? Mythbuntu is set up to power down the PC until either woken up by the BIOS clock or wake-on-lan. Grateful for some ideas on these.

---

### Post by ian dobson on 2010-06-09
Hi,

When mythbuntu starts or better said when linux starts, the first process that starts is upstart. Upstart starts all processes defined in /etc/init, so all you need to do is add your script that wakes up your reciever to a startup script in /etc/init.

Have a look at how other scripts are configured and create a new configuration that starts are early as possible. Maybe look at using the "on start" event to fire your script.

EDIT: Woops, just seen your using 8.10 so you need to use scripts from /etc/rc2.d/ rather than /etc/init. In /etc/rc2.d you'll see symbolic links to the actual scripts in /etc/init.d, the links will have the name something like S88mysql and S99mythtv. This means the mysql will Start at the 88th position and mythtv will start at the 99th position. Linux counts from 1 to 99 starting each script that starts with S then to counter.

If you need any more help let me know.

regards
Ian Dobson

---

### Post by tobiz on 2010-06-09
Thanks for the info.  I'm looking at using update-rc.d for setting up the scripts which I written and tested off-line so far.  If it works I'll let you know.

---

### Post by tobiz on 2010-06-10
That all seems to work now.  I installed the script using update-rc.d using params of "myscript defaults 20 20" so as to get it to power up/down the SR5002 as early as possible in the startup/shutdown sequences.  Thanks for the help. Rgds tobiz

---

