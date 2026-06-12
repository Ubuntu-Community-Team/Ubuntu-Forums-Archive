---
title: "create video from jpeg files...maintain aspect ratio of jpeg"
date: 2010-04-05
forum: Multimedia Software
---

### Post by zuehls on 2010-04-05
I am using the following command to create a video of a bunch of jpeg files.  The problem is that some of the jpegs are portrait and others are landscape.  Ffmpeg is stretching the portrait images.  Is it possible to maintain aspect ratio of the jpegs... perhaps put black bars on the portrait images using ffmpeg?

ffmpeg -r .75 -f image2 -i Image%d.jpg output.mp4

---

### Post by loell on 2010-04-05
I think there's a **-aspect** parameter in ffmpeg.

ie

```
-aspect 4:3
```

probably try it.

---

### Post by zuehls on 2010-04-08
I decided to use imagemagick to fix my problem

---

### Post by no2498 on 2010-04-08
do not see that helping
all the pics must be in the same mode portrait or landscape
1 of the 2 but not both at the same time

1 is say 640x480 the other is 480x640
        wide&fat             thin&wide
best way i can say what it is

---

