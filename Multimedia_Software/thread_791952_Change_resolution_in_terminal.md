---
title: "Change resolution in terminal?"
date: 2008-05-12
forum: Multimedia Software
---

### Post by BrokeEnthusiast on 2008-05-12
Okay so I have been stuck with an 800X600 screen resolution for a couple of days now so I decided to change it.  I went into the screen resolution menu and the auto detect didnt find my monitor so I went down to Mag and browsed the monitor list it had and selected what I thought was mine. apparently I selected the wrong one because now when I startup ubuntu my screen says 79.9 or something MHz are out of range please select different resolution.  My problem is that I cannot select another resolution because the screen just stays black... so I figured i could boot up in restore mode and Im at the terminal and I dont know what to type in to fix this problem.


I have tried :

cd /ect/X11/

but it says that no such file or directory, also I tried xrandr --auto and it said cant open display.  any help is apreciated!!  Thanks

---

### Post by nick_h on 2008-05-12
The directory you were looking for is /etc/X11.

To fix your problem try:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

