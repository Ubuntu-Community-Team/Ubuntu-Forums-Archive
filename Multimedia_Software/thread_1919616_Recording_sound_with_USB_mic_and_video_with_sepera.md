---
title: "Recording sound with USB mic and video with seperate webcam"
date: 2012-02-03
forum: Multimedia Software
---

### Post by JWKingsley on 2012-02-03
I have a G-Track Samson USB Microphone and Logitech webcam and I'm using ubuntu 11.10 on a Thinkpad Edge dual core 2.0 Ghz 15". 

I am using GUVCVIEW to record sound and image. I have done this before using the logitech webcam to record image and sound AND it works recording image and sound from the laptop.

I would like to take advantage of this new cool mic and the webcam at the same time and record directly into guvcview for fast efficient recordings. 

The settings I have used for guvcview: YUY2 - uncomp YUV  
                                       AVI format
                                       PCM -uncompressed (16 bit)

None of the other settings seem to work.

I used this when I recorded directly to webcam with its sound input or with laptop's sound input and it works. 
Video : 640 x 360, 640 x 480, or 1280 x 720  (these are the best for youtube and all seem to work).

Any ideas on how I can get my external USB webcam AND USB Samson G-track microphone working at the same time ?

Thanks :)

---

### Post by definitionofis on 2012-02-27
I have logitech pro 9000 and I had to move up the volume on the microphone settings inside SystemTools->SystemSettings->Sound in Ubuntu 11.10.  Your multiple microphones should be listed there.

Also MJPG with MPEG2 sound works, but I switched to PCM uncompressed because kdenlive cannot edit .avi files unless they are PCM uncompressed. That is my experience, so far. I am new to kdenlive and guvcview.

---

