---
title: "Video problems in Gutsy"
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by Light- on 2007-10-18
Hi,

I just installed Ubuntu 7.10. However, i would like dual screens to work with it. If I use the "Screens and Graphics" utility, all options are greyed out except the "Default Screen" radio button. I have a Radeon 9800 pro, using the open source ati driver (which Compiz works fine with). My screens are configured using the cards DualHead capabilities, so I have my main LCD attached to the DVI port and a secondary CRT attached to the vga port. These monitors are different sizes so they require different resolutions.

Can someone please help?

Also, when trying to play a video in Totem, the screen is black, even after installing the necessary gstreamer plugins to play the video (i was trying to play a h.264 encoded video)

Any ideas?

---

### Post by maep on 2007-10-19
hi, concerning your second question- 
i have the same problem. i suspect gstreamer uses XVideo as output. in other players like mplayer or vlc you can change the video output to X11 Video which worked for me. vlc seemed to perform better.

to change the gstreamer output module use these steps:

```
hit alt+F2
run gconf-editor
find this key /system/gstreamer/0.10/default/videosink
change value to to 'ximagesink'
```

or you just use the old windowmanager :), hope that helps

ps: i think that module has bad performance compared to xvideo, so htis should just be a workaround until a better driver comes along. maybe some gstreamer expert can shed some light on that matter.

---

