---
title: "Your GStreamer installation is missing a plug-in."
date: 2014-04-28
forum: Multimedia Software
---

### Post by dunkuk_gelay on 2014-04-28
Hi... It seems like both of my audio player got above issue when playing m4a files which is Apple lossless. Below are the error warning:

gmusicbrowser
Playing error : Your GStreamer installation is missing a plug-in. at /usr/bin/../share/gmusicbrowser/gmusicbrowser_gstreamer-0.10.pm line 137.

Clementine
Your GStreamer installation is missing a plug-in.

However I can play those files with VLC but I prefer to use VLC for video only and independant audio player. I did try some workaround or fix such as removing gstreamer-0.10 etc and remove or rename the registry.x86_64.bin but no success. And yep, I installed ubuntu restricted extras.

Ubuntu 14.04 x64
Inspiron-5437
Dual boot Windows 8.1

---

### Post by andrew.46 on 2014-04-29
I believe that the gstreamer-FFmpeg pluging is not available in the stock Ubuntu Repositories for 14.04 and perhaps this is your problem. Some discussion here with a suggested fix:

[http://www.webupd8.org/2014/04/10-things-to-do-after-installing-ubuntu.html](http://www.webupd8.org/2014/04/10-things-to-do-after-installing-ubuntu.html)

---

### Post by dunkuk_gelay on 2014-04-29
> **andrew.46 said:**
> I believe that the gstreamer-FFmpeg pluging is not available in the stock Ubuntu Repositories for 14.04 and perhaps this is your problem. Some discussion here with a suggested fix:

[http://www.webupd8.org/2014/04/10-things-to-do-after-installing-ubuntu.html](http://www.webupd8.org/2014/04/10-things-to-do-after-installing-ubuntu.html)

Oh my goodness. I was following the website tutorial regarding post install but how can I really miss that.:mad: Thank you very much for the guidance.

---

### Post by dunkuk_gelay on 2014-04-29
Ah, BTW post #2 solve the issue. Thank you.

---

### Post by andrew.46 on 2014-04-30
Good to hear that the issue is resolved :)

---

### Post by scott092707 on 2014-05-09
[https://launchpad.net/ubuntu/trusty/i386/gstreamer0.10-ffmpeg](https://launchpad.net/ubuntu/trusty/i386/gstreamer0.10-ffmpeg)

reports that "
[LIST]
[*]       Removal requested       on 2014-01-20. 
[*]       Deleted       on 2014-01-20       by [Matthias Klose]("https://launchpad.net/%7Edoko")       lp #1253071, Remove completely gstreamer0.10-ffmpeg src+binaries, **superseded by gstreamer1.0-libav** 
[/LIST]
"
I see that in my [Lubuntu] repositories, gstreamer1.0-libav is available, but not installed.

Has anyone tried this as a possible solution? - it would logically be a better one (if it works) than using the "add a ppa:",  since it is available without adding a ppa, and it is gstreamer 1.0, instead of the older 0.10.

I have already added the ppa and installed the 0.10-ffmpeg, and have no time to remove it, add the libav, and test it right now...

-Scott

---

### Post by Yellow Pasque on 2014-05-09
You can have 0.10-ffmpeg and 1.0-libav packages installed at the same.

In the case of gmusicbrowser, it still uses gstreamer0.10, so installing gstreamer1.0-libav will have no effect.

---

### Post by TBeholder on 2014-05-14
Yup, it's not even in plugins-bad.
I just switched backend on Audio tab. The advantage of "gstreamer" mode is being the only one where Equalizer is available. If you don't need it -
"mpg123/ogg123/..." - everything works except Replay Gain, but low bitrates are accelerated.
"mplayer" - everything works fine.

---

### Post by Yellow Pasque on 2014-05-14
> **TBeholder said:**
> Yup, it's not even in plugins-bad.

What is "it" in this case?

---

