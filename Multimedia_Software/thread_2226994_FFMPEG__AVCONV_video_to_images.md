---
title: "FFMPEG / AVCONV video to images"
date: 2014-05-30
forum: Multimedia Software
---

### Post by thepopasmurf on 2014-05-30
Hi,

I have been using avconv to split a video into images and I have some questions.
The command I am using is:

avconv -i INFILE -f image2 OUTFILE.jpg

The infile is an avi or mpg video.

Does the amount of images produced match the FPS of the video?

My video says 24 fps in the codec but when images are produced, the amount of images suggests a lower fps. Which should I trust?

Is the time difference between each image produced the same?

Thank you

---

### Post by timsdeepsky on 2014-05-30
I have had luck with ffmpeg when i call out the fps in the command....
```
ffmpeg -i input.mp4 -an -qscale 0 -f image2 -r 29 filename%06d.jpg
```
This seems to get me about the right amount of images....
This may be usefull [http://linuxers.org/tutorial/how-extract-images-video-using-ffmpeg]("http://linuxers.org/tutorial/how-extract-images-video-using-ffmpeg")

---

### Post by thepopasmurf on 2014-05-30
wow, thank you.

25 FPS is the default frame rate for grabbing images.

So am I correct in saying that the software will generate inbetween images if the fps of the video is actually lower?

---

### Post by timsdeepsky on 2014-05-30
It is my understanding that if you put the "-r " in front of the "i",,,,ffmpeg treats it as the rate of the input....
If you put the "-r " after the "i",,,,ffmpeg will treat it as the resampled rate for the output....
So i believe this would force 24fps out....
```
ffmpeg -i input.mp4 -r 24 -f image2 foo-%06d.jpeg
```

---

