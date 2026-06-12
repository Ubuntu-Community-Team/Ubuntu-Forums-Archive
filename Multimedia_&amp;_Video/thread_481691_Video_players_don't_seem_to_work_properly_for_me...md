---
title: "Video players don't seem to work properly for me..."
date: 2007-06-22
forum: Multimedia &amp; Video
---

### Post by Kadou on 2007-06-22
It seems that every video player that I have either has some sort of recurring problem or just doesn't work at all. There's a big group of problems that I have:

VLC - I was using this as a standard video player for a while now because it was the only one that actually played videos. Lately, however, it seems that everytime I go to load a video it would start the video itself, but VLC will freeze and no sound would play. A restart of the computer fixed this once, but it's now doing the same thing again. It hasn't done this until just yesterday, so I'm not sure what it is.

MPlayer - This one didn't even load videos before. It gave me an error about video output, so I ended up changing the output to x11 as some people here said. Now, anytime I go to open a video, it freezes on me like VLC except that I have to kill it through the Performance Manager. Likewise, KMPlayer doesn't work and SMPlayer just gives me a black screen whenever I try to play a video (it doesn't freeze, though).

If it helps any, I'm running Kubuntu Feisty Fawn. I've also tried reinstalling each program, yet I always get the same result. Any help would be appreciated.

---

### Post by Gremlinzzz on 2007-06-22
Dont know if this is your problem
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
odds are you have w32 codecs but if not 
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)

---

### Post by Kadou on 2007-06-23
I've tried the methods for VLC and MPlayer before with that, and they still don't work. VLC loads the video without sound and freezes, and MPlayer freezes with the black screen.

---

### Post by benab on 2007-11-20
This worked for me too!  Every now and then the video for a movie would show up as pink and scrambled.  I would have to restart X in order to make the codecs work again.  By following these directions all is well.
Thanks!

---

### Post by axelsvag on 2007-11-25
> **Gremlinzzz said:**
> Dont know if this is your problem
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
odds are you have w32 codecs but if not 
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)

Thank you very much. Everything works fine when I use the desktop now. The only problem is xine where I can´t find "Click File, then Configure and then Preferences" I can´t find any menu which is called file. The next thing is to get mythtv to accept the same change in the Internal player.

---

### Post by jonno on 2007-11-27
> **Gremlinzzz said:**
> Dont know if this is your problem
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
odds are you have w32 codecs but if not 
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)

Ok so I have been getting a weird blue grid of dots on most of my video playback.
I tried the instructions above and here is what I get:
gstreamer-properties: when video plugin is set to auto, I run the test and still get the grid; when set to "X Window System (No Xv)" grid is gone, when set to "X Window System (X11/xshm/Xv)" the grid is back.

Next I tried vlc. Instructions worked great.

Got Xine fixed also although gxine is still broken.

However I just installed the new 2.0 Skype beta in order to use the video calling via my Logitech Quickcam and of course the video has the grid!!! Does anyone know how to change the video driver the webcam is using? Can I just wipe the offending driver so that it always defaults to something that works?

---

### Post by arrizaba on 2007-11-27
> **Kadou said:**
> I've tried the methods for VLC and MPlayer before with that, and they still don't work. VLC loads the video without sound and freezes, and MPlayer freezes with the black screen.

I get the same problem. I have realize that Amarok and other sound players also cause the same freeze, so I believe that ANY program that tries to output sound just crashes/freezes.

With VLC, setting the output to X11 I was able to see video, however without [COLOR="Red"]sound[/COLOR] and the GUI freezing.

---

