---
title: "DIRECT RENDERING =YES IN IBEX  AND NO IN HARDY, PLEASE HELP answer my questions."
date: 2009-01-15
forum: Multimedia Software
---

### Post by hoboboot on 2009-01-15
im currently running hardy (8.04) and i have never been able to get my display working right, the drivers i got just gave a black screen so i've been stuck in vesa mode for the whole time, and well, i just got the intrepid ibex (8.10) cd in the mail, and ran the live edition, noticed that my video works, direct rendering=yes ! glx gears is at 850 frames instead of 25-40 frames under vesa... 


basically i'd even install intrepid and then go through setting up my sound and wireless bull, all over again, just to get that working, but then i have this display issue where my resolution is too big, again... 1600x1200 which is like off the screen cause i have a 1280x768 laptop so... basically i fixed that under 8.04 on vesa, but i fixed it with this tool "screens and graphics" i added to the "other" menu in "applications" aka displayconfig-gtk but in ibex if i try to add it to the other menu, its not an option, and if i open terminal and type 
$ gksu displayconfig-gtk it doesnt open that options screen for me to change the monitor and configure all the stuff? is that because im running it from a live cd, or is it not in 8.10 anymore?

i REALLY WANT my display driver to be whatever its at in ibex off the live cd but i have no idea how to get the driver from it, and set it up in hardy, and or, if i should switch to 8.10 whats the diff between 8.04 and 8.10 besides one has longer support time? 

PLEASE SOMEONE HELP SO THAT I CAN HAVE MYSELF A WORKING DISPLAY WITH COMPIZ AND ETC.... ( I KNOW ABOUT THE WHITELIST, ETC, I JUST CANT FIGURE ALL THIS PRIOR MENTIONED STUFF OUT. ) THANKS IN ADVANCE.

---

### Post by Catalyst2Death on 2009-01-15
You probably need to install/compile the drivers for your video card (ati/nvidia)  

Ati guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

Nvidia:
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=howto+nvidia](http://www.linux-gamers.net/modules/wiwimod/index.php?page=howto+nvidia)

If your running ATI, and your careful (with a little luck) the installation should go smoothly.  Nvidia is pretty straightforward.  Also post the output of:
```

$ glxinfo | grep render
```

It will tell your whether or not it is set to yes, and what renderer your using.  Sometimes it will say that you have direct rendering, but you'll still be on vesa, so its an important distinction.  Hopefully it will fix your resolution problems too.  If it doesn't, boot into recovering mode and choose to automatically reconfigure X.  I've had good luck with that in the past (sorry I don't have specific instructions, but the gist of it is all you really need)

---

