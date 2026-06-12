---
title: "Audacious Problem..."
date: 2008-10-04
forum: Multimedia Software
---

### Post by dfrandin on 2008-10-04
I'm running the Audacious music player (v 1.5.0) on Ubuntu 8.04, and seem to have gotten it into what seems to be a hidden mode.. Instead of the normal windows being seen when starting the program, I only get a small docked icon on the taskbar. The program works fine, from the dropdown menus there, but I'd like to get it back to normal.. I've looked around in the ~/.config/audacious/config and see nothing obvious.. I posted this very same question on the Audacious forums a week ago, 31 people have read it, and nobody has a fix.. Thought I'd try here, since this *is* Ubuntu, and it *is* multimedia... :->

Dave

---

### Post by mc4man on 2008-10-04
Have you tried deleting the config file in ~/.config/audacious/
Delete the accels file also.

---

### Post by markbuntu on 2008-10-04
Do you have the Show Player box unchecked?

---

### Post by dfrandin on 2008-10-05
Thanks for the replies... After snooping around a bit more, found audtool, and its mainwin-show, which seems to have fixed the problem.. Earlier I had tried deleting the ~/.config/audacious/config, with no effect... 

Thanks
Dave

---

