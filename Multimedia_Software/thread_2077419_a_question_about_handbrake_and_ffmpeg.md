---
title: "a question about handbrake and ffmpeg"
date: 2012-10-28
forum: Multimedia Software
---

### Post by shantiq on 2012-10-28
i do not have the repo ffmpeg installed i have instead  

ffmpeg
ffmpeg version N-35917-ge4fe4d0 Copyright (c) 2000-2012 the FFmpeg developers
  built on Sep 10 2012 11:04:03 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)



and my version of handbrake   through deb is here


[ATTACH]226278[/ATTACH]





now since having installed this version of ffmpeg handbrake does not pick up ffmpeg and only works with H-264    which takes a lot longer than ffmpeg


i do not see how to relink the 2 together   anyone knows?     thanx in advance:KS

---

### Post by ron999 on 2012-10-28
Hi
I think your version of HandBrake is a "static build".
If so, it can't link to your installed FFmpeg.
Look for this file:- /usr/share/doc/handbrake-cli/README.debian

---

### Post by shantiq on 2012-10-29
thanx Ron no biggie i do not use it that much but was intrigued


README.Debian yielded this


> handbrake for Debian
--------------------

HandBrake bundles its own copies of ffmpeg and related media libraries. This is
an upstream decision that the Ubuntu maintainers will respect.

This is done by running contrib/getcontrib.sh which wgets each library from
HandBrake's website.


Upstream has asked us to do this because they have modified their libraries to
address the finickiness of the platforms that they support, along with
prerelease patches that add support for advanced HandBrake functionality such as
surround-sound downmixing.

HandBrake then statically links against these libraries, and they are not
installed to the system so it doesn't interfere with other parts of the system.
Different or older versions of these packages are included in the Ubuntu
distribution already, and have passed our guidelines for Multiverse inclusion.




s o my next question obviously is   is there such a thing as non-static handbrake ?  :KS    compile it oneself?  or is the info from above applicable to all versions of Handbrake.  I do not understand all ins and outs here

---

### Post by JohnAStebbins on 2012-10-29
> **shantiq said:**
> now since having installed this version of ffmpeg handbrake does not pick up ffmpeg and only works with H-264    which takes a lot longer than ffmpeg


What does this mean exactly?  I understand the part about not picking up your version of ffmpeg.  The other poster is completely correct that handbrake statically links to *libav*.

But "only works with H-264 which takes a lot longer than ffmpeg" makes no sense whatsoever. HandBrake has a variety of encoders built in (H.264 x264, MPEG-4 ffmpeg, MPEG-2 ffmpeg, VP3 Theora).  And each encoder has a variety of settings that affect speed.  With proper settings, I can get 900fps when encoding standard definition video with x264 (i.e. a 2 hour movie in 4 minutes).  That's faster than any of the other encoders are capable of.

If you want "ffmpeg" encoding, just go to the encoder combo box on the video tab and select it.  There are 2 actually.  One for mpeg-4 part 2 (ASP) and one for mpeg-2.  They both use libav as the encoder (libav is a fork of ffmpeg).  But x264 is faster if you use the right settings.

See this post for help with x264 settings.
[https://forum.handbrake.fr/viewtopic.php?f=6&t=19819](https://forum.handbrake.fr/viewtopic.php?f=6&t=19819)

As far as "non-static" (dynamic) builds go.  There is one in the official repository for ubuntu 12.10.  But be warned that the ubuntu packagers have intentionally crippled it.
See [http://ubuntuforums.org/showthread.php?t=2076246&highlight=handbrake](http://ubuntuforums.org/showthread.php?t=2076246&highlight=handbrake)

---

### Post by shantiq on 2012-10-29
i am really sorry for wasting your time here

i had made a mistake in my line of code and it had returned  ```
encoder ffmpeg unknown
```


so i jumped the gun and thought it had got unlinked somehow


the line was 


> HandBrakeCLI -i ~/Videos/The_Goddess_of_Art_-_The_Goddess_of_Art_Marina_Abramovic.mkv -o ~/Desktop/Marina.mkv -e **ffmpeg2** -w 640 -l 320  -b 1200 -E ffac3  -B 72 -r 25



but i had entered ffmpeg  [COLOR="Red"]without the number 2 or 4[/COLOR]


my bad


again sorry [for my divine diviness]


one of the best and most stable programs ever.  does what it says on the tin time and time again

and John   thanx for all your great work making it available to us all    and thanx for info on H.264

---

