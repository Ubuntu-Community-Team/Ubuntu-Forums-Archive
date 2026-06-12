---
title: "nVIDIA: Saving Settings"
date: 2006-08-02
forum: Multimedia &amp; Video
---

### Post by E-werd on 2006-08-02
I know this is possible because it worked in SuSE 10.0...

How do you save your gamma/digital vibrance/brightness/etc so that, whenever you exit a game or snap back from a screensaver you don't have to open 'nvidia-settings' in order for them to restore?


I am thinking it might reside in /etc/X11/xorg.conf, but I'm not too sure. :confused:

---

### Post by E-werd on 2006-08-03
[IMG]http://frontiernet.net/~dlwood/bumpasaurus.jpg[/IMG]

---

### Post by arbrandes on 2006-08-05
I have the exact same problem, and it's driving me nuts.  Isn't there some global configuration file that sets the defaults?

---

### Post by tseliot on 2006-08-05
Try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

---

### Post by aribezas on 2008-04-19
I have the exact same problem.
If someone find the solution please let me now.
Many thanks

---

### Post by p1977p on 2008-04-22
> **E-werd said:**
> I know this is possible because it worked in SuSE 10.0...

How do you save your gamma/digital vibrance/brightness/etc so that, whenever you exit a game or snap back from a screensaver you don't have to open 'nvidia-settings' in order for them to restore?


I am thinking it might reside in /etc/X11/xorg.conf, but I'm not too sure. :confused:



The information resides in the ***[COLOR=DarkRed].nvidia-settings-rc[/COLOR]*** file in your home folder. The settings are loaded automatically when nvidia-settings starts, but you can load them in the background by using a script that executes ```
**[COLOR=Green]nvidia-settings -l[/COLOR]**
```  everytime you exit the game.

---

