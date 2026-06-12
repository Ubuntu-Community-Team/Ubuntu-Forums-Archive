---
title: "cant play videos with beryl on"
date: 2007-06-26
forum: Multimedia &amp; Video
---

### Post by jerrykun on 2007-06-26
hehe this is funny, my only problem comes when i have beryl on i found that i cant play videos on my labtop. But if i turn off beryl i can see them in all players.

when i have beryl on i get this messege when i run vlc from the terminal
[php]X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  82
  Current serial number in output stream:  83
[/php] 

But it so happens that when i switch my window manager to metacity it plays vidoes just find. btw when i have beryl on the only way for me to see play videos is with mplayer by putting this codec X11( XImage/shm )to make it able to go full screen i had to add this to my Mplayer-config: zoom=yes in the end i found wierd how my Mplayer-config looks all thought im a newby in the linux comminty. this is how it looks after adding the line in the bottom: 
[php]
# Write your default config options here!

zoom=yes
[/php]
 
Any help at with this problem i would gladly apreciate thanks

---

### Post by Gremlinzzz on 2007-06-26
This is in the guide
 How do I fix black windows during video playback

It is a known bug and there is a workaround by changing the video output device on your video player.

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

    * RealPlayer
          o Start RealPlayer
          o Click Tools, then Preferences.
          o Select the Hardware tab.
          o Deselect "Use XVideo"
          o Click on Apply, then OK.
          o Restart RealPlayer. 
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by nike984 on 2007-06-26
> **Gremlinzzz said:**
> This is in the guide
 How do I fix black windows during video playback

It is a known bug and there is a workaround by changing the video output device on your video player.

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

    * RealPlayer
          o Start RealPlayer
          o Click Tools, then Preferences.
          o Select the Hardware tab.
          o Deselect "Use XVideo"
          o Click on Apply, then OK.
          o Restart RealPlayer. 
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

This will be quick fix,
but the video quality will be degraded.
I heard that x11 image is something like image slide show.

---

