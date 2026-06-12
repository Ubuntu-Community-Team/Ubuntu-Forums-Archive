---
title: "ACPI Myth never shutsdown"
date: 2009-02-26
forum: Mythbuntu
---

### Post by 4dognight on 2009-02-26
I decided to set up my myth servers to shutdown and wakeup.
I am following the mythtv/install/whatnext/acpi/wake guide.
I was able to get it to manually wakeup.
On the step to test the MythSetWake I can't get it to shutdown.
I never get any message about impending shut down.I have the Mythshutdowncheck not set in myth config. i have it set to 'exit 0'.

What does Myth use to detect 'idle'?

I should also mention, I have the 'block shutdown before client connected' unchecked. And Had no frontend running. I only have a terminal window open, while running the test.

---

### Post by 4dognight on 2009-02-27
Here are my myth settings

Block shutdown before client connected = unchecked
Idle timeout = 30 secs
Max wait for recording = 1 min
Startup before rec = 200 secs
Wakeup time format = yyyy-MM-dd hh:mm:ss
Set wakeuptime command = sudo /usr/bin/MythWakeSet $time
Server Halt Command = sudo /etc/init.d/mythtv-backend stop
Pre Shutdown check-command = exit 0

I added this to my sudo file 
%mythtv ALL = NOPASSWD: /sbin/shutdown, /usr/bin/MythWakeSet, /proc/acpi/alarm, /usr/bin/MythShutdownCheck, /etc/init.d/mythtv-backend, /usr/bin/mythshutdown, /sbin/reboot, /sbin/grub-set-default

I then ran,
sudo sh -c 'echo "2009-12-12 12:12:12" > /proc/acpi/alarm'

Then ran, cat /proc/acpi/alarm
got back
2009-12-12 12:12:12

Then made sure no frontend was running and started the backend in a terminal

sudo mythbackend &

Then tailed the backend log and waited and waited and waited. I never got any message and the backend never stopped.

Nothing else was running on the server.

Any ideas where to look???

:confused:

---

### Post by 4dognight on 2009-02-28
Well, I turned on verbose messages for 'idle'.  I still see no messages what so ever about 'idle', etc, in the backend log.

Is there something I missed which turns on the 'idle' checking in myth?

This is so frustrating because I can maually set the /proc/apci/alarm and get it to wake up. So I know its going to work , if I can ever get the darn thing to shutdown! ](*,)

---

