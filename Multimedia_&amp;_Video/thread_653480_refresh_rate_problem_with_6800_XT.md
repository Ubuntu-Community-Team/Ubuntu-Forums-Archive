---
title: "refresh rate problem with 6800 XT"
date: 2007-12-29
forum: Multimedia &amp; Video
---

### Post by alisonnic on 2007-12-29
I have just installed Ubuntu 7.10 on a desktop with an nVidia 6800 XT.  I need help in finding a way to control the refresh rate being sent to the monitor by the Restricted Driver.

At certain times the Restricted Driver arbitrarily switches to a refresh rate of 50 Hz, but my monitor does not support this refresh rate. It needs a minimum of 56 Hz.

How can I prevent the Restricted Driver from using a refresh rate below 56 Hz?


Here are some details about what happened:

After installation, which went smoothly, I ran the Restricted Drivers Manager and enabled the NVIDIA accelerated graphics driver (latest cards).  After installing the driver, this asked for a reboot.  I waited until the system updates completed and then rebooted.  

When I did, all went well until Ubuntu got to the login screen.  At that point, my monitor complained that the signal it was receiving was not supported, and displayed nothing.

I unplugged the cable from the monitor and plugged it into another monitor.  This monitor displayed the login screen, and i was able to log in.

I went to System/Preferences/Screen Resolution Preferences and found that the resolution was correct, at 1440x900, but the refresh rate was at 50 Hz.  I switched the refresh rate to 56 Hz (the only other option here) and then switched the cable back to the original monitor.  Now all seemed well.

However, then I tried to watch a movie using Totem, the movie player that came with Ubuntu.  This worked until I switched to Full Screen mode.  At that point the monitor went blank, again complaining that the signal was not supported.

Swapping to the other monitor, I found that the refresh rate had switched back to 50 Hz.

Apparently my monitor (a Dynex 19 inch LCD screen) does not support a refresh rate of 50 Hz.  I need to keep the refresh rate at a minimum of 56 Hz in order for the monitor to work correctly.

I've done some experimenting, including playing with System/Screen and Graphics Preferences (which, incidentally, would not allow me to send a signal to a second monitor plugged into the other jack on the video card) and also duiong a sudo dpkg-reconfigure xserver-xorg.  So far nothing's worked.

How can I keep the nVidia driver from arbitrarily switching to a refresh rate of 50 Hz?  

Thanks in advance for any help you can give me!

-------------------------------------
Here's my system configuration:

Asus A7N8 Deluxe motherboard
eVGA 6800 XT
Athlon XP 3000+ Barton
1 GB memory
Dynex DX-LCD-19 monitor (reports as HISENSE)

---

### Post by alisonnic on 2007-12-31
Okay, here's some more info on this problem.

Following the instructions in this thread:

