---
title: "Black Screen on Logout/Switch User"
date: 2009-05-18
forum: Multimedia Software
---

### Post by svtguy88 on 2009-05-18
Well, I'm finally getting some of the more minor/annoying bugs worked out of my friends Ubuntu media PC/projector setup.  Everything is going well, with the exception of the Intel graphics driver problem that a lot of us are having...but that's mostly sorted out now.  Just some issues with full screen, high-quality flash video.

Anyway, the problem at hand as that when I go to logout or switch to an admin account to change some things (I have the main account locked from doing much....keeps the non Linux minded from messing with anything they shouldn't), the screen goes black.

If I type in the password for the account I'm trying to switch to, the desktop comes back up and everything is golden.  However, it would be nice to have a visible login screen...

One other thing (not sure if it's related or not, or just a newb question....which it could be).  If I do the keyboard command to force a logout, I get a text based login, and not the GUI.  Again...this could be normal, as I'm just getting (more) familiar with linux.

---

### Post by svtguy88 on 2009-05-18
I just realized that the black screen only happens when switching from the regular account to the admin account, and not the other way around at all.

---

### Post by alfh on 2009-07-16
Running Ubuntu 8.04 logging off or switching user on IBM NetVista 83052 CG would give a black screen and force me to power down and restart manually.

Problem disappeared after disabling the ATI proprietary driver. I never used the 3D effects, so no loss, but maybe somebody who wants to use them need another solution.

I tried editing /etc/gdm/gmm.conf and -gdm.conf-custom (setting a line AlwaysRestartServer=true under the Daemon section) to no avail.

Hope this helps somebody.

---

