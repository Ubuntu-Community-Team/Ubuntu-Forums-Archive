---
title: "Desktop Effects + Videos = Totem &amp; MPLayer crash"
date: 2007-06-26
forum: Multimedia &amp; Video
---

### Post by Prosis on 2007-06-26
Hello

I just got a new compter and installed Feisty.  Videos and DVD worked fine in both MPlayer and Totem.  But I wasn't able to activate the desktop effects.  So I installed the right drivers for my graphic card and then I was able to activate the Desktop effects.  But when they're activated, I can't read any video.  Both MPlayer and totem crash whether in Firefox or not.  

So I tried running an MP3 with Totem in text mode and got this error:

```
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 122 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

I tried to deactivate the desktop effects and could read videos again.  

Is there a way I can have both?

Thank you

---

### Post by Gremlinzzz on 2007-06-26
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
          o Video playback problems (black) after installing Beryl (or Compiz)/February 23rd, 2007
          o Re: Movies minus blue background/May 3rd, 2007 

from the guide 
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by Prosis on 2007-06-27
Thank you but that did not work.  I do not have Beryl installed though.

---

### Post by Prosis on 2007-06-27
No one knows?

---

### Post by nandasunu on 2007-06-27
I have the same problem and this solution worked great for me (I am running compiz-fusion, not compiz through desktop effects though).

Thanks a lot :D

---

### Post by jb3nny on 2007-06-27
this should be a sticky .. Thanks Very Much!!! :popcorn:

---

### Post by jasbur on 2007-07-25
I second that. That's been bugging me forever.

---

