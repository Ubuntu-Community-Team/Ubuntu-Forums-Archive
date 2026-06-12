---
title: "Suspend Mythbuntu"
date: 2009-10-19
forum: Multimedia Software
---

### Post by jonnybignote on 2009-10-19
Realised I had this running in the wrong forum...

 I have Mythwelcome shutting down, restarting the system successfully and scheduling recordings etc, thanks to this thread

[http://ubuntuforums.org/showthread.php?t=1176528](http://ubuntuforums.org/showthread.php?t=1176528)

This is a shutdown routine but I'd like to have it work with suspend to ram. I've configured pm-utils to unload my dvb-cards prior to suspend and when called manually, suspend works ok - machine resumes and mythtv works. I have replaced the shutdown command in mythwakeup with 

gnome-power-cmd suspend
This does not work.  After successfully setting wakeup times and pre-shutdown checks, Mythwelcome countdown resets.  

Mythbackend.log states

Suspending
Failed to open connection to "session" message bus: dbus-launch failed to autolaunch D-Bus session: Autolaunch error:

I'm either putting the suspend command in the wrong place, or I'm completely on the wrong path and there is more to do to make this work.

Any help would be greatly appreciated

Jonathan

---

### Post by jonnybignote on 2009-10-19
as an update - there was a problem with the gnome command, so using the pm-suspend debugging command (had to add to sudoers) allowed mythwelcome to suspend the machine - started up fine .

If anyone knows how to invoke the suspend correctly using hal, that would be better (pm-utils does not recommend running the way I currently have it)

Will test recording schedule now

---

### Post by jonnybignote on 2009-10-19
Machine did not wakeup. I believe, according to mythbackend.log, the script which translates the utc time, was not allowed to run - the log states that suspend was invoked and then there is no more output.

More investigation needed

Any ideas?

---

### Post by jonnybignote on 2009-10-20
bump

---

### Post by jonnybignote on 2009-10-22
I guess I can assume that either no-one cares about this feature, or no-one know how to implement it.

If I understand right then...

I can use suspend and have my remote wake up my machine but no scheduling will take place - not great.

or

I can use Nvram-wakeup/acpi to shutdown my machine and it will wake for scheduled tasks but I cannot turn on the machine from my remote  - have to get down to the machine hidden at back of my tv and press the power button (yes, i'm aware I can wol) but that isn't convenient either...

Why is this great piece of software hampered in this way?

---

