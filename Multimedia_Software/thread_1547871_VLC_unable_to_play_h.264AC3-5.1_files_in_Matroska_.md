---
title: "VLC unable to play h.264/AC3-5.1 files in Matroska containers"
date: 2010-08-07
forum: Multimedia Software
---

### Post by omicrondelta on 2010-08-07
With VLC on my Mac or Windows boxes, these videos play fine. When I try using them on my Lucid Lynx or Jolicloud systems, the video will not play at all -- VLC will load, but no audio or video. I'm suspecting that there's a package that I'm missing, but I could be mistaken.

I'm at a loss. Does anyone know how to fix this?

EDIT: I forgot to mention that they play fine under Totem -- actually, the video quality looks better with Totem than VLC on my other systems. So perhaps it isn't a package I'm missing, but something that isn't compiled or linked to VLC when it's compiled.

---

### Post by cavalier911 on 2010-08-07
Your last assumption is correct.VLC for windows offers everything,linux is a different story.You can't get plugins for VLC to enable those options.There is no fix other than to find a version of VLC from a third party repository that has those options compiled in or compile VLC yourself.Run vlc from the commandline in terminal to see the options and errors while trying to play the file.
```
vlc -v video.file.name
```
More info: [http://wiki.videolan.org/Documentation:Play_HowTo/Advanced_Use_of_VLC#Use_the_command_line](http://wiki.videolan.org/Documentation:Play_HowTo/Advanced_Use_of_VLC#Use_the_command_line)

---

### Post by andrew.46 on 2010-08-25
Hi omicrondelta,

Sounds a little odd. I have put a file together using h264 video and ac3 5.1 sound in a matroska container so you can test:

```
wget http://andrews-corner.org/samples/ubf_h264_ac3.mkv
```

Test this one with your recalcitrant copy of vlc and see what results you get, it should play with no problems.

All the best,

Andrew

---

