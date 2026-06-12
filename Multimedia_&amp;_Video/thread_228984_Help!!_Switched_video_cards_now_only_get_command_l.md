---
title: "Help!! Switched video cards now only get command line!"
date: 2006-08-03
forum: Multimedia &amp; Video
---

### Post by aleska on 2006-08-03
:confused: 
First, I know I know, I should have read up before changing hardware.  I'm brand spankin' new to linux let alone ubuntu, so please be kind in your replies.
I had an ATI All-In-Wonder Radeon 9000, and I was sick of trying to get it to function properly.  So, I went out this evening to buy a nvidia.  Its a nvidia geforce 6200 AGP 8x/4x 128MD DDR.
I didn't do or change anything in settings or configurations, etc.
Anyway, I changed cards, started her back up, and before I could get the login page, it basically displayed a couple of error pages, and then spit me out to a command line shell.  gdm won't work.
So, what am I supposed to do?  Do I need to put my old ATI back in, and make some setting changes before I put the nvidia card in? 
Can I fix this from the command line?  If so, what do I have to do.  If it includes editing files, where are they located (directory).
Sorry to be such a numbskle here.  I promise that when I know what the h3ll I'm doing, I'm help the future goofs like me out.  
Help!!!  and TIA!!! :confused:

---

### Post by E-werd on 2006-08-03
Well... since you're at a command line anyhow, I'll skip telling you to open a console. :p

You will need to edit the file "/etc/X11/xorg.conf"

In order to do this...
-type in the command line "sudo vi /etc/X11/xorg.conf"
-scroll down until you get to the "Device" section
-Under this section you have a line that says "Driver", afterwards it may say "ati" or "fglrx"
-hit the 'insert' button on your keyboard to change this entry to "nv"
-press ctrl+c once
-type ":w" then type ":q"

After this, you should be able to run "sudo /etc/init.d/gdm stop" then "sudo /etc/init.d/gdm start" and you should load into gdm.

Afterwards, if you want to install the nvidia-glx drivers, follow a stickied guide at the top of the video/sound forums.

Good luck. :D

---

### Post by catlett on 2006-08-03
The system is loading drivers for your ati card. You need to configure the system for the nividia card. This command takes you through the x setup. You will enter your monitor specs and your video card etc. Just login at the ubuntu text login and then enter this.
```
sudo dpkg-reconfigure xserver-xorg
```
This will get your card working but if you want the lates nvidia drivers for better performance, go here [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by aleska on 2006-08-03
First, thanks so much for the responses...unfortunately, tried both approaches and neither works for me.
I thought maybe rebooting would help...doesn't.
First weird error message to come up is > Failed to start the X server (your graphical interface).  It is likely that is is not set up correctly.  Would you like to view the X server output to diagnose the problem?  <yes> <no>
I go with "Yes".
Doesn't tell me anything special other than where my log file is located "var/log/Xorg.0.log" and my config file is located "/etc/X11/xorg.conf".  Pretty standard I assume...
Same thing promted for checking X server output...verbatim same as before...
So, I thought I'd use vi to view the contents of var/log/Xorg.0.log (BTW - if for just viewing I should use something other than vi...please let me know).

Obviously output of the log file is too long to list, and may not be relevant...but here are some of the warnings...
one of the warnings (WW) line 358 
"(WW) NV(0): Bad V_BIOS checksum"
then there is a series of 7 warnings (WW)'s, each stating
"(WW) open /dev/fb**_X_**: No such file or directory"
...with **_X_** being replaced with number 1 through 7

That is then followed by errors (EE)
"(EE) Unable to find a valid framebuffer device
(EE) NV(0): Failed to open frmaebuffer device, consult warnings and/or errors above for possible reasons"
Followed by more stuff, then 
"(EE) Screen(s) found, but none have a usable configuration.

Fatal Server error:
no screens found"

Ooof.  Should I start all over with a Live CD??
So sad here....I was thinking this Ubuntu stuff was the best thing that had ever happened to me... :cry:

---

### Post by nkife on 2007-02-06
I'm having this same problem.. I know this topic is from a while ago, but I've been searching all day for a solution and can't find any. 

I also have a NVidia card (my monitor is AOC Spectrum) and am trying to install for the first time. I tried the LiveCD but i would just get the "attention out of range" message about my monitor.. 

I then installed from the text-based installer and edited the xorg.conf to include my refresh rates, that didn't help.

Stopped gdm.. Ran dpkg-reconfigure xserver-xorg.. started gdm.. that didn't help.

My Ubuntu version is 6.10, installed from the 64-bit PC (AMD64) install/live DVD.

Has there been any progress on this issue?

Thanks..

---

### Post by bigken on 2007-02-06
use sudo **dpkg-reconfigure xserver-xorg ** again and select vesa as your driver this sould at least get you into the desktop from there you can use automatix to install the nvidia drivers

---

### Post by nkife on 2007-02-06
> **bigken said:**
> use sudo **dpkg-reconfigure xserver-xorg ** again and select vesa as your driver this sould at least get you into the desktop from there you can use automatix to install the nvidia drivers



Awesome. Worked like a charm. Thanks a lot.

---

### Post by bigken on 2007-02-06
pleased it worked for you :)

---

