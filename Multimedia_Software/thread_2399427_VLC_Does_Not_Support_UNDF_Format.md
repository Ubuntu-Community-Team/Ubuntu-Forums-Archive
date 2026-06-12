---
title: "VLC Does Not Support UNDF Format"
date: 2018-08-25
forum: Multimedia Software
---

### Post by jobehead on 2018-08-25
I have recorded many videos but when I tried to play them in VLC media player it shows an error VLC does not support UNDF format. I don't know what is it but I want it to be fixed at any cost. I have googled it and tried to fix it on my own but none of the solutions i tried worked. Please help to solve this issue ASAP.

---

### Post by TheFu on 2018-08-25
Fixed at any cost? If you provide a sample to the VLC team and include $5K-$10K donation, I bet they'd look at it quickly.
You might try mpv and mplayer to see if they recognize the files. Never know.  There are hundreds of odd video formats out there.

[https://ubuntuforums.org/showthread.php?t=2274618](https://ubuntuforums.org/showthread.php?t=2274618)

UNDF probably means "Undefined" ... which means the videos are corrupted or were created by a proprietary device.  Some IP webcams only produce output that works with their proprietary software, which only runs on Windows.

Or your vlc version is old and needs to be updated. Some commonly used video-codecs today weren't available in 2012, for example.

How did you record them?  Be specific about the hardware, software and how transfers were done.

Welcome to the forums.

---

### Post by Yellow Pasque on 2018-08-25
Please run mediainfo on one of them to see what we're dealing with:
```
sudo apt-get install mediainfo
mediainfo filename
```

---

### Post by alexbach420 on 2018-10-30
> **TheFu said:**
> Fixed at any cost? If you provide a sample to the VLC team and include $5K-$10K donation, I bet they'd look at it quickly.
You might try mpv and mplayer to see if they recognize the files. Never know.  There are hundreds of odd video formats out there.

[https://ubuntuforums.org/showthread.php?t=2274618](https://ubuntuforums.org/showthread.php?t=2274618)

UNDF probably means "Undefined" ... which means the videos are corrupted or were created by a proprietary device.  Some IP webcams only produce output that works with their proprietary software, which only runs on Windows.

Or your vlc version is old and needs to be updated. Some commonly used video-codecs today weren't available in 2012, for example.

How did you record them?  Be specific about the hardware, software and how transfers were done.

Welcome to the forums.

Personally, I would recommend you to try this. If that doesn't work, then maybe take the help from these external links - 

[URL="https://validedge.com/vlc-doesn-not-support-undf-format/"]https://validedge.com/vlc-doesn-not-support-undf-format/
[/URL][COLOR=#000000][FONT=Roboto]
[/FONT][/COLOR][URL="https://www.quora.com/I-have-come-across-a-video-file-thats-on-a-undf-format-How-can-I-run-that-file-on-VLC-or-any-other-media-player"]https://www.quora.com/I-have-come-across-a-video-file-thats-on-a-undf-format-How-can-I-run-that-file-on-VLC-or-any-other-media-player
[/URL]
This is a pretty common error so you'd be able to fix it easily.

---

### Post by slickymaster on 2018-10-30
Thread moved to **Multimedia Software** for a better fit

---

