---
title: "h264 Video Cam conversion issues"
date: 2020-04-02
forum: Multimedia Software
---

### Post by Geoff_Lane on 2020-04-02
Folks,

A friend sent me a video file from a bird box video cam, I seem unable to view the video for some reason.

The file type is Binary (application/octet-stream) and the extension is h264

If I run ffmpeg on the file I get loads of error messages with some of output shown below;

```
Consider increasing the value for the 'analyzeduration' and 'probesize' options
Input #0, h264, from '192.168.1.87_1_2020323181445.h264':
  Duration: N/A, bitrate: N/A
    Stream #0:0: Video: h264, none, 25 fps, 25 tbr, 1200k tbn, 50 tbc
```

I have no idea what analyzeduration or probesize is or means.

Strangely, I tried a conversion using VLC, that was successful just once only, called my friend to talk him through how to do it, VLC always fails to convert now.

The one and only time VLC managed a conversion a text box requesting 'UserName and Password' came up, I knew these so entered details and conversion started, subsequent attempts have never shown the UserName and Password box.

Geoff

---

### Post by TheFu on 2020-04-02
Proprietary video files suck.  hope your box didn't get hacked over a video.

---

### Post by Geoff_Lane on 2020-06-19
> **TheFu said:**
> Proprietary video files suck.  hope your box didn't get hacked over a video.

Nothing hacked, nothing went out to internet, all internal.

Geoff

---

