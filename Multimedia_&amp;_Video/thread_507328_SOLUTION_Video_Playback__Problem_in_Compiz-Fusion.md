---
title: "SOLUTION: Video Playback  Problem in Compiz-Fusion"
date: 2007-07-22
forum: Multimedia &amp; Video
---

### Post by kevinmedina on 2007-07-22
I was searching high and low for a solution to a video playback problem while running Compiz-Fusion:

While running Compiz-Fusion, I wouldn't be able to see any video play while either moving the window, viewing desktops in expo, 3d cube, or any other cool effect for that matter; instead I would see a blue screen, including when viewing in full screen.  After days of trying out all sorts of different things, I found the final solution!  It is from Gremlinzzz, written in this thread: [http://ubuntuforums.org/showthread.php?t=480357]("http://ubuntuforums.org/showthread.php?t=480357")

* GStreamer (The default video player in Ubuntu, totem-gstreamer, and any video player that is based on the gstreamer backend)
o Open a terminal and type "gstreamer-properties". Press Enter.
o Click the Video tab.
o Under Default Video Plugin select "X Window System (No Xv)".
o Click Test to verify that video playback is working (you should be able to see the standard TV testing colour stripes).
o Click Close

* VLC (VLC is not installed by default; you need to search in the package manager, then install)
o Start VLC and click on Settings, then Preferences.
o Expand Video and then expand Output modules. You will notice several options for output device.
o Select the item Output modules, and notice the checkbox at the bottom right that says Advanced options. Check the box, and now you have the option to select a different output device.
o Pick X11 video output
o Click on Save and you are set!

* MPlayer (Mplayer is not installed by default)
o Start Mplayer
o Right-click on the screen and select Preferences
o Select the Video tab and under Available Drivers select "X11 (XImage/Shm)"
o Click Save and restart the program for the setting to take effect.
+ Some users reported that MPlayer may not be able to show videos in full screen.

* Xine
o Start xine
o Click File, then Configure and then Preferences
o In experience_level select "Master Of The Known Universe" so that all available settings are visible.
o Select the tab for video.
o Under Driver select "xshm".
o Restart xine.
+ The same process enables Totem that has the totem-xine backend configured.
---

I'm posting this because this solution isn't advertised as being one for the blue screen problem that many people experience with Compiz Fusion but never find the solution to.  I'm going to post this in a variety of other forums where I've found the problem posted. I hope this helps!!!! :)

---

### Post by webjames on 2007-07-25
i am honered to be the first one to thank you for this excellent solution. it worked wonders with my laptop (T41 thinkpad) with the  "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]" card. works perfectly now. many thanks!

---

### Post by kevinmedina on 2007-07-25
I'm so happy to help!!!! :)

---

### Post by HeavyAl on 2007-07-26
I was just in the middle of trying to figure out the same problem and this did the trick! Thanks very much!

---

### Post by kevinmedina on 2007-07-31
I'm glad to hear that this has proven to be the solution! Be sure to repost and give gremlinzzz credit

---

### Post by kane77 on 2007-08-07
wow!! that actualy solved the issue! thanx

---

### Post by Dod_basim on 2007-08-18
Works like a tiger! Thanks alot!

---

