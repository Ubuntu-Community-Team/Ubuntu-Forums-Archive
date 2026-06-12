---
title: "Video files play as blue screen"
date: 2007-08-13
forum: Multimedia &amp; Video
---

### Post by Halifax on 2007-08-13
Okay, so I found a way to fix this in Xine, but I don't really like Xine. I want to figure out how to fix this globally!

If I play a video file (pretty much any file, any program) it plays as a blue screen with sound. If I open another file up in another window, that one plays perfectly. I already know it's not a codec problem, since the files will work, just only if another is open already.

I found a post saying how to fix it in Xine - enable "Master of the known universe" experience level, and then change ... well, I think it was the decoder, but I changed it to XHSA or something like that. I'd know for sure, but I can't check since XINE WON'T LOAD PROPERLY ANYMORE. That's why I don't really like it much.

Anyway, I'd like to figure out how to fix this on every media player. How can I change global video options like that?

---

### Post by haralf on 2007-10-26
Hallo Halifax,

I had the same problem.
sudo dpkg-reconfigure xserver-xorg

was my solution. Eventually reinstall xorg completely.

Regards,

  Haralf

---

### Post by williammanda on 2007-10-26
Please be more specific about what you did during the reconfig of the Xorg file. Was there anything different during the reconfigure? Or was there something that was to be changed that would fix this issue?
Thanks

---

