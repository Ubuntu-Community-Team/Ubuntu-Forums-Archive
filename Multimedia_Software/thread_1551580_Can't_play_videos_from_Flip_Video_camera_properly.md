---
title: "Can't play videos from Flip Video camera properly"
date: 2010-08-12
forum: Multimedia Software
---

### Post by IceDoE on 2010-08-12
I'm running Ubuntu Netbook Edition 10.04 and trying to get videos from a  Flip Video UltraHD to play. After mplayer installs the extra gstreamer  codecs the video will "play" but it shows one frame for about 5 seconds  before skipping ahead to another frame for 5 seconds. The Audio plays  smoothly in the background. 

I've tried playing off of Windows 7 (which I'd prefer not to need) on  the same netbook, and it runs well with just some minor lag/jittering  once in a while, so the hardware can handle it.

I've found that if I use Kino to import and convert the video files (to  NTSC, haven't tried PAL) the resulting .dv file will then play  perfectly. However, this is a long conversion process and should be  unnecessary. The files say they are .mp4 on the camera, but I haven't  had this issue with other .mp4 files.

Any suggestions? I'd guess its a codec issue of some sort, but I haven't had any luck on that front.

---

### Post by no2498 on 2010-08-12
open a terminal type in  [ smplayer ] it tells you how to install it
it loads some 264 files with it along with ffmpg

also look in system, multimedia system selector click video set the plugin to x window no xv

this comes from the cheese help faq's

You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.


you dont need to run the gstreamer-properties this way

hope this helps

---

### Post by IceDoE on 2010-08-12
I tried it and now it won't play videos at all, instead mplayer says "could not determine type of stream".

Not sure but maybe there was some miscommunication though as you mentioned cheese. Flip Video is a standalone/portable video camera, not a webcam, that records to .mp4, though I can't play the .mp4s that it makes.

Edit: Ok, tried it through smplayer instead and it runs the video with similar problems as before. Except now it holds on one frame and then at the end it cuts audio and shows a a somewhat choppy progression of some more of the video.

---

### Post by sjs5132 on 2011-01-06
Just converted to Linux, new to everything here.  Just wondering if you ever found a solution to the Flip Video playback.  Thanks!

---

### Post by Hiker_ on 2011-01-19
The Flip Ultra HD records 60 frames per second, and in 720P resolution. 

You might have better luck converting those files to AVI and then playing them.  There are several MP4toAVI converters out there. 

I was complaining to Cisco support last night about the lack of Flipshare type software for Linux (Ubuntu) and the guy said they did not support it because there are not enough users.  Yeah right. 

I will try the MP4 conversion apps this week.

---

