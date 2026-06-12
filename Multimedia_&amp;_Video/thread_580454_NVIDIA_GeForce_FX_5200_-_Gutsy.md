---
title: "NVIDIA GeForce FX 5200 - Gutsy"
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by eekfonky on 2007-10-18
Just updated to Gutsy and so far so good apart from hoping my graphics card issues would be a thing of the past. When I go to System -> Preferences -> Appearance -> Visual Effects and try to enable 'Normal' all the borders are cut off the windows and I cannot select any of the 4 desktops.
I have installed the drivers with Envy and it appeared to work on reboot, but nothing is different, still the same old problem.

Any Ideas?

---

### Post by wolfbone on 2007-10-19
I don't know what Envy is but I had the exactly the same problems as you (same card). Installing compiz-gnome seemed to fix them.

Not very impressed with the effects though, I then installed compiz, which dragged in the compiz-fusion-plugins*. I then found I needed to install compizconfig-settings-manager so that I could configure all the effects.

---

### Post by FredB on 2007-10-19
> **eekfonky said:**
> Just updated to Gutsy and so far so good apart from hoping my graphics card issues would be a thing of the past. When I go to System -> Preferences -> Appearance -> Visual Effects and try to enable 'Normal' all the borders are cut off the windows and I cannot select any of the 4 desktops.
I have installed the drivers with Envy and it appeared to work on reboot, but nothing is different, still the same old problem.

Any Ideas?

Envy is USELESS with gutsy gibbon. Just remove drivers envy installed. And use restricted manager. Compiz will work flawlessly. No need to install compiz-gnome or any other package.

You'll only need compiz config manager to tweak the effect.

---

### Post by eekfonky on 2007-10-19
Thanks, I tried the 2 suggestions above and to no avail. I used envy as a last resort. I can only assume it will never work. unless anyone has comprehensive guide as to what to do because I've un-installed, purged and re-installed lots of different ways! Plus I've checked out all stickys to do with this - nothing works.

It appears that this just isn't going to work - aaargghh!

---

### Post by bmk789 on 2007-10-19
I'm experiencing this problem too on my laptop with a GeForce Go5200 GPU.  I enabled the extra effects and it works except for the window decoration, etc.  Since we both upgraded from Feisty instead of a clean install of Gutsy, I'm assuming there is a library missing.  I'll try installing a few and post the results.

---

### Post by mohnkern on 2007-10-19
When I tried to use Envy to update to the restricted driver,Envy told me it didn't support the version of Ubuntu I was running (I am on Gutsy).

When I installed the restricted-drivers manager, and attempted to install it that way I got the following error:

/var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-19.9_i386.deb: subprocess pre-installation script returned error exit status 2



As a last ditch effort, I downloaded the driver from the nvidia site, and attempted to compile it (I'd done this before under RHEL 3, 4, 5 with no problem, and the compile *appeared* to run okay, but the X Server crashed when I tried to start it.  Not a happy thing.

If you get a solution, I'd love to hear it.  I'm running the "non restricted" driver right now, but obviously compiz, beryl, and desktop effects don't work.

---

### Post by juniorsonny on 2007-10-19
I have a Nvidia GeForce FX 5200 also. I also used the newest version of Envy which came out 10/18/07.  I don't know if my desktop effects work because I don't use them but I will just to see if I have any problems.  Envy did get all my games working.  But now them computer won't come out of sleep mode if it is left that way for too long.  Will get back to let you know if my desktop effects are not working correctly.

---

### Post by bmk789 on 2007-10-19
Install the "xserver-xgl" package and restart your desktop.  
Solved all my problems.  Compiz now works perfectly.  Enjoy!

---

### Post by eekfonky on 2007-10-19
That just causes a conflict...don't recommend it, but thanks for trying

---

### Post by juniorsonny on 2007-10-19
I haven't tried to install it yet.  I might wait.  just have the hanging up in sleep mode problem.  I've noticed that there is always video card problems with new kernels and upgrades but it all seems to work out after a while.  Or at least for me it has.

---

### Post by pommattski on 2007-10-21
Does anyone have any updates on whether they managed to get this card working properly with Gutsy?... In particular the TV Out?
I am hoping to use one for a MythTV/Gutsy Desktop box...

Cheers, Matt.

---

### Post by NeoLithium on 2007-10-21
I have a GeForce FX 5200 as well; just installed the drivers through the restricted driver manager with no problems.  One thing that did need to be changed, was my monitor- it wasn't autodetected properly, so it wouldn't allow for the proper resolutions.

---

### Post by Victormd on 2007-12-06
For starters, I'm really new to the linux/ubuntu environment. I've just installed a clean version of Ubuntu 7.10 amd64. When trying to install the nvidia restricted driver... it installed just fine, no errors. When I restarted the comp., no GUI... no command line... nothing.
Any suggestions?

---

### Post by IDmeNa on 2008-03-25
I also have a problem with my nvidia 5200 and gutsy; back on feisty my graphics worked all cool without problem, when I upgraded to version 7.10, my nvidia card stop working properly, again I struggle to find the correct drivers and all that stuff... at last, I managed to do something good (I had to use Envy) and my desktop effects (compiz) work excellent for me, although, the problem is far from being completely solved; now I can't run any of the games I used to run, the images move at.... I don't know... 1 frame per minute =S and after a while they just hang, so I have to reboot the desktop. Due to this I'm considering.. downgrading my version of ubuntu =/
Things I've tried:
x Unlocking the "restricted driver" thing
x Choosing the driver manually from the list of drivers given at Sytem/Administration/Graphics
x Download and install the drivers form the oficial site on nvidia
~ Download Envy and let it do its magic thing

Anyone with yet another idea?
Thanks in advance

GeForce FX 5200 - 128 MB
NVIDIA DRIVER VERSION: 169.12
Linux-x86 7.10 (gutsy)

---

