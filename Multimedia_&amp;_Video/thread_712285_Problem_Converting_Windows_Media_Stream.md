---
title: "Problem Converting Windows Media Stream"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by SNYP40A1 on 2008-03-01
I have a file which was streamed video, I saved it to my computer.  I can play the file in VLC / Winamp / Windows Media Player, etc, but I cannot fast forward (or backwards).  I can only play the file straight through and pause.  I first tried converting the file using VLC, it started fine, got through the first two minutes, then hit an error and aborted.  I tried indexing the file using Windows Media File Encoder utility, no good.  I also tried converting the file using Windows Media Encoder and another popular file conversion software that I got off sourceforge.org called MediaCoder.  None of these software could convert the file.  The file was not intended to be downloaded and I think the people hosting the file are taking measures to discourage people from downloading and saving their streams.  How do I convert this file to something seekable?  It's almost like I need a program to "watch" the video and then encode it independent of the file itself.

---

### Post by Bubba64 on 2008-03-01
I looked for ways to convert and couldn't find any, but if you install smplayer from synaptic you can move a streamed video forward and backward. this may be due to that I have every possible plugin and codec and Firefox add ons installed for myself, check it out.

---

### Post by SNYP40A1 on 2008-03-01
> **Bubba64 said:**
> I looked for ways to convert and couldn't find any, but if you install smplayer from synaptic you can move a streamed video forward and backward. this may be due to that I have every possible plugin and codec and Firefox add ons installed for myself, check it out.

It's actually not streamed...it was, but I used another program to save it to my disk.  Even that part was hard, for example, I could not save the file using VLC.

---

### Post by Bubba64 on 2008-03-01
If your using Firefox go to Mozilla add ons and get video downloadhelper this is a good add on for downloading numerous sound or video file types it has a little spinning icon that lights up and spins when your on something that is downloadable. I have saved video from using this downloader that say playing and streaming right next to it but it is not actually streaming just playing in that manner I don't know why or how but the smplayer will move the video forward and backward, As I said I don't know personally how to convert video files and that seems to be your actual goal.

---

### Post by rvm4000 on 2008-03-01
Try with 
```

mplayer -idx file

```

or 

```

mplayer -forceidx file

```

With a little bit of lucky that should allow you to watch the file with seeking.

You can use mencoder to convert it to another format, with something like this:
```

mencoder -oac copy -ovc copy -o output.avi file

```

(if the file is asf, wmv or something similar there could be some troubles)

---

### Post by SNYP40A1 on 2008-03-02
I will try the SM Player, it is a WMV file.  Say I launch the file in Media Player or some other application and watch it all the way though.  Is there a program which can capture the video on my screen and the sound produced by my computer and encode that as a separate file?

---

