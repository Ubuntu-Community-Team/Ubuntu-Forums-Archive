---
title: "flash player has no sound and crashes"
date: 2009-11-22
forum: Multimedia Software
---

### Post by Kraxuntu on 2009-11-22
I've been trying to fix this for a while, but none of the solutions offered seem to help, so I'm posting a call for help.

After upgrading from Ubuntu 9.04 to 9.10 I've been unable to get any flash player to work. The problem persists after two clean installs. I'm using the 32-bit version of Ubuntu. The specific problem is this: flash player loads and starts showing the video, but there is no sound. After a while (this seems to vary) it freezes and crashes Firefox. For a while I could fix this temporarily by reinstalling the flash player, but this did not fix the problem, and it doesn't seem to work anymore.

I've tried installing Adobe flash player and both of the free flash players, with no improvement. This problem appears in both Firefox and Epiphany, latter of which I installed just in order to test if flash would work better with it. The version of Adobe flash player I've been trying to use is the one in repositories (10.0.32.18), but today I tried manually installing the more recent one from Abode, version 10.1. It installed without problems and seemed to work, but did not help with the crashing. Both of the free flash players did worse, with no playback at all.

I would guess the problem has something to do with sound issues, but flash player is the only program with problems with sound. There are no other sound issues.

I hope I have given enough information, and I hope someone can help me with my problem.

---

### Post by lobozoo on 2009-11-24
Okay, I had nearly the same problem and this is how i solved:

First of all restart you computer...
Now open terminal and type these codes..

sudo apt-get remove swfdec-mozilla

sudo apt-get remove mozilla-plugin-gnash

sudo apt-get remove adobe-flashplugin

sudo apt-get remove flashplugin-nonfree

sudo apt-get install flashplugin-nonfree
This will make sure there is no conflicting streamers....

Now type in terminal:

sudo mkdir /etc/adobe

*echo* "*OverrideGPUValidation*=true" >~/mms.cfg

sudo mv ~/mms.cfg /etc/adobe/
Okay now that this is done you need to open you home folder with root permissions. In terminal type:

gksudo nautilus

this will open  a window.
Navigate to this folder
/usr/lib/firfox-3.5.3  or  3.5.5  or witch ever on you have.

Find the files run-mozilla.sh and firefox.sh , in both of these files add these to lines of code as a second line ie: not right at the top of the page and dont put # in front of it neither....

export LD_PRELOAD=/usr/Lib/LibGL.so.1
export XLIB_SKIP_ARGB_VISUALS=1

Now save and exit.......restart  and that should do it. we hope..

---

### Post by UNME on 2009-11-24
Since sound is not there it could be due to known bug in pulseaudio

I assume that alsa is installed in your machine.
I did following:

Step 1 - sudo apt-get remove pulseaudio
Step 2-** reboot machine**
3 Sounds are back (provided you are using alsa - most likely it is already there)

Now there is one caveat - your sounds applet will not work and will be removed from task bar (because that was for pulseaudio)

Work with - Install alsa-mixer (check ubuntu synaptic package manager or what ever is your packager manager) 

Note- few guys here did following as step 4 and it worked:

sudo apt-get install --reinstall pulseaudio and it worked.

Hope it helps

---

### Post by Kraxuntu on 2009-11-25
Edit:

Spoke too soon. 

The first advice did nothing. Reinstalling pulseaudio seemed to help for a while, but then the problem returned -- just like every time I reinstalled flash.

I checked the audio settings, and it says that Firefox is using the ALSA audio plugin. Could this be the problem? Should it be using pulseaudio?

I could try using only ALSA (like you suggested), but I'd prefer using the default one, if I can get it working.

Edit2:

I tried uninstalling pulseaudio and working with ALSA only. In addition to being a bit difficult (no easy way to change the level of volume) it didn't fix the problem. I could still get audio in other programs, but no sound in flash.

---

