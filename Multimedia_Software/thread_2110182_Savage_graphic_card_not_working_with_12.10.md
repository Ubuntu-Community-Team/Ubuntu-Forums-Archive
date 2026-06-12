---
title: "Savage graphic card not working with 12.10 ?"
date: 2013-01-29
forum: Multimedia Software
---

### Post by Xav24 on 2013-01-29
I'm using a thinkpad T22  equipped with a savage graphic card.
It was working very well with xubuntu 12.04 until i decided to upgrade to 12.10. Then after the reboot, i see xubuntu loading and when it's supposed to ask me for the password then the screen is unreadable (same thing with live cd).
I tried different things without success so if someone has a solution...

i join you what my lspci return and my .xsession-errors.
Thanks

---

### Post by tgalati4 on 2013-01-29
Search for nomodeset.  If kernel mode setting (kms) is turned on, then chances are your video won't work.  I had a T22 years ago.  Generally a nice machine, but slow by today's standards.  The S3 graphics chip is one step above drawing with a stick in the mud.  But a colorful stick.

---

### Post by Xav24 on 2013-01-29
> **tgalati4 said:**
> Search for nomodeset.  If kernel mode setting (kms) is turned on, then chances are your video won't work.  I had a T22 years ago.  Generally a nice machine, but slow by today's standards.  The S3 graphics chip is one step above drawing with a stick in the mud.  But a colorful stick.

Thanks for the answer ; i already tried that and also to "force" different modes but it didn't work.
I'm using this machine just for internet, mails and a few php applications that do not require too much ressources ; it was working well enough in 10.04 but i would prefer to find a solution rather than downgrading to 10.04...

---

### Post by tgalati4 on 2013-01-29
Is the s3 module even loading?

```
lsmod
modinfo s3
```

It's possible it was not included in 12.10:

tgalati4@Dell600m-mint14 ~ $ modinfo s3
ERROR: modinfo: could not find module s3

Page through your Xorg log file:

```
cat /var/log/Xorg.log.0
```

---

### Post by kurt18947 on 2013-01-30
Were you using 12.04 or 10.04 previously?  If 12.04 works, it's LTS - supported 'til 2017.  If 10.04, support runs out pretty soon.  If necessary, perhaps move to a non-*buntu distro such as puppy or crunch-bang?  Those are intended for older machines and are less demanding of their graphics subsystems.

---

### Post by Xav24 on 2013-01-30
> **kurt18947 said:**
> Were you using 12.04 or 10.04 previously?  If 12.04 works, it's LTS - supported 'til 2017.  If 10.04, support runs out pretty soon.  If necessary, perhaps move to a non-*buntu distro such as puppy or crunch-bang?  Those are intended for older machines and are less demanding of their graphics subsystems.

Hi kurt,

i was using a 12.04... which was working fine. Just wanted to test the upgrade on this machine. If the problem cannot be solved then i will go back to it but if i can avoid that, i would rather prefer ! ;) 
Moreover, it looks like a 'driver' problem so there should be a workaround then i'll try to find it for a few days more. If I can't, then i will abandon.

---

### Post by Xav24 on 2013-01-30
> **tgalati4 said:**
> Is the s3 module even loading?

```
lsmod
modinfo s3
```It's possible it was not included in 12.10:

tgalati4@Dell600m-mint14 ~ $ modinfo s3
ERROR: modinfo: could not find module s3

Page through your Xorg log file:

```
cat /var/log/Xorg.log.0
```

s3 is not loaded and i don't see anything related to s3 in the modules directory.
here is my lsmod and Xorg log. Any idea on the way to have it loaded ?
If there is no other solution i'll try this : [http://ubuntuforums.org/showthread.php?t=1688211&highlight=savage](http://ubuntuforums.org/showthread.php?t=1688211&highlight=savage). It doesn't appear to look so far from my problem !?

---

### Post by tgalati4 on 2013-01-30
You are running the vesafb or VESA frame buffer video driver.  It is the lowest common denominator for video drivers.  If s3 is not included, then perhaps it was renamed or merged with another video driver.  Load a Live DVD of 12.04 and do an lsmod to see what gets loaded for a video module.

