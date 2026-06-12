---
title: "video split screen in ffmpeg, avidemux, mencoder?"
date: 2008-10-14
forum: Multimedia Software
---

### Post by zach014 on 2008-10-14
Is there a way to create a split screen video from two different AVIs? I've been searching for a while, and I can't find anything except a mention of avidemux. I've looked through the video filters in avidemux and can't find aything useful.

Thanks,
Zach

---

### Post by cotcot on 2008-10-14
I know it is possible with cinelerra but have not tried it myself. With kdenlive i am sure it is possible because i have made a couple of video n videos myself. It is with the picture in picture tool.

---

### Post by zach014 on 2008-10-14
Basically i need to crop the video left 200, save it, take the original video and crop it right 120. Then i need a way to stick the two halves together. I don't think this is what you're describing with kdenlive. This can be done with "StackHorizontal(vid1,vid2)" in avisynth, though. If I wanted, I could go compile that, but it seems i need a newer version of nasm. So I'd rather look for something simpler, for example an avidemux plugin or something in the repositories.

---

### Post by cotcot on 2008-10-15
I do not know about a plug-in for this in avidemux. 
[[COLOR="Blue"]This[/COLOR]]("http://cinelerra.org/docs/split_manual_en/cinelerra_cv_manual_en_8.html") section of the cinelerra manual describes amongst other the 'camera and projector' tools in cinelerra. This tool could be used for your application. But i agree it is not so easy.

---

### Post by jack.herbert on 2010-02-03
ah ah ah. Split screen is tricky. 
I managed to do it once using Blender's video strip editor. I need to do it again now and really wish there was an easier way. An avidemux plugin would be amazing.
Good luck to anyone else googling: split screen avidemux
:-|

---

