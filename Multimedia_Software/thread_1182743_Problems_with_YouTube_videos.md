---
title: "Problems with YouTube videos"
date: 2009-06-09
forum: Multimedia Software
---

### Post by AE000 on 2009-06-09
When I tried to view a YouTube video a window asked me to install a MPEG-4 AAC decoder, after searching it came up with a file named gstreamer0.10-plugins-bad. I did not install it because under its description it says that these decoders "are not up to par compared to the rest". After closing those windows the video played but with no sound.

Trying to solve this I added the Medibuntu repositories following the instructions on this site:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Now when I open Youtube I still don't get no audio and the video is black.

Any advise on how to solve this?

Should I install the w32codecs as described in the above webpage?

Thanks,

Alex.

---

### Post by AE000 on 2009-06-10
I've installed the s32codecs but still can't hear any audio, it still looks for a MPEG-4 AAC codec and brings the one I mentioned before.

Any advise?

Thanks!

Alex.

---

### Post by markbuntu on 2009-06-11
The gstreamer-plugins-bad got that name because the way the code is written is very sloppy, but they do work and will cause you no trouble if you use them.

---

