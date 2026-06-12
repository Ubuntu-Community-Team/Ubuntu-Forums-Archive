---
title: "Ejecting DVDs from MythDVD"
date: 2007-02-01
forum: Multimedia &amp; Video
---

### Post by josesanders on 2007-02-01
I can't get DVDs to eject using the command in MythTV.  Does anyone know of a way to get this to work so I don't have to exit MythTV, go get a mouse, reach back behind my system and plug it in, and right click on the DVD and select eject?  That's really tedious.

---

### Post by kevinlyfellow on 2007-02-02
I'm assuming that you have an eject button set up like so...

[http://www.mythtv.org/wiki/index.php/Eject_Button](http://www.mythtv.org/wiki/index.php/Eject_Button)

Can you confirm that the command `eject` works in your terminal?

---

### Post by josesanders on 2007-02-02
The eject command works from the terminal, and I modified dvdmenu.xml in the eject button section to be:
<action>EXEC eject</action>

It still doesn't work

---

### Post by kevinlyfellow on 2007-02-04
Is it possible that the comp is mounting the dvd as a filesystem, and therefore preventing it from ejecting?  I'll be honest, I'm grasping at straws here... hopefully someone more knowledgeable will pick this up

---

