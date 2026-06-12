---
title: "nividia geforce4 mx440se freezes up"
date: 2006-08-11
forum: Multimedia &amp; Video
---

### Post by vista on 2006-08-11
After i've installed nvidia graphics drivers with the help of automatix,
my system suddenly freezes up, i can move around the mouse but everything
else just freezes. Ive tried rebooting a couple of times but same thing 
happens again, the third time it won't boot past the login screen, 
it just goes to black screen.
I'm using a geforce2 card instead of the geforce4, the geforce2 card seems  
to work with no problems.
Anybody knows how I can fix this problem, i really want to use the 
geforce4 card.
I'm using ubuntu dapper by the way.

---

### Post by tseliot on 2006-08-11
Boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Try point 7 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

---

### Post by vista on 2006-08-11
What do they mean with "get to section screen"
Where do i add > Option "ExactModeTimingsDVI" "TRUE" 
Option "ModeValidation" "DFP-0: NoEdidDFPMaxSizeCheck, NoVesaModes"

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION")

I boot up in recovery and at command line I put in 
sudo nano /etc/x11/xorg.conf but once i'm there what do i do then?
I can't seem to find anything in my xorg.conf where i can add the above options.

Any Suggestions?

---

### Post by tseliot on 2006-08-11
> **vista said:**
> What do they mean with "get to section screen"
Where do i add 

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION")

I boot up in recovery and at command line I put in 
sudo nano /etc/x11/xorg.conf but once i'm there what do i do then?
I can't seem to find anything in my xorg.conf where i can add the above options.

Any Suggestions?
Linux is case sensitive.

It's sudo nano /etc/**[COLOR="Red"]X[/COLOR]**11/xorg.conf and not sudo nano /etc/x11/xorg.conf

---

### Post by vista on 2006-08-11
> Linux is case sensitive.

It's sudo nano /etc/X11/xorg.conf and not sudo nano /etc/x11/xorg.conf

Ok, i'll try that and see what happens.

---

### Post by vista on 2006-08-12
Ok, i tried putting in all the options in xorg.conf but
I don't see any difference except that the card does start up
and everything loads as usual.
But when you move around in the meny, 
everything seems very sluggish, 
if you want load an application for example it takes
forever to load.
I even put in the "RenderAccel" "false" option
but it still behaves the same as above.

I noticed also that my comp has kernel 2.6.15-26-386,
even though my comp is an amd xp athlon 2100+.
Has this got anything to do with my card responding weird?
Is there a safe way to upgrade the kernel to K7 without
messing my computer up badly?

---

### Post by tseliot on 2006-08-12
> **vista said:**
> Ok, i tried putting in all the options in xorg.conf but
I don't see any difference except that the card does start up
and everything loads as usual.
But when you move around in the meny, 
everything seems very sluggish, 
if you want load an application for example it takes
forever to load.
I even put in the "RenderAccel" "false" option
but it still behaves the same as above.

I noticed also that my comp has kernel 2.6.15-26-386,
even though my comp is an amd xp athlon 2100+.
Has this got anything to do with my card responding weird?
Is there a safe way to upgrade the kernel to K7 without
messing my computer up badly?
Post the output of this command:
```
glxinfo | grep direct
```

I don't know if the problem can be solved by using a kernel which is optimised for your CPU. It might be worth trying though:
```
sudo apt-get install linux-k7
```

and reboot

---

### Post by vista on 2006-08-12
When I run the command this is what i get:

direct rendering: Yes

---

### Post by tseliot on 2006-08-13
> **vista said:**
> When I run the command this is what i get:

direct rendering: Yes

It's working just fine.

If it's still slow you can ask here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by vista on 2006-08-13
In the xorg.conf I changed the "nvidia" to "nv" instead.
Seems to be working ok so far, except at the loginscreen,
you can login if you don't mind the flickering image, 
other then that, it's working ok.

---

