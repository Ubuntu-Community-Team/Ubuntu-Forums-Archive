---
title: "Nvidia Driver problems - Cannot detect screen, graphics card, input device settings"
date: 2009-01-24
forum: Multimedia Software
---

### Post by jayekaiser on 2009-01-24
I recently posted this issue in the Hardware & Laptops forum, but didn't get any responses.  I figured that this forum may be a more appropriate place to discuss this as it's likely more a video driver/settings problem than anything else.

I have been running Ubuntu 8.10 with the nvidia 177 drivers on this laptop for about a month now without any problem until recently.

I decided to try the nvidia-180.22 drivers to fix some graphical glitches that I was getting with AWN and compizfusion, however, somewhere in the process, I managed to royally screw up my video hardware settings.

After having problems getting the 180 drivers to work I tried reverting to the 177 drivers, but they would not work any more.

I have tried several methods to get up and running again:
1. Tried using synaptic to remove all nvidia driver files and reinstall them
2. Tried enabling the drivers from the hardware drivers menu (it displays 173, 177, and 180 as options to enable)
3. Tried fixing it with sudo dpkg-reconfigure xserver-xorg (found through googling)
4. Lastly, I've tried installing/uninstalling through Envyng

Regardless of what I do, I'm getting this on boot up every time:

> Ubuntu is running in low graphics mode
Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure them yourself.

I also tried running the .run script for the 173 drivers from Nvidia's website but recieved an error.  Upon reviewing the log file I found this:

> 
echo; \
echo " ERROR: Kernel configuration is invalid."; \
echo " include/linux/autoconf.h or include/config/auto.conf are missing."; \
echo " Run 'make oldconfig && make prepare' on kernel src to fix it
."; \
echo;


I ran make oldconfig and make prepare in the kernel src folder and they went through the process, but didn't seem to do anything.  I still receive the same error.

Can anyone clue me in on what's going on and what I can do to fix it?

---

### Post by jayekaiser on 2009-01-25
I'm still struggling with this problem, and have been for several days now without any progress.  Any help is greatly appreciated, thanks.

---

### Post by rmwoods on 2009-01-28
I am also experiencing a very similar, if not the same, problem. I have all the symptoms listed above.

As another note: lspci recognizes the card just fine (can post if needed).

Thank you.

---

### Post by jayekaiser on 2009-02-03
I finally fixed this.

I was looking around for loose or misplaced nvidia files, and discovered that in /lib/modules/2.6.27-9-generic/video/nvidia/ (I think that's the path, will update if it's wrong) there was a file called nvidiafb.ko that was still in there.  I went into synaptic and completely uninstalled all driver files, then deleted the nvidiafb.ko file.  Next I decided to go out on a limb and try installing the 180.22 drivers (the ones that gave me the trouble in the first place), restarted, lo and behold they worked!

So what I would suggest if you're having problems is to uninstall all driver files (nvidia-glx and the source files) and check your kernel folder for stray .ko files.

There are, however, still some minor problems with 180.22 that I've read several other people are having.  For instance, if I enable desktop visual effects, the screen is completely black when logging in.  However, I've found that by hitting ctrl-alt-f1 to go to the console, and then hitting ctrl-alt-f7 to go back to the UI, it works fine.  From what I've read it seems to be an issue with the drivers trying to default to a vga output...but that's an issue for another thread.

---

### Post by rmwoods on 2009-02-06
Thanks for posting your fix! I am away from home, but will try it when I get back.

---

### Post by madu on 2009-02-08
Hi,

I have had the same problem. But it was fairly easy to come back to normal mode by installing the 177.xx drivers. Anyway I also need to get working with the 180.xx drivers since it is providing some bandwidth increases in CUDA. But strangely its not working and comes up as low-graphics with my screen shift horizontally. Although this isnt even a beta driver.

I just want to know what files you removed in Synaptic. ALL the files with 'nvidia' in it? and also I couldnt find any /video folder is /lib/modules.
I have 2.6 27-11-generic and there is no such folder.

Any ideas?
Cheers.

---

### Post by soad6 on 2009-02-13
hey guys. I see that its almost everyone having this same issue! y hasnt 
anyone looked into this yet! my friend is currently running linux 8.04 Hardy
and i tried to install all the different restricted drivers from the repository, but with no luck the graphics card just seems to not work on linux 8.04. This is really troublesome because he wants to use compiz just to see what its like. The computer is an Acer Aspire 5520, Nvidia Graphics card = nVidia GEForce 7000M rev a2... If any one can help finding either drivers that support this with compiz effects or some other way to fix this so compiz will work properly! thank you again[-o<

---

### Post by soad6 on 2009-02-13
HAHA! i did it! theres a really simple way to get Nvidia 7000M graphics card to work! so simple i cant believe i overlooked it! Just upgrade to 8.10
(intrepid ibex) its supported automatically! duh! and if your running LTS 8.04 or an older LTS that doesnt show the support for upgrading to 8.10 then go to system>administration>softwaresources
go to updates>release upgrade> and change it to normal release. then go to update manager and update itll take aprox 1hr maybe less! and thatll fix the problem with the Nvidia 7000M cards graphics so you can use compiz!=D>

---

### Post by mercury00 on 2010-02-18
Did anyone ever get this working in 8.04?

---

### Post by rizzlesauce on 2010-03-03
I had a similar problem after installing the nvidia linux x86 driver (version 195.36.08[noparse])[/noparse]. Ubuntu would start in low-graphics mode.

To fix this I ended up doing several things:
[LIST=1]
[*]uninstall nvidia-glx from synaptic package manager
[*]delete all nvidia *.o, *.ko, and *.so files from my computer
[*]reinstall the nvidia drivers I downloaded from the nvidia website
[*]edit /etc/X11/xorg.conf to make it look like it did before installing the new driver
[/LIST]

In order to delete the module files, I ran the following commands in a terminal. I recommend not using the -exec argument at first so you can make sure you're not deleting something you don't want to delete.

```
sudo find / -name '*nvidia*.ko' -exec rm {} \;
sudo find / -name '*nvidia*.o' -exec rm {} \;
sudo find / -name '*nvidia*.so' -type f -exec rm {} \;
```

After following these steps and rebooting, the driver worked fine.

I don't know if all the steps I took were necessary to solving the problem, I just know that what I did worked for me.

---

### Post by dfwsupergeek on 2010-03-15
I've been having this problem with my Dell XPS M170 laptop, which I recently upgraded to a 10.04 alpha release hoping it would fix the problem...  NOTHING worked, re-installing drivers, etc... 
I have no idea how this worked, but it did- the only thing I can think of is that uninstalling all the nvidia drivers somehow forced the OS to use the nouveau drivers, but I finally have the right screen resolution! So, thanks for your tips- I uninstalled everything that said nvidia in the package manager, then removed all the nvidia *.so files by running nautilus as superuser... and when I rebooted to reinstall the nvidia driver, my screen is at the right resolution! 
Thanks a million!
[www.dfwsupergeek.com](www.dfwsupergeek.com)
:D

---

