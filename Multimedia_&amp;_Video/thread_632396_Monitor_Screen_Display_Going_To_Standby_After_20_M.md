---
title: "Monitor Screen Display Going To Standby After 20 Minutes"
date: 2007-12-05
forum: Multimedia &amp; Video
---

### Post by mig5 on 2007-12-05
I'm having a problem on Xubuntu.  I'm trying to watch films and every 20 minutes the screen is going into power saving mode.  I believe this is because xubuntu stops transmitting the monitor signal after 20 minutes of inactivity (I'm obviously not moving the mouse/typing while I watch).  I need to change this setting, and make it so the monitor signal doesn't stop being transmitted just because I'm not doing anything.
I've tried settings -> screen saver settings, but even if i set the 'consider idle' time to 2 hours (the max) the screen still acts as there is no signal from the computer after 20 minutes of inactivity.  I have also looked in the Nvidia settings, but not found anything there either.

---

### Post by Jeff250 on 2007-12-05
Try putting:
```
Option "DPMS" "Off"
```
... in the "Device" section of your xorg.conf file.  I suspect that X will need to be restarted as well before this setting will take effect.

---

### Post by mig5 on 2007-12-05
OK, I've done that.  I'm going to leave the computer idle for 20 minutes, then I'll know whether it worked.

---

### Post by mig5 on 2007-12-06
Nope, it didn't work.  I'm wondering maybe instead of Option "DPMS" "Off" it should be Option "DPMS" "False"  (the other options i have in xorg.conf are either true or false).

---

### Post by mig5 on 2007-12-07
[COLOR="Gray"]bump[/COLOR]

---

### Post by mig5 on 2007-12-09
[COLOR="Gray"]Bump[/COLOR]

---

### Post by Catalyst2Death on 2007-12-14
I'm not sure, but if you make sure and backup your xorg.conf file, and your comfortable copying it back to the directory from a command line... you can play with whatever settings you want, and if x11 fails to start you just copy the working xorg.conf file back into /etc/x11/xorg.conf...
I think I have the path right....

---

