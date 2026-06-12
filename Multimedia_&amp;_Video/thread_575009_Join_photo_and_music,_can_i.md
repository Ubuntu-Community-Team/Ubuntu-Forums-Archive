---
title: "Join photo and music, can i?"
date: 2007-10-13
forum: Multimedia &amp; Video
---

### Post by pkslot on 2007-10-13
The thing is, my son made a small "composition" today on my keyboard, while i had hydrogen playing in the background. I recorded it, and i would like to join the music together with a picture of him, so it turns out to be a videofile. Can i do that, and how?

---

### Post by pkslot on 2007-10-14
No clue at all?

---

### Post by Total_Biscuit on 2007-10-14
> **pkslot said:**
> No clue at all?
I have absolutely no idea how to do this "properly" or whether there's some software that will do the job with a single click but I tried something quickly with mjpegtools and avidemux.  The process isn't optimised at all, but it worked for me!

All you need to do is make a whole lot of copies of the original picture for the still image video and then mux it together with the audio track.  To make the video frames take the image, crop/scale it to a suitable size - 720 x 480 or smaller, say - and save as a jpg file.  Next, make 24 x length of the audio track in seconds copies of the image, numbering them from 1 to the desired number of frames (get the track length from the file properties).  Best save the image to an empty directory and use a batch file to do this:
```
#!/bin/bash

for ((F=1; F <= DesiredNumberOfFrames ; F++))
   do
     ln -s "YourImage.jpg" "Frame_$F.jpg"
   done
```
(Using symbolic links rather than making actual copies of the original image has got to save some disk space.)  Next, join all the frames together into an mpeg2 video file:
```
jpeg2yuv -j Frame_%d.jpg -b 1 -f 24 -I p | mpeg2enc -f 3 -b 3000 -o output.m2v
```
Start avidemux and File | Open output.m2v.  Then open the audio track with Audio | Main Track, selecting the right audio type (if the recording isn't wav or mp2/mp3 then convert it first with audacity).  Click the play button.  All things being equal, there will be a still picture with sound!  Finally, use avidemux to save the video in the desired format, e.g. select mpeg4 (lavc) for video, twolame for audio, avi for file format and then File | Save | Save Video...

---

### Post by darksizzle on 2007-10-14
I'm on way too weak of a computer right now to try and start doing any sort of sound/video work but this could work.

-First get ahold of istanbul (sudo aptitude install istanbul)
-Start istanbul, it's going to put a little red record button in your system tray
-Open the picture of your keyboard rockin son with whatever and make it the size you'd like the video to be
-Right click on the red record button and select "Select Area to Record" and do a drag on select the area of your son's photo, also select record sound and unselect record mouse pointer
-Open up the audio of your son's keyboard jam, making sure it's not covering any of the area that you have selected for your son's photo.
-Play your audio and start recording (by left clicking on the record button) in sync as you can
-Stop recording when you've gotten the audio youd like. 

Like I said I don't know how good of a video this is going to get you or how professional it's going to look, but it's something to try haha.  If it looks good and you'd like to convert it to a video to show to windows users (it's going to be in ogg theora, which is a great format that will run on linux boxes, but not off the bat on windows) let me know.  Good luck.

---

### Post by pkslot on 2007-10-14
Thanks, both of you.

I just couldn't figure it out, and i can see two pairs of fresh eyes did wonders. I'll try it in the morning and let you know the results.

Once again, thanks [-o<

---

### Post by jeroach on 2008-05-07
This is not a "solution".  Ubuntu is definitely not consumer ready if this is consider reasonable.  If anyone comes across a usable program that will do this, please let me know.

---

