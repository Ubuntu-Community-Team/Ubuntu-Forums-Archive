---
title: "no video on Chromium/ Lubuntu 12.04"
date: 2012-09-30
forum: Multimedia Software
---

### Post by pottzie on 2012-09-30
This is on a fresh install of Lubuntu 12.04. Lubuntu comes with Chromium (and a big thumbs up on that!) but I haven't found a way to get video working. I've followed a few guides, some say to edit the sources in the Software Center, but the Software Center version I have doesn't appear to give me a way to select my choices, there is no tab to edit any preferences, as far as I know.

 The guide at the top of the Multimedia forum  gives some info, but when I try to run the command to get the (massive) string, it fails. The first command worked, but the mile-long string in the Lubuntu line wouldn't work. As I said, I haven't done anything to enable additional sources.
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
 Bash may be expecting me to have edited something for a source list, but I haven't found what or where I need to ad anything. The guide also suggests getting getdeb, but again it won't work without enabling any additional sources, and I don't know if the instructions are valid with Lubuntu, or just Ubuntu.
 just found this: [http://ubuntuforums.org/showthread.php?t=2064747&highlight=youtube+video+lubuntu](http://ubuntuforums.org/showthread.php?t=2064747&highlight=youtube+video+lubuntu)

 and ran "sudo apt-get install lubuntu-restricted-extras lubuntu-restricted-addons" It ran, but after it finished Lubuntu gave an error box saying that it was unable to open the sources. Youtube still doesn't play, but I'm going to reboot and see if anything changes after doing that.

 Nope, no change after rebooting...except that I've got a big red circle in the package tray (Lubuntu showed an error dialog box and asked if I wanted to file a report, but the screen closed before I could check anything). I also somehow managed to loose my fonts, at least here in the forum.

 And I get this error when I try to update my system:

$ sudo apt-get update
E: Type '<html><head><meta' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.

 Found instructions for getting rid of the error at [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

 The error is now gone, but still no video. Going for a reboot. After rebooting, failed to do anything, in regards to video. I followed another guide:

 helpdeskgeek.com/linux-tips/give-your-ubuntu-installation-full-multimedia-support/

 and after running "sudo apt-get install adobe-flashplugin" I now get a black screen in Opera (trying other browsers besides Chromium, to see if it makes any difference). Chromium now says that I need to install adobe flash player, and links to Adobe's site, but the download won't go, and Bash shows that flashplayer is up to date.

---

### Post by TenPlus1 on 2012-09-30
If you want a quick fix go here: [www.google.com/chrome](www.google.com/chrome) and download/install Google Chrome...  It comes already packed with Adobe Flash 11.3 which works on install...

---

### Post by pottzie on 2012-09-30
Nope, Google Chrome doesn't play video either.

 I have an AMD cpu, and this computer has seemed to have "Linux Teflon," as I've had problems installing various operating systems before. The Lubuntu live cd worked real well, that's why I'm going with it now.
 lscpu shows:
```

lscpu
Architecture:          i686
CPU op-mode(s):        32-bit
Byte Order:            Little Endian
CPU(s):                1
On-line CPU(s) list:   0
Thread(s) per core:    1
Core(s) per socket:    1
Socket(s):             1
Vendor ID:             AuthenticAMD
CPU family:            6
Model:                 8
Stepping:              0
CPU MHz:               1798.459
BogoMIPS:              3596.91
L1d cache:             64K
L1i cache:             64K
L2 cache:              256K


``` 

 I also came across an article saying that if I checked "Log in without password' when I installed (and I did), that somehow that would bork a flash install. Doesn't make sense to me, but that's what it said.

---

### Post by pottzie on 2012-10-01
I seem to have gotten video working by running apt-get update, and then apt-get -u dist-upgrade. It brought in 2 additional files/programs, and now video works....kinda.

 By that I mean that some video plays, but that some web pages that expect have a lot of effects, like Yahoo's home page, still don't work.
 
 But still, I was pleasantly surprised to get anything working. I'm going to mess with this a bit before I mark it solved, and see if I can see what's working and what isn't.

 Edit: Added ffmpeg from Synaptic, and that made things better. Still can't play some videos, while others work. Not sure why. I also have seen some references to copying the .so file from Adobe to..uh, somewhere in my file system. I have no clue where, but I remember needing to do that to get video working in Slackware. Seems funny to have to do as much work to get something going with an Ubuntu variant as a Slackware install, but if that's the way it is, then that's the way it is.

---

