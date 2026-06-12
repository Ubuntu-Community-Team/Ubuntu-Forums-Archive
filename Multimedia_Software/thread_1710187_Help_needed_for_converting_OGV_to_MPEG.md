---
title: "Help needed for converting OGV to MPEG"
date: 2011-03-19
forum: Multimedia Software
---

### Post by user333 on 2011-03-19
I have just captured some screen-shots with GTK-RecordMyDesktop, but now I can't use them. The videos plays right in vlc and totem, but crashs Pitivi and turn into pink splotches in kdenlive. When I convert them using ffmpeg, the video turns into blue and pink splotches. Here is how I'm converting it:

```

ffmpeg -i out.ogv out2.mpg

```

Converting it with vlc crashes the program.

I never had problems like this before. I have used recordmydesktop and ffmpeg many times, but on a 32bit computer. I have a 64 pc now, running ubuntu 10.04 x64.

---

### Post by MartyBuntu on 2011-03-19
Had the same problem as you two days ago.

**OpenShot** did my conversions perfectly.

Strangely, even AviDemux (my go-to application) couldn't do what OpenShot did.

---

### Post by user333 on 2011-03-19
I tried openshot... Still the same problem.

---

### Post by MartyBuntu on 2011-03-19
What format did you try converting to in OpenShot?

---

### Post by user333 on 2011-03-19
I didn't try to convert it, because it plays it back pink and blue.

---

### Post by MartyBuntu on 2011-03-19
> **user333 said:**
> I didn't try to convert it, because it plays it back pink and blue.


Don't worry about the preview for now. Just convert...see if the result works.


I converted my captured .ogv to .mpeg 

Worked great with OpenShot and even was able to then upload to YouTube.

---

### Post by FakeOutdoorsman on 2011-03-19
You will need to compile a newer version of FFmpeg if you want to convert videos from recordMyDesktop. If I remember correctly 10.04's FFmpeg is too old to deal with these. If you can copy and paste then you can compile. See this:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

Example command:
```
ffmpeg -i out.ogv -qscale 2 -ab 128k out2.mpg
```
Increase the *qscale* value if you want a lower quality output. Decreasing the quality will decrease output file size.

---

### Post by user333 on 2011-03-19
I'm following the instructions now... I'll see if that works. Weird thing is, though, it removed some of my video editors.

---

### Post by user333 on 2011-03-19
Thank you!!! My video works fine now! I just needed to use the latest version.

---

