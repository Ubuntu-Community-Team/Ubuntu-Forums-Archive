---
title: "Changing screen resolution in recovery mode"
date: 2010-02-28
forum: Multimedia Software
---

### Post by Firebat451 on 2010-02-28
I have a simple problem for which I assume there is a simple solution, though I can't find it.  I changed monitors and my new one can't display the old resolution.  I assume I'll need to start in recovery mode, but I don't know how to use the shell at all.
In short, how do I change my screen resolution from the shell in recovery mode?

---

### Post by theLumberjack4 on 2010-03-06
I have the same problem.  I've been searching around the internet and can't find any way to do it :S

---

### Post by Firebat451 on 2010-03-07
Actually, a friend of mine got me a solution.  I had to edit my xorg.conf and manually put in my monitor's HorizSync and VertRefresh variables.

Here's my solution, I'll be as detailed as possible.

1) look up HorizSync and VertRefresh values for your monitor.  I found them by Googling my monitor's make and model and looking through the shopping section.  Most online sales have specs for the monitors.

2) Boot up in recovery mode and get yourself a root shell prompt.

3) type 'nano /etc/X11/xorg.conf
   This will open the file xorg.conf for editing

4) Under the Section 'Monitor' add the following two lines (change the values to the ones you found in step one:
   HorizSync          31-80
   VertRefresh        56-75

5) Cross your fingers and reboot.

I hope this works for you.  Good luck.

---

