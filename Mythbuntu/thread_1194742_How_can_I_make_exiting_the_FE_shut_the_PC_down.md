---
title: "How can I make exiting the FE shut the PC down?"
date: 2009-06-23
forum: Mythbuntu
---

### Post by Mattaus on 2009-06-23
Hi all,

The title pretty much says it all: How can I make exiting the Front end, automatically shutdown the machine it is running on?

I have been googling but thus far have had no luck. I can obviously editing and add in existing menu items, and the thought did occur to me to simply add a "shutdown" menu item (actually would this work? 'EXEC sudo shutdown -h  now' or something like that?) 

I'm trying to set it up so that exiting MythTV by accident wont put you back on the desktop. Maybe if I can disable "esc" asking you if you want to quit, and have the shutdown option - or having "esc" shutting the machine down.

I'll keep looking but hopefully someone here has done this already...

Thanks!

---

### Post by tgm4883 on 2009-06-23
There is a setting in the frontend settings that will allow you to do this.  I can't check right now, but I believe it is under the general frontend settings.

---

### Post by Mattaus on 2009-06-23
I used some different search strings than I had previously on these forums and managed to find a few different threads dealing with similar issues.

I can pretty much shutdown or hibernate the system either via the default esc option or by adding my own menu item. I think if I can disable the esc option I will as I feel having a menu item is more intuitive.

---

### Post by Mattaus on 2009-06-23
Got it working exactly as I wanted it to...pretty darn easy. There was already a button commented out in the mainmenu.xml, but it did not work so I changed the behavior to what was suggested in another thread.

---

