---
title: "Suspend to RAM error"
date: 2008-09-21
forum: Mandriva/Mageia
---

### Post by lumos_aeternum on 2008-09-21
Hey guys, as I've said in a previous thread, I'm new to Mandriva. Most things have worked well for me. I just noticed this the other day. 

On the Taskbar, I right click on the KPowerSave Icon and Select Suspend to RAM. It does go into a "Sleep" mode, but when I open my laptop lid later it just hangs with a black screen. It never loads the system back up. Any suggestions? Did I need to configure something or run any scripts to allow this to work correctly?

I would rather not turn off my computer every time I go away, but don't want to waste tons of power leaving it on and running all day if I'm not there.

---

### Post by AdamWill on 2008-09-21
You shouldn't need to configure anything, but suspending is just always kinda a problem area :\. On some systems it just doesn't work. You can file a bug on it - it's probably a kernel issue with some of your hardware - but that's probably all. Did you check the system logs to see if there are any useful error messages?

---

### Post by lumos_aeternum on 2008-09-21
Newbie question then...how do I check the logs? Thanks for your help!

---

### Post by AdamWill on 2008-09-22
Look at the file /var/log/messages . You may need to be root to access it. There's a LOT of stuff in there, so try and just look around the times you tried to suspend.

---

### Post by pelle.k on 2008-09-25
You haven't been very specific on what you hardware is?
Are you running propreitary video drivers?

You may also look at /var/log/pm-suspend.log; it should be fairly evident if it did resume, or not.

---

### Post by lumos_aeternum on 2008-09-25
Sorry, I'm on a Dell Inspiron E1505 with 2 GB RAM...video card, etc. are all as Dell gave them to me.

---

### Post by pelle.k on 2008-09-25
> Sorry, I'm on a Dell Inspiron E1505 with 2 GB RAM...video card, etc. are all as Dell gave them to me. 
**What video card is it?**

---

### Post by lumos_aeternum on 2008-09-26
Radeon Mobility X1400

and...it won't let me read the var/log/messages...

but the pm-suspend.log worked. It appeared to have finished its resume procedures, but I still did not see the screen return to the GUI...it had a cursor and then it blinked for a second and just remained black with nothing in view. The power LED was on, the battery one blinked a few times (probably because it is plugged in and charging) and every once in a while it would blink the activity LED, but not for long...

---

