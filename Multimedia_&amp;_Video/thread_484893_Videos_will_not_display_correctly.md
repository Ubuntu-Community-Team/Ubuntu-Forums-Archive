---
title: "Videos will not display correctly"
date: 2007-06-26
forum: Multimedia &amp; Video
---

### Post by Mr_Mischif on 2007-06-26
I have some AVIs that won't play in any video client I use, including VLC. However, when I play them on a windows box, they work fine. Something that may be of note is that when I try to play thee videos in VLC, the video track is disabled, while the audio track works fine; and when I try to play them in totem, it gives an internal data stream error. Can anyone help?

---

### Post by Depressed Man on 2007-06-26
For VLC, are you running Beryl or Compiz or Compiz Fusion? If so you may need to switch the video output mode to X11.


Gremlinzzz wrote in this thread [http://ubuntuforums.org/showthread.php?t=480357](http://ubuntuforums.org/showthread.php?t=480357)
----
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
---

Hope that helps!

---

### Post by nekoyokoshima on 2007-06-26
I've had a problem for some time with beryl and playing videos. I'm able to play windowed videos with any media player. However I'm unable to switch to full screen.

I was able to solve this issue by turning of the *Blur effects* from *Visual Effects*. I've come across a post in these forums that tell you to disable all effects. However I've pinned it down to *Blur Effects*

Hope this helps in some way any future users. 

I will try to investigate further down to get what is frigging the full screen overlay up

---

### Post by Mr_Mischif on 2007-06-27
> **Depressed Man said:**
> For VLC, are you running Beryl or Compiz or Compiz Fusion? If so you may need to switch the video output mode to X11.


Gremlinzzz wrote in this thread [http://ubuntuforums.org/showthread.php?t=480357](http://ubuntuforums.org/showthread.php?t=480357)
----
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
---

Hope that helps!

I tried it, but it didn't help; also, I'm only running the default skin, and this problem doesn't affect all my videos, only specific ones for no reason I can think of.

---

### Post by nekoyokoshima on 2007-07-02
Have You tried disabling blur effects as I told you in a previous reply? It worked for me

---

### Post by Mr_Mischif on 2007-07-02
> **nekoyokoshima said:**
> Have You tried disabling blur effects as I told you in a previous reply? It worked for me

How do I get to it?

---

### Post by Depressed Man on 2007-07-08
If you are using Beryl it should be under the system tools > beryl settings manager. I think typing in beryl-settings in the terminal also brings it up. 

Then there should be an option for blur somewhere.. visual effects > blur.

---

### Post by Maupertus on 2008-02-15
Hey everyone,

this is the only post that describes my problem exactly.
I didn't install anything new or exotic, so maybe it's because of an upgrade, but 3 days ago I could play avi and mp4, but now I can't. I reinstalled the restricted format codecs in medibuntu, but nothing works.

Does anybody know what the problem can be?

---

