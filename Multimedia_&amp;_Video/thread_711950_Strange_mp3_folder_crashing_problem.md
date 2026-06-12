---
title: "Strange mp3 folder crashing problem"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by NotoriousTF on 2008-03-01
I recently cleaned up my laptop, removed the dual-boot and moved fully over to Ubuntu. After a bit of messing around, I finally got 7.10 installed and working smoothly. Only recently have I copied some CDs onto my hard drive and pulled a file with a sizeable amount of music off my mp3 player. Most of the files are in mp3 format, but some I noticed are in wma.

Only after adding all this music did I notice this odd problem. When I open up my home folder, all works as normal, but as soon as I open up any of the folders which show mp3 files, the file browser just freezes up on me and I have to forcefully close it. Anyone have any idea whats going on? I'm completely stumped!

I might add that the music files are playable via Listen, I've uploaded the music folders and they work a charm.

---

### Post by erginemr on 2008-03-01
You shuld disable the file preview feautore in Nautilus. Please refer to this topic:
[http://ubuntuforums.org/showthread.php?t=661450&highlight=preview](http://ubuntuforums.org/showthread.php?t=661450&highlight=preview)
third item in the penultimate post...

---

### Post by NotoriousTF on 2008-03-01
Thank you very much, it worked a charm!
Just out of curiousity, you said in the post you refered me to, that the error states 'too many open files'. The way my music library folder is organised, I'd only be displaying an album per folder so not that many files. Is there another reason why this could be happening?

---

### Post by erginemr on 2008-03-01
God knows why!.. :confused:

Maybe the background program used to preview audio files was buggy or non-existent at all. I remember, back in days of Edgy Eft, I had no sound preview in Nautilus although active, I had to install an external program (sox maybe) to actually hear the sound. Later on, seeing the performance hit, I had disabled file preview altogether. I need to do a little research in the forum to find out the name of that package.

Meanwhile, could you please try one thing? When you re-enable music preview, do you actually hear the sound when you hover the mouse on the file icon?

---

