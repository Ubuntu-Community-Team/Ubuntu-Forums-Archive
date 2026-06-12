---
title: "Sleep on idle"
date: 2012-09-13
forum: Mythbuntu
---

### Post by jhfry on 2012-09-13
How do I make my 12.04 frontend (only) system suspend when idle.

I have it suspending manually and waking on the remote just fine.  I just want it to suspend automatically if left idle for an extended period.

xscreensaver behaves just the way I want suspend to work, but I don't see any settings there to suspend the computer... just the monitor.  

I installed the xfce-power-manager and applet and was able to get it to suspend fine... but of course it will sleep in the middle of watching something.

What am I doing wrong?

---

### Post by 2F4U on 2012-09-13
I think you misunderstood the concept of suspend. When a computer goes into suspend, the CPU and all hardware components go into a deep sleep state, so no applications are active at that time except for some parts of the kernel. I don't think that is what you want when you are in the middle of a recording, because in fact that would stop any recording. I would suggest that you read a little bit about what suspend is to get the terminology clear:

[http://en.wikipedia.org/wiki/Suspend](http://en.wikipedia.org/wiki/Suspend)

---

### Post by Henk Poley on 2012-09-13
Since you are trying to suspend a frontend-only system, there is no risk in missing recordings. I think this may help: [http://askubuntu.com/questions/138661/how-to-suspend-from-command-line-such-that-screen-is-locked](http://askubuntu.com/questions/138661/how-to-suspend-from-command-line-such-that-screen-is-locked). mythwelcome may have some settings that are used by the new 30 minute mythfrontend 0.25 timeout, if somehow using the screensaver doesn't work out that well.

For backend systems look into nvram-wakeup or the alarm device (/dev/alarm?) for the BIOS to wakeup your machine.

---

### Post by jhfry on 2012-09-13
> **Henk Poley said:**
> Since you are trying to suspend a frontend-only system, there is no risk in missing recordings. I think this may help: [http://askubuntu.com/questions/138661/how-to-suspend-from-command-line-such-that-screen-is-locked](http://askubuntu.com/questions/138661/how-to-suspend-from-command-line-such-that-screen-is-locked). mythwelcome may have some settings that are used by the new 30 minute mythfrontend 0.25 timeout, if somehow using the screensaver doesn't work out that well.


Thanks for the response.  Indeed, there is no reason NOT to suspend a frontend only system when it is idle... and I can do so quite successfully from the remote or menu options I set.

The link you provided is discussing locking the system when manually suspending the system... I definitively don't want to lock it, and I can already suspend it manually.

I have done some reading into mythwelcome, and it appears that the backend will only suspend remote backends using it... no control over frontends.  Perhaps I am wrong, but I can't find any evidence to the contrary.

I suspect I will have to create some sort of cron job that polls xscreensaver, and when it blanks, the script will imitate a suspend using dbus.  But that just seems like a kludge.

---

### Post by jhfry on 2012-09-13
I came up with my own solution.  Check it out here:

[http://www.mythtv.org/wiki/Sleep(Suspend)_When_Idle](http://www.mythtv.org/wiki/Sleep(Suspend)_When_Idle)

---

