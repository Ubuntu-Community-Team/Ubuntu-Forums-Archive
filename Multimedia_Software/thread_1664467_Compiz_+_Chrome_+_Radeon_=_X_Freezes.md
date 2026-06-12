---
title: "Compiz + Chrome + Radeon = X Freezes"
date: 2011-01-11
forum: Multimedia Software
---

### Post by Onion Avenger on 2011-01-11
Here's the problem, I have no idea what exactly is causing this bug, I've searched online and in the forums, and the bug just isn't readily reproducible.  So here goes, first with the symptom:

I have a Dell Inspiron e1505 running Ubuntu Maverick (i386).  The video card is an ATI Mobility Radeon X1300, which uses the radeon driver.  I've used Ubuntu ever since Dapper and I think it was in Karmic that I first started noticing this strange bug (it's happened in every Ubuntu release since then): sometimes, X just freezes on me.  It's not a total freeze because I can move the mouse pointer around, but the desktop is unresponsive.  However, I can VT-switch and work from a shell without any problems.  Upon examining the running processes in [FONT="Courier New"]top[/FONT], nothing seems out of place.  No single process is hogging CPU or memory, system load is good, everything looks fine.  I've checked all of the system logs, Xorg's log, and the .xsession-errors log.  Nothing wrong that I can tell.  Whenever I VT-switch back to X, I can still move the mouse pointer around, but still the desktop doesn't respond.

I've found that I can restart X ([FONT="Courier New"]sudo /etc/init.d/gdm restart[/FONT]), but this of course means I lose all my windows in X.  X restarts just fine, but the system seems a little unstable to me.  For instance, pulse audio doesn't always seem to work.  A reboot clears everything up, however.

Now for the trigger.  I can't figure out what causes the freeze!  At first I thought it was Flash locking up on me, but I don't think that's the case anymore.  Then I noticed it seems to happen more when I use Google Chrome than Firefox.  Finally, I've tried disabling Compiz for over a week and the bug has not showed up.  As soon as I re-enable Compiz and spend five minutes with Chrome, then I have this X freeze.  It seems to me that it usually happens when I'm in the middle of scrolling a page in Chrome.  But it seems to happen at other times, as well.  I can't seem to reliably reproduce the bug.

The problem is I don't know if it's a bug in Chrome, Compiz, the radeon driver, something in the kernel, or something else altogether.  What am I missing?  How can I further debug this problem?

---

### Post by scaltro on 2011-04-24
Same here:

* Ubuntu Natty updated to last sources (24th April 2011)
* AMD/ATI Mobility Radeon HD 4500 Series 
    -- > with AMD/ATI Proprietary Driver 8.84.6-110324a-116088C-ATI
* Compiz Fusion

I have the same issue with Chromium and Chrome.
Where is better to write down the bug?

Happy Easter!

---

### Post by Onion Avenger on 2011-04-25
That's annoying that the problem still exists in Natty. For the record, I think I've found that the issue is some Compiz plugin. If I run Compiz with all defaults, the bug never shows up. If I import a file that has all of my Compiz settings, then the bug is triggered within a few minutes of Chrome usage.

I haven't really had the time to selectively enable and disable plugins to track it down, but that's what I've found. Are you running Compiz with the defaults or did you tweak the settings somewhat?

---

### Post by Yellow Pasque on 2011-04-25
If you can figure out how what triggers it, I'll submit the bug report (I have a Radeon 4550 and a Natty install with fglrx) and try to get a backtrace using gdb.

---

### Post by Onion Avenger on 2011-04-26
Sorry, I don't have much time right now to debug this, but I can at least give you the config file that triggers it for me: [http://paste.ubuntu.com/599459/](http://paste.ubuntu.com/599459/)

This was generated using the profile manager of CCSM. 

It's interesting that both of you are using fglrx, whereas I'm using the radeon driver.

---

### Post by Yellow Pasque on 2011-04-26
> It's interesting that both of you are using fglrx, whereas I'm using the radeon driver.
I run the open-source driver on my desktop, though I don't use Compiz there.

---

