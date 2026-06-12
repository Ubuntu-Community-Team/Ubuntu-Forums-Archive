---
title: "Video playback freezes screen randomly while sound &amp; keyboard works"
date: 2010-02-12
forum: Multimedia Software
---

### Post by vcppp_p on 2010-02-12
Hi,
I'm using Ubuntu since 8.04, and the current (9.10) is a fresh install on new HDD.
The problem was the same each version (8.04, 8.10, 9.04, 9.10) - while I'm playing the video (no matter if I use mplayer [SMPlayer], gstreamer [Totem] or Adobe Flash plugin [YouTube]) the playback freezes randomly for about 5-10 sec. During the freeze the movie is still played, I can hear the sound is OK. If I press [space] in SMPlayer it pauses the playback, so the responses for keyboard actions are ok. Not for the mouse clicks however. I can still move the cursor around the screen but it seems the system is not aware of it (clicking on the "pause" button doesnt pause the movie). Except the cursor, nothing changes on the screen (if the IM [Pidgin] window was blinking because of new message, it freezes etc etc).

Is there any kind of log I could look into just to try figuring out the problem?

Please, help me somehow - it is impossible to watch any movie on my PC (currently I don't have TV...)

I installed windows on external HDD once and it played videos fine so I suppose it's not hardware problem .


thanks in advance...
v.

---

### Post by ToSsMaStR on 2011-01-11
Exactly the same problem here.

Videos work fine in a windows environment. I have tried different players aswell?

---

### Post by ToSsMaStR on 2011-01-11
I think I may have found a solution:

It is from Gremlinzzz on this thread : [http://ubuntuforums.org/showthread.php?t=480357](http://ubuntuforums.org/showthread.php?t=480357)

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

Hope it helps!

---

### Post by wiggie on 2011-02-17
Well this totally screwed my system.

Now everytime  video is open, either through vlc or flash on a website, the system doesn't respond anymore. I can move the mouse, and sometimes move between windows, but clicking totally fails, I cannot move a window, I cannot click the system or applications tab, I cannot log out.

I set it back to the default value, but it still freezes.

---

