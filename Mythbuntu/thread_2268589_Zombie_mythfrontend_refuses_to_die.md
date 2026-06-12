---
title: "Zombie mythfrontend refuses to die"
date: 2015-03-10
forum: Mythbuntu
---

### Post by MoebusNet on 2015-03-10
Mythbuntu 14.04.2 fe/be fresh install version 0.27+fixes. Install completes sucessfully, boots and starts mythfrontend, reports connected to mythbackend. The 'Escape' key pops up 'Do you really want to exit MythTV?' Choosing 'No' returns to mythfrontend; choosing 'Yes' locks up the system (clock time no longer advances, etc.) I can't change to a different TTY, as F1 thru F12 have no effect at any time.

BTW, I do have the traditional error message about 'cannot update nvidia-331 driver' which is all the rage nowadays.

Mythbackend is unconfigured because I can't get out of mythfrontend to get to it.

Suggestions welcome, I've got 8 hours and counting on this install attempt. I sure wish mythfrontend did not start by default on a new install...

---

### Post by Lester_Burnham on 2015-03-10
Hi,
Can you Alt+tab to get the desktop. If not can you ssh in and remove the mythtv.desktop file from ~/.config/autostart/
If you can get rid of that file. Reboot and it will not autostart the frontend.
Lester

---

### Post by MoebusNet on 2015-03-10
@Lester_Burnham - Thanks for the suggestion. Alt+Tab popped up an icon, but immediately returned to mythfrontend when released, so no joy. On the bright side, I walked away from the HTPC with mythfronted shutdown selected, and after an hour (an hour!) mythfrontend closed, allowing me to configure backend, frontend, etc. Needless to say, I immediately deselected autostart mythfrontend in Mythbuntu Control Center.

The only thing I can think of that might have caused this is that my HDHomerun Plus was plugged directly into my HTPC rather than through a router; I changed that and all else went swimmingly.

I'm going to mark this as 'Solved' even if it isn't. I hope the devs will rethink the whole 'autostart mythfrontend by default upon install' thing; it is so trivial to change once everything is configured.

---

### Post by Lester_Burnham on 2015-03-10
Hi,
Boy... You've got some patience :)
I think there's some lingering issues in 14.04 still. Like network changes through the GUI have a long pause after clicking edit. Shutting down via the mythtv menus as you had.

If networking had an involvement in your problem, maybe that was the issue on the front end only machine I had issues with.
Lester

---

