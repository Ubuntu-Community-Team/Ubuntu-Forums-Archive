---
title: "Convert video for YouTube upload"
date: 2007-07-30
forum: Multimedia &amp; Video
---

### Post by ianhaycox on 2007-07-30
I'm trying to convert a movie for upload to YouTube in their suggested format of:

    * MPEG4 (Divx, Xvid) format
    * 320x240 resolution
    * MP3 audio
    * 30 frames per second

I've got an movie.avi file (110Mb) from my camera which Nautilus properties reports as:

Video:
  Dimensions 640 x 480
  Codec Motion JPEG
  Framerate 30 fps
  Bitrate N/A
Audio:
  Bitrate N/A
  Codec Uncompressed 8-bit PCM audio
  Sample rate 16000 Hz
  Channels 1

I'd like to rescale it and change the audio and hopefully reduce it's size. I've looked at mencoder but I think my head is going to explode with all the options along with the surfing I've done. I'm just plain confused now.

Could someone please provide an example command to try to achieve what I'm after.

Thanks.

---

### Post by ianhaycox on 2007-07-30
To answer myself after a bit more experimentation and surfing I found the following seems to work,

mencoder input.avi -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:trell:autoaspect -vf scale=320:240 -oac mp3lame -o output.avi

The only minor glitch is that showing the properties in Nautilus does not seem to report the scale of 320x240 properly. It reports 0x0 !

---

### Post by azdragon on 2007-07-30
I found a program that does a good job of this called AVIREDUX    It is a gui based program and lets you save to many different formats.    I think your packet manager should have it. 

I still am looking for a good program that lets me edit clips together.  I tried LiVES but the audio would never work in it.

---

### Post by stmiller on 2007-07-30
The program you want is avidemux, I believe.

---

