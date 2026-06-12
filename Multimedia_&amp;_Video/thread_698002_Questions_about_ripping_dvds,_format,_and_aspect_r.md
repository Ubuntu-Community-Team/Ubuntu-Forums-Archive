---
title: "Questions about ripping dvds, format, and aspect ratio"
date: 2008-02-15
forum: Multimedia &amp; Video
---

### Post by theknowledgeist on 2008-02-15
Hello, I am having some problems playing DVDs and other types of media files.

I have some DVDs, and media files in formats like DivX, that are in a 4:3 aspect ratio. However, there are black bars on the top and bottom of the screen. I think this occurs because the creator of the video has the file in widescreen format, but wants it watchable on a regular tv, so he adds in the black bars. Anyhow, I have a 16:10 monitor, so when I view these files full screen, there are black bars on the top, bottom, left, and right. This pisses me off because the video is acually in widescreen format but I have to watch it like I had a non widescreen monitor.

1) What I want to do is somehow convert these files to get rid of the black bars on the top and bottom so that the video will be in a widescreen ratio and I can watch full-screen without any black bars. Is this possible?
(I have tried switching the aspect ratio to 16:10 with VLC media player, and while this helps, it stretches the video and doesn't solve the underlying problem). 

2) I have some DVDs of music videos, and I want to rip these DVDs to my hard drive, but I want each video to be its own file. I do not want to lose any video or audio quality at all, and file size is not an issue for me. What format/codec/container should I encode these files in? Also, when I do this, is there any way to fix the aspect ratio problem I described above?

Thanks.

---

### Post by gsmanners on 2008-02-16
All these problems can be solved with proper crop and scale filters. If you don't mind using the console, it's pretty easy with mplayer. For example:

mplayer vid.avi -vf crop=700:460:10:10,scale=640:480 -monitoraspect 16:10

The above line would crop 10 pixels off each side of a 720x480 video. If you use mplayer, you can easily use mencoder the same way for conversion.

If each music video on your disc is its own chapter, you could try ripping each chapter to a different VOB file. To do this with mplayer you would need to know the title number and chapters, then do something like this:

mplayer dvd://1 -chapter 3-4 -dumpstream -dumpfile movie.vob

The above would rip chapter 3 to 4 of title 1. As for format/codec/container, I would use x264 (or xvid if I had a slower CPU) and mkv as the container.

[http://gentoo-wiki.com/HOWTO_DVD_to_Matroska](http://gentoo-wiki.com/HOWTO_DVD_to_Matroska)

---

