---
title: "Help!! I really messed things up"
date: 2006-07-13
forum: Multimedia &amp; Video
---

### Post by Icon41 on 2006-07-13
Yeah I messed up bad this time :( I tried some tutorial on screen resolution and I messed up during the thing though I got a backup of the xorg.config thing and I wan't to know how to load from the backup, im a complete noob with the terminal and console and I don't know the command to do it

---

### Post by hannes_ on 2006-07-13
log in as root

mv /etc/X11/xorg.conf /etc/X11/xorg_currepted.conf

mv /PATH/TO/BACKUP/xorg_BACKUPNAME.conf /etc/X11/xorg.conf

/etc/init.d/gdm restart   use kdm if u have kubuntu!

greetings

---

### Post by T700 on 2006-07-13
At a terminal, ```
gksudo gedit
```

Use the editor to locate the messed up copy of the file.  Make a note of the EXACT file name.  Change it to xorg.config.bak2 (or something unique).  Save it.  Now, use the editor to go to your previously saved backup and change it to the EXACT name of the original file.  Save it.

Close the editor and all open files.  Restart your computer.

Paul

---

### Post by Icon41 on 2006-07-13
its not working, I don't know where my backup is either :( I used a tutorial around these forums

and paul I cant even get into the GDK or whatever, im at a black screen that is similar to the terminal, i tried what you said and it said GDE failed to display

---

### Post by T700 on 2006-07-13
Which tutorial?

Paul

---

### Post by Icon41 on 2006-07-13
read edit

---

### Post by Icon41 on 2006-07-13
I used this tut
[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---

### Post by T700 on 2006-07-13
If you followed that tutorial, your backup should be in /etc/X11

Just open an editor using gksudo, as I mentioned earlier.  Navigate to that directory, and follow my earlier directions.  If you don't have a backup, then it gets trickier, but not impossible.

Paul

---

### Post by Icon41 on 2006-07-13
GTK ERROR CANT DISPLAY
says somthing like that, im in like a console im not in the desktop thing with the drop down menus and the desktop icons

---

### Post by arnieboy on 2006-07-13
since u are in console do the following
```
sudo cp -f /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```
make sure u dont make mistakes while typing the above and keep the cases correct (for example: its X11 NOT x11). 
restart your comp.

---

### Post by Icon41 on 2006-07-13
Problem solved, thanks arnie your a great guy.

---

