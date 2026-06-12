---
title: "Trying To Watch Music Vids. And Movies"
date: 2007-07-28
forum: Multimedia &amp; Video
---

### Post by amyfan on 2007-07-28
ok heres the prob. i have ubuntu OS i got movie player vlc player.
when i load a video it loads yes but it shows no pic unless i move the box its playing in around for a little then sometimes i can get a pic to show but you can hear it playing and the sound in vlc is a little choppy i have been messing with it but cant fix it any so i use movie player but i still have the same prob. but without the sound being choppy just the pic fades to a black screen. i iclosed a screen shot of the player and how it does.
and like i said while ago now if i move it around i can get it to show clear any help tips ideas would be very welcomed thanks all

---

### Post by AdrianOfTyriel on 2007-07-28
I´ve got the same thing! Funny thing is that it works fine in Windows... I have an Intel Graphics proc.

---

### Post by Gremlinzzz on 2007-07-28
What to do if Video players crash while using Beryl

see bug 96226 Currently you will need to change video driver from xv to x11 in ~/.mplayer/config and gstreamer-properties
[edit]
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

    *

---

### Post by amyfan on 2007-07-29
hey Gremlinzzz  thanks for the advice i done what u said and it works great thanks for the info the vids r now like if i was using xp i appreciate ur time and the trouble u went through to help me again thanks /salutes and bows down to the master Gremlinzzz:)

---

