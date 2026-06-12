---
title: "Video hangs but sound plays on"
date: 2008-07-21
forum: Multimedia Software
---

### Post by itssaurav2004 on 2008-07-21
hi guys i am having this weird problem with my ubuntu 8.10 installed desktop:
the video hangs for a while and the sound continues playing in all players vlc,mplayer,etc, i also reinstalled linux mint elyssa but problem exists.

i have 1.5 gb ram with 2.5 gb dedicated to video
my onboard graphics card
GeForce 6150SE nForce 430

plzz help

---

### Post by flytripper on 2008-07-21
whats the format you are watching?

---

### Post by itssaurav2004 on 2008-07-22
mostly avi

---

### Post by irshadcharm on 2008-07-22
**_Fix for Video Playback Problem in Compiz-Fusion_**


While running Compiz-Fusion, You wouldn’t be able to see any video play while either moving the window, viewing desktops in expo, 3d cube, or any other cool effect for that matter; instead you would see a blue screen, including when viewing in full screen. 

*** GStreamer Users** (The default video player in Ubuntu, totem-gstreamer, and any video player that is based on the gstreamer backend)
o Open a terminal and type “gstreamer-properties”. Press Enter.
o Click the Video tab.
o Under Default Video Plugin select “X Window System (No Xv)”.
o Click Test to verify that video playback is working (you should be able to see the standard TV testing colour stripes).
o Click Close

*** VLC Users** (VLC is not installed by default)
o Start VLC and click on Settings, then Preferences.
o Expand Video and then expand Output modules. You will notice several options for output device.
o Select the item Output modules, and notice the checkbox at the bottom right that says Advanced options. Check the box, and now you have the option to select a different output device.
o Pick X11 video output
o Click on Save and you are set!

*** MPlayer Users** (Mplayer is not installed by default)
o Start Mplayer
o Right-click on the screen and select Preferences
o Select the Video tab and under Available Drivers select “X11 (XImage/Shm)”
o Click Save and restart the program for the setting to take effect.
+ Some times MPlayer may not be able to show videos in full screen.

*** Xine users**
o Start xine
o Click File, then Configure and then Preferences
o In experience_level select “Master Of The Known Universe” so that all available settings are visible.
o Select the tab for video.
o Under Driver select “xshm”.
o Restart xine.
+ The same process enables Totem that has the totem-xine backend configured.

---

### Post by itssaurav2004 on 2008-07-23
thanks for the help

---

### Post by irshadcharm on 2008-07-25
Enjoy Ubuntu Rollercoaster

---

