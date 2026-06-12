---
title: "[SOLVED] Totem bad quality?"
date: 2008-12-02
forum: Multimedia Software
---

### Post by nickski on 2008-12-02
I am using totem to play movie files, like .avi for example, and the quality is really bad.  I play them in windows media player on my vista partition and they are fine.  What gives? am i missing some kind of codec or something?  It is really jumpy, and freezes...i cant figure out what is wrong.  I can really take a screenshot, so i cant really show it.  any help is appreciated.

---

### Post by wolfen69 on 2008-12-02
i can't help you with totem, as i uninstall it first thing after a fresh install. try vlc or mplayer.

---

### Post by captgadget on 2008-12-02
How do you remove it and whatabout extensions?

---

### Post by nickski on 2008-12-02
mplayer does the same thing

---

### Post by wolfen69 on 2008-12-02
are you running compiz? if so, turn it off and try the videos.

---

### Post by nickski on 2008-12-03
yes that was it, thank you very much.  I was able to make a profile in compiz to make sure my settings are saved.  In order to turn it off i just turned off visual effects under appearance.  But just in case i saved my profile.  Thanks!

---

### Post by spyder152 on 2008-12-04
Hello, I'm having the same jumpy problem as nickski, my video effect is off and still having the problems, any other suggestions, i have installed the vlc player and same thing... thanks

---

### Post by wolfen69 on 2008-12-04
did you turn off compiz as nickski did?

---

### Post by nickski on 2008-12-04
If you turn off the effects it automatically turns off compiz...

---

### Post by pluckypigeon on 2008-12-04
**for vlc: **

settings > preferences > video > output modules 

check "Advanced" then from the drop down menu select "x11 video output module"
[B]
for totem-xine:[/B]

in a terminal type ```
gedit ~/.config/totem/xine_config
```

find the line (CTRL F)
```

#video.driver:auto
```

and change it to
```

video.driver:xshm
```

**for totem-gstreamer:**

in a terminal type ```
gstreamer-properties
```

click the video tab and select

X Window System (No Xv)

apply and exit

Let me know if this works for you

---

