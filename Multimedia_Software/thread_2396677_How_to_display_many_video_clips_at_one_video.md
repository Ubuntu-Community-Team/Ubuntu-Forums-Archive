---
title: "How to display many video clips at one video"
date: 2018-07-19
forum: Multimedia Software
---

### Post by ahmedfaiqshihab on 2018-07-19
Hello there,

How to display many video clips at one video?

Regards

---

### Post by TheFu on 2018-07-19
Welcome.

The question isn't clear. 

A few options.

a) To playback multiple files in a specific order, make a playlist.   .m3u files are common. VLC,mpv, mplayer and other players will play them.
b) use regex/wildcard pattern match to play all files in a directory.   **vlc *4** or **mpv *4** will play all files ending in '4', like mp4 files would. This would probably result in alphabetic playback order.
c) If you want to merge 4 videos into 1 video, perhaps in different quadrants of the screen, use **OBS**. It is a video production tool great for taking conference videos with slides in 1 video input and a talking head in another video inputs, then compositing them together for a single video output.  It handles multiple audio inputs too.
d) if you want to concatenate 4 videos into 1 video 4x longer and all the videos have the same resolution, video-codec, and audio codec, then you can merge them into 1 file using **mkvmerge -o new-video.mkv file1.mp4 file2.mp4 file3.mp4 file4.mp4** The type of video input file isn't that important if the initial conditions are met.
e) if the input files are different resolutions and different codecs, then transcoding into 1 file will be required. And video creation tool can be used to do that.  **avidemux** is an old one, but still works. **openshot** is another.

Hopefully,  one of those options will work for your needs.

---