[http://ubuntuforums.org/showthread.php?t=651235&highlight=nvidia+resolution](http://ubuntuforums.org/showthread.php?t=651235&highlight=nvidia+resolution)

I was able to get the refresh rate back to 60 Hz, so I can see the X desktop again.

However, it appears that all this did was set the nVidia driver back to the default driver that comes with Ubuntu 7.10.  This has a fixed refresh rate of 60 Hz.

This allows me to see the login screens, and it also allows me to play movies full screen without losing the display due to the refresh rate dropping to 50 Hz.  

But there is a big disadvantage: when being fed the signal at 60 Hz, the Dynex monitor moves the screen display about 1/4 inch to the right, chopping off the rightmost side of the X desktop.  I've got the monitor's horizontal position set all the way to the left, so there's no help there.

Also, with the default driver, I can't get any of the advanced graphical effects that are available in the restricted driver.  So the default driver isn't really satisfactory.

However, if I switch back to the restricted driver, the same problems recur: I can set the refresh rate to 56, which is great (the screen aligns properly and the slithery warpy window behavior is back), but the refresh rate drops to 50 Hz on the login screens and if I play a movie full screen, and the display goes blank.

So the problem is, how do I make the restricted driver behave?  All I want to do is make it keep the refresh rate at 56 Hz no matter what I do.

Is this so difficult?  Can't I just edit some config file somewhere to eliminate the 50 Hz option and make the restricted driver stay at 56 Hz at all times?

---

### Post by bharadwaj on 2007-12-31
but hey the refresh rate sown in the screen resolution may not always be right

---

### Post by alisonnic on 2007-12-31
Good point, bharadwaj.  However, the behavior is very consistent: if the refresh rate being shown in the Screen Resolution Preferences popup is 50 Hz, the Dynex won't display what's on the monitor.  But if the refresh rate shown there is 56 or 60 Hz, the Dynex is quite happy.

BTW, I found a workaround for the loss of the right edge of the screen: if I change the Clock parameter in the VGA menu on the Dynex monitor, I can shrink the width of the screen and get the right-hand edge to show.

So now it's more of a question of getting the nVidia driver to work properly.  I can live without the advanced visual effects, and with a screen that's slightly narrower than it should be, but it bugs me that this terrific video card's capacity is being wasted.

I've poked around in etc/X11, but I can't seem to find a file that sets the refresh rate, even though I recall seeing a refresh rate range parameter in one of the screens of the dpkg-reconfigure utuility.  

Anyone have any idea where this parameter lives, and if I might be able to safely change it to restrict the nVidia Restricted Driver to a minimum of 56 Hz?  

This seems like a fairly trivial thing; I just can't seem to find where to do it.

---

### Post by alisonnic on 2008-01-06
About at my wit's end on this problem.  Tried over and over to set the refresh rate to a minimum of 56 Hz  by editing /etc/X11/xorg.conf and inserting values for the horizontal and vertical refresh rates in the Monitor section below Option "DPMS":

Horizsync 56
Vertrefresh 56

Then I reconfigured X by doing this:

Pressed <Ctrl><Alt>F2 and logged in. Then, reconfigured my X server:
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
Last, I pressed <Alt>F7 to get back to the GUI login screen and restarted X again with <Ctrl><Alt>Backspace.

But all this did was remove the lines I'd inserted into xorg.conf.

If I go to the Restricted Drivers Manager and enable the nVidia Restricted Driver, the same problem occurs: refresh rate drops to 50, which is below the rate that my monitor can display.  I'm hosed.

I've also tried to install the latest driver which I downloaded from nvidia.com.  Their instructions say to set the boot level to 1, 2, or 3 by editing /etc/inittab and then shut down X and all OpenGL apps, but they give nary a clue about how to do any of that on Ubuntu.  /etc/inittab doesn't even exist on my Ubuntu install.

I did find some instructions in another thread for logging in under Safe Mode, and then somehow I managed to shut down X, but I still didn't have any way to set the run level to a safe level in case something went wrong.  Nor did I know how to ensure all OpenGL apps were stopped.

What the heck, I figured, at this point I've got little left to lose.  If I hose the install, maybe I'll try a different flavor of Linux.  Or just buy another copy of XP, much as that thought galls me.  I've wasted way too much time on this problem as it is.

So I executed the nVidia installer package.  It got as far as trying to compile a kernel interface (it didn't find a precompiled one either local or on the web) and produced this message:

ERROR: You do not appear to have libc header files installed on your system. 
       Please install your distribution's libc development package.

I booted back into X and ran the Synaptics Package Manager.  It shows a number of packages starting with libc: libc3*, libc6 (which is installed), libc6-amd64, libc6-dbg, libc6-dev, more libc6's,  libcairo*, libcal*, etc.

How do I tell which one(s) of these I need?  And will I need to install more stuff in order to complete this install?

Has anyone even tried to install these new nVidia drivers on 7.10 Gutsy?  Any success?

Or am I going down the wrong path?  All I want to do is keep the screen refresh rate from falling below 56, while taking advantage of the 3D features of my 6800GT video card!  Is this supposed to be this difficult??

---

### Post by perixx on 2008-01-07
removed - look below

---

### Post by perixx on 2008-01-07
Additional Info and ideas:

Hello...

I'm not sure if it solves your problem, but I've experienced several cases of a false screen refresh output in the video-settings manager. Even I can only choose 70Hz, e.g., checking the actual V-Sync rate in my monitor's OSD menu, will show the 75Hz.

If you're using a TFT skip 56 Hz and use 60Hz instead! AFAIK, most TFT's can support only a single fixed vertical refresh rate (60HZ), or maybe one or two others (75/85Hz), sometimes only in analog-mode; 56Hz seems rather uncommon to me. I would suggest you to use a Vsync spec of "60-75" (if your TFT supports also 75Hz) in your xorg.conf. Make a backup of your current file with:
> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.std
and be sure to have specs you know of they're working in it + "vesa" instead of "nvidia" or "nv" in your driver's section. Thus, you have failsave backup you can jump back to, if things screw up, by doing
> sudo rm /etc/X11/xorg.conf
sudo cp /etc/X11/xorg.conf.std /etc/X11/xorg.conf from the bash (that is, when you get some colorful text error message when booting - use CTRL+ALT+F2 to open a virtual terminal if you can't reach the command line)!

Btw., H-Sync in /etc/X11/xorg.conf is NOT related to your monitor's (picture per seconds) 'refresh rate' (that would be V-Sync), but to the frequency range of your monitor's horizontal resolution range (e.g. 1280 pixels at 19" >> 64 [COLOR="Blue"]k[/COLOR]Hz). 
So sth. like 28 - 64 (min - max) would apply to your H-Sync's range values (provided, you've got a standard 19" TFT). In case your manual doesn't give you the info, just run Windows or any other OS where you can set your maximum screen resolution and look up your current Sync rates in the OSD menu. 
I've read about several issues (and had my share of probs as well) with the 'dpkg -reconfigure' command, so I'm no great fan of it - as the staff member stated, I would recommend to use it only if you've left no choice. Most things can be fixed in the xorg.conf file.

You could also try to set your favourite screen resolutions in the respective section of xorg.conf, by adding the desired refresh rate like so: ```
"1280x1024@60Hz    "1024x768@60Hz" .... etc.
```

If all fails (if you got some weird wide-screen format e.g., try using modelines instead (haven't got info how to do that here, though).


Regarding the installation of your drivers: (assuming you've downloaded the latest Nvidia-installer) you need the libstdc++6 and libstdc++6-dev packages, so as it seems. Maybe also the libstdc++5 package, hardly an earlier one I suppose (if the driver is based on that one). Check also for "linux-headers-generic" and "linux-headers-[kernel version]", "build-essential" and "module assistant". Also look for the existence of the file /usr/bin/ld.

Another idea comes to my mind: when you activate the retricted driver, are you able to run '/usr/bin/nvidia-settings' 
and edit your screen refresh rate there by chance? If not, try running 'usr/bin/nvidia-xconfig' at the bash, check and - if necessary - edit /etc/X11/xorg.conf's H / V Sync settings with
> sudo nano /etc/X11/xorg.conf (save & exit with CTRL+X / Y / ENTER 
and restart your X-server with
> sudo /etc/init.d/gdm restart


I've been installing the newest Nvidia driver myself as of today, and I had the problem, that the installer would compile a kernel-module for an old kernel that was still residing in /lib/modules; I did a "sudo /usr/bin/nvidia-installer --uninstall" to dispose of the misinstalled driver and deleted the old kernel's folder in the mentioned directory: > sudo rm /lib/modules/[OLD KERNEL FOLDER]. [B][COLOR="Red"]
This only applies to you, if you did a kernel-update, of course. Be careful though, not to remove the wrong one!! If you're unsure or only have a single folder here, DON'T DELETE ANYTHING!!![/COLOR][/B] 
**Check your current kernel with > uname -r first!**

After removing this one I still had to wipe a residing part of the previously compiled kernel-module with > rm /lib/modules/[CURRENT KERNEL]/volatile/nvidia*
maybe also this one:
rm /lib/modules/[CURRENT KERNEL]/kernel/drivers/video/nvidia/*
Where of the latter one I'm pretty sure it remains the same, but it's rebuilt during the installation of a new driver.

Having those steps done, you can try your luck again...

If nothing works, do "sudo /usr/bin/nvidia-installer --uninstall" again, edit your xorg.conf as described above, replacing the term "nvidia" in the drivers section with "vesa" and restart your X-server. Then install the old proprietary drivers from the Ubuntu-repos.

Remark: I'm using Xubuntu 7.04, so I cannot guaratee if this also works with Gutsy! I also had a look at the link you've mentioned; there's a sub-link where s.o. states:> Google gave me nothing, and the only information i have is the 50/60 Hz on the label of the flat panel. I try these numbers. I would wager this label is referring to your power line's frequency, not the monitor's Sync-specs (in respect to the 50/56Hz matter above)...!
 

perixx

---

### Post by perixx on 2008-01-07
Hi alisonnc,

here I am again - I've dug up sth. by chance; perhaps this also applies to you (regarding the wrong Screen Refresh options)? It does for several typs of Nvidia cards, as I've seen here:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/92599]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/92599")

good luck!

perixx

---

### Post by alisonnic on 2008-01-09
Than you so much, Perixx!  The first suggestion in your post, to modify xorg.conf and add @56Hz to the resolution declarations was what I needed.  First I switched to the nVidia Restricted Driver, then logged into a terminal window, and added the @56Hz to each resolution.  Once I did this, and rebooted, all seemed well.  

[Actually, you were also right about the refresh rate being misreported.  After I set the refresh rate in xorg.conf to @56Hz and rebooted, the monitor reported this as 60 Hz.]

Oddly, now when I open Screen Resolution Settings, the only available values are 50 and 51 Hz.  So I can't use that utility any more.  But I guess I don't need to.

Anyway, I now get readable screens at login, and I'm able to use the highest level of Visual Effects on the desktop.  Squishy windows, semi-transparency, etc.  And I was able to play an AVI movie in full screen mode without having the refresh rate drop to a level unsupported by my monitor.

The only problem now is that the monitor seems to have gotten messed up somehow.  When make the monitor auto-adjust its size, the desktop squishes down to about 2/3 of the available screen real estate, and scrunches all the way over to the right.

A little tinkering with the manual Clock and Horizontal Position sliders in the monitor's menus allowed me to stretch the desktop out to nearly fill the monitor, so it's workable.

Also, I know this isn't an Ubuntu/X/nVidia problem because the monitor does the same thing when connected to another computer, also sending 1440x900 at 60 Hz.  It used to work fine on the other computer, so there's something wrong now with the monitor.  Maybe plugging and unplugging it while getting the Ubuntu box to work fried something inside the monitor.

Anyway, thianks again!

---

### Post by alisonnic on 2008-01-09
perrix,

I've done a little more tinkering.  Now that I've enabled the restricted driver, I find that I can indeed run .usr.bin.nvidia-settings. Cool!  I didn't even know about this, so thanks for telling me about it.

I also tried running /usr/bin/nvidia-xconfig but although it ran, it didn't seem to do anything.

Since things are working now, I'm not going to try to install the newest driver right away.  Maybe I'll do it sometime when I'm feeling really ambitious!

Thanks again, perrix!  You've been extremely helpful!

---

### Post by perixx on 2008-01-10
> Maybe I'll do it sometime when I'm feeling really ambitious! I'd recommend so :)
It took me a whole day to find out that installing the latest ATI driver only worked when directly running them. 
As those drivers wouldn't run 2 games anymore (and the ATI drivers perform not too satisfactory), I figured, I might try to uninstall them and use a Geforce 6800XT with latest drivers as a test instead.
 
What a waste of time! It got me crashing in EVERY 3D-app I started (I was down to using the 'Linux magic keys' to restart the PC)... and I had REALLY a lot of trouble with getting the drivers up and running - old and new one - each. So until I learned that the Nvidia card just won't work, another day went by. After this, re-installing the ATI drivers left me with  non-functional OpenGL... till I figured out how to fix it (rather easy if you know what to do) and successfully downgraded to my old repository drivers for my ATI card, nearly a 3rd day was gone :P 

I call it 'a crash-course in installing drivers' ^^

perixx

---

