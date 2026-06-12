---
title: "[SOLVED] hd 1080p x264 playback with mplayer"
date: 2008-10-25
forum: Multimedia Software
---

### Post by stefansjs on 2008-10-25
I really hope that somebody can clear up a number of questions I have about HD video playback.  I'll start by saying that I recently acquired a 1080p copy of several movies and they have a lot of trouble on my mythbuntu system.  I have no problem with 720p videos on the mythbuntu computer and when I play the 1080 files in windows on a different computer with slower hardware they run perfectly fine.  I've read many forums and found lots of questions with few solutions, so I hope this forum can answer some questions for me:

1) Is it possible to compile from source the newest x264 codec for use with mplayer?
2) Is it possible to compile from source mplayer itself
3) Will either of these improve performance of my video playback
4) Is there a way to tell mplayer to use both cores of my processor for decoding?
5) Is it true that linux does not have hardware acceleration for x264/h264?

I use mplayer without the GUI, so please provide answers that can be used from the terminal

thank you

---

### Post by cor2y on 2008-10-26
Your answers for questions 1,2,3 and 5 is yes.
Theres a how to in the How To/Guide section of the forums on how to compile mplayer with X264 support [http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)
The answer to question 4 is a maybe, why a maybe?
Because X264 development is always going on and if you want to always have the latest version you'll be updating and recompiling from the svn and combined with mplayer's svn there are sometimes conflicts.

Now for the hardware acceleration bit, yep none of that in Linux ***Yet*** AMD/ATI and the ATI  opensource guys are hard at work on getting this into the closed and open source drivers, they have made some progress but not enough to have anything ready for use by regular folk probably nothing that will be ready before summer of next year. So as of now you better have a midrange type system for 1080p playback even with custom compiled versions of mplayer and X264 you will still need a system with at least a 2.8ghz dual core cpu, a vid card with 128mb of ram and 1gb of ram note that even microsoft and Apple recommend 3ghz cpus for hidef 1080p playback, this was before all the fancy vid cards that have the ability to take the burden off the cpu and thats how you will have to treat your linux system regardless of how modern a vid card you have think of it when it comes to hidef video playback as still being either a Geforce 440 or ATI 9000, what matters here is how powerful the cpu is.

---

### Post by shirilover on 2008-10-26
For number 4 you can try adding -lavdopts fast:threads=2 to your mplayer command.

However, compiling x264 will not improve decoding of h.264 video, since x264 is an encoder.

---

### Post by stefansjs on 2008-10-26
Thank you both very much.  Your responses were very quick and very helpful.  I would just like one clarification.  > However, compiling x264 will not improve decoding of h.264 video, since x264 is an encoder.
I thought that x264 was just the open source version of h264 and that it was not a 1-way codec, but rather was used for encoding and decoding.  After all, if you encode with a different codec wouldn't you need that codec to decode?
thank you again

---

### Post by cor2y on 2008-10-26
libx264 is a decoder as well as an encoder, the same way libxvidcore is a decoder and encoder

---

### Post by WasMeHere on 2011-09-15
Thank you very much shirilover!

> **shirilover said:**
> For number 4 you can try adding -lavdopts fast:threads=2 to your mplayer command.

Your tip helped me getting 1080/50p video work flawlessly on an hp xw8400 workstation with 2 double zeon processors (4 cpu cores). It works well with 2 or 3 threads. This way mplayer works better than VLC with GPU enabled.
[U][http://ubuntuforums.org/showthread.php?t=1830231&highlight=hd+1080+video+crappy+hardware#6](http://ubuntuforums.org/showthread.php?t=1830231&highlight=hd+1080+video+crappy+hardware#6)
[/U]

---

