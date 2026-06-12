---
title: "[SOLVED] Error Installing Nvidia-glx-new In Gutsy"
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by morning_napalm on 2007-10-25
I just managed to upgrade from Feisty to Gutsy.  It certainly wasn't a piece of cake.  I think an issue with the nvidia-glx driver caused a bunch of problems.

I finally got it to work and the Restricted Drivers Manager informed me there was a restricted driver available so that I can enable 3D settings.  I tried using the Restricted Driver Manager to install it and get the following error message:

_An error occurred:  The following details are provided._
E: /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.9_i386.deb: subprocess pre-installation script returned error exit status 2

A copy of the installation details in in the picture attached (not sure how to copy or get a file of that log).

Any help would be greatly appreciated!

---

### Post by sanddgroper on 2007-10-26
While its not the answer you might want to hear you
may need to do a fresh install of 7.10.You might like
to check out some of the posts here of people having
problems after doing a 7.04 to 7.10 upgrade.Also you could
try uninstalling the restricted drivers and reinstalling them
through synaptic to see if the same error occures.

Cheers
Sandy

---

### Post by morning_napalm on 2007-10-26
Thanks for the tip.

I did a little looking this morning and I think the issue I had may be related to Envy.  I am pretty sure I should have used Envy to revert back to the standard nv driver before I did the upgrade to Gutsy.  There is some information on the Envy website that may help and I will try it tonight.

I will keep track of what I do and hopefully it will work.  I will post results here if it does.

---

### Post by Seraed on 2007-10-26
That's the same problem I am having as well. I also did not think to revert back to the original 'nv' driver before my upgrade. I'd rather not do a fresh install, as right now, the only issues on my system stem from not having the nvidia-glx (and glx-new), as in: no compositing, no 3d accel for games, etc.

---

### Post by dabl on 2007-10-26
I don't believe you need to re-install.  Here's what should work:

1. Change to a VESA display:

```
sudo dpkg-reconfigure xserver-xorg
```

choose "no" to autodetect, and choose "VESA" as the display type, and accept defaults.  Set your resolution to 1024x768 or something that's comfortable for the moment, and a safe refresh rate.  Restart the X server with Ctrl-Alt Backspace.

2. Download the current Envy deb file from here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

You want the file "envy_0.9.8-0ubuntu8_all.deb"

3. Install Envy (just right-click the download and use the Gdebi installer).

4. Run Envy.  Best chances of success are if you Ctrl-Alt-F1 to a CLI terminal, and enter ```
sudo envy -t
```

5.  Enjoy your new driver!

:guitar:

---

### Post by Seraed on 2007-10-26
Sorry Dabl, no such luck for me. During the install, Envy spat out the same "subprocess pre-installation script returned error exit status 2" as does the restricted driver manager, and Synaptic.

One thing of note is that everytime I've tried reinstalling the driver the update manager's notification icon pops up in the system tray. If you click on it, it will tell you that the Software Index is Broken. It give you instructions each time to either run "sudo apt-get install -f" or to use Synaptic to fix it.

I've done both options and with Synaptic it tells me that it is the nvidia driver package.

---

### Post by nhutto on 2007-10-31
i am having a similar issue but i do not know what this envy thing is but when ever i try to enable my nvidia driver it says

The software source for the package

   nvidia-glx-new

 is not enabled.

does any one know why this is 
i tried to enable it through the restricted drivers manager in gutsy


NEVERMIND i fixed it i looked up envy and that worked for my thanx man

---

### Post by morning_napalm on 2007-10-31
I removed the old version of Envy and then followed the instructions that were posted by dabl.  This worked great and now things are running smoothly.

Thanks to everyone for your help.  Hopefully this will be helpful to others as well.

---

