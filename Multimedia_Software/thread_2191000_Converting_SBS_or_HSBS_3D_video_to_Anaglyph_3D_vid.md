---
title: "Converting SBS or HSBS 3D video to Anaglyph 3D video"
date: 2013-11-30
forum: Multimedia Software
---

### Post by longer_83 on 2013-11-30
Hi to all!
Recently I have been trying to convert HSBS 3D video to Anaglyph 3D video (1920x1080 according to **mediainfo**) using command: 
CODE]ffmpeg -i test_video_hsbs_3d.mkv -vf mp=stereo3d -acodec copy -threads 10 -b:v 10000k -preset ultrafast -vcodec libx264 test_video_anaglyph_3d.mkv[/CODE]
but output file according to **mediainfo** has resolution 960x1080 (resolution of one of the SBS halfs). My question - how to rescale video to resolution of 1920x1080? Commands:
```
ffmpeg -i test_video_anaglyph_3d.mkv -vf scale=iw*2:ih test_video_anaglyph_3d_new_res.mkv
```
or
```
ffmpeg -i test_video_anaglyph_3d.mkv -s 1920x1080 test_video_anaglyph_3d_new_res.mkv
```
or
```
ffmpeg -i test_video_anaglyph_3d.mkv -vf scale=1920:1080 test_video_anaglyph_3d_new_res.mkv
```
produces video of resolution of 1920x1080 (according to **mediainfo**) with centred 960x1080 video and black fields on sides. Any advices how to rescale (stretch) it properly?

---

