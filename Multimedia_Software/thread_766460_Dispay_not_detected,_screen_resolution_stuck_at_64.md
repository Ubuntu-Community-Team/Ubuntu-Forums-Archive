---
title: "Dispay not detected, screen resolution stuck at 640 X 480"
date: 2008-04-25
forum: Multimedia Software
---

### Post by hollowroom on 2008-04-25
Hello,

Second time here! 

After having massive problems with upgrading from 7.10 to 8.04 I decided to bite the bullet, format my / partition and install from scratch.

After I did, everything comes up, but I'm stuck at 640 X 480, my display isn't detected and the Nvidia X server settings show "CRT-0" as the model, with nothing in the drop down and no way of changing any resolutions, choosing a new display etc.

I'm at my wits end here. Anybody know why this is happening?

Cheers,

M

** If I edit xorg.conf to NOT use the nvidia driver, I can go up to 800 X 600. Nightmare.

**Uninstalled the Nvidia driver using EnvyNG. Rebooted. FINALLY got "running in low grpahics" on reboot, selected my monitor and the resolution, rebooted, got the Nvidia splash screen, and a desktop at 1600 X 1200. No idea how.

---

### Post by fish2ways on 2008-04-25
I've had the same trouble. This is supposed to a "just works" distro? This should not be necessary:
Anyway click on System - Preferences - Main Menu. 
You'll have a list of all the menu items available. If like me your screen is huge and your mouse isn't selecting things, use your up/down keys to select the Other category. If you can use your mouse select Screens and Graphics, if not use the Tab key to work through the options and highlight the Screens and Graphics entry then select it using your spacebar. Exit either using your mouse or Tab to the Close button.
The Other category will now be in Applications. Click on Screens and Graphics entry, enter your password at the prompt and locate your particular monitor from the options. Select your preferred resolution after you've done that and restart your machine. 
Hopefully that should work, it did for me.
Can you imagine a new user working that out? No way, they'd give up and probably never want to use Linux again.
Best of luck.

---

### Post by mehigh on 2008-04-26
Unbelievable

I waited months for this ubuntu release and such an enormous bug slips in????

I cannot get out of the 640x480 resolution. I uninstalled and reinstalled the nvidia driver countless of times using Synaptic and the Envy tool, but still to no avail..

How could this slip in the final release? And i was hoping to install this on my girlfriend's computer so she could switch from windows too...go figure now

Does anybody has a final fix for this?

---

### Post by mehigh on 2008-04-26
problem fixed

i manually selected my monitor (generic 1280 x 1024 lcd monitor). now i can select the resolution.

---

### Post by nishant.narayanan on 2008-06-06
Change the colour depth to 16 bit or click the activate the thousand option than the millions.

Regards 
Nishant

---

### Post by zieglerj on 2008-11-14
How?

---

### Post by zieglerj on 2008-11-14
> **mehigh said:**
> problem fixed

i manually selected my monitor (generic 1280 x 1024 lcd monitor). now i can select the resolution.

How?

---

### Post by xc3RnbFO8P on 2008-11-14
Did install Hardy or Intrepid?

Hardy:
gksu displayconfig-gtk
Choose Generic
and resolution that your monitor supports

Intrepid:
gksu gnome-display-properties
Choose Generic
and resolution that your monitor supports

---

### Post by GTdave on 2008-11-15
I am having a similar problem, except when I type in 

gksu displayconfig-gtk 

it appears to be starting something but nothing happens. I have tried 

gksu gnome-display-properties 

and that opens up a display properties window but I cannot make any changes as it is stuck to 640x480.

Any ideas?

---

### Post by keshava on 2008-11-28
> **GTdave said:**
> I am having a similar problem, except when I type in 

gksu displayconfig-gtk 

it appears to be starting something but nothing happens. I have tried 

gksu gnome-display-properties 

and that opens up a display properties window but I cannot make any changes as it is stuck to 640x480.

Any ideas? 
The same thing is happening to me. Could someone please help us out.

---

### Post by avibp on 2009-01-01
> **Ringi said:**
> Did install Hardy or Intrepid?

Hardy:
gksu displayconfig-gtk
Choose Generic
and resolution that your monitor supports

Intrepid:
gksu gnome-display-properties
Choose Generic
and resolution that your monitor supports

Running Intrepid with my NVidia Geforce FX 5200, these commands don't help.  

gksu displayconfig-gtk <- returns to a blinking cursor after authenicating

gksu gnome-display-properties <- doesn't allow me to select generic or change any other settings from the window (Monitor Resolution Settings) that it opens.

Any help would be appreciated.

------------------

On the other side of this: I can DEACTIVATE the NVidia Driver v.173 via  SYSTEM-> ADMINSTRATION-> HARDWARE DRIVERS which allows me to once again increase the desktop to 800 x 600.

Again, any help would be appreciated.  (And the searching continues)

---

### Post by xc3RnbFO8P on 2009-01-01
I dont know if it helps, but check in Synaptyc Package Manager:
Other Packages Related to nvidia-glx-173
[http://packages.ubuntu.com/intrepid/nvidia-glx-173]("http://packages.ubuntu.com/intrepid/nvidia-glx-173")

---

### Post by mikeh on 2010-04-28
As in [http://ubuntuforums.org/showthread.php?p=9190048#post9190048](http://ubuntuforums.org/showthread.php?p=9190048#post9190048)

If the monitor auto-detect does not work, you can always do it the old-fashioned way and edit /etc/X11/xorg.conf

Just add some lines in the "Monitor" section. e.g.

    HorizSync       31.0 - 83.0
    VertRefresh     50.0 - 76.0

Or whatever your monitor supports.

Then restart X, and the GUI should offer suitable settings.

---

### Post by mwang141 on 2010-04-28
when you install, did you get any notice to install restricted driver (display). e.g. for Nvidia, I installed it, then I can select different resolution. Though comparing to windows, ubuntu xorg still has a long way to improve.

Or you can go to hardware driver, it may pop out another update driver message, then follow it to activate.

---

