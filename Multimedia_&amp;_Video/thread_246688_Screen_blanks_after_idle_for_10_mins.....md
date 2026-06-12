---
title: "Screen blanks after idle for 10 mins...."
date: 2006-08-29
forum: Multimedia &amp; Video
---

### Post by DDM on 2006-08-29
And despite my best efforts I cannot prevent this from happening. I've killed  xscreensaver and the gnome screensaver, set the power management app to never disable the monitor, checked the BIOS, and I've run out of ideas. And I should clarify the thread title, I really mean that the screen blanks after 10 mins without mouse or keyboard input (duh)

TIA for any help

---

### Post by Sam on 2006-08-29
> **DDM said:**
> And despite my best efforts I cannot prevent this from happening. I've killed  xscreensaver and the gnome screensaver, set the power management app to never disable the monitor, checked the BIOS, and I've run out of ideas. And I should clarify the thread title, I really mean that the screen blanks after 10 mins without mouse or keyboard input (duh)

TIA for any help

Try```
xset -dpms
```

---

### Post by cyberdude on 2006-08-29
add this to the serverflags section in xorg.conf  (create the section if it does'nt exist)

Section "ServerFlags"
    Option        "blank time" "0"
    Option        "standby time" "0"
    Option        "suspend time" "0"
    Option        "off time" "0"
EndSection

---

### Post by DDM on 2006-08-30
Thanks, that xorg.conf thing worked. This computer is also my TV for the next few weeks, and getting up every 10 mins to move the mouse was very annoying. Sorry I didn't get back sooner, my ISP decided to take the day off or something.

---

### Post by carnageblood on 2007-12-31
try this```
xset s noblank
```
more info [here]("http://www.shallowsky.com/linux/x-screen-blanking.html")

---

