---
title: "window manager 'not responding&quot; logout/restart/shutdown"
date: 2010-12-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Amroozy on 2010-12-07
i get this error "window manager not responding" every time i try to logout or restart or shutdown... it's asks to wait or i have option to force killing it.. but when i force it i get errors when i login
hope someone has fix for it..

---

### Post by efflandt on 2010-12-07
The "WindowManager not responding" for logout/reboot/shutdown seems to be the norm for now (at least for me).  Not sure if it has anything to do with the **nm-applet memory leak**, but I do not have that problem if I log into a Failsafe session, in which case nm-applet does not appear as a process (dhcp wired network connection still works).

I generally have no problem logging into GNOME Session with Unity working using nvidia drivers on a regular 64-bit natty install (alpha1 plus updates).  If nothing appears but the background, logging into a console (Ctrl+Alt+f1) and doing **sudo restart gdm** seems to clear it up.

I do have issues with applets crashing in GNOME Classic Session.  And even though nm-applet bombs out (bomb icon in System Monitor) it grows.

---

### Post by mc4man on 2010-12-08
Atm I don't bother with the power button in unity for anything
Ctrl+Alt+Del and then use button on login screen is quicker and cleaner.

(For the present Ctrl+Alt+Del is one of the more useful unity tools

---

### Post by kyleabaker on 2010-12-08
I'm seeing compiz not responding when I logout/shutdown/restart, but on login, it fails to load on its own so I have to launch it with a script (compiz --replace &).

---

