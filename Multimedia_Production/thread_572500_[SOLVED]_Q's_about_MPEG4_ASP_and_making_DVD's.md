---
title: "[SOLVED] Q's about MPEG4 ASP and making DVD's"
date: 2007-10-10
forum: Multimedia Production
---

### Post by PsycoGeek on 2007-10-10
I'm thinking of getting [this camcorder from Samsung]("http://www.samsung.com/us/consumer/detail/detail.do?group=camerascamcorders&type=camcorders&subtype=digitalmemory&model_cd=SC-MX10A/XAA").  It uses  MPEG4 ASP to record video.  My questions are:

1.  Does anyone have this camcorder and are you editing the video/making DVD's from it on Ubuntu?

2.  How difficult will it be to produce a DVD from the video that will play in just about any DVD player?

3.  If it will be difficult to convert/edit the video for DVD production, can you recommend a camcorder that will make the experience easier?

---

### Post by theacoustician on 2007-10-11
Recording to MPEG4 to transcode to MPEG2 isn't hard, but you'll lose a lot of quality.  Editing would also be problematic, as there really isn't anything out there that does a great job at editing compressed formats.  Kino is only good for DV, Cinerella is just a pain to use, and just about anything else is extremely simplistic (cut and paste only).

If you're really serious about video editing, find a camera that records to DV or HDV.

---

### Post by eye208 on 2007-10-12
If the camera connects to the PC as a standard USB mass storage device (i.e. no special driver required), it will give you less trouble than some DV cameras.

Conversion from MPEG-4/ASP to any other format can be done using MEncoder or FFMPEG. Editing requires a keyframe-only stream format such as MJPEG. I recommend Blender for editing since it is both stable and feature-rich.

---

### Post by PsycoGeek on 2007-10-12
Well, I found a big problem with this camcorder... it uses a proprietary format and there is no codec for decoding it on Ubuntu.  The only thing I was able to find on it was about 3 years old, and you had to use a hex-editor to replace information in the file headers, and then mabe it would work.

I'm looking into one of the Sony DVD camcorders, the [DCR-DVD408]("http://www.sonystyle.com/webapp/wcs/stores/servlet/ProductDisplay?catalogId=10551&storeId=10151&langId=-1&productId=11039253") to be exact.  It is rated at 1.5lux without using the night shot mode, and can use rewritable media.  I would really like to get one of the hard drive camcorders like the [DCR-SR200C]("http://www.sonystyle.com/webapp/wcs/stores/servlet/ProductDisplay?catalogId=10551&storeId=10151&langId=-1&productId=8198552921665087709"), which also has a 1.5lux rating without night shot mode, but it is a bit price prohibitive for me.

BTW, marking this as "solved" because the Samsung camera will not work with Ubuntu.

---

### Post by eye208 on 2007-10-15
> **PsycoGeek said:**
> Well, I found a big problem with this camcorder... it uses a proprietary format and there is no codec for decoding it on Ubuntu.  The only thing I was able to find on it was about 3 years old, and you had to use a hex-editor to replace information in the file headers, and then mabe it would work.
Here's what I found out:

According to [this forum thread](http://www.stevesforums.com/forums/view_topic.php?id=578751&forum_id=26) the Samsung SC-MX10 captures into AVI files with the four-character code (FourCC) "SEDG". According to [this thread](http://www.moviecodec.com/topics/8929p1.html) the SEDG codec is really just MPEG-4/ASP (DivX, Xvid). This is also what the Samsung website says in its description of the camera's features.

You don't need a hex editor to change the FourCC of an AVI video. This command will do the same thing:

mencoder input.avi -ovc copy -oac copy -ffourcc DX50 -o output.avi

"DX50" is the FourCC of DivX 5.0 video. Note that this command makes mencoder work in stream copy mode, i.e. video and audio data will not be affected by this conversion. There's no loss of quality.

---

### Post by jimdrewes on 2007-12-29
Actually, I found this thread because I just received the Samsung SC-MX10 as a gift, and I was just poking around to see what other people had to say about using it with Ubuntu.  I just plugged it in via USB, pulled off the video clips I wanted to edit, and popped open Kino.  Kino automatically imports the files and changes them to a .dv format.  After that, the clips are a breeze to work with.  I'm not doing any high-end video editing, but its great for my needs.

---

