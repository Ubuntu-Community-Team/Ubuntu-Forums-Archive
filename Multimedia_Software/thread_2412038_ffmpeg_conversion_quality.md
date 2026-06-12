---
title: "ffmpeg conversion quality"
date: 2019-02-07
forum: Multimedia Software
---

### Post by Geoff_Lane on 2019-02-07
Folks,

I hope someone can throw some light on this; I regularly use ffmpeg command line to reduce the size of GoPro videos, what works for me well is the following;

```
ffmpeg -i <input.mp4>  -vf scale=704x396 -b:v 2605555 <output.mp4>
```

This appears to look fine on screen, a 32" TV and YouTube.

I found a useful ffmpeg command line app for Android, looks quite impressive BUT conversion quality seems poor.

If I enter file into ffmpeg for info the video output shows the following;


[LIST]
[*]Video: h264 (Constrained Baseline) only if -c:v h264 used otherwise converted file is mpeg4 
[*]Video: mpeg4 (Simple Profile) Default seems to use this codec 
[/LIST]

Strangely, even though GoPro use h264 this android app will result in mpeg4, if I use c:v h264 then I do get that codec but [B]Constrained Baseline

[/B]I don't get any reference to **Constrained Baseline **when I convert on my Ubuntu 18:04Any suggestions how I can convert without getting Constrained Baseline?
Appeciate this isn't and Android forum but am asking about ffmpeg use which the Android app might be using invisibly.

Geffers

---

### Post by mc4man on 2019-02-09
If your android ffmpeg doesn't allow editing the command then try one that does.
A quick look at this one, it defaults to high profile level 3.0 for  mp4 encoding thru the supplied template. 
(- the template uses -q 5, that's not really used anymore, should  be edited to a -crf value like 28 or 24, whatever.. 
Named FFmpeg Media Encoder in the play store

constrained baseline is meant to be playable on basically any device, targets mobile devices of pretty much any sort..

---

### Post by Geoff_Lane on 2019-02-09
> **mc4man said:**
> If your android ffmpeg doesn't allow editing the command then try one that does.
A quick look at this one, it defaults to high profile level 3.0 for  mp4 encoding thru the supplied template. 
(- the template uses -q 5, that's not really used anymore, should  be edited to a -crf value like 28 or 24, whatever.. 
Named FFmpeg Media Encoder in the play store

constrained baseline is meant to be playable on basically any device, targets mobile devices of pretty much any sort..

Yes did read that Constrained Baseline does target mobile devices. The Android App seems to allow normal ffmpeg flags, -b:v for bitrate works, -vf scale=704x396 works, -preset seems to work. Just always end up with Constrained Baseline :confused:

Geffers

---

### Post by mc4man on 2019-02-09
as said, try a different app.
Here is screen of app I mentioned with an edited "Video MP4 (h264/aac)" template
screen 2 mediainfo of that encode

---

