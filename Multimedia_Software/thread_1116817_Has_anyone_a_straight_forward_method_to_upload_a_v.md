---
title: "Has anyone a straight forward method to upload a video to YouTube in HD using Ubuntu?"
date: 2009-04-05
forum: Multimedia Software
---

### Post by Rytron on 2009-04-05
Hi. Has anyone a straight forward method to upload a video to YouTube in HD using Ubuntu? Thanks.

---

### Post by Rytron on 2009-04-07
**Got it!**

Record video of large area of the screen with gtk-recordMyDesktop
Convert from .ogv to .avi with this command: ```
mencoder out.ogv -o out.avi -oac mp3lame -ovc lavc
```
Open new .avi file in Avidemux (GTK+)
Auto > PSP (H.264) > Target Type: PSP full res (720*480) Source+Destination aspect ratios 1:1 > OK
Save

---

