---
title: "DC10+ card analog video capture"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by pecoronas on 2007-05-08
i have this old pinnacle dc10+ pci analog video capture card and trying to capture some video on ubuntu 7.04
i have installed mjpeg tools and xawtv and i can see the video to be captured on monitor (eg plugging in my tv via scart, or an analog videocam).
but on xawtv, when i try to record or to capture a single image, i get this error (if launched from command line):

```
no way to get: 384x288 24 bit TrueColor (BE: rgb)
```

and recording doesn't start. what am i doing wrong? 
and, question n.2, are there any other apps doing the same job as xawtv? (that is capturing analog video using mjpegtools?)

---

### Post by pecoronas on 2007-05-09
anyone? i really can't get out of it :(

---

### Post by pecoronas on 2007-05-12
this is the dmesg output:

```
[ 4334.243309] DC10plus[0]: VIDIOC_S_FMT - unknown/unsupported format 0x33424752 (RGB3)
[ 4334.243320] DC10plus[0]: v4l_set_format() - video buffer size (128 kB) is too small
[ 4334.243324] DC10plus[0]: VIDIOC_S_FMT - unknown/unsupported format 0x0 (    )
[ 4334.243328] DC10plus[0]: v4l_set_format() - video buffer size (128 kB) is too small
[ 4334.243332] DC10plus[0]: VIDIOC_S_FMT - unknown/unsupported format 0x50323234 (422P)
[ 4334.243336] DC10plus[0]: VIDIOC_S_FMT - unknown/unsupported format 0x32315559 (YU12)
[ 4334.243339] DC10plus[0]: VIDIOC_S_FMT - unknown/unsupported format 0x0 (    )
[ 4334.243342] DC10plus[0]: VIDIOC_S_FMT - unknown/unsupported format 0x0 (    )
```

any idea?

---

