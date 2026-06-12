---
title: "Screencast, reduce file size (ffmpeg)"
date: 2013-04-29
forum: Multimedia Software
---

### Post by Black27 on 2013-04-29
Hi all! I'm trying to use ffmpeg, because I need to save simultaneously webcam and screen videos, but in different files.
I tried to take a look around and I've putted together some snippets, and I've done my first script.
Everything looks fine, but the size of the output file is too big. How can I reduce it?
Here's the script I've done:

#! /bin/bash
unlink screen.mpg
unlink camera.mpg
echo "Starting Desktop Grab"
ffmpeg -f x11grab -s `xdpyinfo | grep 'dimensions:'|awk '{print $2}'` -r 25 -i :0.0 -sameq screen.mpg > /dev/null 2>&1 &
echo "Starting Camera Grab"
ffmpeg -f video4linux2 -s 640x480 -i /dev/video1 -sameq camera.mpg  > /dev/null 2>&1 &
read -p "Press ENTER to stop recording."
ps aux | grep ffmpeg | awk '{print $2}' | xargs kill

Looking around I was able to reduce the quality, but now is too low.
I would like to have something in the middle, a good compromise between quality/size
Here's the second one:

#! /bin/bash
unlink screen.mpg
unlink camera.mpg
echo "Starting Desktop Grab"ffmpeg -f x11grab -r 30 -s `xdpyinfo | grep 'dimensions:'|awk '{print $2}'` -i :0.0 -sameq ./screen.avi > /dev/null 2>&1 &
echo "Starting Camera Grab"ffmpeg -f video4linux2 -s 1280x720 -r 30 -b 600k -i /dev/video1 -vcodec mpeg4 -vtag xvid ./camera.avi > /dev/null 2>&1 &
read -p "Press ENTER to stop recording."ps aux | grep ffmpeg | awk '{print $2}' | xargs kill

Help will be very much appreciated!
Thanks in advance.

---

### Post by Black27 on 2013-04-30
I've found the answer, I write it there if someone else is looking for the solution.
I've just put -qscale:v 10 inside ffmpeg command.
It accepts a value from 1-31, lower is the value higher the quality/size.
The value of 10 is, for me, a good tradeoff.

---

