---
title: "Changing Xorg settings while running"
date: 2007-07-24
forum: Multimedia &amp; Video
---

### Post by ajmedfor on 2007-07-24
Is there any way I can change the screen or layout for Xorg without rebooting? It seems that the command Xorg -screen 'LCD' or Xorg -layout 'LCDandTV' should allow me to switch between my extended screen in xinerama and using just one screen, but instead I just get the error:

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

Why is this? If there is no way to change the settings without rebooting, is there any command I can use to switch my TVout on and off without rebooting the computer? Thanks for your help!

---

### Post by scxtt on 2007-07-24
you can use ctrl+alt+backspace to restart X, w/o restarting your computer ...

---

### Post by ajmedfor on 2007-07-24
right... but there is no way to change screen settings without restarting X? Also, is there any way to do the ctrl+alt+backspace thing from the command line?

---

### Post by scxtt on 2007-07-24
no, you can't make configuration (file) changes and not gvie X the chance to re-read the files (not sure how your "Xorg -screen 'LCD' or Xorg -layout 'LCDandTV'" commands affect :0) ... you should be able to restart X (:0) by either restarting your display manager (kdm,gdm,xdm) or killing :0 - maybe even **/etc/init.d/x11-common restart** (not sure on that one) ...

---

### Post by ajmedfor on 2007-07-24
That command didnt work... basically I have my xorg.conf set up to extend my desktop onto my TV, but the only way I can figure out to change it back to displaying only on my computer is to copy the backup file of xorg.conf and reboot xorg. If this is the case, I would like to write a script which automatically  copies the files, changes my background, and restarts xorg. I have everything figured out except the restarting xorg thing... if you have any suggestions let me know!

---

### Post by scxtt on 2007-07-24
try using **sudo pkill X** ...

---

### Post by The Foz on 2007-07-25
To ease recovery while fiddling with my xorg.conf file, I usually open a remote X session from another PC and make the changes from there.

Then, if the X-server for the local session doesn't restart after the changes, I still have full GUI access to the machine (editors, command line tools, file manager, etc.) to correct the situation.

---

### Post by Randall on 2007-12-24
For the record, it is super easy to restart X for gnome:
sudo /etc/init.d/gdm restart

If you are changing X settings and want to test things out, then just log into one of the text terminals (ctrl-alt-f1). You can then edit your xorg.conf file and restart above with minimal fuss. Once your X is working, you can go back and forth between the text terminal and X. To get to X, ctrl-alt-f7 (usually).

---

