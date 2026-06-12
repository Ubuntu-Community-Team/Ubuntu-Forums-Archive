---
title: "login screen is messed up."
date: 2008-04-25
forum: Multimedia Software
---

### Post by illbashu on 2008-04-25
when every i open my comp i cant log in because i can only see the top left side of my screen, this happend after i upgraded to 8.04 from 7.10

---

### Post by illbashu on 2008-04-25
bump!!!!!!!!!!!!!!!!!!!!

---

### Post by pleasant88 on 2008-04-26
Yeah the same has happened to me. One thing though, with my computer there are redundant entries in grub, and one shows a good login screen but does not load some of my sound drivers,and must be ran in low graphics and the other, has the login problem and no networking drivers.

---

### Post by illbashu on 2008-04-26
mine is completly messed up, i cant even log in because the logoin box is cut off :(

---

### Post by neymac on 2008-04-26
+1

---

### Post by Gwarkill on 2008-04-26
MAJOR BUMPAGE HERE!!!

I am having the same problem. D:

---

### Post by Gwarkill on 2008-04-26
bump

---

### Post by illbashu on 2008-04-27
Bump!

---

### Post by Gwarkill on 2008-04-27
Re-bump

---

### Post by illbashu on 2008-04-27
Re-Re-bump!

---

### Post by illbashu on 2008-04-30
Super BUMP! man someone help us! i dont want to loose my files! :(

---

### Post by raygj on 2008-05-01
hi i had the same problem .
i fixed it by logging out & rebooting the computer into it's BIOS SETUP screen. and changing the setting for AGP Aperture size: Set this to half of your system memory.then save settings option.
on reboot, the LOGON Screen was now displayed Correctly.
regards Ray

---

### Post by The Crazy Parrot on 2008-05-01
Try hitting control-alt-F1 and running

sudo apt-get install xdm

I had a problem with logging in and using xdm fixed it for me.

( you probably need a hard-line connection for this)

---

### Post by SnakeHips on 2008-05-01
try this?

have a look here or something like this (im using xubuntu)
menu/apps/system/setting/login window
goto the "local" tab and from "style" select plain
close, then logout then login

---

### Post by Zorael on 2008-05-01
This is likely due to your xorg.conf saying that the screen should "virtually" be larger than it already is.

Fast fix: pop up **/etc/X11/xorg.conf** in an editor with superuser permissions, search for "Virtual", and comment/delete the whole line. It should mention a resolution. Perhaps it's VirtualSize, not sure; "Virtual" should find it.

Thorough fix: make a backup of said xorg.conf, create a new one with the below command, and then go through your backup and transfer extra options and tweaks you might've entered earlier, from the old to the new one. LEAVE OUT RESOLUTION OPTIONS; they are largely not needed anymore.
```
$ sudo dpkg-reconfigure xserver-xorg
```
There'll be some quick questions about your keyboard layout and such, then the xorg.conf will be restored to defaults.

---

### Post by k_dv700 on 2008-05-01
Same problem here.  I can log on but only see left upper end of screen, no way to scroll.  Once logged in all works.  I fiddled around with login settings and resolution (set differntly, then back) but this does not help.  
Also during boot my screen shows an 'out of range' instead of console like text
Seems like a bug

---

### Post by illbashu on 2008-05-01
i cant log in thats the prob. i pressed alt-ctrl-f1 but it takes me to a screen with a blinking "-"

---

### Post by illbashu on 2008-05-04
anything! plz!

---

### Post by fm1234 on 2008-05-06
illbashu, are you sure you are pressing the combination keys correctly?

pressing CTRL+ALT in combination with any one of F1...F6 should bring you up to a text mode login. Pressing CTRL+ALT+F7 brings you back to the graphics mode.

If you manage to login, then to fix the resolution you should edit xorg.conf file and look for Virtual (capital V) setting and make it the same as the highest. See a previous post in this thread on this solution for more details.

---

### Post by illbashu on 2008-05-06
ok i loged in but i am stuck at 800x600 res :( how do i fix this?

my video card is GeForce FX 5200

---

### Post by illbashu on 2008-05-07
bump! i really need help 800x600 sucks balls! :( i need help installing my grapics card!!

---

### Post by neogeek on 2008-05-07
Tried all the methods posted none worked. :(

---

### Post by smilingfrog on 2008-05-15
I was also having problems with the login screen not displaying properly. I have an ATI Radeon 9800, and it was not displaying properly, after the proprietary drivers were installed. I could get the resolution fixed in gnome and in KDE, but the login screen was not good. Wrong resolution. off to the left. Just like the rest of the posts.
The ```
$ sudo dpkg-reconfigure xserver-xorg
``` seems to have fixed the login screen problem for me so far. Thanks!



> **Zorael said:**
> This is likely due to your xorg.conf saying that the screen should "virtually" be larger than it already is.

Fast fix: pop up **/etc/X11/xorg.conf** in an editor with superuser permissions, search for "Virtual", and comment/delete the whole line. It should mention a resolution. Perhaps it's VirtualSize, not sure; "Virtual" should find it.

Thorough fix: make a backup of said xorg.conf, create a new one with the below command, and then go through your backup and transfer extra options and tweaks you might've entered earlier, from the old to the new one. LEAVE OUT RESOLUTION OPTIONS; they are largely not needed anymore.
```
$ sudo dpkg-reconfigure xserver-xorg
```
There'll be some quick questions about your keyboard layout and such, then the xorg.conf will be restored to defaults.

---

### Post by smilingfrog on 2008-05-15
illbashu, you may want to try this:

[http://ubuntuforums.org/showthread.php?t=766826](http://ubuntuforums.org/showthread.php?t=766826)

maybe you can force your monitor to display the resolution you need.

---

### Post by illbashu on 2008-05-15
i got it fixed, i cant remember the thread i used :/ ill try to find it and post it here...

---

### Post by mc4man on 2008-05-15
If you have used screens and graphics (hidden but atm still effective) or other means to square up your video and your log in screen is to big check in xorg.conf. The line your looking for is virtual - make sure the resolution is not something ridiculous
ex.
```
 clipped
 modeline  "2048x1536@60" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GeForce 7800 Gs"
	Monitor		"Dell P991"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	1024 
```
mine was set to the last modeline - 2048   1536
changing back to 1280  1024 resolved log in screen

---

### Post by Doc Hoss on 2008-05-23
Good call, mc4man!  I was having this problem, and changing the "Virtual" resolution fixed it.  Thanks!

---

