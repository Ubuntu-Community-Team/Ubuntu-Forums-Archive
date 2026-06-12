---
title: "kdenlive - black video from rendering (when not using proxy clips)"
date: 2018-08-24
forum: Multimedia Software
---

### Post by BloodyIron on 2018-08-24
This is regarding : [https://www.reddit.com/r/kdenlive/comments/98pjly/black_video_rendering_when_unchecking_proxy_video/](https://www.reddit.com/r/kdenlive/comments/98pjly/black_video_rendering_when_unchecking_proxy_video/)

I'm trying to hammer out kdenlive to make some Gaming on Linux videos.

Now, when I render my project with Proxy Clips, I get video and audio content just fine, but it is lower fidelity since it's the Proxy Clips.

When I un-check use proxy clips, when telling it to render, with the intent of using the source footage, the resulting render is black video footage with just fine audio.

Now, the source content is 1920x1080@60fps 60mbps video, 192kbps audio, mp4 format.

I'm trying to output to 1920x1080@60fps. I forget the video bitrate, but I kept the audio untouched. But rendering to h264 (or x264, can't recall for sure).

Now, I've done the modifications to use NVENC, which massively helps for rendering times, and clearly that's not the problem as the proxy clips work.

When I render with source footage (black screen result), the rendering time is way less than I think it probably would be if it were doing it correctly.

As mentioned in the reddit thread, I tried making a scratch project to see if my other project got corrupted, or something else that's silly. That did not resolve it.

So, do any of you forum goers have any idea as to what I can do to resolve this?

* I'm on Ubuntu 18.04, and I switch into Enlightenment to render (I normally use XFCE4, but kdenlive doesn't like Compiz, which is what I use with XFCE4).
* i7-980x
* gtx 960, 396.54 I think is the driver I'm using

---

