---
title: "Synergy uses laptop resulotion on external monitor"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by gwidion on 2009-02-04
Hello All,

I have a very frustrating problem with Synergy (1.3.1) and multiple monitors.

I am using XP as the synergy server and a laptop (HP 6910p) as the ubuntu 8.10 client, with an external monitor.

The issue is this:  When I move the mouse pointer to the ubuntu desktop on the external monitor (laptop lid closed), it will only move to some arbitrary dimensions (like 1024x768) instead of the actual dimensions of the external monitor.

I can use the laptop touch pad to access the rest of the desktop real estate, so its just synergy that's messed up.

Thoughts?

---

### Post by gwidion on 2009-02-04
I found my problem.

Two actually.

First, the initial login screen for gnome was at the lower resolution.  This was teh resolution that synergy was grabbing.

Second, synergyc was not recycling between the Login screen and the users desktop.  Therefore it was not getting the users' resolution.

The documents for autostarting synergy in gnome are not very robust, for all the flavors out there. I ended up just putting the start script in the /etc/gdm/Init/Default, PreSession, and then starting the user's version with the Preferences->Sessions->Startup tool.  Seems to work well for me.

Hopes this helps someone!

---

