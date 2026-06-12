---
title: "No GUI after upgrade from  94 to 910"
date: 2009-11-24
forum: Multimedia Software
---

### Post by Mandance on 2009-11-24
Hey all, first time poster long time lurker.

I have an HP mini 311 that I've been trying to get ubuntu to run on.  I finally was able to get a running build by first going to 9.4 and then jump through some hoops to get the wireless card working.  Trouble is, when i selected to upgrade to 9 10 that the GUI no longer loads.  If i select recovery I can get a login screen but thats about it.  Help?

---

### Post by snowpine on 2009-11-24
Try logging in, then typing 'startx' (without the quotes) to start the GUI... what happens? (Please post any errors here.)

(edit) it seems the HP 311 is somewhat problematic. Since I don't own one myself, I'll simply refer you to one of the "mega threads" on the topic: [http://ubuntuforums.org/showthread.php?t=1287896](http://ubuntuforums.org/showthread.php?t=1287896)

Probably you need to install the correct drivers for your nvidia; that is just my random, uneducated guess. :)

---

### Post by Mandance on 2009-11-24
Wow that was a fast reply, so i login in and enter that command.  The screen flashes off for a second and then I end up getting to following error:

 Fatal server error:
no screens found



I remember lurking extremely late last nigh and seeing someone say something about putting a command ro single somewhere will get it too boot.  Though before the upgrade everything was working fine.  It should also be noted that this is a netbook with a Nvidea Ion graphic card.

---

### Post by Mandance on 2009-11-24
Figured it out!

As most of you probably already know that all the commands are still the same as the terminal.  So I just launched the generic Nvidea drivers and its up and running.

---

