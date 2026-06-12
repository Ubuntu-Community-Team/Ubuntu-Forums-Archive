---
title: "Nvidia Drivers: Can someone help me 'root canal' them so I can reInstall?"
date: 2010-09-20
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by TBerk on 2010-09-20
I updated the Maverick beta over the top of 10.04 and lost my ability to confidently boot directly into the GUI. 

My work around is to use the failsafe mode in GRUB, and get in in what it tells me is 'low graphics mode'.  (I believe it too because while static pictures haven't suffered, Video Playback is jumpy and glitchy now...).

I most recently tried to get the Drivers from Nvidia directly; 

NVIDIA-Linux-x86-173.14.27-pkg1.run

But even after 'installing it' I can't successfully reboot and go directly to the log in screen, can't enable Hardware Drivers for the video card, can't count on 'X' loading from scratch, etc.

 Rather than feed me a fish, could somebody help me learn _how_ to Fish?


TBerk

---

### Post by NightwishFan on 2010-09-21
Ubuntu made changes to the Nvidia infrastructure that does not allow installation of drivers manually. You will need to use a supported PPA or the repository. I BELIEVE this is the case with Maverick as well.
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Incompatibility%20with%20nVidia%20upstream%20driver%20installer](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Incompatibility%20with%20nVidia%20upstream%20driver%20installer)

Your best bet is to remove the driver. You can do so by finding the .run you used to install it. Replace the filename.run with the name of your nvidia driver .run file.
```
sh filename.run --uninstall
```

Afterwards it might be wise to hold shift while rebooting and select to go into recovery mode, and run the option to repair the x server (if it still exists I am unsure, cant reboot to check right now).

---

### Post by sdowney717 on 2010-09-21
> Ubuntu made changes to the Nvidia infrastructure that does not allow installation of drivers manually. You will need to use a supported PPA or the repository. I BELIEVE this is the case with Maverick as well.

I just successfully manually installed the latest driver from the nvidia site
.run file

boot into recovery mode
find the file
run it like this ./nameoffile.run
ignore the symbolic link

---

### Post by SeijiSensei on 2010-09-21
I'm running Maverick on a system with an NVIDIA card and have never needed to update my drivers manually through a number of kernel updates.  I recommend you uninstall your current driver as NightwishFan suggests, then use the "Additional Drivers" application to find the NVIDIA driver in the repositories that matches your current kernel.  Once you've installed the version that Ubuntu expects, you should find that the driver is automatically updated along with the kernel.

---

### Post by sdowney717 on 2010-09-21
I like running the latest video drivers straight from nvidia.
IMO, this gives you the best driver you can get.
When I just upgraded to MM, the one they gave me would not let me boot into 2.6.35 kernel.
manually installing nvidia.run driver and now I can boot into 2.6.35


nvidia2601904.run

[http://www.nvidia.com/object/linux-display-ia32-256.53-driver.html](http://www.nvidia.com/object/linux-display-ia32-256.53-driver.html)

I am currently running 2601904

[http://www.nvidia.com/object/linux-display-ia32-260.19.04-driver.html](http://www.nvidia.com/object/linux-display-ia32-260.19.04-driver.html)

---

### Post by NightwishFan on 2010-09-21
I read there was some lack of compatibility with the manually installed drivers now, however I could be wrong. As I no longer have Nvidia cards I have no clue. :)

---

### Post by sdowney717 on 2010-09-21
it gives you a symbolic link error message.
But the driver installs and works.
Been doing that error for a long time.

---

### Post by TBerk on 2010-09-21
1) I installed the Nvidia driver _after_ the upgrade to MM beta 'broke' my pre-existing , & working, Nvidia/10.04 combination.

2) I installed the ...RUN file from Nvdia's site, but it didn't help.  I can uninstall it, (and will) but it'll take me back to square one, not back to Zero so to speak like I'm looking to do.

3) I'm familiar w/ using hte 'Hardware Drivers' app, but it doesn't help as I end up with "Drivers are loaded but not active..." as other have also related.


More to follow.

TBerk

---

### Post by dino99 on 2010-09-21
use genuine ubuntu packages , if our devs makes some tweaks its because of some needs/reasons, thats it.

sudo rm -f /etc/X11/xorg.conf

add this ppa to synaptic sources tab:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

update, upgrade then reboot and check driver activation (system admin additional drivers)

---

