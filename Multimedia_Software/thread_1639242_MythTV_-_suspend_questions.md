---
title: "MythTV - suspend questions"
date: 2010-12-06
forum: Multimedia Software
---

### Post by Bentley8 on 2010-12-06
I have an older computer I'm trying to use as a PVR.  I've got a Hauppauge PVR-150 card and MythTV 0.23 installed.  I'm running Ubuntu 10.10, but do have the Mythbuntu Control Centre installed.  It's a combined frontend and backend.

I can watch live TV and record shows, sometimes.

My problem has to do with suspending the computer.  I use this computer for web browsing, gaming, and watching flash movies.  I leave it on all the time and just let it go to suspend (S3) when it's idle.  I tap the keyboard, bring it up and use it for a while, then leave it alone so it goes back to suspend.

However, if I have a TV show I want MythTV to record, it won't wake from suspend to record it.  How do I set it up to do this?

I performed the Suspend and Resume tests in the 'System Testing' utility and it passed, so the system is capable of suspending and waking itself on a schedule.  I just don't know how to tell MythTV to do this.

Also, if it's recording something in the background, the system doesn't see this as activity, and it will suspend in the middle of the program, and MythTV stops recording.  How do I prevent a suspend when the backend is recording?

It's a noisy computer (fan noise) so I don't want to leave it on all the time.  I tried using ACPI wakeup but it won't shut down after a recording, even if the frontend is not running, besides I like the immediacy of just resuming from suspend.

Any ideas?

---

### Post by Bentley8 on 2010-12-07
Bump with great justice!

---

### Post by Bentley8 on 2010-12-08
myth-bump-u

---

### Post by AKADAP on 2010-12-08
As far as I know the ACPI method is the only method that works with myth. (works great for me).

The suspend you are using is probably part of the screen blanker. Whatever it is, it has no knowledge of MythTV, and no idea when MythTV needs to have the computer awake. All it pays attention to is the keyboard, and the mouse.

If you haven't already found it look at this:
[http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup)

specifically the section labeled "Desktop users". With this setup, you log out when you want to allow the system to automatically power up and down, and login when you want the system to run continuously.

---

### Post by Bentley8 on 2010-12-20
Okay, I've spent the past week experimenting with ACPI wakeup to see if I can get things working properly.

The reason I wanted to go the suspend-to-ram route is because when I use ACPI the system will wake as it should, record as it should, but when it shuts down something odd happens.  The power button turns amber on the computer and monitor and it's no longer responsive.  This is not a sleep state.  The system is dormant, with no fans or hard disks spinning.  It's almost like it's off, but not quite.  It won't wake if you press any keys on the keyboard, and pushing the power button does nothing. Most importantly, it will not wake on its own to record another program.  I have to press and hold the power button for a few seconds to shut the system completely down.  If I try and restart it right away, it just goes back to that same non-responsive state.  I usually have to wait a long time, an hour sometimes, before I can restart the computer and have it back in use.

I did a complete reinstall of Ubuntu and MythTV, basically a virgin, vanilla system.  Problem persisted.

I thought I was dealing with a hardware component issue, probably the power supply.  So, I switched over to another computer (same make and model - Dell GX270) which I have no problems with, and the problem persisted.  I went back to the original system and left it running for days, pushing the limit, having it record show after show, never letting the system shut down.  Ran fine, recorded everything, never had a hiccup.  But when it tries to shut down on it's own, that's when I get this problem.

I started using MythWelcome, using the instructions on the web site given above, to see if that would change anything.  It didn't.

So, I'm back to where I started.  Any ideas on figuring out where the problem lies?

---

### Post by BicyclerBoy on 2010-12-21
I have heard from MythTV forums that the ACPI on core2duo chipset motherboards (and later) usually work.
Your box pre-dates this processor ?

Can't offer any other advice because I just use the bios RTC to wake the PC at a fixed time. Manual shutdown.
I gave up on Suspend & hibernate as they never appeared to work on my setup from *buntu 8.04-10.04.

---

### Post by Bentley8 on 2010-12-22
It's a Pentium 4 processor.

I read on the Dell support forums that the solid amber light indicates a problem with a component, usually the power supply.

So, I removed everything off the motherboard, unplugging it all, including the processor and RAM and CMOS battery.  Plugged everything back in and now the amber light problem has gone away.  In a sense.  Now, the power light isn't amber when it hangs up, it's green.  

After recording, instead of MythWelcome shutting it down, the monitor goes to sleep, fans and everything keep purring right along, like it's halfway going to shutdown and hanging, and not responding to keyboard activity.  I have to press and hold the power button for a few seconds to make it completely shut off.  Wait a few minutes and restart.

Also, now the computer won't wake up to record.

I figured the BIOS might be corrupted so I flashed it and it still won't wake up.

Is there a log file somewhere that might shed some light on what's going on?

---

### Post by Bentley8 on 2011-01-12
Success.  Finally.

Okay, in looking at the ACPI Wakeup - MythTV wiki I noticed a statement that said some computers may have a problem with HPET and to disable it by modding the kernel parameters at boot.  

I figured what the heck, and put the HPET=disable parameter in the right places in grub2, and it worked.  ACPI shutdown and waking works.  It's been working steadily for a week now with no hiccups except one (for some reason it set the wake up time in epoch time about a minute before the current system time -- still can't figure out why it did that, but it didn't hurt anything -- just kept the system from shutting down).

Now, I still wanted to do suspending and was able to get that working as well, using ' sudo sh -c "usr/sbin/pm-suspend" ', but the PCI slot/riser that the PVR-150 tuner is on does not wake from S3, but from S5 (according to cat /proc/acpi/wakeup).  The BIOS of the system does not support waking from S5, only S3.  The result was that my system would go to sleep and wake up beautifully, but the tuner card would never turn back on.  Dang.

So, it looks like that just won't work. An irreconcilable difference.  I'll use ACPI to shutdown/wake instead.  

But I did want to give a final update and report that HPET was the root of the problem.  I haven't noticed any real problem with disabling HPET (except maybe that one time warp I mentioned earlier).

---

