---
title: "Program to add watermark to videos?"
date: 2009-09-21
forum: Multimedia Software
---

### Post by jahgamer189x on 2009-09-21
Are there any programs that work in ubuntu that allow me to add a watermark to my videos.
(Other than avidemux)
Many Thanks

---

### Post by cor2y on 2009-09-21
Try Kdenlive [http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/ubuntu-packages](http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/ubuntu-packages) you will have to render out to a new video format though so read the tutorials on usage

---

### Post by jahgamer189x on 2009-09-23
Thanks!:) I got the watermark to work and it's a great program to edit videos.

However, rendering a 5 min video estimates at about 2 hours to complete! I have not set the output to be really high quality either. Do you know how to fix this? Or does it take that long?

---

### Post by cor2y on 2009-09-23
It shouldnt take that long.
You will have to either play around with the default rendering profiles (adjusting settings like resolution, bitrate etc) or create your own custom rendering profile, easy enough to do but you must have some knowledge of the synatax of ffmpeg nothing in depth there should be a video tutorial about creating custom rendering profiles available on the site and text based ones on the forums.

---

### Post by jahgamer189x on 2009-09-24
I have configured the settings and quality settings etc. but it still takes about 2 hours.
Just in case it helps, when I press help>about KDE; it says version 4.2.2.

---

### Post by cor2y on 2009-09-24
Which render profile are you using when you click the render button?
There are several from hdv , mpeg4, H.264 to flash  and ram video

---

### Post by jahgamer189x on 2009-09-24
I have tried Xvid4 (.avi) and HDV. Both render really slow.

---

### Post by cor2y on 2009-09-24
They shouldnt be taking that long.
What bitrate are you selecting and how many passes?
In general i use 1 pass and 1000k bitrate for most of the files i render out.
Depending on how long the clip is and the resolution selected for rendering.
A 1000k bitrate mpeg4 or xvid video file with mp3 128k audio and a resolution of 852x480 (480p widescreen standard) with transitions, normalized audio track and a runtime of about 8 mins takes about 5 mins to render out to mp4 format.

Edit 
Also i am not on a super computer, its an Athlon X2 5400 dual core with 3gb of ram.
Certainly not a top of the line rig.

---

### Post by jahgamer189x on 2009-09-24
That's a lot better! Only 13 minutes now for a video 5.3 minutes long. You have helped so much, thanks.

---

