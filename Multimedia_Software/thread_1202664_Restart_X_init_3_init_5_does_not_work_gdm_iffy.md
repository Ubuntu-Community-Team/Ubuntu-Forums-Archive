---
title: "Restart X init 3 init 5 does not work gdm iffy"
date: 2009-07-02
forum: Multimedia Software
---

### Post by jerez76 on 2009-07-02
I am use to init 3 to shut down X server and init 5 to restart it (also restarting with logout cntrl+alt+backspace.) To my understanding, gdm stop start restart is suppose to restart X but if you do a gdm stop go back to ctrl+alt+f7 X is still up. Is that right?

---

### Post by muted1987 on 2009-07-02
if your using 9.04 i know that the ctrl+alt+backspace is dsabled there is a command i saw that will re enable it i think it is something like ```
dontzap -disable
``` maybe someone can verify this before you try this or search for this command to get the correct reference as for the drop to tty session i stil lcan use ```
sudo /etc/init.d/gdm stop
``` to stop session and ```
sudo /etc/init.d/gdm start 
``` to start x again hope this helps

---

### Post by jerez76 on 2009-07-02
i've used gdm stop/start under tty1 but going back to tty7 X is still there. i guess I am having an issue with the recent intel update.

---

### Post by muted1987 on 2009-07-02
when you type```
sudo /etc/init.d/gdm stop
``` do you get stopping gnome desktop manager [OK]

and vice versa when started 

or try not issuing the start command and going to the x screen to see if its there, sry if you've tried this but its not clear what steps you have tried.

i have a via chipset / amd processor so im no help on the intel update sry.

---

