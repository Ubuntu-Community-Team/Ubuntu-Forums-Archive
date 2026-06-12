---
title: "audio advantage micro"
date: 2009-07-18
forum: Multimedia Software
---

### Post by houblon on 2009-07-18
when I asked the techs at Turtle Beach about a driver for the Audio Advantage Micro, they told me to install the Audio Advantage Micro USB sound card as "C-Media USB Audio Device, chipset number CM106.

How do you install it as "C-Media USB Audio Device"? It is ALSA supported but I haven't been able to locate a driver.

---

### Post by neu2buntu on 2009-07-18
i have an external usb with the same chipset and it works perfectly when run through "qjackctl" (frontend for jack audio connection kit) using the alsa drivers. im not sure what version of alsa has these drivers but i am using the latest!!!

---

### Post by houblon on 2009-07-25
I finally found the way to get the audio advantage micro working by reinstalling stuff that I messed up with all my attempts. 

I went to the Comprehensive Sound Problem Solutions Guide v0.5e at 
[http://ubuntuforums.org/showthread.php?t=205449&highlight=82801G+Sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=82801G+Sound)

and did the following. It worked perfect.


Getting the ALSA drivers from a *fresh* kernel

Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. One way to go back to the old setup is to reinstall Ubuntu. However, this step is actually quite unnecessary since you are reinstalling everything because of one thing.

A faster way, is to just remove the problematic packages and reinstall them cleanly.

(1) Remove these packages
Code:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils


(2) Reinstall those same packages
Code:

sudo apt-get install linux-sound-base alsa-base alsa-utils

[list][*]
VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:

sudo apt-get install gdm ubuntu-desktop


(3) Reboot
[*][left]
VERY IMPORTANT NOTE: Xubuntu (XFCE) users have reported that packages 'gdm' and 'xubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:

sudo apt-get install gdm xubuntu-desktop


(3) Reboot
Now you may ask "I already had the packages, so why did I go through the trouble of removing them, then installing them". The answer lies in the --purge option which removes all the extra information that accumulated from tinkering and upgrading. After doing a purge then install, the packages are unpackaged as if it they are brand new.
(4) At this point, try using
Code:

 aplay -l

you should get your soundcard listed.

    * Success - Your soundcard is detected. Go onto the Using alsamixer section, then try playing something on your music or media player.
    * Failure - Your card was not detected. You should try compiling your driver, so go onto ALSA drive Compilation.

---

