---
title: "Audacity: Error Initializing Audio"
date: 2006-08-05
forum: Multimedia &amp; Video
---

### Post by bobonthenet on 2006-08-05
I am trying to use Audacity for creating and editing some sound files.  I've only just installed it and I'm getting this error.  I've included the screen shot.  Hopefully I've posted it correctly.  Of course Audacity is useless if I can't play or record sound so hopefully someone can help me get it working.

---

### Post by stmiller on 2006-08-05
[http://audacityteam.org/wiki/index.php?title=Linux_Issues](http://audacityteam.org/wiki/index.php?title=Linux_Issues)

You must kill the process 'esd' or 'arts' for audacity to run.

> If you use Audacity with Ubuntu 6.06 LTS "Dapper" (i.e. with the GNOME desktop) and you are greeted with this error message, try disabling the eSound (ESD) server in the Sound Preference Panel. Navigate to "System" > "Preferences" > "Sound". The Sound Preferences panel opens. Click on the "Sounds" tab. See if the box next to "Enable software sound mixing (ESD)" is checked. Uncheck it and click on the "Close" button. Audacity should now work.

---

### Post by Ambimom on 2006-08-05
I am getting the same error...I've uninstalled and reinstalled audacity and unchecked the ESD as you recommend....it still won't initialize.

Any ideas?

---

### Post by bobonthenet on 2006-08-05
Worked for me!  Thanks a bunch!

---

### Post by clibre on 2006-08-11
It' works. Thanks for the solution;)

---

