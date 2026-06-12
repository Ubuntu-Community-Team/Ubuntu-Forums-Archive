---
title: "Timelapse video Timestamp using ffmpeg"
date: 2013-06-27
forum: Multimedia Software
---

### Post by Hunter362 on 2013-06-27
I've been using the same command in a script, that creates hourly timelapse videos from a webcam.
Previous Ubuntu ver 10.04, just upgraded to 12.04
What has worked for months, now no longer likes the Date input for creating the name of the current video.

relavant portions of script are:
  date=`date +%b-%d-%a_%X.avi`

  ffmpeg -f image2 -r 15 -i horizion%04d.jpg -b 800k -vcodec mpeg4 ${date}

Which used to give me a filename of: Jun-19-Wed_21:01:01.avi
Now when ran, I get:  Unable to find a suitable output format for 'Jun-27-Thu_09:01:01'

Tried it with avconv and no luck with that either.... What changed??
Which ran hourly and worked fine.

** Update **
playing around with different formats today, it seems that the %X  for the time format was not liked by ffmpeg.

ffmpeg version 0.8.6-4:0.8.6-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Apr  2 2013 17:02:36 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[image2 @ 0x25f7760] max_analyze_duration reached
Input #0, image2, from 'horizion%04d.jpg':
  Duration: 00:00:40.50, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: mjpeg, yuvj420p, 640x493 [PAR 72:72 DAR 640:493], 8 fps, 8 tbr, 8 tbn, 8 tbc
Unable to find a suitable output format for 'Jun-28-Fri-11:23:25'

Removing the %X and just have Jun-28-Fri for the date and all is well again.

---

