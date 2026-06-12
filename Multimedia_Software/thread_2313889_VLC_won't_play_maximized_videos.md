---
title: "VLC won't play maximized videos"
date: 2016-02-16
forum: Multimedia Software
---

### Post by corbin.loftis on 2016-02-16
I am having trouble playing flv, mpg and some other files in VLC. Whenever I open an FLV file, for example, and attempt to maximize it, the window maximizes, but the video just kind of floats in the middle of the screen, and windows can pass behind the video and in front of the VLC window (between them). I have installed ubuntu-restricted-extras, and have reinstalled VLC, but it has not changed. Does anyone have any ideas?

---

### Post by SeijiSensei on 2016-02-16
Try [SMPlayer](http://smplayer.sourceforge.net).  It's in the repositories.

---

### Post by corbin.loftis on 2016-02-17
It seems it also does it in SMPlayer. The video is detached from the player, and when I click on Firefox, the video will stay at the front (hovering over firefox), but the rest of the player will disappear.

---

### Post by corbin.loftis on 2016-02-17
Here is a screenshot. The video is within the black square (though it won't show up on the screenshot for some reason). I is maximized, but the video stays the same size as it was when it was small...

[http://i.imgur.com/O7Xoxys.png](http://i.imgur.com/O7Xoxys.png)

---

### Post by mc4man on 2016-02-17
Sounds more like a video output or video driver problem.  If you know your hardware specs post along with whatever release of Ubuntu you're using.

For vlc you could try changing 2 settings, assuming they are available for the version you have.
Here on 14.04 it would be - 
 Open vlc >  Input/Codecs tab > 'Hardware-accelerated ..' & if on Automatic change to Disabled (scr. 1
Also in  Tools > Preferences. Under the video tab change 'Output'  to XVideo (scr. 2). Give that a try. If no good then go back &  try X11

If you vlc looks different then post info about hardware & which Ubuntu
(- ```
sudo apt install inxi
```

```
inxi -b
```

---

### Post by corbin.loftis on 2016-02-17
I disabled the automatic hardware-accelerated encoding and enabled X11 under video output and it seems to be working correctly! Thank you! Is there a way to make the change to X11 system-wide, as other players still seem to have the same difficulty.

---

### Post by mc4man on 2016-02-17
> **corbin.loftis said:**
> I disabled the automatic hardware-accelerated encoding and enabled X11 under video output and it seems to be working correctly! Thank you! Is there a way to make the change to X11 system-wide, as other players still seem to have the same difficulty.
Probably not, you'll have to do individually & may find some hard if not impossible to switch to X11 like totem (impossible?), & parole (command line setting
(gstreamer0.10 had gstreamer-properties, gstreamer1.0 doesn't have anything like that. Only older hardware would need to use X11 so I guess gstreamer assumes either the app can set or too bad.

---

