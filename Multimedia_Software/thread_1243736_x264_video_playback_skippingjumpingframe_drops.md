---
title: "x264 video playback skipping/jumping/frame drops"
date: 2009-08-18
forum: Multimedia Software
---

### Post by penguinchrissy on 2009-08-18
Hi I'm trying to play back x264 files in the .mkv container on my Pentium 4 desktop with 1 gig of ram. I have two computers with the close to the same hardware just one has a dedicated video card and the other doesn't. When I try and play a x264 .mkv file I always get skipping/lagging/frame drops no matter what media player I use. I have tried totem gstream/xine. mplayer, and vlc. With totem and mplayer the video will be choppy while the audio is fine. An example is a scene where someone gets shoot. I can seem them pull out the gun but then it freezes on that frame but I hear all the audio of whats happing then it skips to a frame where everyone is on the floor dead. On vcl the video is really messy it will have things from all different frames all at once like it can't finish playing one thing before another. Things get kinda weird because this problem doesn't persist with all my videos. Videos that have x264 .mkv with DTS seem to play ok I can notice a little skipping but it is watchable. These problems exist and are the same wither or not I have the video card or not. The playback is a little better with the card but still not watchable. 

Is there anything I can do to get these to play back smoothly?

The only fix I've found is moving to windows which is the last thing in the world I want to do. 

I didn't post any logs because I'm not 100% sure how to get them. If they would be helpful could you please point me to a how to so I can get them or if it is just a couple lines of commands post them for me, that would be appreciated.

I really want to get this figured out so I can update to HD videos. I love using Ubuntu and don't want to go back to windows just cause it can't play some media files.

Please help I'll give any suggestions or fixes a try.

---

### Post by Revolutionary101 on 2009-08-18
> **penguinchrissy said:**
> Hi I'm trying to play back x264 files in the .mkv container on my Pentium 4 desktop with 1 gig of ram. I have two computers with the close to the same hardware just one has a dedicated video card and the other doesn't. When I try and play a x264 .mkv file I always get skipping/lagging/frame drops no matter what media player I use. I have tried totem gstream/xine. mplayer, and vlc. With totem and mplayer the video will be choppy while the audio is fine. An example is a scene where someone gets shoot. I can seem them pull out the gun but then it freezes on that frame but I hear all the audio of whats happing then it skips to a frame where everyone is on the floor dead. On vcl the video is really messy it will have things from all different frames all at once like it can't finish playing one thing before another. Things get kinda weird because this problem doesn't persist with all my videos. Videos that have x264 .mkv with DTS seem to play ok I can notice a little skipping but it is watchable. These problems exist and are the same wither or not I have the video card or not. The playback is a little better with the card but still not watchable. 

Is there anything I can do to get these to play back smoothly?

The only fix I've found is moving to windows which is the last thing in the world I want to do. 

I didn't post any logs because I'm not 100% sure how to get them. If they would be helpful could you please point me to a how to so I can get them or if it is just a couple lines of commands post them for me, that would be appreciated.

I really want to get this figured out so I can update to HD videos. I love using Ubuntu and don't want to go back to windows just cause it can't play some media files.

Please help I'll give any suggestions or fixes a try.

I have similar problems with H.264 .mkv files but if I use H.264 in .mp4 it works fine. Maybe it is because all of the problems have not been fully ironed out of the .mkv container. This may be because MKV is still a fairly new media container format.

---

### Post by penguinchrissy on 2009-08-18
Would there be any quality loss going from theh .mkv file to the .mp4?
Whats the best program to use and not get quality loss?

---

### Post by Bachstelze on 2009-08-18
> **penguinchrissy said:**
> Would there be any quality loss going from theh .mkv file to the .mp4?

That wouldn't make any difference. MKV and MP4 are containers. Whether you mux your H.264 video stream into one or the other doesn't make it any different for decoding purposes.

For your playback problems, try [CoreAVC]("http://ubuntuforums.org/showthread.php?t=1034075").

---

### Post by Revolutionary101 on 2009-08-18
> **penguinchrissy said:**
> Would there be any quality loss going from theh .mkv file to the .mp4?
Whats the best program to use and not get quality loss?

You could use avidemux and just copy the music and video tracks and only change the container from .mkv to .mp4

---

