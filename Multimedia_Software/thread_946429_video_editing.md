---
title: "video editing"
date: 2008-10-13
forum: Multimedia Software
---

### Post by rob1984 on 2008-10-13
hello!

i just wanna ask if you guys could recommend something that will let me:

*take a series of screenshots from a video file (eg. one per minute)
*join two/several video chunks together (eg. join a two disc vcd into one mpg)

the lighter the better and i ain't afraid of the command line

thanks in advance

---

### Post by cor2y on 2008-10-13
for taking screenshots at certain intervals mplayer can do that with a script.
Video Contact Sheet is the best i've seen so far as relates to scripts that use mplayer and ffmpeg.
[http://p.outlyer.net/vcs/](http://p.outlyer.net/vcs/)

If you need a GUI theres Videocut which will be available by default in the Intrepid Repos but now requires for Hardy that you download the source or deb from the official site.
[http://code.google.com/p/videocut/](http://code.google.com/p/videocut/)

Finally for video editing like you wish to do there are several tools.
Gui based : Avidemux, Open Movie Editor , Kdenlive, cinelerra etc
Cmdline : mencoder, ffmpeg 
The trick for all those tools is you need to read the documentation to get the best out of them usually a quick google search or visiting the home pages will yeild what you are looking for.

---

### Post by cotcot on 2008-10-13
Putting chunks together : 
```
cat chunk1 chunk2 > chunktogether
```

---

### Post by rob1984 on 2008-10-14
thanks a lot i'll check them out. also i didn't realise cat could do that! thanks.

---

