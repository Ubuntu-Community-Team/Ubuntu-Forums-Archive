---
title: "ffmpeg: Join/Combine two images and a video together"
date: 2012-09-19
forum: Multimedia Software
---

### Post by vsiege on 2012-09-19
I have been using ffmpeg to convert video formats and join multiple videos together successfully but now I have some additional needs and I need a bit of assistance getting started. 

Problem 1 (the more pressing of the two):
I have two jogs (with diff. dimensions) that I would like to join with a mp4. I would like jpg 1 at the beginning of the video and and jpg 2 to be at the end. The result should be a mp4 file with the still images presented for 3 seconds each in the beginning and the other at the end sandwiching the original video.

Problem 2:
Ten jpgs combined into one video, each staying on screen for 3 seconds.

---

### Post by Merrattic on 2012-09-19
This makes a video out of a still image:
```
ffmpeg -loop 1 -i 1.jpg -r 25 -t 3 output.mp4
```
(-r is frame rate, -t is time in seconds)

Do this for each then concatenate your ten videos.

---

### Post by vsiege on 2012-09-19
Thank you for your post. I am able to make a video file from what you posted. Then I combined 'cat' both the image and a video. The result was a the still image for three seconds then the original movie - great..... but...... the audio from the original movie is now appearing during the still too. Is there any way to fix this. Heres my code:
```

ffmpeg -loop 1 -i flowers_0.jpg  -r 30 -t 3  -s 504x336 -acodec libfaac begin.mpg
ffmpeg -i bloom0.flv -acodec copy p2.mpg
cat begin.mpg p2.mpg> img2Vid00.mpg
ffmpeg -i img2Vid00.mpg -vcodec libx264 -acodec libfaac final.mp4

```

---

### Post by Merrattic on 2012-09-19
You may need to put some audio in your images video (just record some silence and add it into the mix)

---

### Post by vsiege on 2012-09-19
Sounds like it could work. Can't test it until tomorrow.

---

