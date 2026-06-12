---
title: "Codec Problems (MPEG4)"
date: 2008-01-29
forum: Multimedia &amp; Video
---

### Post by handsomeDave on 2008-01-29
I'm having problems playing mpeg4 encoded movies. I can play them in the terminal like
mplayer filename.avi
but then I don't get movie controls
when I try to play them with VLC or totem, I get a green bar across the top of the screen, and other colours are messed up, anybody have any ideas how to fix this?

---

### Post by yabbadabbadont on 2008-01-29
Does it work correctly if you play them from a terminal using **gmplayer**?  That will launch the GUI version of mplayer.

---

### Post by handsomeDave on 2008-01-29
yes and no, it plays the movie, but i get an error related to the gnome-screensaver, and then i lose the controls

---

### Post by philc on 2008-01-30
I had a similar problem in the past. This might help:

[http://ubuntuforums.org/showpost.php?p=4120806&postcount=7](http://ubuntuforums.org/showpost.php?p=4120806&postcount=7)

---

### Post by handsomeDave on 2008-01-30
philc, your fix didn't work, but the link you gave had something that did

* VLC (VLC is not installed by default; you need to search in the package manager, then install)
o Start VLC and click on Settings, then Preferences.
o Expand Video and then expand Output modules. You will notice several options for output device.
o Select the item Output modules, and notice the checkbox at the bottom right that says Advanced options. Check the box, and now you have the option to select a different output device.
o Pick X11 video output
o Click on Save and you are set! 

Thank you so much:grin:

---

