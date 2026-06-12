---
title: "Preventing blanking, latest xorg on 10.10, no gui, old settings kill xserver,"
date: 2011-02-14
forum: Multimedia Software
---

### Post by harrycam on 2011-02-14
Hi,

I cant seem to get the Xserver blanking to stop on this new distro. X version 1.9.0

On multiple machines all installed with the Maverick latest server version

Then xorg and nvidia added, Using startx from ssh to bring up the server or starting x from init and waiting for ssh command to start the app. No gui login or window manager installed, just straight X install and startx to launch it. 

Everything works fine but I cant stop the blanking. Nearly everything I do stops the server start up.


In Section "ServerLayout"  or Section “ServerFlags” of Xorg.conf

these options are rejected

        Option “BlankTime” “0"
        Option “StandbyTime”  “0"
        Option “SuspendTime”  “0"
        Option “OffTime”   “0"

from the log:

[  7579.498] (==) Using config file: "/etc/X11/xorg.conf"
[  7579.498] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  7579.498] Parse error on line 10 of section ServerLayout in file /etc/X11/xorg.conf
        The Option keyword requires 1 or 2 quoted strings to follow it.
[  7579.498] Parse error on line 10 of section ServerLayout in file /etc/X11/xorg.conf
        "“0&#8243;" is not a valid keyword in this section.
in xorg.conf 


If  put an .xinitrc file in the users home with one line to run  xset

exec xset s off

It runs the command and the server dies, I expect that is correct operation, the server expects a window manager and runs till the manager exits.  


I can put xset in the command script to run the app but that is no help if the command arrives after the screen is blanked. No keyboards or mice on the machines, display only.
 
The remaining option might be a script for run startx, sleep 2 seconds then run xset?



Firstly why don't these options work in xorg.conf?  As per the man page that comes with the install.

Failing that, how to I get xset to run when the server has just come up, without killing it off.

reg HCA

---

### Post by harrycam on 2011-02-15
I think I have found it,

not just xset s off and xset -dpms as seems to have been the normal solution quoted

But also xset s nonblank seems to be required.

H. :)

---

