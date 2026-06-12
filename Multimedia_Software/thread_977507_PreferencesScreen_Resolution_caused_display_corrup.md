---
title: "Preferences|Screen Resolution caused display corruption"
date: 2008-11-10
forum: Multimedia Software
---

### Post by Deeta on 2008-11-10
I used "Preferences|Screen Resolution" to change my resolution from 1280x1024 to 1024x768.
This caused excessive screen corruption (happening upon log-in of a user) (gdm login screen still works fine and ungarbled)

I am on 8.10 and my question would be:
"Would anyone know where exactly the screen resolution too wrote its value too? Cause if I can revert it back to its previous value it should work again"


What I tried:
"GNOME(safe) session does not work and causes screen corruption too"

"envyng does not work as none of the proprietary drivers support the rv280"

"sudo dpkg-reconfigure -phigh xserver-xorg"
does not help :-/

"xfix in recovery mode"
does nothing at all (as it just edits xorg.conf)

"xrandr -d :0.0 -s 1280x1024"
crashes the X Server
 
".xprofile"
file is not present so it could not have caused the trouble (and creating one with above command in it crashes too)

---

