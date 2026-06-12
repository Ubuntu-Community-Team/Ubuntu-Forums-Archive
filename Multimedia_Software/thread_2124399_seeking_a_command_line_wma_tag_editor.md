---
title: "seeking a command line wma tag editor"
date: 2013-03-10
forum: Multimedia Software
---

### Post by parminides on 2013-03-10
I use vorbiscomment to put tags on ogg files. Is there a similar command line program to tag wma files? I tried exiftool, which looked promising, but it can only read wma tags. I can't find anything that's not gui.

---

### Post by cortman on 2013-03-11
Isn't .wma a Microsoft proprietary format? I doubt you'll find anything for it for GNU/Linux.

---

### Post by andrew.46 on 2013-03-11
FFmpeg will tag wma files with the *-metadata string=string* option. Having said that there are several different different types of wma and I have not tested them all :).

---

### Post by parminides on 2013-03-11
> **cortman said:**
> Isn't .wma a Microsoft proprietary format? I doubt you'll find anything for it for GNU/Linux.

Several of the gui tag editors claim they can work with wma files.

---

### Post by parminides on 2013-03-11
> **andrew.46 said:**
> FFmpeg will tag wma files with the *-metadata string=string* option. Having said that there are several different different types of wma and I have not tested them all :).

I don't have FFmpeg on my computer. I'd rather use something a little less bulky, if such a program exists. I might end up trying FFmpeg eventually. Thanks.

---

### Post by parminides on 2013-03-11
As a test, I assigned some tags to a wma file using Winamp in Windows. The audio player I use in Ubuntu (Clementine) wasn't able to read them. I assigned more tags with Windows Media Player and Clementine still couldn't read them. So perhaps Clementine doesn't read wma tags since it's Windows proprietary. Or perhaps the tagging features within Winamp and Windows Media Player aren't universal.

---

