---
title: "Handrake Resolution or Display settings"
date: 2020-07-02
forum: Multimedia Software
---

### Post by Geoff_Lane on 2020-07-02
Folks,

Used Handbrake to copy a DVD and all successful, I have used default settings but chose a format close to original.

I am baffled by some of Handbrake's readings;

Source 720x576 (1024x576)

Output size 704x576 storage,  1001x576 display 

Now I understand the first mentioned on each line is the resolution but not sure how the second numbers keep the aspect ratio.

No issues with conversion, just trying to understand what it all means.

Geoff

---

### Post by Yellow Pasque on 2020-07-02
It's because of the (auto)crop settings. Personally, I never let Handbrake crop, especially when it's just a few pixels on each side. I'd rather the resulting file be slightly bigger and make sure the aspect ratio is correct, then get rid of a few black border pixels.

---

### Post by SeijiSensei on 2020-07-02
The video might use [anamorphic widescreen](https://en.wikipedia.org/wiki/Anamorphic_widescreen#DVD_Video). DVDs in this mode have pixels that are wider than normal, enabling the DVD player to output an image in the 16:9 aspect ratio.

---

### Post by Yellow Pasque on 2020-07-02
^Yeah, if it's not cropped it should be:
Output size 720x576 storage, 1024x576 display

---

### Post by Geoff_Lane on 2020-10-30
Thanks folks, video editing is a fine art.  Amazing the amount of options.

Generally use ffmpeg for simple editing just to reduce file size but handbrake is good.

Geoff

---

### Post by Tadaen_Sylvermane on 2020-10-31
I find the default Video settings to be fine so far at 1300 movie rips. The only thing I do adjust is the RF slider to 20 from 22, and only because the default used to be 20. Gotta keep consistent!

---

### Post by TheFu on 2020-10-31
I find handbrake makes smaller video files, faster than my ffmpeg scripts.  It also makes dealing with multiple audio, SRT, SUB tracks easier. I'm fairly certain, ffmpeg can do everything that handbrake does, but my ffmpeg skills just aren't up to the level that a few tweaks in Handbrake solve, at least for me.

As for the different resolutions.  One is the display resolution and the other is the internal encoded resolution. If those don't match, some stretching needs to happen at playback time.  I tend to leave it as is on both when going from mpeg2 --> h.264.

For h.264, I use 19.5 for the quality setting. My goal is to avoid any artifacts, regardless of the video type (talking/action/space/sitcom).

---

### Post by Geoff_Lane on 2020-11-01
> **Tadaen_Sylvermane said:**
> I find the default Video settings to be fine so far at 1300 movie rips. The only thing I do adjust is the RF slider to 20 from 22, and only because the default used to be 20. Gotta keep consistent!

Indeed, whatever was suitable before should continue to be fine.

Geoff

---

