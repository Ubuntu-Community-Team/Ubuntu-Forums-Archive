---
title: "pm-suspend, visudo and lirc issue"
date: 2013-02-13
forum: Mythbuntu
---

### Post by davidstoll on 2013-02-13
I've been using pm-suspend as my mythtv shutdown command as well as the irxevent with the power button on my remote via lirc to suspend my machine for months.

However, about a week ago, not only does the lirc function for this command stopped working, but running the pm-suspend actually shuts down my machine.  pm-suspend-hybrid works as I would expect, but I can't use that because it doesn't put it in a state that my USB ports still have power, so lirc can't wake it back up.  That's why I originally went with pm-suspend...usb still has power.

I have (always had) this in my visudo file:
user ALL=(ALL) NOPASSWD: /usr/sbin/pm-suspend

Where "user" is my login name, so I (or mythtv or lirc or irxevent) doesn't have to be root to run it.  But that is no longer the case either.

I also have (always had) this in my rc.local file:
sudo sh -c "echo enabled > /sys/bus/usb/devices/2-4/power/wakeup"
sudo sh -c "echo enabled > /sys/bus/usb/devices/2-4/power/wakeup"

In other words, I put all the things in place to have pm-suspend work in mythtv and lirc without being root and have power to the correct usb ports to be able to wake from sleep via lirc, but it all stopped working in the last week or so, but had been running fine for months.  This is a frontend and is only used for mythtv, so nothing really gets changed, just updates as they roll in.

Can someone help me troubleshoot this?  I'm not sure what to look for to begin the process.  The only thing I can think of is a kernel update may have broken something, but again, I'm not sure how to trouble shoot that either.

Thanks for any help you can provide.
David

---

