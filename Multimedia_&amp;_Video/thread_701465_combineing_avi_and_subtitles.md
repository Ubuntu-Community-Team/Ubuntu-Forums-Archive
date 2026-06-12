---
title: "combineing avi and subtitles"
date: 2008-02-19
forum: Multimedia &amp; Video
---

### Post by kxr1der on 2008-02-19
I want to combing an avi file with a subtitle file (.srt) into 1 file, are there any applications that do this and if there is can you explain how its done, i have tried a few but couldnt figure out how to do the combine

---

### Post by pbcartwright on 2008-02-19
I use a command-line program called tovid. I think it has the capability to add subtitles

see :
$ man tovid
 -autosubs
              Automatically  include  subtitle files with the same name as the 
             
Get subtitles from FILE and encode them into the  video.   WARNâ&#128;
              ING:  This hard-codes the subtitles into the video, and you canâ&#128;
              not turn them off while viewing the video. By default, no subtiâ&#128;
              tles  are  loaded.  If  your video is already compliant with the
              chosen output format, it will be re-encoded to include the  subâ&#128;
              titles.

---

### Post by fs3rp4 on 2008-02-19
avidemux

Grafical and very easy to use...

---

### Post by kxr1der on 2008-02-19
i have avidemux but i dont know how to add the srt file

---

### Post by fs3rp4 on 2008-02-19
> **kxr1der said:**
> i have avidemux but i dont know how to add the srt file

Open the video file with avidemux

In the left side there is Video and sound buttons menus.


Select video and change to your desired encoder. Example Xvid4

Select Filters/Subtitles and insert your subtitle

Select save. Write the video name, like test.avi and go


The encode will start...

---

### Post by kxr1der on 2008-02-19
i followed those instructions but the subtitles dont show up on screen

---

### Post by fs3rp4 on 2008-02-19
Did you want watch a video with these subtitles or did you want to hard encode it in the video?

---

### Post by santaslittlehelper on 2008-02-19
Hi

You might need to set the font path.
"filters > subtitles > and double click subtitler" path could be /usr/share/fonts/truetype/msttcorefonts/arial.ttf, you should be able to see the subs with preview.
If you get problems with weird characters open the .srt file in and text editor or use something like Gaupol and save it as UTF8.

---

### Post by Etheral_Reality on 2008-06-09
uh well i can't speak for kxr1der, but i'm having the same problem, is it possible to hard code it into the video?

---

