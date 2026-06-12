---
title: "Mythtv with xbmc script help"
date: 2010-07-16
forum: Mythbuntu
---

### Post by jonnybignote on 2010-07-16
Hi all

I'm running Myth for tv and recording playback but XBMC for music and video (iso dvd) playback.

Mythbuntu 9.10 64bit (don't want to move to 10 yet as everything else working fine)
Using PulseAudio on system for compatability but Alsa for Myth and XBMC

I run this script (cobbled together from various sources) from keyboard shortcut to launch XBMC.

```
#!/bin/bash

#kill mythfrontend
killall mythfrontend.real
#lock mythwelcome
mythshutdown -l
# Test to see if XBMC is running first
if ps -ef|grep -v grep|grep -i xbmc.bin
then
# Do nothing
echo "XBMC already Running!"
else
# Startup XBMC
ps aux|grep -v grep|grep -i pulseaudio|awk '{print $2}'| xargs kill -9
xbmc
fi
if ps -ef|grep -v grep|grep -i xbmc.bin
then
sleep 10
else
mythshutdown -u
fi

```

It quits any running mythfrontend, checks for existence of xbmc process and if not running already, kills PulseAudio (if I remember correctly) which loses me the menu sounds but gives me audio in the media files via alsa:spdif.

The problems then start.  I want it to keep checking for process xbmc.bin and, if not found (ie I closed it) then run mythshutdown -u which will unlock the timer on mythwelcome to allow the machine to standby.

I obviously don't have the right kind of code to achieve this and need some kind of loop.  If I quit xbmc inside of the 10 secs then it works (obviously) but I want it to keep checking constantly while I'm using it and then act upon it after I close.  I'm also having a problem in that going back to Mythtv the sound doesn't work until I either change channel or exit and go back in again - do I have to stop the pulseaudio server again?

Sorry for my lack of knowledge here...any help greatly appreciated.

---

