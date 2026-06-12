---
title: "audio/video problems after burning DVD"
date: 2009-01-16
forum: Multimedia Software
---

### Post by jmd9qs on 2009-01-16
hi all,

recently i concatenated several .avi files with avimerge, then used ffmpeg to convert them into ntsc-dvd format. i then authored the resulting .mpg file with dvdauthor and finally burned with growisofs.

when i went to play the dvd, the audio and video quality was great. however, as the film progresses, the playback gets really jerky (like normal "skipping"). i cant seem to figure out why, because the video files on my computer play just fine all the way through. is this a fault with dvdauthor? or maybe the dvd-player that i am using? please help me figure this out. here is an example of how i set all this up:

```
avimerge -o final_video.avi -i vid_1.avi vid_2.avi vid_3.avi

ffmpeg -i final_video.avi -target ntsc-dvd /media/disk/final_video.mpg

dvdauthor -o /media/disk/FinalVideo -t -c 0,30:00,01:00:00 /media/disk/final_video.mpg

dvdauthor -o /media/disk/FinalVideo -T  

growisofs -Z /dev/dvd1 -dvd-video /media/disk/FinalVideo 
```

anyone see problems here? should i take the transcode route? (ie split the .avi into seperate audio/video files and remux with mplex)

i'm tearing my hair out here! please help!

---

