---
title: "8800gt, can't change resolution, video crash, can't boot"
date: 2008-09-14
forum: Multimedia Software
---

### Post by nonzer0 on 2008-09-14
Ubuntu 8.04 x64 amd Hardy Heron
nvidia 8800gts
OK.  Here is the story.  I have an 8800gts, had compiz, desktop cube, virtualbox, everything working great this morning.  Was in fact trying to figure out a good meathod of backing up my system incase this happened.  Anyways, I get home from work, turn my computer on, and it is stuck in 600 by 400.  I checked that the nvidia driver was enabled (system -> administration -> hardware Drivers) and it was.  OK, i tested the desktop cube and other effect and they worked, so i tried to change the resolution again (sys. -> prefer. -> screen res.) and i cannot change the resolution.  I disable the nvidia drivers, restart the computer, and my resolution is back to normal, i can adjust it to its max.  So i reinstall (enable) the nvidia drivers and the resolution is stuck again at 400 x 600.  Tried to force detect, doesnt work.  
While researching the problem, one person suggested using EnvyNG.  I used it, restarted my computer, and the resolution was at 300 x 400.  I checked to see if the proprietary driver was installed and it was not.  So I enabled it, restarted my computer, watched the ubuntu loading animation, and on load up i got a bunch of colored bars and a window at the bottom saying running in low graphics mode.
I could not start up ubuntu.  There was a window with the option to choose my video card driver.  Finally, I restarted it in recovery mode, not really knowing what to do, and i saw something along the lines of "atempt repair of X-config.." i did it and I am back into my computer.  Now i have the normail 1020x786 res. but the vid. driver isn't installed.

So heres my questions: How can I get my videocard working again, and what could have cause this/how can I prevent it from messing up out of nowhere again!?!

---

### Post by cyclobs on 2008-09-14
hmm... to me it sounds like you xorg.conf got really messed up on detecting the monitors.

my option would be to install the envy drivers since they are nice and easy and seem to always work for me :)

---

### Post by nonzer0 on 2008-09-14
> **cyclobs said:**
> hmm... to me it sounds like you xorg.conf got really messed up on detecting the monitors.

my option would be to install the envy drivers since they are nice and easy and seem to always work for me :)

I never messed with my xorg.conf file, I don't know what could have caused this.  Is there any way to do a restore of the file, try and get ubuntu to try and rerecognize the vid. card as though it was just installed, or install another driver through envy?  I tried that EnvyNG.  I chose Nvidia, install the nvidia driver (automatic), and it didn't work.  Any help would be greatly appreciated.

On repair boot up I chose "repair X server"

---

### Post by nonzer0 on 2008-09-14
OK. I know it has something to do with virtual box. does anyone know how or why virtual box would ruin my xorg file?

---

### Post by nonzer0 on 2008-09-16
After over 12 hours of reading posts and trying everything possible, I figured out what the problem was after going through an 8 page thread someone started.  It turns out my monitor cable was just a little loose.  

lol.  What a nightmare.  I suppose it could have been worse.
I appreciate the help though.

---

