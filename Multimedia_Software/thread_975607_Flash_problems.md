---
title: "Flash problems"
date: 2008-11-08
forum: Multimedia Software
---

### Post by bearcat on 2008-11-08
I'm having an ongoing problem with Flash in webpages that I'm not sure how to correct. It was doubly frustrating watching the US election on Tuesday night because these problems crop up most prominently on news websites.

The video clips and interactive results maps on CNN, for example, caused my computer to commit the Linux equivalent of the old classic Windows BSOD about seven or eight times on Tuesday alone. On MSNBC's site, on the other hand, sometimes the maps just wouldn't load at all, forcing me to shut down and restart Firefox, and if I try to watch Olbermann or Maddow via webvideo I can't watch two segments in a row without either reloading the page or restarting Firefox -- if I don't do one of those two things, the video player just stops after the first segment and doesn't load the next one no matter how many times I click on anything. 

On YouTube, conversely, I don't have too many problems unless I have more than one browser window open at once -- in which case the videos just don't load and the place where they should be just stays a blank greyish square. 

Any advice on what I can fix, or am I just stuck with this kind of frustration?

---

### Post by gandaran on 2008-11-08
it would help if you provide details of what you have installed for flash
adobe flash 9 or 10? gnash or swfdec flash?

---

### Post by bearcat on 2008-11-08
The only information I can find is flashplugin-nonfree 9.0.124.0ubuntu2. If you need more information than that I need assistance knowing where to look besides synaptic.

---

### Post by gandaran on 2008-11-08
> **bearcat said:**
> The only information I can find is flashplugin-nonfree 9.0.124.0ubuntu2. If you need more information than that I need assistance knowing where to look besides synaptic.
which ubuntu you running 8.04 or 8.10
try updating to  flash 10
post also the output of **locate libflash** here

---

### Post by bearcat on 2008-11-10
8.04, hanging back on the update for a week or so because I want to wait for any initial bugs to iron out. Not sure how to upgrade to Flash 10 if my update manager isn't giving me the option, though.

/usr/lib/flashplugin-nonfree/libflashplayer.so
/usr/lib/openoffice/program/libflash680lx.so
/usr/lib32/libflashsupport.so
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so

---

### Post by psyke83 on 2008-11-10
> **bearcat said:**
> 8.04, hanging back on the update for a week or so because I want to wait for any initial bugs to iron out. Not sure how to upgrade to Flash 10 if my update manager isn't giving me the option, though.

/usr/lib/flashplugin-nonfree/libflashplayer.so
/usr/lib/openoffice/program/libflash680lx.so
/usr/lib32/libflashsupport.so
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so

Your problem is a combination of PulseAudio and a bug in Flash 9's libflashsupport API. There is an excruciatingly detailed bug for this issue: [bug #192888]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888")

This bug is fixed in Intrepid; it is **not** fixed in Hardy. You can fix it (unofficially) in Hardy by following this guide: [http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

P.S. Following that guide will also upgrade Flash to the latest release, and won't interfere with official updates or distribution upgrades.

---

### Post by bearcat on 2008-11-10
Okay, thanks. I'll try that this afternoon.

---

### Post by gandaran on 2008-11-10
> **bearcat said:**
> 8.04, hanging back on the update for a week or so because I want to wait for any initial bugs to iron out. Not sure how to upgrade to Flash 10 if my update manager isn't giving me the option, though.

/usr/lib/flashplugin-nonfree/libflashplayer.so
/usr/lib/openoffice/program/libflash680lx.so
/usr/lib32/libflashsupport.so
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so

your flash should be updated by now! do you have the update channels enabled?
or try a complete removal of flashplugin-nonfree and run these commands
sudo apt-get autoclean 
sudo apt-get clean  
sudo apt-get update
now reinstall the flashplugin-nonfree, check if it's version 10
you can remove liflashsupport then, it's no longer needed with flash 10, it may even conflict

are you running ubuntu 64-bits? adobe flash sometimes doesn't work very well in 64-bits systems.

---

### Post by psyke83 on 2008-11-10
> **gandaran said:**
> your flash should be updated by now! do you have the update channels enabled?
or try a complete removal of flashplugin-nonfree and run these commands
sudo apt-get autoclean 
sudo apt-get clean  
sudo apt-get update
now reinstall the flashplugin-nonfree, check if it's version 10
you can remove liflashsupport then, it's no longer needed with flash 10, it may even conflict

Hardy briefly had the Flash 10 plugin, but it was removed because it needed many critical updates that were too disruptive for a SRU (Stable Release Update), including: complete removal of libflashsupport, updated 64bit libraries, nspluginwrapper 1.1.2, ALSA libraries >1.0.15 and a different default configuration for PulseAudio.

Hardy's latest version (in backports) of flashplugin-nonfree is: "10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2"

As you can see, it's "really" Flash 9 - a packager was forced to keep the higher version number in the package version string to ensure that Flash 10 would be downgraded to Flash 9.

See my post above for instructions to (unofficially) upgrade all the necessary components.

---

