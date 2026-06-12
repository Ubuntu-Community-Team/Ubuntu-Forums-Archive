---
title: "Arrow Keys Don't Work Correctly in VNC MythTV Frontend"
date: 2016-07-11
forum: Mythbuntu
---

### Post by jamoody on 2016-07-11
I upgraded from Ubuntu from 12.04.5 to 14.04.4 and MythTV from 0.27.5.71 to 0.28-40.  I had to modify ~/.vnc/xstartup to the following to get the desktop to come up in VNC (several lines commented out, added startxfce4):
   #!/bin/sh
   # Uncomment the following two lines for normal desktop:
   unset SESSION_MANAGER
   # exec /etc/X11/xinit/xinitrc
   #[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
   #[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
   #xsetroot -solid grey
   #vncconfig -iconic &   
   startxfce4 &
   x-terminal-emulator -geometry 1920x1080+10+10 -ls -title "$VNCDESKTOP Desktop" &
   x-window-manager &

Both the main (TV) display and the VNC session now come up as expected with MythTV main panel.  The physical keyboard works fine, but the VNC keyboard arrow keys do not work as expected in any MythTV panel.  DOWN works like ENTER and UP, LEFT, RIGHT appear to be ignored, but in any case do not perform the intended function.  The arrow keys work as expected in other VNC applications such as gsmartcontrol, Firefox, Ubuntu Software Center, xterm, Thunar File manager; the problem seems limited to MythTV in VNC.  The remote (StreamZap), where remote UP/DOWN/LEFT/RIGHT are mapped to keyboard UP/DOWN/LEFT/RIGHT, correctly controls both the main (TV) and VNC MythTV sessions.  I'm running vnc4server 4.1.1.

Any suggestions on why VNC arrow keys are not working as expected?

---

### Post by jamoody on 2016-07-14
The problem seems to be limited to the arrow keys.  The alphabetic keys seem to work fine.  But it's kinda tough navigating around the MythTV menus without the arrow keys.  Does any body have any suggestions on how to proceed?

---

### Post by jamoody on 2016-07-15
SOLVED -
This is a problem in QT5 [https://bugreports.qt.io/browse/QTBUG-44938](https://bugreports.qt.io/browse/QTBUG-44938)
I added 
   export XKB_DEFAULT_RULES
to ~/.vnc/xstartup and it seems to have resolved the issue, arrow keys now work in VNC client.

---

