---
title: "how can I encode this?"
date: 2006-08-27
forum: Multimedia &amp; Video
---

### Post by Therrol on 2006-08-27
I have a "CBT Nuggets" video from my school. THe video is all FLV files. There is a screen capture part using the techsmith codec, and some webcam parts, I don't know what format they are. I want to encode these for ipod (so m4v files). the specs are as follows: 320x240, 64kbps audio, 4fps for screen capture and 15fps for the webcam videos. since these are prety long, it should work out to be 5gb for the whole series. can somone help me do this? Is there any good mpg encoding software for linux?

---

### Post by Angel777 on 2006-08-28
you can do it easily with ffmpeg : 

ffmpeg -i file_to_convert.??? outpufile.m4v

Just check the manual of ffmpeg for more options

---

