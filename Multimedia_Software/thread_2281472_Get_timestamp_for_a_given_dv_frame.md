---
title: "Get timestamp for a given dv frame"
date: 2015-06-07
forum: Multimedia Software
---

### Post by bill-lancaster on 2015-06-07
This replaces my earlier thread.
I'm looking for command line code to retrieve timestamp data for a given frame in a .dv file
Any ideas

---

### Post by SeijiSensei on 2015-06-07
I don't really understand the question, Bill.  How are you determining which frame you want the timestamp for?  If you're watching it with something like SMPlayer it shows the elapsed time in minutes and seconds at the bottom of the application.  Do you mean the exact timestamp in hundredths of a second?  You might be able to guess pretty accurately by jumping to just before the frame, seeing its timestamp, and using the frames/second rate to estimate the exact location of the frame of interest.  Most video is shot at 23.976 frames/second.

From the command line you could use mplayer for this.  Play the video from the command prompt with "mplayer /path/to/video.dv" and watch both windows.  The terminal window will report the elapsed time in tenths of a second:
```
A:  56.8 V:  56.8 A-V:  0.000 ct:  0.041   0/  0 17%  0%  0.5% 0 0 
```
Here it is at 56.8 seconds.  I can't say I know what all the other values mean though.

---

### Post by bill-lancaster on 2015-06-07
Oh dear, I'm getting confused with my terms.
If, for example, I watch a dv file using Kino, the information panel will show me the date & time that a particular frame(or section) was recorded.  It seems that each frame has this info.
I would like to examine a number of dv files and divide them into sections according to date.
Unfortunately, these files were captured from tape using dvgrab (which worked very well).  The task took several days!  Then(too late) I discovered that dvgrab would split the files into date sections!
Hope this explains things a bit better.

---

### Post by SeijiSensei on 2015-06-07
Sorry, but I can't help with that, I'm afraid. Good luck!

I did visit the home page for Kino, which reports the project has been dead since 2009.  It looks to have used ffmpeg and/or mencoder as the engine.   

Maybe this would help: [http://einar.slaskete.net/2011/09/05/adding-time-stamp-overlay-to-video-stream-using-ffmpeg/](http://einar.slaskete.net/2011/09/05/adding-time-stamp-overlay-to-video-stream-using-ffmpeg/)

It looks like the datestamp can be referenced from the ffmpeg command line as %T.

---

### Post by bill-lancaster on 2015-06-08
Thanks, there are a few clues in the information you found.  I'm following them up and if I get a result I'll post it here.

---

