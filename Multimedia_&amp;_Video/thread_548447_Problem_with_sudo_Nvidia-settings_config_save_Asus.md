---
title: "Problem with sudo Nvidia-settings config save Asus laptop"
date: 2007-09-11
forum: Multimedia &amp; Video
---

### Post by zanson on 2007-09-11
i get the following error when trying to save the config files through the GUI:

ERROR: Unable to determine valid vertical refresh ranges for display device 'CMO' (GPU: GeForce Go 7600)!

ERROR: Failed to add display device 'CMO' to screen 0!

ERROR: Failed to add X screen 0 to X config.

ERROR: Failed to add X screens to X config.

ERROR: Failed to generate an X config file!



Im running Ubuntu 7.04
Asus F3JM laptop
Nvidia Geforce GO 7600
Native video res is 1280x800

i can edit the xorg.config file myself, but it's easier through the GUI to setup dual screen.

in any case, even if i can manually do the config, i still want to try and get this fixed.

i found another site where someone was having the same problem error but theirs no way to read it because it is in Czechoslovakian....
[http://forum.ubuntu.cz/viewtopic.php?pid=97456](http://forum.ubuntu.cz/viewtopic.php?pid=97456)

Thanks in advance for the help.

---

### Post by bensode on 2007-10-11
Did you ever get an answer to this?  I'm having the same issue with my Dell Precision M70 with a Go 1400.

What I'm having a problem with is if I run nvidia-settings without sudo I can setup the dual screen twinview to work when I apply.  It works but I can't save the settings so everytime I boot my laptop, I have to unplug the monitor, login, plug in the external monitor, detect displays, enable twinview on external monitor, apply, accept and then everything works fine.

If I use sudo nvidia-settings, I can save the file anywhere I need to but then X breaks.  How does it break, well it's a doozy:

If I reboot or restart X with the external monitor plugged in, the main screen is FORCED to the external monitor (physically to the right).  Login, desktop, menubar, icons all happen on the external monitor and not the laptop monitor.  The laptop monitor in essence assumes the role of the external monitor like everything was reversed.

I can't say definitively that this is a hardware problem because the BIOS splash, Grub and Ubuntu loading screen splash appears on the laptop display as it should and just as X starts, everything flips.

I've changed permissions on /etc/X11/xorg.conf to 777, I've done a chown username:username /etc/X11/xorg.conf and still the same unable to generate an X config file! error.  It's an inconvenience that I am forced to deal with and although I don't regularly reboot or restart X, it irks me.

I've also followed the manual steps in getting Xinerama to work with this nvidia 1440Go with the same problem of things getting flipped at a reboot or when restarting X.  My previous laptop was a Dell XPS with an ATI card and manually setting up dual screens was a snap with Xinerama.  I'm beginning to think this is an Nvidia hardware or binary driver problem.

---

