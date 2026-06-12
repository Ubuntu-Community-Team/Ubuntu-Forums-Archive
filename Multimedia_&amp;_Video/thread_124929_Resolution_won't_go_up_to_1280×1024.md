---
title: "Resolution won't go up to 1280×1024"
date: 2006-02-02
forum: Multimedia &amp; Video
---

### Post by amugofcoffee on 2006-02-02
I recently received a copy of Ubuntu (from your fantastic free CD delivery service) and I couldn't be more happier. but I only have one squabble: My display resolution is able to go up to 1280×1024 (because I think 1024x468 is way too small) but if I used the Screen Resolution Preferences dialog, the highest possible is 1024x468. I am running an installation with Wine, Galeon, Epiphany and Gnome Apps (i.e. Bluefish, GNumeric, etc.)

---

### Post by MartinG on 2006-02-02
This is probably because you are using the default driver for your graphics card.  If you go here [http://help.ubuntu.com/starterguide/C/ch04.html](http://help.ubuntu.com/starterguide/C/ch04.html) you will find instructions on how to first enable extra repositiries and then install a better driver.

---

### Post by amugofcoffee on 2006-02-02
Sorry, but:

A) I'm not using ATI or NVidia.
B) I have xserver-xorg-driver-i810 installed.
C) I know the 1280×1024 resolution is possible because it so on my Windows Me and Knoppix also running on this computer.

Any help?

---

### Post by MartinG on 2006-02-02
I don't know about this particular driver's abilities, but try reconfiguring.  To do this, log out of Gnome and at the login screen choose a console (terminal?) login.  Then do ```
sudo dpkg-reconfigure xserver-xorg
```While working through the screens (you have to use the Tab key to move around, as the mouse won't do anything, and Space to select/deselect options), pay particular attention to the range of resolutions enabled. After this, exit the console and you should be back at the login.  Restart X (Ctrl+Alt+Backspace) and you will (I hope) have the resolutions you want.

---

### Post by mishranurag on 2006-02-02
When you are going through the process of selecting the resolution, make sure to select the highest possible resolution your monitor can take only and nothing else. If you choose higher and lower (e.g. 1280 x 1024 and 1024 x 768 both), then UBUNTU will choose the lower resolution. At least that's what happened to me!

Good Luck
Anurag

---

### Post by amugofcoffee on 2006-02-02
Big problems! I can't even start the XServer! That makes it the third time I messed up a Debian Distro (I messed up Knoppix twice :) ). Is there a way to revert the changes?

---

### Post by MartinG on 2006-02-02
After logging in at the terminal, do the following:```
cd/etc/X11
ls -l
```In the list this produces, xorg.conf is your most recent (non-working?) file; others have names like xorg.conf_backup, etc.  Find the most recent of these, and do:```
sudo cp <this_recent_file> xorg.conf
```This should restore how it was before.

Next (or maybe better first) can you post the contents of /var/log/Xorg.0.log from your failed attempt, so we can see why X failed?

And to while away the time, you could retry the re-configuring process :)

---

### Post by amugofcoffee on 2006-02-02
Thanks! It actually worked! (the filename for the backup, by the way, is xorg.conf~)

---

