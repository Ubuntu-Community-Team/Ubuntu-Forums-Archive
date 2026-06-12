---
title: "Xorg.conf resets to defaults at login"
date: 2007-05-26
forum: Multimedia &amp; Video
---

### Post by darsu on 2007-05-26
Hi,

I have set up NVidia drivers with the Envy script on my KUbuntu 6.10 system. I use Openbox for window manager.

The **nvidia-settings** tool gives me two choices of refresh rate at 1280x1024: 60 and 75 Hz. The former appears to be default. I set my screen mode to 1280x1024 at 75Hz and save the settings to /etc/X11/xorg.conf as prompted by the program.

If I now restart the computer and observe the screen mode from the monitor's internal settings menu, the mode I chose stays correctly active up through the KDM login screen; but when I log into Openbox, xorg.conf is obliviously rewritten to its original settings and I end up in 1280x1024 at 60 Hz. How can I prevent this reset? 


A minor related issue: my monitor is capable of 1280x1024 at 91Hz. How do I go about enabling such a mode? The ModeLine entry of xorg.conf is so vaguely documented in the man pages that I'm afraid to fiddle with them.

---

### Post by josesanders on 2007-05-29
In my experience, the NVidia driver doesn't have the authority to overwrite your xorg.conf file, but it doesn't complain or tell you that it failed.  I would check that the xorg.conf file is actually modified when you save your settings.  If in fact it is not being overwritten, then just save it to a file in your home directory, then copy it to the right location manually.

---

