---
title: "8800gts &amp; Nvidia Drivers -- Blank screen + No Video!  7.04 or Gusty same results..."
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by TwistedLincoln on 2007-07-10
I am unable to get my new 8800gts to work with Ubuntu using any of the Nvidia drivers.

All I end up with is a blank screen once gdm starts.  I can't switch to a virtual console.  I get no startup audio sounds or other feedback that the system is loading without the video -- everything just stops.  My monitor goes into sleep mode after a few seconds, and all hard drive activity ends.

[I]
**Here's what I've tried** -- note: I've tried each of these steps on both Ubuntu 7.04, and Ubuntu "Gusty Tribes 2" as well as Debian 4.0r0.  All were the 32bit versions.  All produce the exact same results.  Also note that I tried each test on the same machine, and once it failed, I did a fresh install before the next test:[/I]


**Installing either the nvidia-glx-new or nvidia-glx packages via Synaptic:**

Yes, I'm aware of the various bugs with these packages and the 8800 series cards.
Here's a few threads that I found that are relevant:

[[COLOR="Blue"]Bug in linux-restricted-modules-2.6.20[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641")

[[COLOR="Blue"]Missing module links in nvidia-glx-new[/COLOR]]("http://ubuntuforums.org/showthread.php?t=449105&highlight=libwfb.so&page=2")

I followed all of the suggestions posed in those threads, and while the workarounds do stop the X server blue screens and messages regarding incorrect modules, all I end up with is a black screen upon gdm starting...

**Installing the [[COLOR="Blue"]Nvidia 1.0-9755[/COLOR]]("http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html") drivers from the package downloaded from Nvidia.com:**

As indicated in the instructions, I removed the restricted drivers, the nvidia kernel, etc. from the system, using the "purge" feature of apt, and I installed build-essential.  The driver package installs without incident, but once the system is restarted, I get a black screen.  

Just to be sure, I then did a fresh install, and tried the other option -- adding the "nv" to the excluded modules list in the linux-restricted-modules-common config file as indicated here: [[COLOR="Blue"]Installing Nvidia drivers under Ubuntu[/COLOR]]("http://www.nvnews.net/vbulletin/showthread.php?t=72490")

Again, black screen.

**Installing the [[COLOR="Blue"]Nvidia 100.14.11[/COLOR]]("http://www.nvidia.com/object/linux_display_ia32_100.14.11%20.html") drivers from the package downloaded from Nvidia.com**

Same tests, and the same results as with the 1.0-9755 drivers...

**Installing the drviers via the [[COLOR="Blue"]Envy script[/COLOR]]("http://www.albertomilone.com/nvidia_scripts1.html"):**

The script installed the drivers properly, but again, a blank screen was the result...

**Logging into a failsafe terminal, then switching to runlevel 3:**

I only tried this because a [[COLOR="Blue"]user reported that it worked for him[/COLOR]]("http://ubuntuforums.org/showthread.php?t=431360&highlight=8800gts").  It didn't for me.  I still get a blank screen.

**Getting rid of the splash option in Grub:**

I can't remember where I read it, but some people reported that the black screen issue would be resolved if you remove the splash option from Grub.  Unfortunately, it looks like it only applies to the 64bit LiveCD not even starting with the "nv" driver.  It didn't help me a bit.

---------------

In each and every case, I can get X to work just fine using the "nv" driver instead of the proprietary Nvidia one.  But of course then I get no 3d acceleration, and my new 8800gts is worthless...

After I get a black screen, I reboot into single user mode, and check the contents of /var/log/Xorg.0.log.  Absolutely nothing seems out of place.  In fact, the log looks exactly the same as when I boot into X using the "nv" driver.  

Can anyone give me any insight as to what is causing this problem?  Is there another possible solution I haven't tried?

---

### Post by TwistedLincoln on 2007-07-11
Anybody have any thoughts on this?  This is driving me nuts...

Between Wine and Cegega, I've managed to get almost all of my games working within Ubuntu.  But that doesn't help me too much if all I get is a black screen... :)

---

### Post by Theimon on 2007-07-11
I had this too with my nVidia 6600(AGP). I went through hell and back to get this fixed. Eventually i found out that my video card wasn't recognized properly. It showed as a PCI card and somehow the i2c modules were to blame. 
I blacklisted the i2c modules in /etc/modprobe.d/blacklist, made sure xorg.conf was using the nvidia driver, rebooted the system and my card got recognized as it should. (simple step-by-step by yours truly on the nvnews forum: [http://www.nvnews.net/vbulletin/showpost.php?p=1231193&postcount=17](http://www.nvnews.net/vbulletin/showpost.php?p=1231193&postcount=17) ) 
After that the card has been running smoothly ever since.
I know AGP isn't the same as PCI-E, but I don't think there's much difference when it comes to the nvidia driver. So you might to check this out. Let me know how this works out, cause I got some new hardware coming in next week including a PCI-E nVidia 8500GT ;)

---

### Post by TwistedLincoln on 2007-07-14
Unfortunately, that solution didn't help.  I still get the black screen.

I re-tried the same fixes using the 64-bit version of Ubuntu, and the result was the same...

Is it possible that this isn't a software problem?  The only thing I can think of is some kind of incompatibily with my motherboard.  I'm running a Biostar N4SLI-A9.  I updated to the latest BIOS version, but that changes nothing.  I only suggest the motherboard as a possible culprit due to a report of a user having problems with the Windows Nvidia drivers using the same card and motherboard (his post can be found here: [[COLOR="Blue"]http://forum.pcmech.com/archive/index.php/t-175270.html[/COLOR]]("http://forum.pcmech.com/archive/index.php/t-175270.html"))

In any case, I'm really running out of ideas here. 

Can anyone else help?  I've searched and searched on this forum, and many others, as well as Google, but I can't find anyone who has the same issue...

---

### Post by TwistedLincoln on 2007-07-15
[B]UPDATE: 
[/B]
I removed the Biostar motherboard, and replaced it with an Asus A8S-X one instead.  I then did a fresh install of Ubuntu 7.04 (32bit).  I then removed the restricted driver modules, and the nvidia-kernel, and upgraded to the latest generic kernel in the repositories.  I installed kernel-devel and build-essentials.

I then proceeded to download the 100.14.11 drivers from Nvidia's website.

I then rebooted, and switched to a virtual console using Ctrl-Alt-F2, and stopped X using "sudo /etc/init.d/gdm stop"   I then installed the Nvidia drivers.

After a reboot... SUCCESS!  I have a picture!  Glxgears reports 12,000 - 14,000 fps!  Perfect!

Of course I still have no idea why the 8800gts wouldn't work with my Biostar motherboard.  Unfortunately, the Asus board that did work isn't mine -- I borrowed it from a friend.

I'm going to order a new motherboard now, but without knowing exactly what caused the incompatibility with the Biostar board, I risk repeating history with its replacement.  Perhaps I'll see if I can simply order an Asus A8S-X...

---

### Post by loserboy on 2007-07-17
I've also had good success with Gigabytes FWIW

---

### Post by dabl on 2007-07-17
Yep, that 8800GTS requires the 100.14.11 proprietary driver -- -9755 won't hack it.  And the nvidia-glx-new package has -9755, so you're stuck doing your own installation.  A lot of folks prefer the Envy script installer to do the installation, but it doesn't work in 100% of cases.

---

### Post by heldal on 2007-08-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **dabl said:**
> Yep, that 8800GTS requires the 100.14.11 proprietary driver -- -9755 won't hack it.  And the nvidia-glx-new package has -9755, so you're stuck doing your own installation.  A lot of folks prefer the Envy script installer to do the installation, but it doesn't work in 100% of cases.

nvidia's driver version 1.0.9755 works just fine with 8800GTX/GTS using the original driver-pack from nvidia. I've used it with a 8800GTS since feisty was released using nvidia-glx-new with the missing bits added from nvidia's driver pack. 

Ubuntu's problem is that the package maintainers have left out a x-server-module when they created the package. The missing module doesn't affect older GPUs.

The new 100.X driver is required for the most recent 8500, 8600 and mobile chips though. It also fixes a couple bugs for the 8800s but isn't required to make them work.

This is ridiculous. The problem was reported months ago and is still not fixed even though its as simple as a file + possibly a symlink missing in nvidia-glx-new. The current package is simply incomplete.

---

### Post by nitebum on 2007-08-07
> 
This is ridiculous. The problem was reported months ago and is still not fixed even though its as simple as a file + possibly a symlink missing in nvidia-glx-new. The current package is simply incomplete.

This. ](*,)

I mean come on. Its a popular card and a popular OS. I'm starting to come around to the idea that the whole Linux-Desktop thing is a sad joke.

---

### Post by dabl on 2007-08-07
> **nitebum said:**
> This. ](*,)

I mean come on. Its a popular card and a popular OS.

Ummmmm .... do you understand that the installed base of Linux desktop users is right about 2% of the total desktop & laptop market?  Ubuntu may be popular with you and me (it is!), but it's not POPULAR.  :-({|=

---

### Post by armin00as on 2007-08-07
***I fully agree on the "sad joke" part; ***

Linux Ubuntu appears to be a major pain in the neck, in every regard. 
Even though I like "tweaking" and "messing around" with my PC (upgrades, updates, maintenance, troubleshooting, installing new stuff...) my last 4 week with Feisty have been more hell than I would have expected it. Funny, but I'm not even using "ancient" parts. But, I guess _that exactly_ is the problem. It seems that especially people with 3+ -year equipment have gotten MythTV (and other stuff) running right out of the box. Guess I'll have to downgrade for the Ubuntu experience, huh?

Even though I got my NVIDIA 8800 GTS running without a problem(???) after only 1(!) day, I'm still trying to get MythTV working, but to no avail.
Nobody seems to have too much of a real clue around here (or in other Forums) either, even though I'm eternally grateful for the sparse support I've received (Thank You!!!)

[rant]
[B]I have to admit, it's great to have a free OS and software and join a great community of (Linux) Freaks, and all... But I simply can't stand wasting all my time with trying to fix the stuff that's breaking apart again as soon as I turn my back (or upgrade)... 
And even though my guts hate the "Evil Microsoft Empire", at least their crap is working!! 

If anybody knows of a working commercial Linux-based DVR solution (..I couldn't find any..), please let me know, as I'm growing sick and tired of trying to get MythTV running. 
After all, I think naming the Linux DVR software "MythTV" is no coincidence: 
I don't really believe anymore that anyone with 'rather new equipment' -and without a 'Geek degree' and triple MBA in Software Engineering- has ever gotten MythTV to work. So many issues and problems wherever you look...
Sure, Linux (Ubuntu) is more than just running a 'free' DVR - but that's the particular part of importance to me; hoping to kiss MS Windoze good-bye once and for all eventually...
[/B][/rant]

I'm afraid, 
It doesn't look like that's ever going to happen. 
I guess it's back to Windows XP and BeyondTV again now, which were actually working great for me thus far. I just hated having to switch between OS' (XP/Feisty), and I was hoping for a working alternative to VISTA, but that was just a pipe dream, so it seems... .

Seems like I'll take a break from Linux and wait until things (compatibility, drivers etc.) get better ....- or properly fixed. 
I'd love to pay some $$$ for working Linux solutions (such as a DVR) - if they would only work! -- Any ideas??

See you next Spring.
...and thanks for everything.

---