There is a "savage" driver, but it looks like it's for higher-end video cards:

tgalati4@Dell600m-mint14 ~/Desktop $ modinfo savage
filename:       /lib/modules/3.5.0-17-generic/kernel/drivers/gpu/drm/savage/savage.ko
license:        GPL and additional rights
description:    Savage3D/MX/IX, Savage4, SuperSavage, Twister, ProSavage[DDR]
author:         Felix Kuehling
srcversion:     AA9A37DA6E205D877D946B4
depends:        drm
intree:         Y
vermagic:       3.5.0-17-generic SMP mod_unload modversions 686

The other post tweaks the vesa module with some xorg.conf settings.

---

### Post by Xav24 on 2013-01-30
> **tgalati4 said:**
> You are running the vesafb or VESA frame buffer video driver.  It is the lowest common denominator for video drivers.  If s3 is not included, then perhaps it was renamed or merged with another video driver.  Load a Live DVD of 12.04 and do an lsmod to see what gets loaded for a video module.

There is a "savage" driver, but it looks like it's for higher-end video cards:

tgalati4@Dell600m-mint14 ~/Desktop $ modinfo savage
filename:       /lib/modules/3.5.0-17-generic/kernel/drivers/gpu/drm/savage/savage.ko
license:        GPL and additional rights
description:    Savage3D/MX/IX, Savage4, SuperSavage, Twister, ProSavage[DDR]
author:         Felix Kuehling
srcversion:     AA9A37DA6E205D877D946B4
depends:        drm
intree:         Y
vermagic:       3.5.0-17-generic SMP mod_unload modversions 686

The other post tweaks the vesa module with some xorg.conf settings.

It's what i thought when i read the log but i was not sure... that's why i was wondering about trying the tweaksin xorg.conf.
Here are the results of the commands

---

### Post by tgalati4 on 2013-01-30
So it looks like the *savage* module was loaded in 12.04 and you get full resolution and decent performance.  But for some reason the vesafb module gets loaded in 12.10.  This is affectionately called a *regression*.  Something works in an old version and mysteriously breaks in a newer version.

I would follow the link that you posted and put the *savage* module in xorg.conf.

---

### Post by Xav24 on 2013-01-30
I'll try that in a few hours then i let you know...

---

