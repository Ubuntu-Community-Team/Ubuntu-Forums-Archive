---
title: "oops - mistaken symbolic link /dev/video"
date: 2006-10-09
forum: Multimedia &amp; Video
---

### Post by gontofe on 2006-10-09
Oops,

I was trying to get my webcam to work, as it was detected by the system, but for some reason camorama et al didn't think there was a video device there.

Following some instructions I found somewhere, I created a symbolic link as below:

ln -s /dev/video1 /dev/video0

But that was a mistake, now in camorama I get a window of whatever's on my pc screen instead of the webcam, how do I fix this?

---

### Post by gandalf2041 on 2006-10-09
Can't you just delete the symbolic link you created?

---

### Post by gontofe on 2006-10-10
oh, I spoke too soon, I did try doing that, thought it didn't work, tried doing ctrl alt backspace to restart x, didn't work...

However, the full restart seems to have done the trick.

---

