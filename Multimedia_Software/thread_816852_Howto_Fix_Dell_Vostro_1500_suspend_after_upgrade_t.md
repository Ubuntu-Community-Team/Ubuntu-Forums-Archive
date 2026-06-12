---
title: "Howto: Fix Dell Vostro 1500 suspend after upgrade to Hardy Heron 8.04"
date: 2008-06-03
forum: Multimedia Software
---

### Post by edwardblum on 2008-06-03
If your like me and you spent weeks and weeks trying to work out why your laptop would not resume from suspend even after going through all the tutorial to fix it that vaguely relate to the problem.

One thing that I did find was that suspend worked on a fresh install of ubuntu, got me thinking...

Can i not run the script that runs when ubuntu does a fresh install.. I CAN! using dpkg-reconfigure

Straight from the manual: reconfigures packages after they have already been installed. Pass it the names of a package or packages to reconfigure.
**It will ask configuration questions, much like when the package was first installed.**




Remember to backup your old Xorg.conf before continuing incase you made custom changes to your xorg.conf >>

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
```

as my laptop was running a  NVIDIA 8600M GT i reconfigured the NVIDIA packages using

```
sudo dpkg-reconfigure nvidia-settings nvidia-glx-new
```

this applies to all nvidia cards as i had the same problem on my desktop and funnily enough the same problem (suspend broke after upgrading the hardy heron)  on my gilfriend machine who was running intel graphics for hers i had to run dpkg-reconfigure...

```
sudo dpkg-reconfigure xserver-xorg-video-intel
```
 
works! 




Hope it works as it did for me, now if you get a Blank White screen this seems to be a problem with gnome screen saver you can disable the screen saver after resuming by disabling lock on resume.

run:

```
gconf-editor
```

then unclick apps>gnome-power-manager>lock>suspend

temporary solution to fix it!

Also if you find that you computer resumes into tty1 and you have to help it along by pressing Ctrl + Alt + F7 your not alone tho i do find that waiting a couple of second it does eventually switch to the GDM. I guessing its timing out on some devices, any one fixed that bug?

---

### Post by mdcallag on 2008-06-13
Using gconf-editor to change the settings for apps>gnome-power-manager>lock>suspend worked for me. Thanks. I have a Dell Vostro 1400 with an Nvidia 8400M GS and Hardy.

:)

---

