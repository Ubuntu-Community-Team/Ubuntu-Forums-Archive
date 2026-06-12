---
title: "time-lapse photography: mencoder and lossy compression"
date: 2011-05-15
forum: Multimedia Software
---

### Post by oldmankit on 2011-05-15
I am doing some time-lapse photography and found a cool command to convert jpges into video ([http://electron.mit.edu/~gsteele/ffmpeg/]("http://electron.mit.edu/%7Egsteele/ffmpeg/")):
```
mencoder "mf://*.jpg" -mf fps=10 -o test.avi -ovc lavc -lavcopts vcodec=msmpeg4v2:vbitrate=800
```The problem I now face is that I probably want to edit the output file in something like kdenlive, snip around a bit, add audio etc., and then render it again.  So the video ends up being encoded (with lossy compression) twice.  I don't like that. 

:?:

My question is, is there a kind of raw format that  I can use initially so that I only do lossy compression once.

several hundred jpgs -> one raw video format -> kdenlive for editing and mixing -> mpeg.

---

### Post by solitaire on 2011-05-15
[I]If you can convert the jpg's to png's then you could try this:
[/I]

*[http://web.njit.edu/all_topics/Prog_Lang_Docs/html/mplayer/encoding.html](http://web.njit.edu/all_topics/Prog_Lang_Docs/html/mplayer/encoding.html) :*

*Creating an uncompressed file from all the PNG files in the current dir:*
    ```
 mencoder -mf on:w=800:h=600:fps=25:type=png -ovc rawrgb   -o output.avi \*.png
```


Not sure if you could just swap png for jpg but give it a go.

---

### Post by oldmankit on 2011-06-18
I've found a solution better than I could have hoped for.  Kdenlive.

Project -> add slideshow clip 
Select folder containing jpegs (preferably not too large files)
Change 'frame duration' from hours:minutes:seconds to frames, and select how many frames per second you want.  I tried 5 which worked well for my project (which was shot in the wild at 1 frame per second).

Bang.  Your finished (after a little wait, if you have thousands of jpegs like me).  You can select any effects you want with this, for example ken burns effects (entitled 'Pan and Zoom' in kdenlive).

The interface of kdenlive is deceptively friendly: it's actually powerful program.

---

