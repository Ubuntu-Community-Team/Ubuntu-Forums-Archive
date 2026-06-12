---
title: "[SOLVED] Videos Do Not Play, Even With Codecs"
date: 2007-08-01
forum: Multimedia &amp; Video
---

### Post by ghindo on 2007-08-01
I've got Feisty Fawn running on a Dell Inspiron 1420 with an Intel X3100 graphics chip, and I can't play any movies.  I've got the appropriate codecs installed (gstreamer), but to no avail.  When I open them in Totem, the window just automatically closes.  When I open them in Xfmedia, nothing plays.

Help?

---

### Post by wolfen69 on 2007-08-01
have you tried vlc?

---

### Post by Malh on 2007-08-01
WTS VLC 0g System-Administration-Synaptics-VLC or 
[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

---

### Post by ghindo on 2007-08-01
Same thing happens with VLC.  I open the video, and VLC Player just immediately closes.

---

### Post by Malh on 2007-08-01
That's odd, VLC plays pretty much anything for me.  I can't think of a single instance where it has failed me.

---

### Post by ghindo on 2007-08-01
> **Malh said:**
> That's odd, VLC plays pretty much anything for me.  I can't think of a single instance where it has failed me.Ditto.  I'm stumped.  :(

---

### Post by bumbleskull on 2007-08-01
what is the container of the video? and do you know what codec it was encoded with?

---

### Post by ghindo on 2007-08-01
> **bumbleskull said:**
> what is the container of the video? and do you know what codec it was encoded with?I've tried playing multiple videos - .avi, .mkv, .mpg, .mov, .divx, .wmv - none of them work.

---

### Post by bumbleskull on 2007-08-01
o ok, I thought it was one video giving you problems. VLC should be able to decode mpeg and avi with no issues whatsoever.

I have no ideas on this then

---

### Post by ghindo on 2007-08-01
Bump.  Could this problem have something to do with the [new drivers I installed recently]("http://ubuntuforums.org/showthread.php?t=506744")?

---

### Post by modorf on 2007-08-01
run the video player for the xterm window.
This will allow error messages to be echoed to the term.

I was thinking that it could be related to your video card and drivers, not having XV support.

please post what `gxlinfo` gives you (reports opengl and video support)

---

### Post by ghindo on 2007-08-01
> **modorf said:**
> run the video player for the xterm window.
This will allow error messages to be echoed to the term.

I was thinking that it could be related to your video card and drivers, not having XV support.

please post what `gxlinfo` gives you (reports opengl and video support)How do I go about doing this?

---

### Post by ghindo on 2007-08-01
Bump.

---

### Post by Gremlinzzz on 2007-08-01
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

Sources

---

### Post by ghindo on 2007-08-01
Thank you so much!  The gstreamer solution did the trick!

---

### Post by DMXell on 2007-08-02
It fixed my problem too. Thank you so much!

---

### Post by jasmuz on 2007-12-25
Thanks.. solved my Openchrome video driver and VLC Xv extension problem.

---

### Post by AntoineL on 2008-03-13
Thanks I had the same problem (Totem ad VLC closing immediatly when trying to render a video) on my Toshiba U300-TP7 (Intel GM965 graphics), and your solution solved it.

---

### Post by milia on 2008-03-19
> **Gremlinzzz said:**
> How do I fix black windows during video playback

It is a known bug and there is a workaround by changing the video output device on your video player.

    * MPlayer (Mplayer is not installed by default)
          o Start Mplayer
          o Right-click on the screen and select Preferences
          o Select the Video tab and under Available Drivers select "X11 (XImage/Shm)"
          o Click Save and restart the program for the setting to take effect.
                + Some users reported that MPlayer may not be able to show videos in full screen. 



Thanx !!!!

I have a workable mplayer now :)).

---

### Post by txtinman on 2008-03-22
This didn't help my problem with avi files. I hacve a video camera that creates avi movies. VLC can play the audio but not the video. Totem says that sedg codecs are not handled. How can I get Linux to play these files? Can it be done?  Avidemux, which also does not play the video, has this to say about the file:

---