### Post by TBerk on 2010-09-21
> **NightwishFan said:**
> Ubuntu made changes to the Nvidia infrastructure that does not allow installation of drivers manually. You will need to use a supported PPA or the repository. I BELIEVE this is the case with Maverick as well.
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Incompatibility%20with%20nVidia%20upstream%20driver%20installer](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Incompatibility%20with%20nVidia%20upstream%20driver%20installer)

Your best bet is to remove the driver. You can do so by finding the .run you used to install it. Replace the filename.run with the name of your nvidia driver .run file.
```
sh filename.run --uninstall
```

Afterwards it might be wise to hold shift while rebooting and select to go into recovery mode, and run the option to repair the x server (if it still exists I am unsure, cant reboot to check right now).

I actually tried running that command from within the GUI (failsafe, low-rez mode) and found it balked and told me so. So, I rebooted to a command line environment and ran the file from there, and it looked liked it installed.  (error message says "scripts failed to run, do you want to cont?", and I replied 'yes')

Only the GUI won't default to ON and I can, again only get it to load if I choose the second GRUB menu option;

(Recovery mode). Then FailsafeX, low graphics mode, one time session... blah, blah, blah.

Major difference this time around is the additional drivers app sees the 173.14.27 native driver aw installed, but the Nvidia X server still won't start up correctly.

I can do the same command w/ the --uninstall on the end, and I will next, but it'll only take me back to the same trouble I'm currently experiencing, namly I can boot Ubuntu 10.10 into a gui environment, only if I failsafe, low graphics, One time (and/or restart X) every time.

If I let the GRUB default to a 'normal' boot it drops me out into a command line state to log in and running 'X' wont fly at that point.


TBerk
I can smell fish, and maybe there is bait on the line, but I don't think I have a line in the water yet...

---

### Post by TBerk on 2010-09-21
> **dino99 said:**
> use genuine ubuntu packages , if our devs makes some tweaks its because of some needs/reasons, thats it.

sudo rm -f /etc/X11/xorg.conf

add this ppa to synaptic sources tab:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

update, upgrade then reboot and check driver activation (system admin additional drivers)


THIS Sir, shows promise....
I'm posting prior to a reboot that may just 'fix' every thing. 


(Synaptic is currently downloading an additional 27M of goodness...)


So, How many pulls should I let out the line then?


TBerk
I think I might be fishing after all...

---

### Post by TBerk on 2010-09-21
Partial, and Qualified Success. At least I can now let GRUB default to a 'normal boot and have the GUI environment load as expected.

And, I can see the System:Administration:Additional Drivers show both "current version correct" as well as the Nvidia_173, the later driver I have removed and again rebooted. 

Currently, and the reason I say partially successful, is I see from Additional Drivers I have the correct driver installed BUT Nvidia Xserver wont act right, it keeps wanting me to run 'nvidia-xconfig' as Root, but that doesn't seem to do anything.

I'm going to leave well enough alone, for now, and pick this back up in a few days. 

Thx for the help.


TBerk

---

### Post by VinDSL on 2010-09-21
> **NightwishFan said:**
> Ubuntu made changes to the Nvidia infrastructure that does not allow installation of drivers manually. You will need to use a supported PPA or the repository. I BELIEVE this is the case with Maverick as well.[...]I have manually installed nVidia .run files several times in Maverick.  I have probably done this 2 times a week, since I installed Alpha 3 (now Beta).

As a matter of fact, installing the .run files is the only thing that's kept me going!

After (almost) every kernel update, since I installed Maverick, I am stuck at Plymouth.  Booting into safe-mode, dropping to root (in tty), and manually re-installing the nVidia drivers from a .run file does the trick every time.

I purged my system of all supported nVidia drivers, 3 weeks ago.  They don't work worth jack on my 7600 GT.  And, this is NOT a condemnation... just saying!  

All I have been running is certified/beta builds from nVidia .run files, and they have worked great - albeit, having to be re-installed and built off the new kernel, on every update.

If somebody has a better way of keeping Maverick going, let me know.  But, the .run files have been a blessing, so far!  ;)

---

### Post by sdowney717 on 2010-09-21
> As a matter of fact, installing the .run files is the only thing that's kept me going!

same here. It is all I use going back several years. I dont understand why this works for some people and apparently not others. It is nice to always have the latest driver.
My card is nvidia 8400gs pcie.

---

### Post by VMC on 2010-09-21
Here's how I [**_install nvidia drivers manually on Maverick_**]("http://ubuntuforums.org/showthread.php?t=1467074"). If the first post#1 doesn't work, try post#35. 

This topic was first posted for Lucid, but works for all my Mavericks installs.

---

### Post by NightwishFan on 2010-09-21
I am glad it works. I assumed it would not was all.

---

