---
title: "log on screen"
date: 2008-06-02
forum: Multimedia Software
---

### Post by justaguylinux on 2008-06-02
Hello After getting past 600x800 res problems. i now have a a logon menu that is shifted down and to right. I can still enter password and log on but the "smaller  window" that allowed the different desktop and a few other commands is not accessible. after logging in all other things are fine.
thanks for any advise :confused:

---

### Post by Snappo on 2008-06-02
> **justaguylinux said:**
> Hello After getting past 600x800 res problems. i now have a a logon menu that is shifted down and to right. I can still enter password and log on but the "smaller  window" that allowed the different desktop and a few other commands is not accessible. after logging in all other things are fine.
thanks for any advise :confused:

If you tell me how you fixed your resolution problem i will do anything i can to help you with your login screen problem (had this on another pc).

---

### Post by makatak on 2008-06-03
"now have a a logon menu that is shifted down and to right. "

I have the same issue.....  Any suggestions would be helpful.

---

### Post by justaguylinux on 2008-06-03
> **Snappo said:**
> If you tell me how you fixed your resolution problem i will do anything i can to help you with your login screen problem (had this on another pc).
I fixed the res by install 915 package intell fix and restarting of x-server.
hope this info helps & thanks

---

### Post by rburks on 2008-06-03
Hey guys I have the same problem with my login screen being "down and to the right".  I'm running Nvidia proprietary drivers on a Geforce 7800GS AGP card.  Grub starts fine and looks normal, then the Nvidia logo screen shows up normally also, and finally the Gnome log-in screen comes up off center and slightly oversized.  The options at the bottom of the screen are cut off and therefore cannot be reached or seen.

This seemed to happen after I started playing around with the "Screen and Graphics" menu item.  My Gateway 24" LCD Wdiescreen monitor was showing up as Plug and Play monitor, so I chose Generic 1920x1200 LCD and set the Widescreen box.  The only refresh choices I get are 50 and 58hz.  Well the screen shifted some so I had to move Cairo-Dock a bit and then I restarted.  That's when the log-in screen changed.  I can see the mouse cursor shifted right and down some after typing my password, which is also off-center, and then just before the desktop appears I see the mouse pointer center itself correctly as the wallpaper comes up.  Now everything is normal.

Oh well I'll just go back to Screen and Graphics and change it back.  Wrong.  Nothing I select in any part of that program will have any effect on my system.  I can't set it back to plug and play, or even something crazy like Viewsonic 17" CRT.  Unchecking the Widescreen button also does nothing.  It's like the program no longer takes any of my commands.  I can select anything I wish but hitting Apply or Ok does nothing, it just sits there until I close the window.

I've looked around the forums and examined my xorg.config file, even adding some stuff I've seen elsewhere to no avail.  The screen resolution looks the same as it did before I started messing with it so now I wish I didn't do any playing around.  Naturally I hadn't got around to backing up my original xorg.config file before I tore everything up.

Rob

---

### Post by justaguylinux on 2008-06-05
after last update and reboot all is well not sure how but log-on is centered and working fine.
thanks for all info
maybe reboot just like windows cured it?

---

### Post by rburks on 2008-06-05
justaguylinux:

That's good you got it fixed.  I've updated & rebooted and it's still the same.  I noticed the update included another kernal update plus an nvidia driver that compiled with it.  However my problem is elsewhere I suppose....

Rob

---

### Post by rburks on 2008-06-08
Ok I solved the problem.  I had to open xorg.config and comment out (#) the virtual line.  That's all it took.

Rob

---

