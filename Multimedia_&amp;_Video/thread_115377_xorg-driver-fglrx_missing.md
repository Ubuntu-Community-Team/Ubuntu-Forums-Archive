---
title: "xorg-driver-fglrx missing"
date: 2006-01-10
forum: Multimedia &amp; Video
---

### Post by tornadotsunamilife on 2006-01-10
When using the command: sudo apt-get install xorg-driver-fglrx it says that it is missing (the file/repository, sorry new to this sort of thing). I believe it is the source of the problem in which the x server doesn't work using either the ati or vesa driver (which are installed) and I'm hoping this driver will fix things. My current card is an X850XT(PCI-e) and I should add that I cannot actually access any desktop (GDM?) but can use commands in a command prompt style thing.

Sorry if this is in the wrong area (already posted something similar in 'support')

TIA

---

### Post by Gentleman on 2006-01-11
edit your xorg.conf - file (#sudo nano /etc/X11/xorg.conf) and add "Option  "noaccel" to the "device" section (I think it uses the "ati" driver) 

Now you can start x with: #sudo /etc/init.d/gdm restart without hardware accelation.

update ubuntu and just folow this how-to to install the ati drivers.
[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

---

