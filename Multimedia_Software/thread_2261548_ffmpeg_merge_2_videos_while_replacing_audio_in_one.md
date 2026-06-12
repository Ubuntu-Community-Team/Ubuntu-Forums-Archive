---
title: "ffmpeg merge 2 videos while replacing audio in one video... at the same time"
date: 2015-01-19
forum: Multimedia Software
---

### Post by Valpskott on 2015-01-19
So, I've been tearing my hair since yesterday trying to solve this problem.
The real life situation is far more complex than the Title discribes. Although, the title sums up the most significant part of the problem.

Lets say I have 2 video files (intro.mov and video.mov). I output the audio from video.mov into audio.mp3 which I process with sox. I then want to replace the audio in video.mov with audio.mp3, while merging this video with intro.mov infront of it.

Right now I'm doing this in 2 stages, first stage is combining the videostream with audio.mp3 into a new videofile. Second stage I merge intro.mov with the newly combined video. This means the videostream from video.mov is rendered twice.

I'm producing videos for my youtube-page on a dayly basis, the intros I use are always under 10 seconds, while the rest of the video most often can range from 20-50 minutes, so I would cut the renderingtime almost in half if I got this to work.

I've compiled ffmpeg from source, so I've got most if not all of the recent features.

---

