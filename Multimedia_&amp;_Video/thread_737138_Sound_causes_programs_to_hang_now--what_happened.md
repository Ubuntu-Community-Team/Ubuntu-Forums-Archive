---
title: "Sound causes programs to hang now--what happened?"
date: 2008-03-27
forum: Multimedia &amp; Video
---

### Post by caljohnsmith on 2008-03-27
I'm using gutsy, and up until today, my sound was working great.

But now, if I try to play any sounds, it causes the program to hang that is trying to play it, or the program simply acts like it can't play the sound file at all. Or in the case of Audacity, if I try to load up Audacity, it simply doesn't load. If I go to System > Preferences > Sound, and hit the "test" button, the sound program hangs no matter which driver is selected. If I try the play a sound file in KMPlayer, KMplayer can't play it and just sits there. This all used to work before today.

One thing that DOES work is going to the command line and type "mplayer audiofile.wav" or whichever audio/video file I want, and the sound works great. :confused:

Note I went thru the sound troubleshooting guide ([http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)) and reinstalled all the sound packages as it describes. This worked briefly after I rebooted--I loaded up Audacity fine, played sound fine. But then I went to my setup login screen utility (right-click my login name at top of screen) to get back my "login successful" sound, and when I clicked on "play" the program froze up. And after that I was back to the same problems--audacity wouldn't load, etc. :confused:

Anybody have any ideas of how to troubleshoot this? Any help would be gratefully appreciated!

---

### Post by ubuntu-freak on 2008-03-29
Do you have both onboard sound and a sound card? Did these problems occur after installing Audacity? Try removing Audacity and fix your sound with those packages again. If you have two sound devices, install asoundconf-gtk, press alt+f2, then type in "asoundconf-gtk", press enter and select the sound device you wish to use.
 
Hope that helps.
 
Nathan

---

