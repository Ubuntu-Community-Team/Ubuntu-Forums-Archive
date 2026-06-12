---
title: "Installed DVD Playback support and now video lags"
date: 2007-08-24
forum: Multimedia &amp; Video
---

### Post by AngryGnome on 2007-08-24
Hello... I just installed DVD Playback support on Feisty and now all video lags when it is full screened.  Not just DVDs, but other video as well.  The computer I'm running Ubuntu on isn't the best when it comes to graphics but I've never had a problem watching videos before.  I don't even have a graphics card... it's just Intel Integrated (crappy, I know).  Any ideas on how to solve this problem?  Any help would be appreciated.

Thanks.

---

### Post by AngryGnome on 2007-08-24
Sorry to bump the post... but I really need some help with this... I'm still not able to figure out why the video is lagging now when it didn't before.

Thanks again.

---

### Post by RomeReactor on 2007-08-24
Hi. Which version of Ubuntu do you have? What method did you use to enable DVD playback? Do you have Desktop Effects (Compiz, Beryl, Compiz Fusion) running when this happens? Which video player are you using? Please post the specifications of your system--specific video card model, RAM, processor.

---

### Post by AngryGnome on 2007-08-25
> **RomeReactor said:**
> Hi. Which version of Ubuntu do you have? What method did you use to enable DVD playback? Do you have Desktop Effects (Compiz, Beryl, Compiz Fusion) running when this happens? Which video player are you using? Please post the specifications of your system--specific video card model, RAM, processor.

Feisty, I used the method described in this thread: [http://ubuntuforums.org/showthread.php?t=532677&highlight=DVD+Playback](http://ubuntuforums.org/showthread.php?t=532677&highlight=DVD+Playback) , I don't use Desktop Effects, it doesn't matter which video player I use... I've tried VLC and Totem and the lag happens in both, I don't use a video card... I just have Intel Integrated graphics, 768MB of RAM and an Intel Celeron D processor.  Yes, I know Intel Integrated graphics and Intel Celeron processors suck... but I've never had a problem with playing video until now.

Thank you again. :-)

---

### Post by Gremlinzzz on 2007-08-25
You could try this from the guide
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_DVD_playback_capability](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_DVD_playback_capability)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by RomeReactor on 2007-08-25
If you changed totem from gstreamer to xine, as suggested in the thread you mentioned, make sure you also have the rest of the xine codecs:
```
sudo apt-get install libdvdnav4 libdvdplay0 libdvdread3 libdvdcss2 libxine1 libxine1-ffmpeg libxine-extracodecs
```
If you still use totem-gstreamer, make sure these codecs are installled:
```
sudo apt-get install libdvdnav4 libdvdplay0 libdvdread3 libdvdcss2 gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
```

---

### Post by AngryGnome on 2007-08-25
> **RomeReactor said:**
> If you changed totem from gstreamer to xine, as suggested in the thread you mentioned, make sure you also have the rest of the xine codecs:
```
sudo apt-get install libdvdnav4 libdvdplay0 libdvdread3 libdvdcss2 libxine1 libxine1-ffmpeg libxine-extracodecs
```
If you still use totem-gstreamer, make sure these codecs are installled:
```
sudo apt-get install libdvdnav4 libdvdplay0 libdvdread3 libdvdcss2 gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
```

I installed all of that (most of it was installed already).... and the video still lags when full screened.  Could it be a driver issue?

Thanks again for your help and patience... I'm no expert when it comes to video codecs/drivers and Linux.

---

### Post by RomeReactor on 2007-08-25
Did you change video drivers recently? that could be the cause, so you could try switching from the **intel** driver to the **i810** or viceversa. Or reconfigure Xorg:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and change the driver then.

This could also be related to [this bug in Xorg 7.2]("https://bugs.launchpad.net/ubuntu/+source/xcb/+bug/88815"); the problem *seems* to be fixed by downgrading **libx11-6** (currently at version 1.1.1-1) to version 1.0.3-4--[this comment by Martey Dodoo]("https://bugs.launchpad.net/ubuntu/+source/xcb/+bug/88815/comments/39") in the bug report contains links to the .deb packages. Others in the bug report suggest waiting for the new Intel driver that's on the way.

On a side note, have you tried launching the video players through the terminal and then opening a video, to see if you get a BadAlloc error? If you *do* get it, you could try Gremlinzzz suggestion, if you haven't already.

---

