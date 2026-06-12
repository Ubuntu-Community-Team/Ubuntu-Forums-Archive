---
title: "How To : Convert .ogg Files To MP4 For Internet Uploading!"
date: 2008-01-29
forum: Multimedia Production
---

### Post by GamingMazter on 2008-01-29
If you use record my desktop or other screen recording programs you will know that it starts off (once finished) as a .ogg file which you can't upload to most websites e.g: YouTube. There is a very simple way to convert this to MP4 for putting on your device or the web. First save the .ogg video to your desktop and make sure you have VLC Media Player. Open VLC and click file-->wizard then click Transcode/Save To File then click next. Make sure select a stream is selected and click browse. Then select your .ogg video file. After that make sure the video type is H624 and the bitrate is anything above 512 (Your Choice). Then click on MP$ from the choices. After that save the file and make sure you have .mp4 at the end of whatever you name it. Wait for it to finish and you are done! Enjoy Your Videos!

---

### Post by eye208 on 2008-01-29
VLC has some bugs affecting the transcode if the video includes sound. When I tried to transcode to H.264/AAC/MP4 using VLC, the result was a video without sound but with two (!) AVC streams inside.

There is another transcode method for .ogg files based on MEncoder and MP4Box:

```
mencoder file.ogg -vf harddup -ovc x264 -nosound -mc 0 -noskip -of rawvideo -o file.264
mencoder file.ogg -ovc raw -oac faac -of rawaudio -o file.aac
MP4Box file.mp4 -new -fps __ -add file.aac -add file.264
```

---

### Post by rootkit on 2008-02-01
I have some more complex scripts that does almost the same thing with some tweaks: [http://ubuntuforums.org/showthread.php?t=684571](http://ubuntuforums.org/showthread.php?t=684571)

---

