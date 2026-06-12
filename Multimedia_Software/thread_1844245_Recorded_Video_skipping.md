---
title: "Recorded Video skipping"
date: 2011-09-14
forum: Multimedia Software
---

### Post by Jwood725 on 2011-09-14
I am having issues with playing video that i record and imported to my pc. I'm using Ubuntu 10.04 and the issue is. Whenever I play video it starts skipping frames, while the sound under it stays flawless.

---

### Post by papibe on 2011-09-14
Which kind of video?
   Is it HD, or what resolution?
    Which format?

What player are you reproducing it with?

Regards.

---

### Post by Jwood725 on 2011-09-15
It is recorded in HD but watched as SD. Format is .MOV and I am using Movie Player (totem package?), however it does it with vlc also. I haven't tried to use anything else, and it doesn't do it with Internet video. Just the recorded video I shot.

---

### Post by papibe on 2011-09-15
Could you post the video's CODECS?

While playing it in VLC, go to Tools -> Codec Information. Paste or rewrite what it says in that window.

Regards.

---

### Post by Jwood725 on 2011-09-15
Stream 0
    Type: Video
    Codec: avc1
    Language: English
    Resolution: 1440x1080
    Display Res.: 1440x1080
    Frame Rate: 29.970029

Stream 1
    Type: Audio
    Codec: mp4a
    Language: English
    Channels: Stereo
    Sample Rate: 48000 Hz

---

### Post by papibe on 2011-09-15
That is a HD video, to reproduce it without skipping you need to have video hardware acceleration. Do you have that working on your computer?

Another possibility would be to resize/reencode the video to something that you can reproduce using just your CPU.

There are command line options like mencoder or ffmpeg that can do the job pretty easily. If you feel more comfortable using a GUI application, off the top of my mind: WinFF and Handbreake.

Hope it helps.
Regards.

---

### Post by no2498 on 2011-09-16
if you save the videos with a space in the name
it will do the same thing

---

### Post by Jwood725 on 2011-09-17
> **papibe said:**
> That is a HD video, to reproduce it without skipping you need to have video hardware acceleration. Do you have that working on your computer?

Another possibility would be to resize/reencode the video to something that you can reproduce using just your CPU.

There are command line options like mencoder or ffmpeg that can do the job pretty easily. If you feel more comfortable using a GUI application, off the top of my mind: WinFF and Handbreake.

Hope it helps.
Regards.

Ok, I'm not sure if I have a video hardware acceleration, however it seems that recoding it has worked for this video. I changed it to a NTSC DVD format and it runs smoothly. I used Pitivi Video Editor to render it with. So thanks for the help sorry for being such a noob, but ya gotta start somewhere

---

