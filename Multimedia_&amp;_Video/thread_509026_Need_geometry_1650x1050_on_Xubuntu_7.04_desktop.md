---
title: "Need geometry 1650x1050 on Xubuntu 7.04 desktop"
date: 2007-07-24
forum: Multimedia &amp; Video
---

### Post by wb0gaz on 2007-07-24
Need help in matching screen geometry preference of the LCD monitor on my computer.

My new video card (MADDOG CHAMPION MX400 64MB 4X AGP ---    www.mdmm.com/spec.php?productid=144   --- under Xubuntu 7.04/xfce is offering me geometry options up to 1280x1024.

My monitor is a Viewsonic VG2230wm and it tells me it's ideal geometry is 1650 x 1050 (or something close to that.) I also tried booting the Ubuntu 7.04 live CD and got the same maximum geometry. The monitor will handle 1280x1024 but aspect ratio is not good and pixel filtering in the monitor produces a less than fully sharp image.

How shall I proceed?

Very tks,

Dave
wb0gaz@hotmail.com

---

### Post by arcticFire on 2007-07-25
When I've had issues with my install not providing me with higher screen resolutions I've done this - assuming you have standard Xubuntu install:

Start admin priviledged file manager
-------------------------------------------
Open up a terminal and type in: sudo thunar. This will open your file viewer as admin priviledged user.

Backup copy of current xorg.conf
--------------------------------------------
Using nautilus go to /etc/X11 directory. Select xorg.conf file and right-click on it and choose copy. Then right-click again and choose paste. This makes a backup copy of xorg.conf in case of fff - fat finger factor.

Edit xorg.conf file
----------------------
Select xorg.conf and choose open with mousepad. Scroll down to the Section "Screen".
You should see lines like: 
        Modes      "1024x768" "800x600" "640x480"

What I've done in the past is simply edited the lines to look like this:

        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"

or in your case:

        Modes      "1650x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"

I actually do this to every Modes  line in the SubSection so that the higher res is available at whatever colour depth. 

Then save your xorg.conf file.

Restart X
-----------
Now restart X/Xfce - your desktop by pressing Ctrl + Alt + Backspace. You should be running at the highest res it can cope with or at least give you the option to choose it.

I hope this helps.

---

### Post by wb0gaz on 2007-07-25
I did some additional research, and found:

[http://ubuntuforums.org/showthread.php?p=2587126](http://ubuntuforums.org/showthread.php?p=2587126)

which points me to "ENVY", a script for setup of ATI and Nvidia based GPU cards.

This worked *perfectly*, with no effort at all --- it generated a new xorg.conf; I saved to /tmp, then copied into /etc/X11, restarted X, and it is finding my correct geometry.

Dave

---

