---
title: "Mythtv 0.21 firewire issue"
date: 2008-03-13
forum: Multimedia &amp; Video
---

### Post by blcvegas on 2008-03-13
I upgraded my mythtv box to the latest version 0.21 and can't get my firewire input to work.  When I look at the tuners under system information, I get tuner not available for the firewire input.

I suspect a couple of possible reasons.  First, I am using the same mythtv-backend script from the previous version.  When I upgraded, it flagged that the file had been updated and asked me whether I wanted to keep the old script (with the firewire changes) or change to the new script.  I kept the old script.  If I need the new script, I don't know how to get just that file updated.

The second possib reason I can think of is that the firewire setup menu in the backnd no longer asks for which port and node you are using.  I don't see where to tell it in either the frontend setup menu or in the backend setup.

When I run firewire tester, it works like a champion.

If anyone could shed some light on this, I'd appreciate it.

---

### Post by blcvegas on 2008-03-26
I finally figured this one out.  There is apparently a bug in 0.21that causes a permissions problem. When setting up the firewire capture in the backend, it no longer requires inputs for firewire port and node.  It gets the GUID automatically, but only if the permissions are right.  The easiest way around this is to run sudo mythtv-setup and the GUID should show up.  If the backend setup is run through the regular menu selection, it won't allow an input for GUID and the firewire won't work.

---

