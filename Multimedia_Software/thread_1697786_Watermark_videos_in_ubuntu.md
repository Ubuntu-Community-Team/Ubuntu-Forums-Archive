---
title: "Watermark videos in ubuntu"
date: 2011-03-01
forum: Multimedia Software
---

### Post by ltoso on 2011-03-01
Hi,
is there a program or some command line utility or a video editor using which i can watermark videos in ubuntu with my logo or site name in text.

please recommend

---

### Post by inobe on 2011-03-01
try openshot, see how that works for you.

[http://www.openshot.org/features/](http://www.openshot.org/features/)

---

### Post by FakeOutdoorsman on 2011-03-01
> **ltoso said:**
> Hi,
is there a program or some command line utility or a video editor using which i can watermark videos in ubuntu with my logo or site name in text.

please recommend

You can do this with FFmpeg, but you will have to compile it because the version from the repository is too old and does not come with the filters that you will need. Compiling is easy with these instructions:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

Now for an example command. You didn't mention what output format you would prefer so I'll give you a very basic command. Logo on bottom left:
```
ffmpeg -i input -vf "movie=logo.png [logo]; [in][logo] overlay=10:main_h-overlay_h-10 [out]" output
```

Logo on bottom right:
```
ffmpeg -i input -vf "movie=logo.png [logo]; [in][logo] overlay=main_w-overlay_w-10:main_h-overlay_h-10 [out]" output
```

*man ffmpeg* has more information on filters. If the logo does not look correct then try using RGB instead of indexed PNG.

FFmpeg can also render text with the **drawtext** filter. Before compiling you'll need to install **libfreetype6-dev** and then add *--enable-libfreetype* to your FFmpeg *./configure*. Again, see *man ffmpeg* for more info on that filter. I've never tried this filter myself.

---

