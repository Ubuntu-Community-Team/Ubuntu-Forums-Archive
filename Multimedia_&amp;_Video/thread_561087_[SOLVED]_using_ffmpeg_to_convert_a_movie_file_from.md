---
title: "[SOLVED] using ffmpeg to convert a movie file from .avi to .mov (quicktime)"
date: 2007-09-27
forum: Multimedia &amp; Video
---

### Post by berliita on 2007-09-27
Why can't i convert an .avi movie file to the .mov (quicktime) format with ffmpeg? I tried the following command:
<code>
$ ffmpeg -i input.avi output.mov
</code>

My shell reciprocated with the following error message:
<code>
Unsupported codec for output stream #0.1
</code>

Where can i get the required codec? I've already got the gstreamer0.10-ffmpeg, the libquicktime and the w32codecs packages installed.

---

### Post by berliita on 2007-09-27
I've found the answer in some other posting in this very forum, namely: [http://ubuntuforums.org/showthread.php?t=395695](http://ubuntuforums.org/showthread.php?t=395695)

To reiterate, use the "target" option, as follows:
<code>
$ ffmpeg -i input.avi -target X-dvd output.mov
</code>
where X stands for one of "ntsc" or "pal" (both work for me).

---

