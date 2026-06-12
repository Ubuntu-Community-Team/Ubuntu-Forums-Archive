---
title: "pm-suspend without sudo"
date: 2011-03-06
forum: Mythbuntu
---

### Post by veehexx on 2011-03-06
i'm trying to get IREXEC to initiate suspend when i press the power button on my controller.

however, when i run IREXEC, and press the power button, it requests sudo password.

i believe IREXEC is running in daemon mode, as set in /etc/rc.local.
however, i dont know what user context irexec is running under so im unable to confirm if that user has the right setup in /etc/sudoers.

currntly, my sudoers file is standard, apart from the following 2 lines at the very end of the file:
> myth ALL=(ALL) NOPASSWD: /usr/sbin/pm-suspend
%power ALL=(ALL) NOPASSWD: /usr/sbin/pm-suspend


'myth' is the user account that the mythtv frontend runs under. if i understood another thread here, %power is a group..

can someone help me out with how to get this working; mythtv almost setup now :)



update: sorted!
i was close with the above commands, however the correct one is> mythtvuser ALL=(ALL) NOPASSWD: /usr/sbin/pm-suspend. just for clarity, 'mythtvuser' is not a user i am aware of (the frontend login is 'myth' user); i'm guessing it's a built-in user.

---

### Post by samarthmath on 2012-09-01
use gksu pm-suspend in a script

if you want it to ask for password on resume

#!/bin/bash
gnome-screensaver-command --lock && gksu pm-suspend

---