### Post by Xav24 on 2013-01-31
Finally, the solution described in there ([http://ubuntuforums.org/showthread.php?t=1688211&highlight=savage](http://ubuntuforums.org/showthread.php?t=1688211&highlight=savage)) worked perfectly without having to change any line.
It's too bad that it's not working with the correct drivers but anyway it works !!! :p
Thanks again for the help.

---

### Post by tgalati4 on 2013-01-31
This simply comments out the savage module and substitues the VESA frame buffer module with several discrete settings to get graphics to work.  I wonder what the difference in performance is?  Try running extremetuxracer with both modules (in 12.04 and 12.10 with vesafb) and see what the framerate differences are.

---

### Post by Xav24 on 2013-01-31
> **tgalati4 said:**
> This simply comments out the savage module and substitues the VESA frame buffer module with several discrete settings to get graphics to work.  I wonder what the difference in performance is?  Try running extremetuxracer with both modules (in 12.04 and 12.10 with vesafb) and see what the framerate differences are.

Is there an other way like a tool to check the framerate, i installed it with my 12.10 but i've got a 'freezed' picture each 30 sec...:) so i cannot imagine installing it with my livecd...

---

### Post by tgalati4 on 2013-01-31
Like I said, an S3 is like drawing with a stick in the mud.  Sorry, that was an unfair test.  Yes, you can simply run:

```
glxgears -info
```

And framerate will be displayed in a console:

394 frames in 5.0 seconds = 78.766 FPS
378 frames in 5.0 seconds = 75.386 FPS
369 frames in 5.0 seconds = 73.623 FPS

Your numbers will be lower, I'm sure.  And it's in the standard distro, so you can run it in the LiveDVD.  I would be curious to see the difference.  It's just not as much fun as tuxracer.

---

### Post by Xav24 on 2013-01-31
It's not very far from what you have...:lolflag:
With the **12.10**, i've got :
62 frames in 5.0 seconds = 12.391 FPS
62 frames in 5.0 seconds = 12.254 FPS
46 frames in 5.0 seconds =  9.197 FPS
70 frames in 5.0 seconds = 13.982 FPS

With the **12.04** (live cd) :
31 frames in 5.0 seconds = 6.161 FPS
33 frames in 5.1 seconds = 6.530 FPS
33 frames in 5.1 seconds =  6.534 FPS
33 frames in 5.0 seconds = 6.542 FPS
XIO: fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0" after 646 requests (644 known processed) with 0 events remaining.

you're right, it's less fun than tux but i can make it work at least. :)

---

### Post by tgalati4 on 2013-01-31
Now that is interesting!  The VESA framebuffer driver is a faster stick in the mud than the savage driver.  Who would of thought?  I supposed you could use the vesafb module in 12.04 with similar results.  

Well glxgears will just be playable at 12 frames per second.

I'm running Mint 14 on a crappy, 9-year-old, Dell 600m laptop with an OK
graphics card and the open radeon driver.

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Radeon RV250 [Mobility FireGL 9000]

It's quite usable and it was given to me as a freebie because Unity ran too slow on it, forcing the owner to get a new laptop with Windows7.  

I put 2GB of RAM on it and it runs Linux Mint Mate quite well (gnome2 fork).

My other laptop is a T43P with a newer ATI FireGL card, and it runs ok with the radeon driver as well.

---

### Post by DELOMOSNE on 2013-05-02
> **Xav24 said:**
> Finally, the solution described in there ([http://ubuntuforums.org/showthread.php?t=1688211&highlight=savage](http://ubuntuforums.org/showthread.php?t=1688211&highlight=savage)) worked perfectly without having to change any line.
It's too bad that it's not working with the correct drivers but anyway it works !!! :p
Thanks again for the help.

Hello,

 Excuse  me, I'm French and I do not write a correct English


I have the same problem with  S3 Savage MX-MV.
I do not understand how you solved this problem in xubuntu 12.10.
Which file did you change to the display work?
Regards

 
Max DELOMOSNE

---

### Post by DELOMOSNE on 2013-05-03
Here is  the complete  solution for the  S3 Savage  MX-MV

At the time  of display  problem
..
Ctrl + Alt + F1 (or F2, or F3 etc.).
During your session, your screen becomes a console.
Login:
Password:

It  starts by  generating its xorg.conf.new which does not exist in Xubuntu 12.04

sudo X-configure

Copy  / etc/X11

sudo  cp / home / .... / xorg.conf.new / etc/X11/xorg.conf

Install  wim editor

sudo  apt-get install vim

Afterwards, edit the xorg.conf file using vim:

sudo  vim / etc/X11/xorg.conf

To  insert text, press i, then esc when done.
To delete an Entire line, dd (that is, the d key twice).
To quit without saving exchange, q.
To save changes,: wq.

Correct  the following  in:

Section  "Device"
         [...]
        Identifier "Card0"
# Comment out or delete the following line
# Driver "modesetting"
# Add the following line
      Driver "vesa"
EndSection

Restart  BOOT: Ctrl + Alt + Del.

:P:guitar:

Max DELOMOSNE

---

### Post by tormod on 2013-06-24
Support for Savage cards got broken in 12.10 but has now been fixed in Saucy (see [https://bugs.launchpad.net/bugs/1083032](https://bugs.launchpad.net/bugs/1083032)). The fix will be backported to 13.04, hopefully soon.

The 3D support for Savage cards (and all other older cards) was removed in mesa 8 (Ubuntu 12.04). However you can install the needed drivers from [https://launchpad.net/~xorg-edgers/+archive/mesa-legacy](https://launchpad.net/~xorg-edgers/+archive/mesa-legacy)
Then glxgears and tuxracer should work fine again.

---

