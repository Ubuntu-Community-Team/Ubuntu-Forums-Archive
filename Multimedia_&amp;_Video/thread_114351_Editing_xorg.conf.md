---
title: "Editing xorg.conf"
date: 2006-01-08
forum: Multimedia &amp; Video
---

### Post by Kobra on 2006-01-08
Ok, I want to edit my xorg.conf to acomodate the next larger screen resolution, but I have no idea what to add and where.  I have my optimal screen frequency and scan frequency, etc...  Where do I add the screen resolution and stuff?

---

### Post by Snackmaster on 2006-01-08
I'll second that motion. I've been reading in these forums how to backup xorg.conf  what to edit and and where to add it, but I can't edit the file using sudo and terminal or using the GUI where's attributes are read only and I don't have access to set the file  permissions or attributes. Absolute newbie question, how do I edit such a file?

I'm on an ATI Radeon 9000 card which Ubuntu Device manager reports as an NVidia Riva TNT Pro.  I can get appropriate resoluitons and color depths but not refresh rate.

I'd like to edit xorg.conf because no matter the resolution or color depth my only available refresh rate is 60mhz. Need to edit for what my Dell P991 + card support.

---

### Post by somerandomnerd on 2006-01-08
If you open the terminal (Applications>Accessories>Terminal) and put in this line;

sudo gedit /etc/X11/xorg.conf

it should get you in there.

(How it works- "sudo" means "do this as superuser- the equivalent to loggin in as Root in most Linux distros; it will ask you for your password before it will carry it out. "gedit" is the name of the text editor, and " /etc/X11/xorg.conf" is the path and name of the xorg.conf file.)

Beware- if you mess it up, you might kill "X", the graphical interface, leaving you stuck at a command line when you next try to log in. Make sure you have a backup xorg.conf and you know how to restore it from the command line!

---

### Post by Snackmaster on 2006-01-09
Thank you! That worked perfectly.
I now have proper refresh rates so my eyes will last a good bit longer.
Here's the lines I edited with numbers that I used
 HorizSync    85.0 - 120.0
 VertRefresh  50.0 - 190.0

Why can't Ubuntu detect the proper card (Radeon 9000 in my case) and available refresh rates? ATI Radeon is extremely common and no where near the bleeding edge...

---

